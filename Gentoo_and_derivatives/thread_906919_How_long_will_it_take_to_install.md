---
title: "How long will it take to install?"
date: 2008-08-31
forum: Gentoo and derivatives
---

### Post by crimesaucer on 2008-08-31
I have a fast, high speed cable Internet, a brand new HP Pavilion dv9920us with 4GB AMD Turion64x2 TL-60, and 2 years of Linux experience, 1 year of it on Archlinux, where I enjoy using console and installing without a gui.


I am comfortable with Arch AUR/ABS package builds and also compiling normally.


My problem is that I only have this laptop, and no other computer to read the install wiki with, is there a wiki or handbook with instructions available on the install? Or do I have to write it all down or go find a printer to print it out?


I also have the NVIDIA GeForce 7150M / nForce 630M graphics card that works perfectly on my Archlinux, is there any problems with nvidia and Gentoo?


Any info would be cool, thanks.


.....also, would Gentoo AMD64 be faster than Arch64?

---

### Post by trimeta on 2008-09-01
As for reading the manual, if you can get internet from the LiveCD environment (which you should, via ethernet if nothing else), you can browse it while you're installing. Also, even if you use the amd64 LiveCD, it's recommended you don't do the graphical install; open up a terminal window and proceed with the command-line install. I'll be honest, a full install can take up to a day (8 hours), if you're compiling X and QT and GTK+ and a desktop environment or two. Best to start on a weekend.

As for comparison with Arch...I've never used Arch, and much of the alleged performance gain of Gentoo is mythical. But being able to configure USE flags does create leaner packages, especially if (for example) you compile things without GUIs when you're sure you'll never use them. Plus you can avoid pulling in dependencies that only support features you don't want anyway. In my opinion, though, the real advantage of Gentoo is a deeper control over your system, rather than any performance gains.

---

### Post by Bachstelze on 2008-09-01
As said above, use a Live CD to install from, not the minimal CD. Also, do yourself a favor and use your Ubuntu Live CD. The Gentoo one is, even in the Gentoo community, widely regarded as mediocre.

For a first install, how long it will take will depend on you, and on how easily you will get used to "the Gentoo way". The compiling itself will obviously not take very long on that hardware.

---

### Post by crimesaucer on 2008-09-01
> **trimeta said:**
> As for reading the manual, if you can get internet from the LiveCD environment (which you should, via ethernet if nothing else), you can browse it while you're installing. Also, even if you use the amd64 LiveCD, it's recommended you don't do the graphical install; open up a terminal window and proceed with the command-line install. I'll be honest, a full install can take up to a day (8 hours), if you're compiling X and QT and GTK+ and a desktop environment or two. Best to start on a weekend.

As for comparison with Arch...I've never used Arch, and much of the alleged performance gain of Gentoo is mythical. But being able to configure USE flags does create leaner packages, especially if (for example) you compile things without GUIs when you're sure you'll never use them. Plus you can avoid pulling in dependencies that only support features you don't want anyway. In my opinion, though, the real advantage of Gentoo is a deeper control over your system, rather than any performance gains.

Thanks, I don't mind spending a day in the console.


So I will be able to use the live AMD CD and install from the console using it? 


And This will have the AMD64 handbook with all of the commands that I'll need to use? 


I looked at the AMD64 handbook, it was a lot of the same procedures as Arch, just in a different order, and sometimes slightly different commands.




Thanks again for any info.

---

### Post by Bachstelze on 2008-09-01
> **crimesaucer said:**
> So I will be able to use the live AMD CD while installing from the console? This will have the AMD64 handbook with all of the commands that I'll need to use?

Have you use a live CD before? It will give you a full desktop environment, so you can open a Firefox window to browse the documentation, and a xterm to do the actual work.

---

### Post by crimesaucer on 2008-09-01
> **HymnToLife said:**
> Have you use a live CD before? It will give you a full desktop environment, so you can open a Firefox window to browse the documentation, and a xterm to do the actual work.

