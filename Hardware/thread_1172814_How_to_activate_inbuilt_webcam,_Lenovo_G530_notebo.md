---
title: "How to activate inbuilt webcam, Lenovo G530 notebook"
date: 2009-05-29
forum: Hardware
---

### Post by snej on 2009-05-29
G'day,
 
With my Lenovo 3000 G530 4446-25M notebook I am struggling to get the inbuilt webcam to work in Ubuntu 9.04. All my research on the web so far did not lead to any success. I have tried to set it up with EsayCam2 and run it with Ekiga and Cheese. All I get is error messages or the "bouncing ball". EasyCam2 just terminates the set-up with no effect (and it does not give me any useful error message either). I am using the "qt" version of EasyCam2.
 
From searching various forums I have retrieved the following information about my system:
 
```
 
~$ lsusb
...
Bus 002 Device 003: ID 5986:0205 Acer, Inc 
...
~$ dmesg | grep uvc
[   10.186065] uvcvideo: Found UVC 1.00 device Lenovo EasyCamera (5986:0205)
[   10.188110] usbcore: registered new interface driver uvcvideo
[  537.431659] uvcvideo: Failed to query (130) UVC control 1 (unit 0) : 2 (exp. 26).
~$ 
```
 
Also, according to this source ([http://linux-uvc.berlios.de/](http://linux-uvc.berlios.de/)) the webcam, being a UVC device, should work without having to install any UVC kernel driver (which is included in Linux 2.6.26 and newer, and Jaunty comes with 2.6.28-11 generic).
 
The camera works under XP.
 
Is there anyone with the same notebook or webcam model who managed to bring it to life? Any help is highly appreciated.

---

### Post by snej on 2009-06-02
Something really strange happened today. Without having touched the notebook for the last few days the webcam worked when I started Ekiga. I was even able to make adjustments to the image parameters (colours, brightness, size etc).
 
But I still do not get anything from Cheese. Just a test screen with coloured bands and noise pattern.
 
Can anyone explain this? My only explanation for this is that something must have changed. And the only thing I did last time was trying some of the commands such as lsusb and dmesg.
 
I would still like to hear from you if there is a solution to make this webcam operate without any limitations.

---

### Post by snej on 2009-06-04
I am puzzled. This time I definitely did not change anything between yesterday and today. But today Cheese and even VLC gave me a video image from my webcam! No mirror image or upside-down effects either.
 
The notebook was not even connected to the internet. Therefore it is not a possibility for drivers or updates to have been installed. I am lost for explanations but happy for now. :)
 
Anyone make any sense out of this?

---

### Post by lht4512 on 2009-06-07
I bought the same laptop and have the same problem trying to make the webcam work, I went to Lenovo website and download the driver software, just follow this link below
 
[http://consumersupport.lenovo.com/en/DriversDownloads/drivers_show_213.html](http://consumersupport.lenovo.com/en/DriversDownloads/drivers_show_213.html)#, the name of the driver is LN1CAM6WW3, I haven't install it yet  because i don't have my G530 laptop with me.  You can try to install it to see if you have any luck, let me know.  I ll install it once i have it with me.
 
[EMAIL="LHT4512@YAHOO.COM"]LHT4512@YAHOO.COM[/EMAIL]

---

### Post by snej on 2009-06-08
I am not sure if this would work since it is a driver for Vista.
 
As I said in my previous post the camera seems to work now with some "erratic" behaviour. I will keep observing.
 
Unfortunately, I can not really tell you - lht4512 - what exactly I did to make it work. Maybe some of the auto-updates fixed it?
 
Let me know how you go.

---

### Post by gerryg001 on 2009-09-27
Lenovo 3000 G530 4446-36U with Hardy 8.04
lsub
Bus 008 Device 002: ID 090c:3371 Feiya Technology corp
dmesg | grep uvc
uvcvideo: Found UVC 1.00 device Lenovo EasyCamera
usbcore: registered new interface driver uvcvideo

So, I didn't get your failure. However, if I run cheese the screen goes black after a few seconds, and Xorg runs 100% cpu. They are also discussing cheese problems at
[https://bugs.launchpad.net/ubuntu/+source/cheese/+bug/254235]("https://bugs.launchpad.net/ubuntu/+source/cheese/+bug/254235")

---

### Post by deyoungaza on 2009-11-02
Lenovo G550. Jaunty 9.04.

Same thing here. It didn't work after a installing Jaunty on my new laptop. After a few days, it just started working with Cheese & Ekiga.  I installed Jaunty twice on this laptop (I messed up an upgrade to Karmic and reinstalled Jaunty), and this happened both times.

Go figure.

---

### Post by snej on 2009-11-20
I just wanted to give you an update and let you know what I believe fixed my problem. 

Trying to recap what happened I believe the webcam stopped working all of the sudden as soon as a new kernel was installed. If the old kernel version (where the cam worked) is started from Grub the cam still works.

After I had given up on the webcam for some time I tried to make it run again (in the meantime using kernel version 2.6.28-16) and it worked after following the advise in this post: [http://ubuntuforums.org/showpost.php?p=6292874&postcount=8](http://ubuntuforums.org/showpost.php?p=6292874&postcount=8)

So after all I am happy now with how things work. :p

---

### Post by ariscanete on 2009-12-12
Guys,

I think your Ubuntu Linux must have updated its support driver database for your webcam....just keep on doing that online update.  You didn't manually update its system because the Ubuntu itself is automatically monitoring online and update it...

---

