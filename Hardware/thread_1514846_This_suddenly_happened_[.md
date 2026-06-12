---
title: "This suddenly happened :["
date: 2010-06-21
forum: Hardware
---

### Post by guyshoxton on 2010-06-21
Mouse + track pad stopped working
I have been using Ubuntu for 1 year now, ive used Ubuntu 9.04, 9.10, and 10.04.
Suddenly, on friday (friday the 18th) My mouse AND track pad stopped working, only the right click button worked (im right handed)...
And now i tried re installing ubuntu 10.04 three times on my harddrive, and still, the button worked but after about 10 minutes or so the left click (reminder: i am right handed) button stops working =(

---
i tried to install ubuntu 9.10, installed perfect but the mouse wouldnt work (and the track pad didnt work either...

I then erased my harddrive (completely) and removed the operating system from it... and then i installed ubuntu 9.10 and now from it im upgrading to ubuntu 10.04....

--
im using it while its updating... my mouse stopped working!!! and i some how got to open firefox, and im using the "tab" key + enter key to get around this website =[

SOME ONE PLEASE HELP!

---

### Post by prylux on 2010-06-21
This happened to me after an update from Kernel 2.6.32-21 to 2.6.32-22
I had to go back to the older kernel and now everything works.

(I am assuming you know that [ALT+F1] gets you into the menu to select programs)

To check your kernel version input this in a term:
[INDENT]echo `uname -r`[/INDENT]
The (`) is on the tilde key (~)

If your running 2.6.32-22 you can open Synaptic and search for
[INDENT]linux image 2.6[/INDENT]
Look for 2.6.32-21 generic and click it and mark it for installation.
Do not remove any kernels at this time.

Restart your computer and hold down the [SHIFT] key while starting up, this will allow you to select the kernel with grub.

If everything works then you can go back into Synaptic and do the same search and mark the 2.6.32-22 generic kernel for removal.

Also make sure your automatic updates are set to notify and not to install.

Let us know if this worked...

---

### Post by dabl on 2010-06-21
If it turns out that the problem is not solved with an older kernel, as prylux suggested, then I think maybe it is a hardware problem in your computer (not the OS).

You said you used 9.10 before and it worked correctly, but now it fails with 9.10 running.  That suggests the problem is not the OS.

---

### Post by guyshoxton on 2010-06-21
> **prylux said:**
> This happened to me after an update from Kernel 2.6.32-21 to 2.6.32-22
I had to go back to the older kernel and now everything works.

(I am assuming you know that [ALT+F1] gets you into the menu to select programs)

To check your kernel version input this in a term:
[INDENT]echo `uname -r`[/INDENT]
The (`) is on the tilde key (~)

If your running 2.6.32-22 you can open Synaptic and search for
[INDENT]linux image 2.6[/INDENT]
Look for 2.6.32-21 generic and click it and mark it for installation.
Do not remove any kernels at this time.

Restart your computer and hold down the [SHIFT] key while starting up, this will allow you to select the kernel with grub.

If everything works then you can go back into Synaptic and do the same search and mark the 2.6.32-22 generic kernel for removal.

Also make sure your automatic updates are set to notify and not to install.

Let us know if this worked...
will this work with Ubuntu 10.04 LTS ? i currently have 9.10 but am installing 10.04, and im writing from my iPod =P

And thank you!

---

### Post by guyshoxton on 2010-06-21
> **prylux said:**
> This happened to me after an update from Kernel 2.6.32-21 to 2.6.32-22
I had to go back to the older kernel and now everything works.

(I am assuming you know that [ALT+F1] gets you into the menu to select programs)

To check your kernel version input this in a term:
[INDENT]echo `uname -r`[/INDENT]
The (`) is on the tilde key (~)

If your running 2.6.32-22 you can open Synaptic and search for
[INDENT]linux image 2.6[/INDENT]
Look for 2.6.32-21 generic and click it and mark it for installation.
Do not remove any kernels at this time.

Restart your computer and hold down the [SHIFT] key while starting up, this will allow you to select the kernel with grub.

If everything works then you can go back into Synaptic and do the same search and mark the 2.6.32-22 generic kernel for removal.

Also make sure your automatic updates are set to notify and not to install.

Let us know if this worked...
i am running 2.6.31-14-generic <-- thats why my mouse and track pad wont work?

---

### Post by prylux on 2010-06-24
> i am running 2.6.31-14-generic <-- thats why my mouse and track pad wont work? 

Based on the information in your first post I thought this could be a solution to check not a definite answer. It could be a hardware issue like *dabl* said, though if both your trackpad and mouse is not working then I personally think it is some configuration getting mucked up. 

But I am saying this without knowing the hardware your running ubuntu on.

I have also had a problem with a mouse and it turned out to be something Very Simple (took me two or three days to figure it out, AFTER I already tried a bunch of complicated things #-o) [http://ubuntuforums.org/showthread.php?t=1512841]("http://ubuntuforums.org/showthread.php?t=1512841")

Could you post some more information on your hardware it might help...

I'm not an expert on all things Linux but I'm pretty good and willing to try and help you find a solution...:)

---

### Post by guyshoxton on 2010-06-24
> **prylux said:**
> Based on the information in your first post I thought this could be a solution to check not a definite answer. It could be a hardware issue like *dabl* said, though if both your trackpad and mouse is not working then I personally think it is some configuration getting mucked up. 

But I am saying this without knowing the hardware your running ubuntu on.

I have also had a problem with a mouse and it turned out to be something Very Simple (took me two or three days to figure it out, AFTER I already tried a bunch of complicated things #-o) [http://ubuntuforums.org/showthread.php?t=1512841]("http://ubuntuforums.org/showthread.php?t=1512841")

Could you post some more information on your hardware it might help...

I'm not an expert on all things Linux but I'm pretty good and willing to try and help you find a solution...:)

well how come i had ubuntu 10.04 and it worked, then i decided to re install, and it suddenly didnt work. 0_0

how do i get my hardware info to give you?

i know i have a t-series gateway laptop.

---

### Post by lidex on 2010-06-25
Are you currently using lucid or karmic? If lucid then you should be using 2.2.32.xx kernel not 31. Try this:
```
sudo apt-get update
sudo apt-get upgrade
sudo update-grub
```
Now **reboot**.
Check kernel version:
```
uname -a
```

---

### Post by guyshoxton on 2010-06-26
2.6.32-21-generic <-- I use Lucid and that is my kernel verson.

---

### Post by guyshoxton on 2010-06-26
> **lidex said:**
> Are you currently using lucid or karmic? If lucid then you should be using 2.2.32.xx kernel not 31. Try this:
```
sudo apt-get update
sudo apt-get upgrade
sudo update-grub
```
Now **reboot**.
Check kernel version:
```
uname -a
```

i use lucid and this is my kernel version... 2.6.32-21-generic

---

### Post by JlyGrnMigt on 2010-06-30
I don't think this is hardware.  This has come up on the forums without a solution a number of times, and each time I see a post a person has a different computer.  I'm still using 9.10 on a Zareason Terra, and have been looking for a solution since March (intermittently...).  Someone mentioned that it was a problem with the synaptics driver, but gave no info on where the correct driver was to be found.

My kernel: 2.6.31-22-generic

For a hopefully temporary workaround, I plug in a USB mouse before starting up, and disable the touchpad immediately.  If I forget to do that and accidentally brush the touchpad, all of the weird problems come back and my usb mouse is as useless as the touchpad.  I'm going to reboot and try the older kernel with the mouse unplugged.

---

### Post by lidex on 2010-06-30
Check your logs.
```
cat /var/log/Xorg.0.log
cat /var/log/syslog
cat /var/log/messages
cat /var/log/user.log
```

---

### Post by macogw on 2010-07-02
Any of you considered filing a bug on the Synaptics driver?
```
ubuntu-bug xserver-xorg-input-synaptics
```

---

