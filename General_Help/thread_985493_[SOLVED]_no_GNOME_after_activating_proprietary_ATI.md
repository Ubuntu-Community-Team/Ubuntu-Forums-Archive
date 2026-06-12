---
title: "[SOLVED] no GNOME after activating proprietary ATI driver"
date: 2008-11-17
forum: General Help
---

### Post by xjgnsdof on 2008-11-17
I just installed a fresh copy of 8.10 and updated the system. I then activated the proprietary ATI driver for my Radeon 4850s in CrossFireX, but when I rebooted, I had a text-only login and command line; there was no GUI.

Does anybody know how to proceed?

---

### Post by Skripka on 2008-11-17
> **elgilicious said:**
> I just installed a fresh copy of 8.10 and updated the system. I then activated the proprietary ATI driver for my Radeon 4850s in CrossFireX, but when I rebooted, I had a text-only login and command line; there was no GUI.

Does anybody know how to proceed?

Firstly login at that text prompt and try:

```

sudo /etc/init.d/gdm start

```

To get back GDM...hopefully....if not-tell us what your computer spits back at you.

---

### Post by Marcus Derekus on 2008-11-17
Try booting all the way up then CTRL+ALT+F7

Please post results

---

### Post by xjgnsdof on 2008-11-17
CTRL + ALT + F7 gave me an endless blinking cursor. 

Trying to start GNOME as root gave me a message saying that GNOME was starting, but nothing else.

---

### Post by Marcus Derekus on 2008-11-17
boot into recovery mode and choose the xfix (xserver fix) option

Please post results

---

### Post by xjgnsdof on 2008-11-17
Nothing. It returns me to the recovery menu. Something about overwriting a custom xorg file, even though it's not.

---

### Post by doorman on 2008-11-17
In your /etc/X11/ dir you should have the xorg.conf file. If there was any change in the file, there should be also one or more xorg.conf.XXXXXXX, where the Xs make a date and time. back up your current copy:
```
$ sudo cp xorg.conf xorg.conf.backup
```
then, copy one of the mentioned X files as xorg.conf (be sure to copy the most recent configuration):
```
$ sudo cp xorg.conf.XXXX xorg.conf
```
finally, make sure gdm is not running (kill it if necesarry) and restart it.

In case nothing happens, try
```
$ sudo dpkg-reconfigure xserver-xorg
```

---

### Post by xjgnsdof on 2008-11-17
Nothing. Same ugly black screen.

---

### Post by Marcus Derekus on 2008-11-17
Sorry for not fully explaining. 

boot recovery, run **xfix** option then run **resume** option.

post results or anything else

BTW what it means a custom config files is:

a configuration that was confgured by your graphics driver when you installed the driver. (which seemed to cause the problem)

the xfix option takes the graphics configuration back to default like if you just installed Ubuntu.(no package removal or anything so all your personal data will not be changed, just graphics config)
 
once done we can go from there. 

NOTE: I have heard that xfix doesn't always work right in 8.10 but it dont hurt trying

---

### Post by xjgnsdof on 2008-11-17
I had to get some schoolwork done, so I just reinstalled 8.10 and decided to use the default non-proprietary drivers. I will try running xfix in recovery mode and resuming if enabling the proprietary drivers gives me problems. I'm really only doing this because I want to enable Compiz.

EDIT
I have included my xorg.conf file after a fresh installation of 8.10 below. I remember my old xorg.conf being huge and full of settings:

```
Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection
```

---

### Post by Marcus Derekus on 2008-11-17
OK good luck

---

### Post by xjgnsdof on 2008-11-19
I still can't access the desktop. I booted into recovery, selected xfix (which created a xorg.conf.xxxxxxxxx, where the string of x's is the date), and finally selected resume. It brought me right back to the textual login.

I have a copy of my original xorg file saved as "xorg.conf.backup" in addition to the xorg file with the date after it. What should I try now?

---

### Post by xjgnsdof on 2008-11-21
anyone?

---

### Post by xjgnsdof on 2008-11-22
Because nobody's suggestions worked, I decided to start over. I installed a fresh copy of 8.04 and realized that I needed to install fglrx. Once I did, I manually installed and successfully ran Catalyst 8.10 drivers.

I then upgraded to Intrepid and enabled the proprietary ATI driver. Compiz works just fine, but it crashes to a 2D desktop after only a minute or so. I have no idea how to proceed.

---

### Post by xjgnsdof on 2008-11-22
I decided to manually install the Catalyst 8.10 drivers. After following the directions on the wiki (I think I posted the link in this thread somewhere), I get the following message when I boot:

```
Ubuntu is running in low-graphics mode

The following error was encountered. You may need to update your configuration to solve this.

(EE) Failed to loan module "glx" (module does not exist, 0)
(EE) module ABI major version (o) doesn't match the server's version (1)
(EE) Failed to load module "dri" (module requirement mismatch, 0)
(EE) Failed to load /usr/lib/xorg/modules/drivers//fglrx_drv.so
(EE) Failed to loan module "fglrx" (loader failed, 7)
(EE) No drivers available.
```

What a disaster... What should I do?

---

### Post by xjgnsdof on 2008-11-23
Intrepid is just too buggy on my system. I've switched back to Hardy Heron; hopefully Jaunty will be able to recognize my video card drivers.

---

### Post by xjgnsdof on 2009-01-02
I've decided to dig up this old thread because I had the time to install Ubuntu 8.10 again and finally succeeded.

The key (at least, for someone with a setup like mine) is to avoid the open source version of ATI's driver (that is, the one that you find when you select Hardware Drivers). Instead, install all updates after your fresh installation. then, [manually install Catalyst 8.12]("http://http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide").

---

