---
title: "Ways to conserve battery on my laptop."
date: 2009-01-08
forum: Hardware
---

### Post by studentidiot on 2009-01-08
Is there anyway to conserve battery on my Vaio FZ340E/b in Ubuntu 8.10?

I only get about 40 minutes of battery, and an hour tops. Compare that to Vista where I can get about 2-2.5 hours of battery and four hours tops with advanced power saving features.

To make matters worse the backlight is stuck on highest.

There doesn't seem to be much, if any, power saving options for Ubuntu users using laptops. 

What can I do to increase battery life?

---

### Post by Amerinidiot1231 on 2009-01-09
I as well experience much shorter battery life on my inspiron 1525.  

As far as your lack of dimming try going to System--> Preferences --> Power management.  Under the battery tab the option to dim on battery power is there.  If not try Fn + down to dim the screen manually.

Vista can reduce the speed of the processor to greatly reduce power consumption.  Im not sure if ubuntu supports this or not.

---

### Post by studentidiot on 2009-01-09
> **Amerinidiot1231 said:**
> I as well experience much shorter battery life on my inspiron 1525.  

As far as your lack of dimming try going to System--> Preferences --> Power management.  Under the battery tab the option to dim on battery power is there.  If not try Fn + down to dim the screen manually.

Vista can reduce the speed of the processor to greatly reduce power consumption.  Im not sure if ubuntu supports this or not.

Unfortunately that doesn't work, either. Ubuntu is totally incabapible of changing the brightness at all. Hopefully, this will be fixed in a year or two.

---

### Post by Amerinidiot1231 on 2009-01-09
You could try to reinstall ubuntu, if you havnt already.  Several times that has fixed issues I have had.

---

### Post by sdennie on 2009-01-09
Though not specific to your laptop, this thread contains a lot of tricks to increase battery life: [ HOWTO: XPS m1330 power savings]("http://ubuntuforums.org/showthread.php?t=847773")

---

### Post by iggykoopa on 2009-01-09
you could also look into the power management gui I'm working on here [http://ubuntuforums.org/showthread.php?t=988309&page=1](http://ubuntuforums.org/showthread.php?t=988309&page=1) . Just follow the installation instructions and when it's installed left click the icon in your system tray and enable any options you want, the defaults are safe but won't save you as much power.

---

### Post by studentidiot on 2009-01-09
Thats that GUI your working on looks promising.

Why doesnt Ubuntu have advanced power management in it??

Isn't that pretty important?

---

### Post by iggykoopa on 2009-01-09
There is pretty advanced powermanagement built in, there just isn't an easy way to access it. Thats why I'm trying to work on the gui, give it a try and if you have any problems let me know in it's thread.

---

### Post by hasi63 on 2009-03-19
Hi,
I also own a sony laptop (Vaio vgn-fz21s) and until recently wasn't able to control the brightness of the screen. It has an Nvidia geforce 8400m GS graphic card. 
I have found a solution to this problem: use the new NVCLOCK 0.8 from [http://www.linuxhardware.org/nvclock/#download](http://www.linuxhardware.org/nvclock/#download).
If you want installable packages (deb) you can find them on:
[http://kanotix.com/files/thorhammer/updates/nvclock/](http://kanotix.com/files/thorhammer/updates/nvclock/)
Just download     nvclock_0.8b4-0_i386.deb  and smartdimmer_0.8b4-0_i386.deb and install both packages. 
Using either one from terminal you can control your screen brightness. This can conserve much of your battery and your eyes.
Hope this helps a bit. Hasi63

---

### Post by Leviathan433 on 2009-03-19
What about spinning down your hard drive?

---

