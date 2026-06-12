---
title: "Removable CD drive freezes Ubuntu..."
date: 2006-09-07
forum: Hardware &amp; Laptops
---

### Post by ghstzr0 on 2006-09-07
I have a Fujitsu Lifebook T4010 with Ubuntu Dapper 6.06 LTS installed on it.   The notebook comes with a removable bay cd drive/2nd battery.  I can remove the 2nd battery just fine without any problems, but I cannot seem to remove the CD drive without totally freezing Ubuntu (even Ctrl + Alt + Backspace has no effect).  I have even tried completely unmounting the drive first.  Any ideas??

---

### Post by armalite on 2006-10-23
I had the same problem. I have a Lifebook C1110 and system freezed when removing cd drive.
A small googling pointed me out to the solution: hotswap.

Just install hotswap package (I installed it via synaptic).
After you installed that package, you can use hotswap, xhotswap and khotswap (super user only, see later below) in order do disable your cdrom and successfully remove it without hanging the system.

It turned out that there's also a small useful applet doing this for gnome. At the moment there is no .deb, so i done it "the hard way". Don't blame me since i didn't done a .deb package... sometime in the future i'll try to do that.
I found the tar.gz in the hotswap official page: [http://timstadelmann.de/hotswap.html](http://timstadelmann.de/hotswap.html)  (google "hotswap gnome", second link).

In order to install the applet, i done the following:

- unpacked the archive with tar -xxvf gnome-hotswap-applet-0.3.0.tar.gz

- cd gnome-hotswap-applet-0.3.0

- ./configure --prefix=/usr

- make

- sudo su

- make install

then restart gnome, and the applet should show in applet manager (left click over a panel as usual).

Last thing: it appears that hotswap (command line, this is the backend used by gui frontend) needs to be executed by root user. This is an issue if you run (as you should) gnome as a standard user. So, i done the last few things, in order to let execute hotswap as i was super user. Again, this is the hard way, so i don't take responsibility about security issues.

- chmod 4755 /usr/bin/hotswap

You can test first with hotswap command line, either user and superuser, after via gui (gnome hotswap applet).

Batteries don't need hotswap to be disconnected or reconnected.

Everythings works for me. I have tried with a cdrom present at boot, later i'll try to connect a device not present at system boot.

---

### Post by petit_prince on 2007-03-11
Hey folks,

created a .deb-Package for the gnome applet the other day, see [http://ubuntuforums.org/showthread.php?t=382142](http://ubuntuforums.org/showthread.php?t=382142)

Daniel

---

### Post by armalite on 2007-03-12
Yes, I tried to debianize the sources a while ago found on Tim Stadelmann's page (as you see, submitter mail and my account here have the same name :)  ).

As you see, I'm not an expert in doing such a debianization and much work has to be done: apart from putting the right things in /debian, i have no clue on how to manage a python source and how to follow the Debian Python Policy.

So i'm really sorry if the debianization is so poor. It anyway works on my Fujitsu-Siemens laptop quite good.

---

### Post by petit_prince on 2007-03-14
> **armalite said:**
> Yes, I tried to debianize the sources a while ago found on Tim Stadelmann's page (as you see, submitter mail and my account here have the same name :)  )..
Didn't mean to take credits for debianizing the sources -- just thought a ready-to-install .deb-Package might save a lot of pople some time. That's why I linke to my other thread, where I clearly state that it wasn't me who debianized the sources :-)

> **armalite said:**
> 
As you see, I'm not an expert in doing such a debianization and much work has to be done: apart from putting the right things in /debian, i have no clue on how to manage a python source and how to follow the Debian Python Policy.

Neither am I. Most of my .deb-packages are wine-based anyway and contain Windows-binaries... no redistribution = no review = no worries ;-)

> **armalite said:**
> 
So i'm really sorry if the debianization is so poor. It anyway works on my Fujitsu-Siemens laptop quite good


Dude... I couldn't care less about the quality of your debianization -- it does the job for me.
Thanks for doing that!
Actually, you might want to give my verison a try, too, because of the two gksudo-calls :-)

---

