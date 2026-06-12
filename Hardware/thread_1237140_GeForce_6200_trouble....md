---
title: "GeForce 6200 trouble..."
date: 2009-08-11
forum: Hardware
---

### Post by ScarletWyvern on 2009-08-11
Before I begin, I'd just like to make it clear that I'm pretty new to Linux. The most advanced thing I've done so far (where I've actually understood what I'm doing completely) is install a program from a .tar.gz. If something I say sounds like it doesn't make any sense, it's probably because I have no idea what I'm talking about.

 Anyway, I installed Ubuntu on an older computer I have, and it was running fine. I have a Nvidia GeForce 6200. I tried to enable desktop effects, but I couldn't. I forget the exact error, but I hit up Google, and I wound up downloading drivers from the repository.  Well, I rebooted my computer, and it told me that it had "Failed to initialize the NVIDIA kernel module," and that it was going to boot into low-graphics mode. 

I downloaded the official driver from Nvidia's website, and I tried to install it.  It told me that I had an X server running, and that I needed to exit X.  I had (and still really have) no idea what that means. I've been Googling for hours, now. After doing some stuff involving Ctrl+Alt+F1, killing the GNOME Desktop Environment, and something with init 3, I managed to get the driver installer to work. 

It told me there it had to compile something with the kernel, because one didn't exist, and it couldn't connect the the Nvidia FTP. In the end, it said the installation was successful.  

Upon restarting the computer, it gets to the screen with the loading bar and the Ubuntu logo. When the bar is almost full, it switches to text, the last entry being "Checking Battery State... [OK]." Then, it give me the familiar, "Failed to initialize the NVIDIA kernel module."  

My question is: What in God's name do I have to do? My Google-Fu is all but empty...  

If you guys need logs or something, I'd be more than happy to put out, if you explain to me how to get them. >___>

EDIT: I disabled the Version 180 driver that I got from the repository... The computer starts without errors, now. I really would like to get desktop effects working though...

---

### Post by ViperChief on 2009-08-11
Personally, I probably would uninstall all the nVidia drivers. Then, make sure you have the kernel source installed, and re run the script from nVidia. That's how I usually install my video drivers. I think I have the same card as you...either that or a 6600. Whenever I follow the directions for that manual install, it works pretty well.

---

### Post by stewie17 on 2009-09-12
> **ScarletWyvern said:**
> Before I begin, I'd just like to make it clear that I'm pretty new to Linux. The most advanced thing I've done so far (where I've actually understood what I'm doing completely) is install a program from a .tar.gz. If something I say sounds like it doesn't make any sense, it's probably because I have no idea what I'm talking about.

 Anyway, I installed Ubuntu on an older computer I have, and it was running fine. I have a Nvidia GeForce 6200. I tried to enable desktop effects, but I couldn't. I forget the exact error, but I hit up Google, and I wound up downloading drivers from the repository.  Well, I rebooted my computer, and it told me that it had "Failed to initialize the NVIDIA kernel module," and that it was going to boot into low-graphics mode. 

I downloaded the official driver from Nvidia's website, and I tried to install it.  It told me that I had an X server running, and that I needed to exit X.  I had (and still really have) no idea what that means. I've been Googling for hours, now. After doing some stuff involving Ctrl+Alt+F1, killing the GNOME Desktop Environment, and something with init 3, I managed to get the driver installer to work. 

It told me there it had to compile something with the kernel, because one didn't exist, and it couldn't connect the the Nvidia FTP. In the end, it said the installation was successful.  

Upon restarting the computer, it gets to the screen with the loading bar and the Ubuntu logo. When the bar is almost full, it switches to text, the last entry being "Checking Battery State... [OK]." Then, it give me the familiar, "Failed to initialize the NVIDIA kernel module."  

My question is: What in God's name do I have to do? My Google-Fu is all but empty...  

If you guys need logs or something, I'd be more than happy to put out, if you explain to me how to get them. >___>

EDIT: I disabled the Version 180 driver that I got from the repository... The computer starts without errors, now. I really would like to get desktop effects working though...


I'm having a similar problem. I had a few wallpapers that I was trying out and everything was going fine. Then, just yesterday, I decided to change the one I have now. Instead, I got an error saying my "graphics driver does not support the necessary extensions to use this tool".
[IMG]http://picasaweb.google.com/lh/photo/r7cVVa0Gi9XYBiyZKAidxg?feat=directlink[/IMG][IMG]http://picasaweb.google.com/lh/photo/r7cVVa0Gi9XYBiyZKAidxg?feat=directlink[/IMG][IMG]http://picasaweb.google.com/lh/photo/r7cVVa0Gi9XYBiyZKAidxg?feat=directlink[/IMG][IMG]http://picasaweb.google.com/lh/photo/r7cVVa0Gi9XYBiyZKAidxg?feat=directlink[/IMG]
Now I cannot figure out what to do. I thought it might have something to do with some other app I had installed, but when I reinstalled "jaunty" I still had the problem.

---

