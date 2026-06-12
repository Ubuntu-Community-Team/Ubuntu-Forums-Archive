---
title: "Ubuntu 17.04 Gnome Wacom stylus not recognized"
date: 2017-05-09
forum: Hardware
---

### Post by SreckoMicic on 2017-05-09
Wacom stylus is not recognized in Settings . Other part of tablet are recognized, Pad and Express buttons, and I can set them up in Gnome settings. Express buttons are messed up though. Anything I can do? 
I would like to avoid using terminal with xsetwacom to setup stylus.
[http://screencloud.net/v/vnul7](http://screencloud.net/v/vnul7)

Tablet is small one, CTH480S2 [Manga].

---

### Post by razvanc-r on 2017-05-09
tehehe, was looking to see if others have the same problem as well :)

---

### Post by Areku The O.F. on 2017-07-26
I'm having the same problem with my Wacom Bamboo Capture CTH-470. The tablet itself it's recognized but not the stylus, the funny thing is that the stylus still works (the tablet led turns white with the stylus as it should) but it's not recognized for configuration.

---

### Post by SreckoMicic on 2017-09-20
Issue is in 17.10 too ....

---

### Post by aegisprime on 2017-09-22
My Intuos 2 wasn't working with 16.04 but the following (from [http://linuxwacom.sourceforge.net/wiki/index.php/Main_Page](http://linuxwacom.sourceforge.net/wiki/index.php/Main_Page)) got it working:


1) sudo apt-get install linux-headers-$(uname -r) build-essential
2) Download **input-wacom-0.36.0.tar.bz2** (*not* 0.35) here: [https://sourceforge.net/projects/linuxwacom/files/xf86-input-wacom/input-wacom/](https://sourceforge.net/projects/linuxwacom/files/xf86-input-wacom/input-wacom/)
3) Unzip it, open a terminal in the folder and run:
4) ./configure
5) make
6) sudo make install
7) sudo reboot

---

### Post by virgosun on 2017-11-30
mine manual install from wacomlinux, both internel and external devices GUI enables[ATTACH=CONFIG]277693[/ATTACH]

---

### Post by gravier on 2018-01-04
Just update the wacom_wac.c with this one depending on which version kernel version you're in (most likely 4.5)
This one is compatible with trusty (3.17)
[ATTACH]278045[/ATTACH]

Or you can patch the src yourself based on this update: [https://www.spinics.net/lists/linux-input/msg53553.html](https://www.spinics.net/lists/linux-input/msg53553.html)

---

### Post by bsolomon3000 on 2018-01-15
Hi,

I'm very new to Linux so forgive my ignorance.  I've tried the above but I get this result.
robert@Z400-Bob:~$  sudo apt-get install linux-headers-$Bob -r build-essential
E: Command line option 'r' [from -r] is not understood in combination with the other options.

I've been trying for days to get my Intuo 3 to work.

Thanks

---

### Post by jlinux7 on 2018-01-22
Hello, i am new to this forum. I have been searching for a couple days for a solution to this issue also. I have a Fujitsu t series convertible. the built in wacom pen worked fine in build 17.04 but is not recognized in 17.10. I also tried the commands previously mentioned but still does not work.

---

### Post by mörgæs on 2018-01-23
Hi and welcome to the fora.

Have you tried how it works in 18.04 (development release)? You don't have to install, a live boot will do.

---

### Post by jlinux7 on 2018-01-29
Hello. I am running Ubuntu 17.10. I have automatic updates on. I was running 17.04 and got the auto update to 17.10. I wan to try the install that aegisprime posted but wanted to make sure that the steps given is exactly what to type. I am slowly getting used to linux after many years of windows.
thanks for your patience and help!!!!

The instructions for aegisprime were correct but that did not resolve the problem. Mysystem is a fujitsu t series lifebook with Penabled wacom. The pen worked perfectly in 17.04 but does not work at all in 17.10. This was a great feature because i could fold the laptop into tablet mode and use the stylus. I guess i will wait for the next release.

If there are more suggestions i will be glad to try.
Thanks

---

### Post by mörgæs on 2018-01-30
> **jlinux7 said:**
> I guess i will wait for the next release.

Why? You can test it now.

If it works: Good for you.
If it doesn't: Please report the bug to the developers.

---

### Post by SreckoMicic on 2018-02-25
I am on 17.10 now and still ahve this probelm. Also have second tablet, Wacom One which not recognized at all.

---

### Post by mörgæs on 2018-02-25
And have you tried 18.04?

---

### Post by SreckoMicic on 2018-02-25
No not yet. Will try with VM. I am using Pop_OS!.

---

### Post by wildmanne39 on 2018-02-25
> **SreckoMicic said:**
> No not yet. Will try with VM. I am using Pop_OS!.
Please notice the title of the thread is Ubuntu 17.04 Gnome if you are using Pop_OS you need to create a thread here:

[https://ubuntuforums.org/forumdisplay.php?f=452](https://ubuntuforums.org/forumdisplay.php?f=452)

Even though it is based on ubuntu it is not an official flavor so it goes in the sub-forum I linked above even if you are running on a system76 computer.

Thanks

---

### Post by SreckoMicic on 2018-02-25
I know, I created this thread. Back than I was using 17.04. In mean time I switched to PopOS but also had same issue with Ubuntu 17.10. I will try 18.04 to see what happens there. It was working OK on 16.04.

---

### Post by eezacque on 2018-03-12
Same problem here with my Cintiq. It has always worked straight out of the box, but Ubuntu 17.10 broke it.

---

### Post by eezacque on 2018-03-12
> **aegisprime said:**
> My Intuos 2 wasn't working with 16.04 but the following (from [http://linuxwacom.sourceforge.net/wiki/index.php/Main_Page](http://linuxwacom.sourceforge.net/wiki/index.php/Main_Page)) got it working:

This is not working for my Cintiq.

---

### Post by fuho on 2018-04-24
I can confirm similar issue in 18.04 beta 2. Running it on ThinkPad x220t the stylus is not recognized in the settings app, but works (behaves as mouse).

Interesting thing is that I tried this in live version of Fedora which uses the same settings app and there it was recognized, even on the same hardware.

---

### Post by SreckoMicic on 2018-05-04
Just tried with 18.04 and it does not work.... Wacom One is not recognized at all. Wacom Intouse Pen and Touch small is recognized but in settings stylus is not so you can not set it up. In 2018 I need to wobble with terminal like I did 13 years ago .. lovely...

---

