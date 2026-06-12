---
title: "Upgrade broke x config, can't fix"
date: 2009-02-26
forum: Installation &amp; Upgrades
---

### Post by philentropist on 2009-02-26
I just upgraded to hardy heron, and the video/screen settings are all messed up now.

I tried reconfiguring with dpkg-reconfigure xserver-xorg, but apparently that doesn't configure video cards anymore.

Then I tried the "System>Preferences>Screen Resolution" utility, but it only allows me to select 800x600, while I have a widescreen monitor.

Finally I tried replacing xorg.conf with a backup and restarting X, which brought up a configuration utility.  The utility presented the correct options, but when clicked save, it went back to the old settings and xorg.conf was unchanged.

What can I do to fix this?  I'm disappointed to see that the ubutnu team is apparently working very hard to render a once great distro completely useless.  Hopefully the community will make up for the new version's shortcomings.  Thanks in advance for your help.

---

### Post by avtolle on 2009-02-26
You might need to manually edit your /etc/X11/xorg.conf file and input the correct information into it. To do this, get to the command line (Applications>Accessories>Terminal)and using the editor of your choice (I use nano for this) make a backup copy of your file, then```
sudo nano /etc/X11/xorg.conf
```which opens the file for editing. Once you have edited this to your satisfaction, then do Ctrl+o to write the file out, press Enter to accept the file name (which should be /etc/X11/xorg.conf and if not, edit to read that way) and ctrl+x to exit Nano. Then restart X by Ctrl+Alt+Backspace, which logs you out and then comes back to the login screen. Log in, and see if the changes "took".

The issue is the newer version of xorg that was included in 8.04, and I believe an even newer version is in 8.10. I'm not pleased about the "new and improved" version, but as I understand it, the intent was to make editing of the xorg.conf file unneeded by more users, making it a better experience. When it works, it's just fine; but for those of us who have problems, it doesn't help, and in fact IMHO hinders the process of resolving them. Good luck.

EDIT: See [https://help.ubuntu.com/community/XORGHardy](https://help.ubuntu.com/community/XORGHardy) for more information.

---

### Post by Revo___ on 2009-02-26
Give
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
a try or as a root put this into your xorg.conf - after you took a backup:

```
Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection
```

Replace "nvidia" with the correctly installed driver of your graphics card.
Let me know what it does.

---

### Post by philentropist on 2009-02-26
I've tried editing xorg.conf myself, and as far as I can tell, X is completely ignoring it.  Also, in the absence of any auto configuration utilities, does anyone know where I can get the necessary xorg.conf info for my setup (ati aiw128 and samsung syncmaster 206bw)?

This whole experience has been quite nostalgic... it's a lot like installing slackware in 1999.

---

