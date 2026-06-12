---
title: "Webcam has strange behaviour"
date: 2010-12-16
forum: Hardware
---

### Post by AngelDE98 on 2010-12-16
Hi to everyone . I had some problems already with my WLAN card but these WERE problems . My current problem ( and not my only one ) is my Webcam . If I start CAMORAMA it gets me just an ERROR that it could not be read . If I start it again it just could not find /dev/video0 ! If I do ```
sudo move /dev/video1 /dev/video0
``` or rename it with ```
sudo nautilus
``` then I get this error again or it works . And cheese has sometimes the problem that it can not find the whole device or just shows a black image . I already changed some configurations in ```
gstreamer-properties
``` ( I left them at end just as they were but the Device needs to be changed in Video Input ) but or it is not showing WebCam in the device list ( the Device needs to be named video1 to be shown or to work sometimes in cheese and this s**ks ) or just another ERROR. I heard about an Command to start camorama with loading /dev/video1 but cheese is changing the name from /dev/video0 to /dev/video1 and vice versa if it has an black image . This is just weird ... Can someone help me ? I think it is HARDWARE FAILURE but I had this feeling by my WLAN card too and it was SOFTWARE FAILURE . Thanks for any help . 

Special Information : 
Laptop : eMachines E525 ( No modified Hardware ) 
System : Ubuntu Desktop Edition 10.10 ( WIBU with BRUG NOT GRUB )
Main System ... emm ... Sub System : Windows Vista Home Basic ( Destroyed my Laptop serveral times )

---

### Post by IcarusR on 2010-12-16
First try googling the exact error you get.

Second rather than moving /dev/video0 why not create a softlink to /dev/video1

Start camorama forcing it to use video1

```
camorama -d /dev/video1
```

Try searching for your webcam details on the forum. 

Personally I use guvcview for webcam.

---

### Post by AngelDE98 on 2010-12-16
I did this command thing after I changed some settings again and cheese and camorama ... booth are currently working . I think tomorow it will come back . 
Tommorow I gonna start camorama in terminal to see the output . I did it one time ago but only remember something with unsuported buffers or buffers out of bounds .

---

### Post by AngelDE98 on 2010-12-17
My laptop is going me on nerves ... The webcam just works again ( just currenty ) ! At the beginning it had or a black screen or camorama could not find video1 ... but now it just works ! No other error ... If it comes back I will tell it . 

But I have just another Problem : 
Because I need this webcam for chatting and I have multiplie chat clients , it is working currently ( GOOD ) . But my Microphone is not working in Flash ( the settings Input volume bar is minimum ) ( BAD ) . It was a big problem as I got ubuntu the first time when I wanted to geh the Webcam work with the Microphone at same time . But now my Microphone strikes ! No error , just INPUT VOLUME BAR is 0 . I think I need to add that I tried the last stable release and the last beta release ... I think I just try the stable one again .

---

### Post by AngelDE98 on 2010-12-17
Webcam Bug back ! Now I just get some errors but other ones than the old back in my memories ... 

Camorama Output : 
```

(camorama:25718): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated
libv4l2: error dequeuing buf: Eingabe-/Ausgabefehler

```

Cheese Output : 
```

libv4l2: error dequeuing buf: Eingabe-/Ausgabefehler
libv4l2: error dequeuing buf: Eingabe-/Ausgabefehler
libv4l2: error dequeuing buf: Das Argument ist ungültig

```

Eingabe-/Ausgabefehler : INPUT-/OUTPUT ERROR
Das Argument ist ungültig : NOT VAILD ARGUMENT

I have german language and my translations are just above ... 

Hopefully it is no Hardware failure because sometimes if I " shake " my Monitor ( my Webcam is just another built-in Webcam in my Laptop ... ) it gets sometimes some white stripes . 

Thanks for any help .

Edit : After serveral restarts of cheese and camorama it finally launches my webcam . But I still think something is wrong . As you see libv4l2 probally I need a replacement for my Webcam ( Special Driver / Firmware ? ) .

---

### Post by IcarusR on 2010-12-17
You could try starting cheese from terminal like this

```
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so cheese 
```

But you say it works some times & not others. I wonder if it is a faulty webcam.
Can you borrow a usb webcam & see if that works ?

---

### Post by AngelDE98 on 2010-12-17
Umm ... this command gave me a FILE NOT FOUND . 

And I just installed my EyeToy webcam and it is working right . 

EDIT : It freezes sometimes so I need to restart CHEESE and in CHEESE CONFIGURATION this device is video2 and my builtin webcam video0 ... what is video1 ?

---

### Post by AngelDE98 on 2010-12-19
What is the modprobe for my Webcam ?

---

### Post by AngelDE98 on 2010-12-21
Nevermind ... Can someone help me with this : ```
gstreamer-properties-Message: Error running pipeline 'Video for Linux 2 (v4l2)': Der Versuch Videobilder von Gerät »/dev/video0« auszulesen schlug fehl. [gstv4l2bufferpool.c(573): gst_v4l2_buffer_pool_dqbuf (): /GstPipeline:pipeline0/GstV4l2Src:v4l2src1:
The buffer type is not supported, or the index is out of bounds, or no buffers have been allocated yet, or the userptr or length are invalid. device /dev/video0]

```

That is the latest ERROR from gstreamer-propereties ... 

And is there any alternative to Video 4 Linux ( v4l ) or v4l2 ?

---

### Post by AngelDE98 on 2010-12-22
First time I ever do this ... 

BUMP

---

### Post by AngelDE98 on 2010-12-23
BUMP 

Oh man ... I get soo much errors ... 3 topics already ...

---

### Post by AngelDE98 on 2010-12-23
Ok ... I found out that Cheese is starting with an black screen at special monitor angles ( degrees ) and if it started normally and I changed my monitor angle to an unsuported I get white stripes ... Why ? 

I still mark it as solved .

---

