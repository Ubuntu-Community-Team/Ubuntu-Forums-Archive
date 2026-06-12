---
title: "dual boot without boot menu? I want it hidden"
date: 2008-10-14
forum: General Help
---

### Post by mfaust731 on 2008-10-14
Ok, I have to use XP on my work laptop, but it KILLS me to use it at home.
I want to daul boot it with ubuntu however I would rather not have the boot menu pop up every time I boot up while on the job ;)

Is there anyway to dualboot w/o boot menu - like only boot ubuntu is the spacebar is held down ?

---

### Post by WWSmith36 on 2008-10-14
Yes you can boot without having the grub menu show.  You will just have to edit your /boot/grub/menu.lst file.

```
gksudo gedit /boot/grub/menu.lst
```

First uncomment the this line
#hiddenmenu
**hiddenmenu**

Change the default time **DO NOT SET IT TO ZERO**
timeout		10
**timeout         2**

Choose which entry boots by default 
default		0
**default         x**

where x is your winXP entry: Note grub counts the ¨title¨ entries.  First one is zero and then they increment +1 from there.

Hope this helps

---

### Post by earthpigg on 2008-10-14
you can turn the 30 second GRUB timer down to like 5 or 2 seconds.

```
sudo apt-get install bum
```

=)

---

### Post by drs305 on 2008-10-14
These settings can also be changed via a gui app called startup-manager so you don't have to manually edit menu.lst. There are lots of things you can safely tweak to suit your needs such as default OS, menu timeout, boot splash image, how many kernels to display, and more.

To install:
```
sudo apt-get install startupmanager
```
To use:
System, Administration, StartUp-Manager

To learn more:
Click this link: [StartUp-Manager]("http://ubuntuforums.org/showthread.php?t=818177")

---

### Post by earthpigg on 2008-10-14
> **drs305 said:**
> These settings can also be changed via a gui app called startup-manager so you don't have to manually edit menu.lst. There are lots of things you can safely tweak to suit your needs.

To install:
```
sudo apt-get install startupmanager
```
To use:
System, Administration, StartUp-Manager

To learn more:
Click this link: [StartUp-Manager]("http://ubuntuforums.org/showthread.php?t=818177")

ah, typo on my part above?

(at work, on windows computer... :) )

---

### Post by mfaust731 on 2008-10-14
if I use the hiddenmenu option, how do I select ubuntu?

---

### Post by drs305 on 2008-10-14
> **mfaust731 said:**
> if I use the hiddenmenu option, how do I select ubuntu?

Without intervention it would run whatever the default was. To view the grub menu, after you get your BIOS system beep, you would start hitting the ESC key and the grub menu should appear - if your timing is good ;-). Then you can select whichever setting you want.

That is why many recommend leaving the timeout to 1 or 2 so you can at least see it and hit ESC or tab to another choice during the boot.

---

