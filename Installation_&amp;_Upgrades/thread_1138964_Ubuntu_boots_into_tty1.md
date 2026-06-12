---
title: "Ubuntu boots into tty1"
date: 2009-04-26
forum: Installation &amp; Upgrades
---

### Post by R4P7UR3 on 2009-04-26
My Ubuntu seems to be booting to tty1 and opening a terminal...

From there I cant really do anything since I'm not very familiar w/ ubuntu and its commands.

I've read in some threads about pressing [ctrl+alt+F7] to get into tty7(?) I guess for some reason I thought that would fix it. All it seems to do though is put a little blinking underscore on my screen like I'm supposed to type something in. But when I just press random buttons to see if its supposed to do something, nothing shows up on screen.

Does anyone know what I'm possibly doing wrong or whats wrong w/ Ubuntu.

I honestly don't think it's Ubuntu, that its more along the lines of some of my hardware because this problem occurs w/ fresh installs of 8.10, 9.04 and Kubuntu 9.04.

It's almost like the Graphical Interface itself itsn't booting since it's only a terminal.



Sry, I'm a Linux Nub.

-Rapture

---

### Post by lisati on 2009-04-26
How did you install Ubuntu - from a "LiveCD" or from an "alternate" installer disk?
Did you accidentally install the server edition?

---

### Post by R4P7UR3 on 2009-04-26
I installed from the LiveCD on all occasions and I'm positive it wasnt the server editions.

---

### Post by shecky on 2009-04-26
What happens when you type startx into tty1?

---

### Post by R4P7UR3 on 2009-04-26
> **shecky said:**
> What happens when you type startx into tty1?

Okay I'm looking at the screen now (posting from my lappy) I'll type everything I see.

"Boot from (hd1,0) ext3    88460464-6957-4385-812c-12f72c34459f
Starting up...
[     1.032446] ACPI: Expecting a [Reference] package element, found type 0
Loading, please wait...
usplash : Setting mode 1152x864 failed
usplash: Using mode 1024.768
19+0 records in
19+0 records out
kinit: name_to_dev_t(/dev/disk/by-uuid/04b17dd0-01e0-4625-8898-4ca58965d622) = dev(8,5)
kinit trying to resume from /dev/disk/by-uuid/04b17dd0-01e0-4625-8898-4ca58965d622
kinit: No resume image, doing normal boot...
Ubuntu 9.04 "rapture-desktop" tty1"

Okay when I type startx in I get this long error that after says "Fatal server error: no screens found" and about consulting wiki.x.org


Also says
"ddxSigGiveUp: Closing log
giving up.
xinit No such file or directory (errno2): unable to connect to X server
xinit: No such process (errno3): Server error.

---

### Post by R4P7UR3 on 2009-04-26
I was just staring at my screen again and noticed before it says that Fatal server error it says

(==) Log file: "var/log/Xorg.0.log", Time: Sin Apr 26 17:33:32 2009
(==) Using config file: "/etc/X11/xorg.conf"
(EE) No devices detected.


Hope this helps somehow.

-Rapture

---

### Post by shecky on 2009-04-26
You could try to manually configure X with:
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by R4P7UR3 on 2009-04-26
> **shecky said:**
> You could try to manually configure X with:
```
sudo dpkg-reconfigure xserver-xorg
```

Okay, I did that. It doesnt seem to have done anything. I still get that same error after the config.

Thanks though, any other suggestions?

---

### Post by igorc on 2009-04-26
The kinit error is not really an error but info message which means the pc/laptop tried to boot from hibernation but couldn't find the image file. You can disable this by putting "noresume" (without quotas) after "ro quiet splash" or what ever you have in the kernel line in the grub menu.lst file.

What do you have connected to the PC, is it an LCD screen, CRT monitor or a TV maybe? What kind of graphic card you have? Both ATI ( even command line owns like aticonfig e.g.) and Nvidia have there own config tools for their drivers so you can try them instead to get initial xorg.conf file.

---

### Post by R4P7UR3 on 2009-04-27
> **igorc said:**
> The kinit error is not really an error but info message which means the pc/laptop tried to boot from hibernation but couldn't find the image file. You can disable this by putting "noresume" (without quotas) after "ro quiet splash" or what ever you have in the kernel line in the grub menu.lst file.

Okay I tried this but it didnt seem to have any affect to my problem. It's still putting me into the display manager. I'm not sure if inserting that was supposed to solve my problems (my guess is it wasnt) but I think we're getting closer to the solution at least. xD

> **igorc said:**
> 
What do you have connected to the PC, is it an LCD screen, CRT monitor or a TV maybe? What kind of graphic card you have? Both ATI ( even command line owns like aticonfig e.g.) and Nvidia have there own config tools for their drivers so you can try them instead to get initial xorg.conf file.

I have a LCD Monitor connected to my computer and I'm SLI'ing Nvidia cards. Do you happen to know which of these commands could possibly get me out of this if indeed it is a video card issue. They're 9800 GT's btw.

I took a picture of the screen I get every time I boot up kubuntu. I hope it helps somehow.[IMG]http://i269.photobucket.com/albums/jj47/fallenxsniper/0427091745a.jpg[/IMG]

---

### Post by jonboy99 on 2009-04-29
Hi mate i've also had this issue after upgrading ubuntu, and have SLI (8800GT cards).
It appears this issue is caused by problems with the nvidia drivers and ubuntu not working well with SLI and ubuntu not knowing which card to use.

I eventually found my way to the envy site (great guy who has made many scripts for installation of video card drivers in ubuntu) and installed his text script to remove nvidia drivers.  My system then immediately booted up.  I'm just about to try using his scripts to reinstall nvidia drivers to see if that works, but at least my system is booting right now.

Am a bit pissed off as I upgraded systems, got this error and assumed it was to do with the upgrade, so did a fresh reinstall only to get the same error when I used ubuntu's restricted device manager thing to install the drivers, and I couldn't find any reference on the net to nvidia being a cause of this problem despite people all over suffering the same isssue.

This is the envy site:

[http://albertomilone.com/envyngfaq.html#A](http://albertomilone.com/envyngfaq.html#A)

and you want to type this line in at the terminal:

sudo apt-get install envyng-core

then this:

sudo envyng -t

And choose the option to uninstall the nvidia driver, then reboot and all should be well.  Hope this works for you.

---

### Post by jonboy99 on 2009-04-29
Nope reinstalled the drivers using envy and it boots into console again.  Uninstalling as above fixed it.  I'll live without it at present as I don't really game in ubuntu, but it needs sorting out - there're plenty of us SLI users out there.


Edit, fix for SLI users here:

[http://ubuntuforums.org/showthread.php?p=7179456#post7179456](http://ubuntuforums.org/showthread.php?p=7179456#post7179456)

I still can't get advanced desktop effects working for some reason though.

edit 2 : yes I can, just entered the number for the other card in xorg.conf

---

