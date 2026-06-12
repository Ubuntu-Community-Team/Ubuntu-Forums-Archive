---
title: "What to do with 2 screens"
date: 2009-09-29
forum: Hardware
---

### Post by bd41 on 2009-09-29
I just started ubuntu.

I have two screens, but it seems that ubuntu doesn't support mutiple displays?

or am i wrong?

---

### Post by wojox on 2009-09-29
What do you have for graphics? Open a terminal and post this back:

```
lspci
```

---

### Post by doas777 on 2009-09-29
short answer, ubuntu doesn't but your vidcard driver probably does, so it amounts to the same thing.

first step is to make sure you have good drivers installed for your vid. then it's a matter of configuring it.

so, do you have drivers installed?

---

### Post by bd41 on 2009-09-29
> **wojox said:**
> What do you have for graphics? Open a terminal and post this back:

```
lspci
```

00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:02.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (ext gfx port 0)
00:0a.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 5)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [IDE mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Link Control
01:00.0 VGA compatible controller: ATI Technologies Inc RV770 [Radeon HD 4870]
01:00.1 Audio device: ATI Technologies Inc HD48x0 audio
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
03:0e.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)

---

### Post by jerrrys on 2009-09-29
your video card supports two monitors

[http://reviews.cnet.com/graphics-cards/visiontek-radeon-hd-4870/4507-8902_7-33132909.html?tag=mncol;rnav](http://reviews.cnet.com/graphics-cards/visiontek-radeon-hd-4870/4507-8902_7-33132909.html?tag=mncol;rnav)

---

### Post by bd41 on 2009-09-29
> **jerrrys said:**
> your video card supports two monitors

[http://reviews.cnet.com/graphics-cards/visiontek-radeon-hd-4870/4507-8902_7-33132909.html?tag=mncol;rnav](http://reviews.cnet.com/graphics-cards/visiontek-radeon-hd-4870/4507-8902_7-33132909.html?tag=mncol;rnav)

yes, but how do i get it to work on ubuntu?

---

### Post by jerrrys on 2009-09-30
this may help

[http://www.uluga.ubuntuforums.org/showthread.php?t=878709](http://www.uluga.ubuntuforums.org/showthread.php?t=878709)

more here

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=Radeon+HD+4870+install&as_qdr=all&sa=Google+Search&lang=en#1064](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=Radeon+HD+4870+install&as_qdr=all&sa=Google+Search&lang=en#1064)

---

### Post by doas777 on 2009-09-30
well that depends entirely on your answer to my question. what drivers (if any) have you installed?

if you have not installed any drivers, the easiest way to get them is to go to ati.com, and download their linux driver package.

after you have the package downloaded just open a terminal (applications -> accessories) and enter these commands, replacing anything in <> with the actual values

```

sudo chmod u+x <path to downloaded driver package>
sudo sh <path to downloaded driver package>

```
(note, you can use your mouse to drag a file into the terminal window. when you do so, the path is added to the active line automatically.)

it should run the install script, and after a reboot, you should be ready to go.

following an successful install, you will find your vid driver config application in the Applications menu. 

good luck

---

### Post by bd41 on 2009-09-30
> **doas777 said:**
> well that depends entirely on your answer to my question. what drivers (if any) have you installed?

if you have not installed any drivers, the easiest way to get them is to go to ati.com, and download their linux driver package.

after you have the package downloaded just open a terminal (applications -> accessories) and enter these commands, replacing anything in <> with the actual values

```

sudo chmod u+x <path to downloaded driver package>
sudo sh <path to downloaded driver package>

```
(note, you can use your mouse to drag a file into the terminal window. when you do so, the path is added to the active line automatically.)

it should run the install script, and after a reboot, you should be ready to go.

following an successful install, you will find your vid driver config application in the Applications menu. 

good luck

got the driver, but says need to be super user. Sudo is not asking for password?

---

### Post by bd41 on 2009-09-30
how do i get by this super user thing

---

### Post by clutch| on 2009-10-01
sudo doesn't work?

super-user means that you need to be root for the cmnd to work, so you should just be able to enter sudo <cmnd> and then your password when it prompts. 

try sudo -i, enter your password and it should say root@<yourname>.  then try the cmnd you're trying to run again.  Be careful though - being root will allow you to do things that could damage your system.  If you're nervous I would get a second opinion, because I haven't been using linux for very long lol.  I used sudo -i the other day when I needed to do something though, and it worked out ok for me.

---

### Post by doas777 on 2009-10-01
the problem may be the 'sudo sh'.

there are a few ways to run a script.
the most reliable is to navigate to the location of the script file, and enter
```

./<scriptfilename>

```give that a try. just use 'cd' to navigate to the location of the script file, and then run it with './'.

if that doesn't do it, then something is weird.

btw, the file you are running is a .run file, correct? if it is .tar.gz then you need to extract it somewhere first.

---

