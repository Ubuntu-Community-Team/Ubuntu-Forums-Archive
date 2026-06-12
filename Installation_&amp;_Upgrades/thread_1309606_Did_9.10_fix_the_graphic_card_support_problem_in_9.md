---
title: "Did 9.10 fix the graphic card support problem in 9.04?"
date: 2009-11-01
forum: Installation &amp; Upgrades
---

### Post by Blue Dolphins on 2009-11-01
When I upgraded to 9.04, it was all jacked up, which I eventually found out was because of isssues with support for some graphics cards(If I remember right, mostly RADEON ones), including mine(a RADEON 7500) on my IBM t42 laptop.  I had to downgrade back to 8.10 because of this.

Did 9.10 fix this issue, or should I stick with 8.10?

---

### Post by Sunflower1970 on 2009-11-01
I just upgraded to 9.10. I have a Raedon 7500 M6 LY and the fix I originally found for 8.10 worked--sort of--for 9.10, only I'm getting some odd lines across only the top of the screen when desktop effects are enabled. 

Here's the link to the fix:
[http://ubuntuforums.org/showthread.php?t=1051571](http://ubuntuforums.org/showthread.php?t=1051571)

I'm still working on figuring out how to get rid of the lines.

I *know* desktop effects run and run smoothly on this card. I just need to figure out the workaround...

---

### Post by g160689 on 2009-11-02
yes found link for package
[http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=RADEON](http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=RADEON)
hope this helps!

---

### Post by Blue Dolphins on 2009-11-03
Ah, thanks, I'll probably give 9.10 fresh install a go in about a week, after I back up some data.  Hopefully it'll run smoothly.

---

### Post by Blue Dolphins on 2009-11-09
> **Sunflower1970 said:**
> I just upgraded to 9.10. I have a Raedon 7500 M6 LY and the fix I originally found for 8.10 worked--sort of--for 9.10, only I'm getting some odd lines across only the top of the screen when desktop effects are enabled. 

Here's the link to the fix:
[http://ubuntuforums.org/showthread.php?t=1051571](http://ubuntuforums.org/showthread.php?t=1051571)

I'm still working on figuring out how to get rid of the lines.

I *know* desktop effects run and run smoothly on this card. I just need to figure out the workaround...

9.10 works graphically without having to installing nothing, except for a random black rectangle in the corner on startup, but it don't bother me none cuz it goes away after 5 seconds.  The screen goes to **** when I tried the special effects just to see if they work, but I don't use them.  On 9.04 is was messed up even without effects.

---

### Post by Mark Phelps on 2009-11-09
Basically -- NO.

ATI dropped Linus support for lots of legacy cards back in May of this year. The Linux drivers they have now won't work with the legacy cards, and the older legacy card drivers won't work with Ubuntu versions newer than 8.10.

So, open source drivers are the only viable option for 9.10.

---

### Post by darkod on 2009-11-09
I don't know what sort of problems you have/expect but I also had big problems with Ubuntu 9.10 and integrated Radeon HD3200 on my desktop. Plus I am new to Ubuntu but this morning I finally solved my problem.

To cut a very long story short, when trying to launch live environment of 9.04 it was kicking me into busybox with a firmware bug powernow-k8 ACPI_PSS etc error. I was interested more in 9.10 anyway but starting the live environment was simply rebooting my PC just when you expect the login screen to show up. A wrongly assumed it's the same bug, it actually was the video driver.

If trying the live environment of 9.10 is rebooting your computer just before the login screen here is what worked for me:
1. Nevermind the rebooting and select the Install option at main menu of the CD/USB stick.
2. Install as normal, it will allow you to do that.
3. After the first reboot after install, try the Ubuntu (normal mode) option.

If it works, great. Most probably it will also reboot your PC just before the login screen the same as the live environment was doing. In this case:

1. When it reboots from grub menu select Ubuntu (recovery mode).
2. In the first next menu select "root with networking" to have internet access.
3. Install the EnvyNG package for video driver with:
sudo apt-get install envyng-core envyng-qt
4. Run EnvyNG in text mode with:
envyng -t
5. Select option for ATI or Nvidia driver (Nvidia cards seem unaffected by this problem)
6. After the driver downloads and installs, it will ask to reboot. Do that.
7. Then in the grub menu just select the Ubuntu (normal) and it should work fine loading the login screen fully and then the desktop.

I have seen quite a few threads with ATI cards and Ubuntu rebooting the computer but no solution. The above finally worked. It seems the driver integrated in the image has some conflict with what ever. The driver that EnvyNG downloads works perfect.

Just for reference, the downloaded driver was reported as: 8.660-0ubuntu4

Cheers.

---

