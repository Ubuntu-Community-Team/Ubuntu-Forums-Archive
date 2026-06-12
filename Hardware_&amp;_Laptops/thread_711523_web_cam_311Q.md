---
title: "web cam 311Q"
date: 2008-02-29
forum: Hardware &amp; Laptops
---

### Post by Angelo1982 on 2008-02-29
Hi, I am using ubuntu gutsy for a week now, And I can install my web cam genius 311q. If somebody can help me please!!!

---

### Post by linuxwizard on 2008-02-29
What have you tried or used  to get your webcam working ? Did you install any drivers ?  Try using Ekiga see if the cam works/detected. You may have to work with the settings > Open Ekiga > Edit > Preferences > Video > Video Devices > try changing some of the settings. If that does not work post results of the command > lsusb

---

### Post by Angelo1982 on 2008-03-01
Hi, I tried eking but did not detected the web cam. I also tried CAMORAMA and this error message appears COULD NOT CONNECT TO VIDEO DEVICE (/dev/video0) PLEASE CHECK CONNECTION. I also tried to install Easycam like this
deb [http://blognux.free.fr/debian](http://blognux.free.fr/debian) unstable main  (I found that command in another forum) but this happend
angelo@angelo-laptop:~$ deb [http://blognux.free.fr/debian](http://blognux.free.fr/debian) unstable main
bash: deb: orden no encontrada ( unable to find the order or something like that as you can see my ubuntu is in Spanish).

I haven tried anything else, I can find the drivers, using the Ekinga I also notices that my mic is not detecter either, I am using a Lenovo 3000 N100. The sound is perfect, but no mic ,no cam. Thank you.

---

### Post by linuxwizard on 2008-03-01
post results of the command > lsusb

---

### Post by Angelo1982 on 2008-03-02
Hi, when I try the command you told me this is what happens 

angelo@angelo-laptop:~$ lsusb
Bus 005 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 0458:7025 KYE Systems Corp. (Mouse Systems) 
Bus 002 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 0a5c:2101 Broadcom Corp. 
Bus 001 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 08ff:2580 AuthenTec, Inc. 
Bus 003 Device 001: ID 0000:0000  
angelo@angelo-laptop:~$

---

### Post by linuxwizard on 2008-03-02
No webcam listed. Make sure cam is plugged in or try another USB port. Than post results again.

---

### Post by Angelo1982 on 2008-03-02
I tried the 4 usb ports my laptop has and the same thing happend. I am  trying to find the drivers for the cam so I can use it. Thank you..

---

### Post by linuxwizard on 2008-03-02
Your system is not recognize your cam. Even if you knew which driver you need for your webcam it is not going to work.

---

### Post by Angelo1982 on 2008-03-02
Well, thank you... do you know any cam who work right out the box with ubuntu?

---

### Post by linuxwizard on 2008-03-02
This is a good list to start with > [http://mxhaard.free.fr/spca5xx.html](http://mxhaard.free.fr/spca5xx.html). Alot of Logitech just works. I have Logitech Quickcam Chat which just worked, didn't do anything just plugin ready to go. The only issue I have is make sure it gets enough light to the cam or the colors don't look right.

---

### Post by Angelo1982 on 2008-03-04
Hi, thank you for the recommendation. But I have one more question. Right now I am using WinXp, and I notice, that when I plug in the cam, the "on" light does not light until I actually use the cam. But in ubuntu the "on" light does light (am sorry for writing like this English is not my native languages and some times is hard) as soon as I plug it. what does that mean? 

One more thing, I know you probably can´t answer me but I´ll try. The mic on my laptop in not recognize it can you help me please?. Thank you very much.

---

### Post by linuxwizard on 2008-03-05
Look over these they may help.

[https://help.ubuntu.com/community/AudioCapture](https://help.ubuntu.com/community/AudioCapture)

[http://ubuntuforums.org/showthread.php?t=385739&highlight=HOWTO+microphone](http://ubuntuforums.org/showthread.php?t=385739&highlight=HOWTO+microphone)

---

### Post by Angelo1982 on 2008-03-05
Thank you very very much!!! the links work great for the mic specially the second one!! thank you very much!!!

---

### Post by linuxwizard on 2008-03-05
You're Very Welcome I am glad the links helped you and your mic is working.

---

