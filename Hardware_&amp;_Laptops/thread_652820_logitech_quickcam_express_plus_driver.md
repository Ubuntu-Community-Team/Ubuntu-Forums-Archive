---
title: "logitech quickcam express plus driver"
date: 2007-12-29
forum: Hardware &amp; Laptops
---

### Post by rrofes on 2007-12-29
hello all,

i am looking for the driver to make work the logitech quickcam express plus. Be aware it is the PLUS model.

Using the lsusb command, I see that I have:
Bus 001 Device 002: ID 046d:092f Logitech, Inc.

I have tried to compile the driver spca5xx from [http://mxhaard.free.fr/download.html](http://mxhaard.free.fr/download.html) but i get errors from the compiler. I would like to know if there is an easier solution like a driver already compiled for ubuntu.

thanks,

---

### Post by linuxwizard on 2007-12-29
You shouldn't have to do anything except plug that cam in and it should work. Have you tried using it with Camorama, Cheese, Ekiga ?

Even Skype shows it as Works out of the box.
[https://wiki.ubuntu.com/SkypeWebCams](https://wiki.ubuntu.com/SkypeWebCams)

---

### Post by rrofes on 2008-01-08
thanks,
I've tried cheese and camorama, they don't find the camera! it is plugged, the led is on and works ok with windows.
cheese says: unable to find a camera, sorry!
camorama says: could not connect to video device (/dev/video0)
I have skype for linux 2.0.0.27 installed, and also qt4, d-bus and libasound2 (all needed by skype)
any other idea?

---

### Post by rrofes on 2008-01-14
well, i have no answer... maybe i sould submit a bug...

---

### Post by linuxwizard on 2008-01-14
No it is not a bug. Everything that I come across shows that cam just works. When you tried to compile the driver something got messed up, which you didn't need to do because that driver is included in the Ubuntu kernel. Not sure what to tell you now. maybe recompile the driver. Or maybe someone else will answer that can help you more with this.

---

### Post by rrofes on 2008-01-15
Thnaks for your answer. Well, I have the feeling (but just a feeling!) that maybe nothing has been messed up when I tried to compile the driver, because the compilation was completely unsuccessful from the beguining. The compiler was not able to find some header files...
I will try to test the camera in other machine with ubuntu, but this will take me some days. If someone has more ideas to help...

---

### Post by daveofdave on 2008-01-21
Hi I've had the same issue  running the same cam on gutsy which irritated me somewhat as having had trouble with an old labtec webcam and failed to get it to function ,I bought this cam specifically because all the expert opinion said it would work  out of the box ! this is not true!
I have had some success getting it to function on skype by following the instructions posted here [http://ubuntuforums.org/archive/index.php/t-651375.html](http://ubuntuforums.org/archive/index.php/t-651375.html)  .But on camarama I only get a very poor b& w  picture and cheese just crashes the whole caboodle.
Can anyone  sort this

---

### Post by rrofes on 2008-01-21
great! that worked!

[http://ubuntuforums.org/archive/index.php/t-651375.html](http://ubuntuforums.org/archive/index.php/t-651375.html)

The main solution has been to install gspca-source package and after compile it.
It seems that gspca is not embedded in the ubuntu kernel or it doesn't work, at least with my camera.
Now I notice that the image is too dark (as other people found) but that's another problem that I will try to solve with indications found in the link above.
Thanks all!

---

### Post by daveofdave on 2008-01-21
Hi rrofes
I'm glad that worked for you, will the cam work with other progs ? -camorama, cheese  etc because mine doesn't and I would like to try and sort it If I can

---

### Post by rrofes on 2008-01-23
yes, now it works with skype, camorama and cheese
but i still have the dark image problem... i will try to solve it

---

