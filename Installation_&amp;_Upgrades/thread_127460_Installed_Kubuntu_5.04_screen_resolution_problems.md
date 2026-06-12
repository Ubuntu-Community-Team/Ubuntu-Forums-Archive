---
title: "Installed Kubuntu 5.04 screen resolution problems"
date: 2006-02-09
forum: Installation &amp; Upgrades
---

### Post by jamesr on 2006-02-09
Hi all,

I have just installed Kubuntu 5.04 because I had problems installing 5.10 Kubuntu and Ubuntu. 
Ubuntu bum burn of CD
Kubuntu near end of installation  after primary reboot to Hard Drive, gave error not enough space or corrupt file.
Tried expert install to reduce install size but system failed to boot, obviously my error somewhere.

So I tried 5.04 install was satisfactory until it called up the KDE screen. I had forgotten that X defaults to the highest resolution so I see no picture.  How do I change the default settings to 600x480 so I at least see the screen.

My system is a tad under powered

K2-450 128 MB 2.00GB HD

but it was recommended to me as replacement software for another system that is running Corel linux , ie older KDE and that system has even less power.

---

### Post by encompass on 2006-02-09
Try this one... if you don't know what it is in the setup just press enter and it will use what it had before... pay attention to the resolutions section... in that you will find the resolution you will wnat to use.  Pick which one you want to set for your highest.

sudo dpkg-reconfigure xserver-xorg

OH YES... and if you need to boot to single user... I THINK you choose reocvery mode or what ever it is at the grub boot menu.  Ping me if you need better details.  BTW, if you want to not use a lot of ram GET away from KDE it will not help you at all.
:o

---

### Post by jamesr on 2006-02-09
[QUOTE=encompass]Try this one... if you don't know what it is in the setup just press enter and it will use what it had before... pay attention to the resolutions section... in that you will find the resolution you will wnat to use.  Pick which one you want to set for your highest.

sudo dpkg-reconfigure xserver-xorg

OH YES... and if you need to boot to single user... I THINK you choose reocvery mode or what ever it is at the grub boot menu.  Ping me if you need better details.  BTW, if you want to not use a lot of ram GET away from KDE it will not help you at all.
:o[/QUOTE]
Hi

Thanks for the reply, As you recognised the problem was that the Monitor would not sync properly, so I tried the following

Cntrl-Alt-F1

to get console screen then 

sudo dpkg-reconfigure xserver-xorg

Then Rebooted the system.

now the system only boots to the console prompt. I had already done this before I received your reply so I initially I thought that I screwed up on the command, so seeing your reply was a great news but no prize winner yet.

What do I have to do now to get the correct screen ie KDE.

TIA

---

### Post by newuser111 on 2006-02-09
you probably installed the wrong video card driver, run the command again and select vesa

---

### Post by jamesr on 2006-02-09
Hi

I reinstalled from the start, I need the practice!!! but restricted the screen resolutions in the list and it worked. But one point I noted was that the list was not as complete as the time of the installation , it suggested only the resolutions that I had manually set up.

Thanks for all of the help. I have another question or two so I will be starting a new thread/s after hunting the old messages for answers.

---