Yes, and sorry for the mixup, I was re-editing my question to be more clear. I've used the ubuntu/xubuntu live cd as well as the text mode cd's, and the new Arch live cd which really isn't a live cd like ubuntu, but rather a cd that comes with an instructions wiki page to reference while installing in a non-graphical mode.


My favorite way to install was with Arch in the console using nano.


My question is meant like this: You said that it is better to use the console (no gui) for an AMD64 install, correct? So, my question is if I will be able to access the AMD64 handbook while in console..... would I be using a different virtual terminal like tty1 while I had the live CD open with firefox on tty7..... or would I not be able to do this? If I couldn't do it that way, then would I be able to install an app like elinks and then connect to the gentoo AMD64 wiki handbook using elinks as the console browser?


Or will it just be better to have it written down on paper to not have to even worry about using the live cd?


Sorry for any confusion.

---

### Post by Bachstelze on 2008-09-01
> **crimesaucer said:**
> You said that it is better to use the console (no gui) for an AMD64 install, correct?

No. All you need is a terminal, it doesn't matter whether it is a "real" console or a terminal emulator in a graphical environment (gnome-terminal, Konsole, xterm, etc.).

So it is better to choose the second solution, because it will also allow to browse the web (to read the handbook, or ask a question in the forums if you're stuck), or even play games or watch movies if you get bored while it's doing the compiling ;)

---

### Post by trimeta on 2008-09-01
Yea, sorry if I confused you when recommending against the "graphical" installer; I was referring to the "Install Gentoo" button on the desktop of the LiveCD, not using gnome-terminal from within a GUI. It's definitely best to install from gnome-terminal or kterm within a GUI.

---

### Post by crimesaucer on 2008-09-01
> **trimeta said:**
> Yea, sorry if I confused you when recommending against the "graphical" installer; I was referring to the "Install Gentoo" button on the desktop of the LiveCD, not using gnome-terminal from within a GUI. It's definitely best to install from gnome-terminal or kterm within a GUI.

No problem, I though you meant like an Arch install with only the virtual consoles, nano, and a ncurses menu..... which I like as long as my Ethernet is detected and I can reach the Internet with elinks.


If it's a live CD using gnome or xfce4, where I can use firefox to read through the handbook and just use gnome terminal or xfce4 terminal to do the commands step by step, then I should be using Gentoo in no time!!!!!


I thought it was going to be like an Arch install using no gui at all and all of those steps..... and no Internet connection. I was a bit nervous.


Thanks for the info, and any added tips would be appreciated.

---

### Post by RedSquirrel on 2008-09-02
> **crimesaucer said:**
> Thanks for the info, and any added tips would be appreciated.

I recommend that you use the stage3 files from [funtoo.org]("http://funtoo.org/"). They are built weekly and may save you some time and effort.

You can use any LiveCD to install Gentoo since nothing from the CD ends up in your finished Gentoo installation. There is no need to print out the handbook since you can access the latest version from the web (even on the console). You can use one virtual console for the installation and another for browsing the Gentoo Handbook with links. (That's how I did it.)

I used the Gentoo Minimal CD, but it is possible that this CD will not detect your hardware correctly. If you have a LiveCD that works well with your machine, it may be best to use that (and it saves burning yet another CD ;)).

Gentoo provides binaries for some applications, for example, Firefox, Thunderbird, and OpenOffice (package names end in "-bin") which would save you a bit of time if you want to install those applications. Having said that, with your fast hardware you may want to compile them yourself just for fun.

---

### Post by crimesaucer on 2008-09-03
@- RedSquirrel: Thanks again, I still haven't tried to install yet..... I guess it's difficult to scrap a perfectly working Arch64 (flash, java, nvidia-beta, wireless....), I'm building a few more experimental Arch kernels to try a few more settings/patches, but when I get around to installing Gentoo, I'll remember this info, thanks.

