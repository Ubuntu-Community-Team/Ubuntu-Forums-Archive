---
title: "Err: Screen(s) found but none have a usable configuration"
date: 2007-07-26
forum: Hardware &amp; Laptops
---

### Post by benny@linux on 2007-07-26
hello all , 
i am just installed ubuntu fiesty on my new ex600 msi notebook 
but have to do it from safe graphics mode cause when tried to load normally i got the err ive mention on the title 

after installetion the linux came up like in safe mode :
Resolution 800x600 and no 3d support (main resulution should be 1280x800 as its a wide 15.4 screen)

i have an 8400g m graphic card (nvidia geforce) 
so ive install all the updates 
and download the latest driver from nvidia site , it said to support my hardware
and after installetion i got the same error again 
so i went over and restore xconf.org and write this messege .. 
also tried to install nvidia-glx-new with no use.. 

any one have a solution?

---

### Post by benny@linux on 2007-07-26
anybody? ?

---

### Post by benny@linux on 2007-07-26
up

---

### Post by DeltaZero on 2007-07-26
I've had the same problem when I installed NVIDIA drivers on my GeForce6800GS. In the end I have just given up, using standard nv drivers.
One thing you can try is look up vertical and horizontal refresh rates for your screen and edit /etc/X11/xorg.conf accordingly. It allowed me to use 1280x1024 with the stock nv driver at least...

---

### Post by benny@linux on 2007-07-26
you think that this is only tempotary problem or that no one is working on a solution?

---

### Post by benny@linux on 2007-07-27
but even nv not working for me :(

---

### Post by DeltaZero on 2007-07-27
Did you change the refresh rates like I told you?

---

### Post by benny@linux on 2007-07-27
> **DeltaZero said:**
> Did you change the refresh rates like I told you?

yep ,didn't help thu...

---

### Post by Nicolae on 2007-07-27
I had a similar problem; I ended up having to unload and reload the nvidia module after every reboot:

sudo rmmod nvidia
sudo modprobe nvidia
sudo /etc/init.d/gdm restart

It worked for me. I ended up just using the drivers in the official repos and it worked fine, but I don't know if that version supports your card or not.

---

### Post by benny@linux on 2007-07-28
didnt help either - said : nvidia module not found

---

### Post by benny@linux on 2007-07-30
up

---

### Post by Yuri77 on 2007-08-05
I have the same notebook, and managed to install the drivers with this link:
[http://www.nvnews.net/vbulletin/showthread.php?t=72490](http://www.nvnews.net/vbulletin/showthread.php?t=72490)
Now it works OK.

---

### Post by benny@linux on 2007-08-07
yuri77

Your The Best - Its Worked!!! 
Thank You Very Much!!!!!!!!!!=D>=D>=D>=D>=D>

---

### Post by Zheng on 2007-09-03
I have ASUS W7S white laptop with Nvidia 8400G M card same as you, I was able to get all the following hardwares to work (not working perfectly though).

1. Nvidia 8400M G (Working, but poor performance with Beryl)
2. Bluetooth (Only tried to connect to my Bluetooth mouse and its working)
3. Webcam (upsided- down image)
4. Built-in Audio - Working perfectly!
5. WiFi lan (Intel 4965 WiFI Link AGN) - Working perfectly!
6. Synaptics Touchpad (Scrolling function not working after I installed all the hardware drivers)

Here is the suggestion for your video card:
download & install Envy to install nVidia driver, then use nVidia settings program to configure your display properly (1280x800 resolution)  

Just dig & follow the nVidia card installation guide in the forum search, then you will be done with your card. Good luck!

---

