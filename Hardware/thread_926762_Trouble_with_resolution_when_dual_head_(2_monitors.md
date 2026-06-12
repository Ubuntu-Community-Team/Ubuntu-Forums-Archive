---
title: "Trouble with resolution when dual head (2 monitors) are used"
date: 2008-09-22
forum: Hardware
---

### Post by Zikona on 2008-09-22
Hello all:

I am having difficult time configuring resolution for my second monitor. Both of monitor are exactly the same. My laptop is D610 with ATI X300 video card. Laptop is docked when both monitors are used. I am able to move my mouse curser across both monitors with help of aticonfig command. I have also used envy GUI to install ATI drivers. Did anyone run into this problem with configuring resolution on second monitor and if so, how did you correct it?

My specs:
Laptop: Dell D610
Video card: ATI x300
1st Monitor: Dell 1908Fpt connected via DVI to a docking station (resolution is correct)
2nd Monitor: Dell 1908Fpt connected via BGA to a docking station (resolution is not correct)

[COLOR=Red] xorg.conf attached.[/COLOR]

---

### Post by Nettoyer on 2008-09-22
When you installed your Ati drivers, did they install the Ati control panel?  That's how I was able to get my two monitors to run.  Not sure if this is a solution to your problem, good luck.

---

### Post by Zikona on 2008-09-22
What is the best way to install Ati control panel?

apt-get or go to ATI site?

---

### Post by Nettoyer on 2008-09-22
Trying to remember exactly.  
These are the steps I basically did to install my video card drivers (sapphire x1950 pci-e)

1. install fglrx: sudo apt-get install xorg-driver-fglrx
2. went to ati site and downloaded the linux driver for my card
3. ran the install from the terminal instead of a gui: sudo sh ./ati-etc.etc.run
4. reboot.

I believe the ati control panel comes with the drivers via their website. Also, always always **always** make sure to backup your xorg.conf file before making drastic changes, so you can revert to your old settings! It's located at /etc/X11/xorg.conf

---

### Post by Zikona on 2008-09-22
Nettoyer:

I have followed you instructions and having different problem. WHen fglrxinfo is exectured it shows:

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI MOBILITY RADEON X300
OpenGL version string: 2.1.7979 Release


Which is exactly what I have but I am unable to execute ATI catalyst control center. Is there something that stands in its way?
Perhaps I should remove AT catalyst somehow and start again.

---

### Post by Nettoyer on 2008-09-22
Well, my knowledge of Ubuntu is limited to what I have learned over the past few days.  I did some searching online and found this
thread.  I don't know if it helps you though.

[http://ubuntuforums.org/showthread.php?t=512500](http://ubuntuforums.org/showthread.php?t=512500)

Later tonight, I'll do some more searching when I can get back to my box at home.

---

### Post by Zikona on 2008-09-22
Well, I am thinking that I have tried way too many ways to get this to work and that&#8217;s why ATI catalyst control panel is not coming up. It did couple weeks ago but then I tried something else. This is my work laptop so I am thinking I am going to start from the beginning by reinstall fresh copy of UBUNTU and install ATI drivers directly from their site.

---

### Post by Nettoyer on 2008-09-22
If it's any consolation, I reinstalled 2-3x and eventually got mine to work.  Best of luck to you!

---

### Post by Nettoyer on 2008-09-23
Hey, I was doin some digging and came across this link which may help you.

[http://ubuntuforums.org/showthread.php?t=914416](http://ubuntuforums.org/showthread.php?t=914416)

---

### Post by Zikona on 2008-09-24
I have reinstalled UBuntu from the start and installed ATI drivers from ATI site without any success. Does anybody have any idea how to get this working?

---

### Post by markbuntu on 2008-09-24
The directions for properly installing the driver are here:

[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

This will also install the Catalys Control Center which you will find either in Applications/Other or Applications/Accessories.

---

