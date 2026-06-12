---
title: "Absolutely no driver works for my video card."
date: 2010-02-24
forum: Hardware
---

### Post by dimilunatic on 2010-02-24
Hello all! I have a laptop with an NVIDIA Geforce Go 6800 video card. Cpu is Intel Pentium M @1.60 GHz and 2.0 GB RAM.

When running Ubuntu Karmic from the live CD, I noticed that the default "nv" driver would freeze the system at random times, even when a simple task is run on the shell. What's worse is that it always happened when I tried to move a window or drag-and-drop some files. This whole problem carried on after installing and still happens to this day. 

For this reason, I installed the proprietary driver. Even worse; after the Ubuntu splash, the screen turns white with some black lines, whereas I can hear the log-in screen sound. This happens with every version of the proprietary driver. Envy had the same result.

Then, I turned to nouveau. Nothing, nothing, nothing. The system never reaches the log-in screen, but mentions something about a problem that is solved but needs a reboot. No progress, though. The same message goes over and over.

So, I'm doomed to run the low-graphics mode. 800x600 on a 17 inch screen; you get the picture. Any ideas? I'm desperate, as this laptop used to be my main Linux work center, before doing a clean install of Karmic. :(

---

### Post by dabl on 2010-02-24
Says [[COLOR="Green"]**here**[/COLOR]](http://www.nvnews.net/vbulletin/showthread.php?t=122606) that the 190.53 driver should run your card. 

Sometimes it's the "process" of installing the driver than can be a problem.  This guide is for Kubuntu, but the only difference for Ubuntu is that your display manager is gdm rather than kdm, and your text editor is gedit rather than kate, and your GUI launch command is "gksu" rather than "kdesudo":

[http://kubuntuforums.net/forums/index.php?topic=3107406.0](http://kubuntuforums.net/forums/index.php?topic=3107406.0)

Take it carefully, step by step, starting where it says "The Official Nvidia Way" and I'll cross my fingers.  :)

---

### Post by dimilunatic on 2010-02-24
Thanks for the advice! I followed it step-by-step and installed it. The same thing happened again, though; before I get to the log-in screen, I get a white screen with black lines. :/ I had to modify the xorg.conf, so I could get the low-graphics mode again and log in.

---

### Post by dabl on 2010-02-24
OK.  Must be something "special" with your chip and hardware.

I would first try installing the next oldest released driver, 173.14.25 and see if does better.  If so, you can be done.  If not, I would pursue some research on the nvnews forum, perhaps starting here: [http://www.nvnews.net/vbulletin/showthread.php?t=120492](http://www.nvnews.net/vbulletin/showthread.php?t=120492)

---

### Post by dimilunatic on 2010-02-24
> **dabl said:**
> OK.  Must be something "special" with your chip and hardware.

I would first try installing the next oldest released driver, 173.14.25 and see if does better.  If so, you can be done.  If not, I would pursue some research on the nvnews forum, perhaps starting here: [http://www.nvnews.net/vbulletin/showthread.php?t=120492](http://www.nvnews.net/vbulletin/showthread.php?t=120492)

Actually, 173.14.25 worked slightly better in the sense that it just gave me errors and no white screen. :D

According to it:
> Failed to load the Nvidia kernel module.
Failed to load module "nvidia" (module-specific error, 0)

---

### Post by dabl on 2010-02-24
Did you remove the restricted modules?

```
sudo apt-get remove --purge linux-restricted-modules-`uname -r`
```

?

And also, go to the filesystem root, "/", and issue 

```
sudo rm -rf nvidia*
```

?

and insert "nv" in the /etc/default/linux-restricted-modules-common file, in DISABLED MODULES="nv"

?

---

### Post by dimilunatic on 2010-02-24
> **dabl said:**
> Did you remove the restricted modules?

```
sudo apt-get remove --purge linux-restricted-modules-`uname -r`
```

?

And also, go to the filesystem root, "/", and issue 

```
sudo rm -rf nvidia*
```

?

There were none of either, to begin with.
> and insert "nv" in the /etc/default/linux-restricted-modules-common file, in DISABLED MODULES="nv"

?

This file doesn't exist at all in my filesystem. Should I create it and add it?

---

### Post by dabl on 2010-02-24
No, if there's no /etc/default/linux-restricted-modules-common file on your system, ignore that.

But, how can there not have been files named nvidia* if you previously installed an Nvidia driver?  That doesn't make sense to me -- where did they go?

Are you changing to the filesystem root, before you issue that comand?

```
cd /
```

and then issue ```
sudo rm -rf nvidia*
```

---

### Post by dimilunatic on 2010-02-24
> **dabl said:**
> No, if there's no /etc/default/linux-restricted-modules-common file on your system, ignore that.

But, how can there not have been files named nvidia* if you previously installed an Nvidia driver?  That doesn't make sense to me -- where did they go?

Are you changing to the filesystem root, before you issue that comand?

```
cd /
```

and then issue ```
sudo rm -rf nvidia*
```
Yes, I do. :/

---

### Post by dabl on 2010-02-24
> **dimilunatic said:**
> Yes, I do. :/

That's weird.

So, when you run the proprietary installer, does it give you any error output, at any stage?

---

### Post by dimilunatic on 2010-02-24
Nope, until when I actually get to use it. I'm trying something else now and if that doesn't work, maybe I'll try once again with the proprietary one.

---

### Post by dabl on 2010-02-24
> **dimilunatic said:**
> Nope, until when I actually get to use it. I'm trying something else now and if that doesn't work, maybe I'll try once again with the proprietary one.

OK. Meanwhile, Google found this: [https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/208718](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/208718)

which reminds me, did you do

```
sudo apt-get install linux-headers-`uname -r'
``` 

and

```
sudo apt-get install build-essential
```

?

---

### Post by dimilunatic on 2010-02-24
> **dabl said:**
> OK. Meanwhile, Google found this: [https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/208718](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/208718)
This looks exactly like my problem.

> which reminds me, did you do

```
sudo apt-get install linux-headers-`uname -r'
``` 

and

```
sudo apt-get install build-essential
```

?

Yep. Nada result is nada. :P

---

### Post by dabl on 2010-02-24
#-o

Color my butt kicked!  It is clearly a phenomenon that has been seen before, as indicated in the other thread, but I cannot fathom what is preventing your system from loading the driver module after it is built.  It's hard to tell whether it is even building.

---

### Post by dimilunatic on 2010-02-25
Any ideas, guys? My instinct says to work with the nouveau driver. Does anyone have any experience there?

---

### Post by dimilunatic on 2010-03-09
Just bumping the thread, wondering if anybody has an idea. Right now, my laptop works with vesa on KDE, which btw freezes much worse than Gnome with any other driver. I prefer KDE, since even at 800x600, it still looks ok.

I can't run efficiently any graphics-dependent applications, though. Help?

---

### Post by U-Toto on 2010-03-09
Hello,

I have been dealing with this same issue for months going from distro to distro. Glad to see someone else is getting help, but, sad to hear you have the prob. I am currently running the v185 and get only 800x600 as well as the highest. I did, however, just see on NVIDIA's NVNEWS about the v190 and higher drivers. I am trying to download v190.53 to try to no avail. Any ideas? And, have you already tried these?

---

### Post by dimilunatic on 2010-03-09
Glad too for finding someone who shares at least part of my problem. I believe I've tried every single nvidia driver back from 90-something to 190.53, even nv and nouveau. Nothing works, unfortunately.

Now that I think about it, I'll go try *again* the v185 and let you know. Hope dies last. :P

EDIT: Nope, white screen with random black lines.

---

### Post by U-Toto on 2010-03-09
Please, how did you download the drivers above v185? My system doesn't even show them as available. 

And, dumb curiosity here. How is your system physically connected? Perhaps this might be a cause (no offense intended).

---

### Post by dimilunatic on 2010-03-09
> **U-Toto said:**
> Please, how did you download the drivers above v185? My system doesn't even show them as available. 

And, dumb curiosity here. How is your system physically connected? Perhaps this might be a cause (no offense intended).

Neither does mine; I downloaded them off the nvidia site.

No offense taken. The system is just a normal Fujitsu Siemens laptop of 4 years or so. Before installing Ubuntu, I was running Windows XP just as fine, without any problems, so it's not a hardware error. At some point, I was paranoid enough to reinstall windows xp and check if the problem came on there, but it didn't.

---

### Post by Objekt on 2010-03-09
I can't solve the original problem, but I can commiserate.  I am having very similar issues on my system, with newer hardware (GeForce 9800 GTX+) and LTS releases of Ubuntu, specifically 8.04.3 and 8.04.4 (32-bit in both cases).

Neither Ubuntu 8.04.3 LTS nor 8.04.4 LTS detects that I have an Nvidia-based video card, so I can't install the Nvidia proprietary drivers using the usual approaches (jockey-gnome or EnvyNG).

I also tried this: I installed the 32-bit Nvidia 190.53 .run package manually, at the command line, after stopping Xserver.  It went through all the normal steps with no error messages, but it doesn't work.  When I boot after "installing" the 190.53 drivers, I get the garbled display, and then have to manually tell Xorg my monitor & choose a compatible (read: low-res, low refresh rate) display mode with a generic VESA driver.  The nvidia-settings program will run, but says I am "not using" the NVidia driver (well yeah, I'm using the generic VESA one, because the Nvidia one failed to load).

My 8.04.4 LTS install had all the latest updates before I tried to install the 190.53 package, so I can't fathom what is wrong.  

I know 8.04.3 LTS does work with some Nvidia hardware, because I installed it on a different machine without issues.  That machine had a built-in Nvidia GeForce 7025 device.  The "Hardware Drivers" wizard popped up on the first boot, just as you would expect.

I started threads about this weeks ago, but have yet to get a single reply.  I guess no one else is having a problem with LTS releases on (some) Nvidia hardware?

---

### Post by U-Toto on 2010-03-09
Sorry, didn't realize it was a laptop. I dual-boot XP on mine as well. It's video works flawlessly too.

---

### Post by dimilunatic on 2010-03-09
At least I am not the only one and that gives me hope for Nvidia fixes. After all, this laptop was meant to be a complete desktop replacement for my lab projects; the programs that I need to work can even run on a PIII. :P Presentations, though, are also a part of lab life and without a proper video card driver, the laptop will probably not show output to a projector. :/

---

