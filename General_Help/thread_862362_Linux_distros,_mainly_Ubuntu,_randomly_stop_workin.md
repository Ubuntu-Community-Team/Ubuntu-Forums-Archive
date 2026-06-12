---
title: "Linux distros, mainly Ubuntu, randomly stop working."
date: 2008-07-17
forum: General Help
---

### Post by LIJI on 2008-07-17
Hey,
I've been using Linux and Ubuntu since 2006, and I'm a big fan of Linux and Open Source.
This computer had Ubuntu Linux 7.4, and as soon as I updated to 7.10 the problems started.

Once I've updated to 7.10 I had many instabilities issues. I've tried reinstalling, and it solved a few problems, but one day I booted and was in front of a terminal screen saying that apt is uninstalled, while 10 minutes ago it was working. I've tried using Kubuntu, but the programs and the shell started randomly crashing. At this stage I quite had enough of Ubuntu and tried Fedora, which I've used for quite long in a Virtual Machine. It had problems with the installation, and I had to repeat the installation process for 5 times before it actually worked. I can't remember what was the reason, probably the fault of my buggy ATI card, but it stopped working.

Then Ubuntu 8.04 came out and I've decided to give Ubuntu yet another chance. It was quite good, it had support for my buggy awful ATI. I used it for a while, and then had to go back to Windows to do some Windows project for about a month. When I was done with the project, I've booted to Ubuntu again. **After 1 month of inactivity, I booted to Ubuntu and it failed to start Gnome because X11 didn't start.** There was no reason for X11 to magically disappear (Like apt in a previous installation)! At this stage it was the last straw, and I've got back to Linux. Then a friend of mine recommended Mandriva to me. I tried it, and I liked it a lot. But it didn't support my buggy ATI card again, so it had many graphical glitches like mouse tearing and couldn't run Compiz Fusion correctly. (It did the 3D effects and stuff right, but it didn't refresh the windows' content correctly) I used it for about a week and came back to Windows until my nVidia card arrives. (I planned getting it half a year ago but it was delayed again and again)

Today I've finally got my nVidia 8600 GT, after having a lot of troubles with my ATI card (Not only Linux ones, but that's off topic) and I wanted to boot to Linux again, and annoyingly enough, **After 2 months of inactivity, I booted to Mandriva and it failed to start KDE because X11 didn't start.**

After all of these problems a Linux fan like me can easily begin to hate Linux, and I'm trying my best to not hate it, but with all of these problems it's getting harder and harder. Can anyone explain why the hell those problems keep happening to me without any valid reason? How can I use Linux, whatever distro, that will run correctly, without crashing, and without the need to reinstall it again a week later?

Thanks in advance to anyone helping,
-Lior 'LIJI' Halphon.

---

### Post by tosoth on 2008-07-17
You can have some hardware problems. Maybe this happens because of some HDD errors. Are you sure your HDD is ok? Other possibilities: faulty power supply or RAM. Don't you have any strange problems with Windows also?

---

### Post by LIJI on 2008-07-17
Not other than the usual Windows problems. (Windows XP SP2, updated)

My Hardware:
Intel Core 2 Dou @ 1.86GHz*2
1 GB of RAM
nVidia 8600 GT (Previous installations used ATI X1300 Pro)

In case it's an hardware problem, how should I test what is the faulty hardware?

---

### Post by LIJI on 2008-07-19
Anyone?

---

### Post by coffeecat on 2008-07-19
> **LIJI said:**
> Today I've finally got my nVidia 8600 GT, after having a lot of troubles with my ATI card (Not only Linux ones, but that's off topic) and I wanted to boot to Linux again, and annoyingly enough, **After 2 months of inactivity, I booted to Mandriva and it failed to start KDE because X11 didn't start.**

If I've understood your post correctly, there's a simple but annoying reason for this. The Xserver installation in Mandriva was setup for the ATI card and X11 crashed when it found a different graphics card. This is, imho, absolutely unforgiveable and I agree with you. It's not a Mandriva fault, it's not even a Linux fault. It's a fault of X (which don't forget is used on other Unix-type systems other than Linux). I'm sure it's not difficult to ensure that X defaults back to a low-res vesa display in situations like this, but it seems that the xorg devs are indifferent to this problem. It wouldn't be pretty but at least you would still have a GUI (of sorts) to fix things. Even Windows can manage this (as I discovered in a new build when I booted a new installation of XP with a nvidia card before I had installed the nvidia driver).

Anyway - enough of ranting. Here's a fix for Mandriva - I hope. It should work, but no guarantees. Boot up, let X crash and then log in at the console. Su to root and:

```
nano -w /etc/X11/xorg.conf
```I'm hoping nano is installed by default in Mandriva here. :roll: If not post back or use your favourite terminal editor. Find the section called "Device" and change the line < Driver "whatever" > to < Driver "nv" > Don't worry that VendorName and BoardName are wrong for now. The 'nv' driver is the open source driver and will, hopefully, get you into a GUI. Now reboot and if you get a GUI, go into the Mandriva control centre and set up the video properly (with the proprietary driver if you want).

---

### Post by LIJI on 2008-07-19
Thank you very much, I'll try it soon and report sucess or failure. :)

---

### Post by LIJI on 2008-07-22
Ok, so Mandriva does not have Nano, so modifing the file was easier with a Live CD (In contrast to learning this complex Vi thing.).
I've got Mandriva to work, but everytime I launched an RPM program or command it crashed.

I've uninstalled Mandriva and reinstalled Ubuntu 8.04 hoping it won't let me down again. It's currently working with my 8600 GT, Compiz Fusion installed and enabled, and so far evetything is perfect. But how can I really make sure it won't become unusable again? How these previous problems I've writen in the first happened anyway?

Thanks,
Lior 'LIJI' Halphon

---