---

### Post by RedSquirrel on 2008-09-03
> **crimesaucer said:**
> @- RedSquirrel: Thanks again, I still haven't tried to install yet..... I guess it's difficult to scrap a perfectly working Arch64 (flash, java, nvidia-beta, wireless....), I'm building a few more experimental Arch kernels to try a few more settings/patches, but when I get around to installing Gentoo, I'll remember this info, thanks.
You're welcome. :)

Had you considered setting up a dual boot? If you set aside some free space on your disk for Gentoo, you can install it from Arch.

[http://www.gentoo.org/doc/en/altinstall.xml#doc_chap5](http://www.gentoo.org/doc/en/altinstall.xml#doc_chap5)

---

### Post by crimesaucer on 2008-09-03
> **RedSquirrel said:**
> You're welcome. :)

Had you considered setting up a dual boot? If you set aside some free space on your disk for Gentoo, you can install it from Arch.

[http://www.gentoo.org/doc/en/altinstall.xml#doc_chap5](http://www.gentoo.org/doc/en/altinstall.xml#doc_chap5)

Well, I have Vista using 2 primary partitions already, and I have my arch /boot on a primary partition, and my 4th partition is an extended partition with my Arch SWAP on a logical and my /root on another logical....



I guess that I could use gparted live to resize somethings, but I'm not too sure how I would go about a triple boot with Vista taking up 2 partitions. And I need Vista at the moment because my iRiver isn't compatible with linux, and my digital camera also has issues.

---

### Post by handy on 2008-09-05
I expect you will be at it for 3 days, by the time you have your system completely set up with everything on it that you desire/need.

I wish you well.

---

### Post by crimesaucer on 2008-09-20
***** please excuse all spelling errors, I'm using epiphany with no spell check*****





Well, I finally tried to install Gentoo from the live CD and the stage 3 tarball.


On my first attempt I booted to a regualr gentoo kernel..... well, nv didn't work with my NVIDIA GeForce 7150M / nForce 630M, and I was unable to fix X with editing the xorg.conf or messing with modprobe..... I'm not familiar with nv, I use the regualr nvidia driver to install with Archlinux, and then upgrade to a beta driver that works better.


So I tried again with the gentoo nox kernel, and tried to install it 'the Arch way' with only the tty virtual console and ncurses.


Well, I messed up my first install by running "installer", I thought I had read the handbook correctly, but in the first part I accidentally thought I had to run the installer to get to the next "chrooting" part.... so it was a total fail and wiast of time.


So, when I actually tried my second "for real time", I booted to the nox gentoo live kernel, and then followed every instruction perfectly. I rechecked my work each time, I took my time, I had all 6 tty's open with links and other helpful pages like the make.conf.example or lspci and lsmod.


I'm VERY sure that I followed every step perfectly... I had all of the correct and safe CFLAGS, the latest snapshot and stage 3, I know I built my kernel correctly with the correct module since I have been building the zen2 patched Arch kernel for the last month (I basically have memorized menuconfig), fstab was perfect, partitions perfect, everyting was building correctly using emerge..... But on the last step for grub, the menu.lst looked so different compared to Archlinux..... but I just followed the default instructions and then exited chroot and rebooted..... FAIL.... eveything FAILDED..... 12 hours of following every step and rechecking it twice..... a totally unbootable grub, even my Vista partition was unable to be logged into.


So, I reinstalled Arch, built my zen2 2.6.26 patched kernel with all of the CFLAGS, and am now attempting to use "pacbuilder" to re-build my entire system from source with the proper CFLAGS.


I would still like to try Gentoo, but that installer took so long to get to a point that I couldn't fix.

---

### Post by regomodo on 2008-09-20
The first time I tried Gentoo my kernel failed to boot. A kernel panic aboutno partitions available. I figured it out by compiling the ide/sata drivers into the kernel rather than as modules. It's a small fix so shouldn't take too long.

---

