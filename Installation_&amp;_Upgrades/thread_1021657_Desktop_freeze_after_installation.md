---
title: "Desktop freeze after installation"
date: 2008-12-25
forum: Installation &amp; Upgrades
---

### Post by jjmmjjmm on 2008-12-25
Hello

I really want to use Ubuntu, but i dont have any lucky with the installation. I use a notebook Acer 4002WLMi with: Intel Pentium 1.6ghz ; ATI Radeon 9700 64mb ; 1256 memory ram.
After the installation on d: (clean) don´t appear nathing on desktop, but i can move the mouse. 
I have try vga=771 and noapic nolapic but dont have sucess.

Can someone help me ?

Thanks

João

Portugal

---

### Post by lemming465 on 2008-12-26
Which version of Ubuntu, 8.10?  If you installed from a live CD, does the live CD work OK?  Does the CD pass the self-test?

---

### Post by abn91c on 2008-12-26
you probably will need to remove compiz or try to log in recovery and disable compiz/desktop effects

---

### Post by jjmmjjmm on 2008-12-27
The version ubuntu is 8.10. I have tried by live cd and when i got the desktop screen and move the mouse i get a black screen.
Thanks abn91c, but what i need to do to disable compiz/desktop effects ?

Thanks

João 

Portugal

---

### Post by abn91c on 2008-12-27
ctr+alt+f1 to get to the prompt, then sudo apt-get remove compiz followed by sudo apt-get remove compiz-core, then reboot

---

### Post by wpshooter on 2008-12-27
Have you tried installing from the ALTERNATE (text based) version of Ubuntu ?

---

### Post by jjmmjjmm on 2008-12-28
Thanks. No, i go try, ([http://www.ubuntu.com/getubuntu/downloadmirrors#alternate](http://www.ubuntu.com/getubuntu/downloadmirrors#alternate)). If dont work go try with others distros like: opensuse, mint, fedora or mandriva. Any sugestion ?

Thanks

João 

Portugal

---

### Post by lemming465 on 2008-12-30
Good luck with the alternate install try.   abn91c's advice about removing compiz is worthwhile too; turning that off has helped me when there were issues with binary nvidia drivers on some PC's.

If Ubuntu isn't working out for you due to hardware issues, maybe try Fedora 10.  I've been impressed with its hardware recognition, particularly for wifi chipsets.

---

### Post by Diogo_C on 2008-12-30
Same problem here. I removed compiz but the problem isn't solved.
I think vga ati9700 64mb is the source of the problem but my system boots in Windows XP as usual.

---

### Post by lemming465 on 2009-01-01
There are at least 3 X driver choices when dealing with ATI chips: vesa, the ati open source family, and the proprietary fglrx.  If you are getting blank or black screen, you need a different one.  Assuming that you can boot in "recovery mode" (single user), you can edit /etc/X11/xorg.conf with vim or nano and change the driver.  Find the section at the bottom that looks like```
Section "Device"
	Identifier	"Configured Video Device"
	Driver	"fglrx"
EndSection
``` and try a different driver, such as **vesa** or **radeon**.  You won't have fglrx unless the restricted driver is installed and active, but that may well have happened by default during the initial install.

---

### Post by jjmmjjmm on 2009-01-01
Can you explain what i need to do to edit xorg.conf ? 
I reboot in recovery mode, and in the root line i write: cd etc, after i write dir and can´t see the folder x11.

Can help me ?

Thanks.

João

Portugal

---

### Post by jjmmjjmm on 2009-01-01
[QUOTE=```
Section "Device"
	Identifier	"Configured Video Device"
	Driver	"fglrx"
EndSection
```[/QUOTE]

Ok, i can edit xorg.conf but in my configurations dont appear the "drive".


Device       "configured video device"
Identifier

Monitor      "configured monitor"
Identifier

Screen       "Default screen"
Identifier

Any suggestion... ?



João 

Portugal

---

### Post by lemming465 on 2009-01-01
To edit xorg.conf:```
cd /etc/X11  # note upper case X
cp xorg.conf xorg.conf.bak # save a copy
nano xorg.conf  # or vim or emacs or ...
```
If there is no paragraph starting **Section "Device"** ... **EndSection** add one.  Inside it put one of **Driver "vesa"** or **Driver "radeon"** or **Driver "flgrx"**.  If one of them works OK for you, keep it and be happy.

---

