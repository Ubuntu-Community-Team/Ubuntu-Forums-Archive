---
title: "[SOLVED] Different keyboard layouts for login and Gnome?"
date: 2008-08-31
forum: General Help
---

### Post by stoneage on 2008-08-31
My keyboard layout has somehow become set to USA for the login and then reverts to UK afterwards. It is set to UK in 'Keyboard Preferences'. How could this have happened and how can I change it. I am unable to use my password to login but it works for admin purposes once I am logged in. (I changed it to log in then tested).

I could change my password, but that is not really the point. How could I have two different keyboard layouts set?

---

### Post by Rocket2DMn on 2008-08-31
What does it show in your xorg.conf file?
```
cat /etc/X11/xorg.conf
```

---

### Post by stoneage on 2008-08-31
Seems normal:-

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"en"
EndSection

I've been looking into it and I had 'Separate layout for each window' checked in 'Keyboard Preferences', and if I lock screen it says GBr, but Hibernate came back up USA. Having unchecked it though the problem persists, and Hibernate comes back on GBr.

I noticed though as it goes into Hibernate a text displays something about 
i8042 AUX 00:0a activation failed
i8042 KBD 00:0b activation failed

Significant ?

EDIT - it actually may not be a US layout, it seems to be just one key that won't function, SHIFT+3, it shows 3 on the login screen but £ after login.  ??

---

### Post by Rocket2DMn on 2008-08-31
What if you set
Option "XkbLayout" "en"
to
Option "XkbLayout" "uk"
I'm not entirely sure if that is the correct option, but you can try reconfigung X as well.
First make a backup
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
sudo dpkg-reconfigure xserver-xorg
```
You should get asked about keyboard stuff, you may have to fiddle a couple of times if the autoconfig option doesn't work correctly.
After you reconfigure (or even after just editing xorg.conf) you will have to restart X with CTRL+ALT+BACKSPACE.  If you are using different video settings than default, you may have to copy those in from your backup (like running dual head).

---

### Post by stoneage on 2008-08-31
Issue resolved, thanks:-

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"gb"
EndSection


I didn't need to reconfigure. When I was reading through the options it offered gb as a layout, so I tried that one and it's fine now.

---

