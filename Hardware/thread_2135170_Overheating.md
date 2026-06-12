---
title: "Overheating"
date: 2013-04-13
forum: Hardware
---

### Post by pranavbaitule on 2013-04-13
Hi. I have Ubuntu 12.04 installed on my laptop and it heats up a lot, the fan is way too noisy.
I have installed 'psensor' and this is what it shows -

[[IMG]http://i1281.photobucket.com/albums/a517/pranavbaitule/Screenshotfrom2013-04-13200919_zpsc0ceb9d3.png[/IMG]]("http://s1281.photobucket.com/user/pranavbaitule/media/Screenshotfrom2013-04-13200919_zpsc0ceb9d3.png.html")

My graphics card is ATI Mobility Radeon HD 4250. Also I opened 'Additional drivers' and selected this - 

[[IMG]http://i1281.photobucket.com/albums/a517/pranavbaitule/Screenshotfrom2013-04-13202559_zps019508aa.png[/IMG]]("http://s1281.photobucket.com/user/pranavbaitule/media/Screenshotfrom2013-04-13202559_zps019508aa.png.html")

How can I lower the temperatures? Please help.

---

### Post by dabl on 2013-04-13
Your links aren't working correctly.  From the HTML source I looked at the second one, which shows the fglrx driver installed but not in use.  Being an Nvidia user I can't be certain, but pending better advice from the ATI crowd, I would advise doing this:

1. In system > additional drivers, change back to the open source radeon driver, and reboot.

2. ```
sudo apt-get update && sudo apt-get install linux-headers-$(uname -r) build-essential
```

3. In systemsettings > additional drivers, set it back to your fglrx driver, and reboot.

Now, is it working correctly when you look in systemsettings > additional drivers?  It should show the fglrx driver in use.

---

### Post by pranavbaitule on 2013-04-13
> **dabl said:**
> Your links aren't working correctly.  From the HTML source I looked at the second one, which shows the fglrx driver installed but not in use.  Being an Nvidia user I can't be certain, but pending better advice from the ATI crowd, I would advise doing this:

1. In system > additional drivers, change back to the open source radeon driver, and reboot.

2. ```
sudo apt-get update && sudo apt-get install linux-headers-$(uname -r) build-essential
```

3. In systemsettings > additional drivers, set it back to your fglrx driver, and reboot.

Now, is it working correctly when you look in systemsettings > additional drivers?  It should show the fglrx driver in use.

Nope. It still shows that 'the driver is activated but not in use'.

---

### Post by Mark Phelps on 2013-04-13
The forums are chock full of folks installing the post-release drivers -- and then having serious display problems.  I would choose the beta version from the list, over the post-release version.

---

### Post by pranavbaitule on 2013-04-14
> **Mark Phelps said:**
> The forums are chock full of folks installing the post-release drivers -- and then having serious display problems.  I would choose the beta version from the list, over the post-release version.

Ok. I chose the beta drivers now and still I get the message 'This driver is activated but currently not in use' and the temperature is also above 90[COLOR=#444444][FONT=arial]° C. [/FONT][/COLOR]

---

### Post by Feathers McGraw on 2013-04-15
This worked for me for the ATI Mobility Radeon 5470. Try it without installing kubuntu first but if when you've rebooted you get no desktop then the driver is incompatible with GNOME and you'll need to try something with KDE (like Kubuntu) or something else that doesn't use GNOME:

1. Install Kubuntu.
2. Remove any existing fglrx drivers and their settings:
```
sudo apt-get remove --purge fglrx*
```
3. Install the required driver:
```
sudo apt-get install fglrx fglrx-amdcccle
```
4. Configure the driver
```
sudo aticonfig --initial
```
5. **Reboot**
6. To get full hardware acceleration:
```
sudo apt-get install xvba-va-driver libva-glx1 libva-egl1 vainfo
```


Hope that does it!

Feathers

---

### Post by CatKiller on 2013-04-15
If it's getting that hot when it's not under load then I suspect inadequate cooling. The judicious application of a can of compressed air would seem to be in order.

---

### Post by pranavbaitule on 2013-04-15
> **Feathers McGraw said:**
> This worked for me for the ATI Mobility Radeon 5470. Try it without installing kubuntu first but if when you've rebooted you get no desktop then the driver is incompatible with GNOME and you'll need to try something with KDE (like Kubuntu) or something else that doesn't use GNOME:

1. Install Kubuntu.
2. Remove any existing fglrx drivers and their settings:
```
sudo apt-get remove --purge fglrx*
```
3. Install the required driver:
```
sudo apt-get install fglrx fglrx-amdcccle
```
4. Configure the driver
```
sudo aticonfig --initial
```
5. **Reboot**
6. To get full hardware acceleration:
```
sudo apt-get install xvba-va-driver libva-glx1 libva-egl1 vainfo
```


Hope that does it!

Feathers

Ok. I did what you said and somehow the temperature is down to 75[COLOR=#444444][FONT=arial]° C.

But fglrx isn't installed! I get this in the terminal when I type 'fglrxinfo' - 

[/FONT][/COLOR][[IMG]http://i1281.photobucket.com/albums/a517/pranavbaitule/Screenshotfrom2013-04-15211134_zpsadfd369f.png[/IMG]]("http://s1281.photobucket.com/user/pranavbaitule/media/Screenshotfrom2013-04-15211134_zpsadfd369f.png.html")

Also, when I go into System Settings>Details>Graphics, it shows the driver is VESA: RS880M. Will I have to manually install the legacy drivers?

---

### Post by pranavbaitule on 2013-04-15
> **CatKiller said:**
> If it's getting that hot when it's not under load then I suspect inadequate cooling. The judicious application of a can of compressed air would seem to be in order.
[FONT=arial]
Yes. The dust accumulation is definitely there but when I run windows, the temperature is between 60[COLOR=#444444]°[/COLOR] C - 75[COLOR=#444444]°[/COLOR] C which is high but it doesn't touch 90[COLOR=#444444]° C unless I play games[/COLOR].[/FONT]

---

### Post by Feathers McGraw on 2013-04-15
Interesting...I'm stumped.

Have you considered trying [Lubuntu](http://lubuntu.net) or [Xubuntu](http://xubuntu.org)? They are supposed to be good with older hardware, and it's possible that if you ask less of your graphics card it'll cool off a bit.

Feathers

---

### Post by pranavbaitule on 2013-04-15
> **Feathers McGraw said:**
> Interesting...I'm stumped.

Have you considered trying [Lubuntu]("http://lubuntu.net") or [Xubuntu]("http://xubuntu.org")? They are supposed to be good with older hardware, and it's possible that if you ask less of your graphics card it'll cool off a bit.

Feathers

Ok. I'll switch to that soon.

---

### Post by zrdc28 on 2013-04-16
ubuntu unlike windows does not throttle back your cpu, if you will install " jupiter" it will throttle back the cpu for you. 

[http://www.ubuntugeek.com/jupiter-light-weight-power-and-hardware-control-applet.html](http://www.ubuntugeek.com/jupiter-light-weight-power-and-hardware-control-applet.html)

---

### Post by QIII on 2013-04-16
> **zrdc28 said:**
> ubuntu unlike windows does not throttle back your  cpu, if you will install " jupiter" it will throttle back the cpu for  you.

This is not quite correct.  Every one of my Linux machines throttles the CPU.  This is a different situation.  Jupiter is an option if the OP is using the open source Radeon driver.


@pranavbaitule --

Since this is a mobility GPU, could you tell me if it is on-die (an APU) or on the motherboard?

Does this machine have hybrid ATI/Intel graphics?

Thanks!

---

### Post by pranavbaitule on 2013-04-17
> **QIII said:**
> This is not quite correct.  Every one of my Linux machines throttles the CPU.  This is a different situation.  Jupiter is an option if the OP is using the open source Radeon driver.


@pranavbaitule --

Since this is a mobility GPU, could you tell me if it is on-die (an APU) or on the motherboard?

Does this machine have hybrid ATI/Intel graphics?

Thanks!

1) It is on the motherboard.

2)I have ATI/ATI switchable graphics and not ATI/Intel.

Edit: Now Ubuntu will boot only in low-graphics mode. :confused: 
And I have already tried Jupiter and it didn't work for me. But I am not sure if I was running the open source driver or the proprietary one.

HELP!!

---

### Post by QIII on 2013-04-17
Hello again!

I suspect that what has happened is that only one of the adapters was initialized and the one that is being used has not.

Please go through the process of uninstalling the fglrx and fglrx-amdcccle again and reboot.

Then, when you initialize during reinstall, use

```
sudo amdconfig --adapter=all --initial
```

For reference, please see the ATI wiki in my signature.

Read "2.1. Installing via the command line" and pay attention to item 6, where I have specified using "--adapter=all" for notebook users with multiple GPUs.

You should them be able to use CCC to switch between the two.  Switching is not "on-the-fly" as it is with Windows, so you will have to reboot after making the change.


Best wishes.


QIII

---

