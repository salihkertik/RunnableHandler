# RunnableHandler

Basic Project - Learning Process

Bu projede Runnable ve Handler kullanarak bir geri sayım uygulaması yaptım.

In this project, I made a countdown application using Runnable and Handler.

# Projenin genel kodları aşşağıdaki gibidir;

Tanımladığımız nesneler ve değişkenler(
TextView textView;
    Runnable runnable;
    int number;
    Handler handler;
    Button button; )

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        textView = findViewById(R.id.textView);
        button = findViewById(R.id.button);
        number=0;
    }

    public void start (View view)
    {
        handler=new Handler(); // run metotumuzu ayarladıktan sonra handlerın içerisinden runnable'ı çağıracağımız için böyle bir nesne oluşturuyoruz.

        runnable=new Runnable() //runnable metotu oluşturunca altta hazır override methodunu bize sağlıyor.
        {
            @Override
            public void run()   // hazır gelen metotumuzun içine gereken bilgileri yazıyoruz.
            {
                textView.setText("Time: " + number);
                number++;
                textView.setText("Time: "+number);
                handler.postDelayed(runnable, 1000); // runnable'ı her 1 saniye de bir çalıştır.
            }
        };

        handler.post(runnable);   // handler'ın içerisinde runnable'ı çağırıp ele alıyoruz.
        button.setEnabled(false); // start'a bastığımız andan itibaren butonu tıklanmaz yapıyoruz.
    }

    public void stop (View view)
    {
        button.setEnabled(true); // stop tuşuna bastıktan sonra start tuşunu aktif hale getiriyoruz.

        handler.removeCallbacks(runnable); // runnable'ı kapat diyoruz.
        number = 0;
        textView.setText("Time: "+number); // Time'ı 0 a tekrar döndürüyoruz.
    }
    
    
# Kullandığım Kütüphaneler;
~import androidx.appcompat.app.AppCompatActivity;

~import android.os.Bundle;

~import android.os.Handler;

~import android.view.View;

~import android.widget.Button;

~import android.widget.TextView;
