---
title: "Graphic user interface (GUI) disappeared upon login - only get login text-prompt"
date: 2009-11-04
forum: Installation &amp; Upgrades
---

### Post by AlexOslo on 2009-11-04
I just installed 9.10 which has been working fine until today upon startup, GUI disappeared and only get a textbased prompt at the top of the screen saying:

[COLOR="DarkRed"]Ubuntu 9.10 [username]-desktop tty1

[username]-desktop login:[/COLOR]

When I type in the login and password, I get the text:

[COLOR="darkred"]Last login: Wed .............. on tty1
Linux [username]-desktop 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 ...i686

To access official Ubuntu documenation, please visit:
[http://help.ubuntu.com/](http://help.ubuntu.com/)

19 packages can be updated.
10 updates are security updates.

[username]@[username]-desktop:~$[/COLOR]

What can be wrong, and more importantly, what can I do to get back the GUI upon startup? Anything I can type on the last prompt?

I had closed down the normal way beforehand, and had found no irregularities otherwise before this.

---

### Post by Xeora on 2009-11-04
I had a simular problem so I'll describe what happened with me and what I did to fix it.

1) my HDD wasn't properly fsck'ed before so the upgrade caused my HDD to go RO mode which may be because this is a reburished drive and such. in that case I used "fsck -y" to let it fix itself since I'm no master nor really know what I was doing past reading the man pages.

2) after that GUI wouldn't work but i could login (via terminal login) and then start X (BTW "startx") will hopefully start your GUI in that mode.

3) I had to reconfigure my driver to match the new kernel. (ATi fglrx for my Radeon3100HD) "aticonfig --initial"

since then I've been fine, still problems with audio that I'm still working out (I think it's something between Pulse and ALSA)

Granted I haven't tried a reboot of my system after getting the GUI login for KDE (I'm on Kubuntu so YMMV)

all commands I used are in double quotes good luck.

---

### Post by Sunflower1970 on 2009-11-04
It's probably a video driver problem. There are different solutions for different graphic cards.

I had something similar happen to me. I have an nVidia 7600GT card. This should work for nVidia cards. I don't know about ATI's, or Intel (I'd think it should, though). The way I was able to correct it is below: 
1. log in at command prompt
2. edit the xorg.conf like so: 
```
sudo nano /etc/X11/xorg.conf
```
3. look for a section that will say something like this: 
```
Section "Device"
	Identifier	"Default Device"
	Driver	"the driver here"
	Option	"NoLogo"	"True"
EndSection
```
4. Change the Driver to vesa
5. To save in nano, Ctrl+X, then when prompted to Save, hit the 'Y', then hit enter.
6. Reboot

I rebooted, was able to get myself to the desktop, and was then able to install the correct proprietary driver for my card, rebooted again, and all worked well.

---

### Post by AlexOslo on 2009-11-04
> **Sunflower1970 said:**
> It's probably a video driver problem. There are different solutions for different graphic cards.

I had something similar happen to me. I have an nVidia 7600GT card. This should work for nVidia cards. I don't know about ATI's, or Intel (I'd think it should, though). The way I was able to correct it is below: 
1. log in at command prompt
2. edit the xorg.conf like so: 
```
sudo nano /etc/X11/xorg.conf
```
3. look for a section that will say something like this: 
```
Section "Device"
	Identifier	"Default Device"
	Driver	"the driver here"
	Option	"NoLogo"	"True"
EndSection
```
4. Change the Driver to vesa
5. To save in nano, Ctrl+X, then when prompted to Save, hit the 'Y', then hit enter.
6. Reboot

I rebooted, was able to get myself to the desktop, and was then able to install the correct proprietary driver for my card, rebooted again, and all worked well.
Thank you Xeora and Sunflower1970!
I did "startx" and the returne (a page of text) revealed the problem:

[COLOR="Red"]Parse error on line 1 of section (null) in file /etc/X11/xorg.conf
     "HorizonSync" is not a valid keyword in this section.
...
Fatal server error:
no screens found[/COLOR]

which is probably the reason why I previously got the message "unknown" for monitor when trying to detect and configure it. GUI worked a few times, but now quit.

I did Sunflower1970's point 2. and reached the text-based xorg.conf, but that's as far as my ability could take me (up to and including point 2.).

---

### Post by AlexOslo on 2009-11-09
Could the fact that no screen was detected imply a hardware failure (e.g. screen card)?

---

