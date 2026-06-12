---
title: "Screen freezes before log in (Acer Aspire 2010)"
date: 2008-05-05
forum: Hardware
---

### Post by cerebellum on 2008-05-05
Greetings,
I have been using 7.04 and 7.10 happily on my Acer Aspire 2010 and excited to try out 8.04

It installed nicely with nothing wrong, but every time I get into the login screen 8.04 hangs and the screen goes fuzzy.

Any ideas?
Please advice.
Thnx.

---

### Post by Zorael on 2008-05-05
Did you upgrade or install fresh?

What videocard do you use?

---

### Post by cerebellum on 2008-05-05
> **Zorael said:**
> Did you upgrade or install fresh?

What videocard do you use?
I did a fresh install.
Acer Aspire 2010 uses ATI Radeon 9700 Mobility

---

### Post by cerebellum on 2008-05-07
bump..
desperate.. -_-
trying to install with text mode and will see what happens next.

---

### Post by cerebellum on 2008-05-07
No luck.. same thing after installation from text mode,
Still cannot get into desktop. Sometimes i can hear the sound that prompts for username and password.

Please advice.

---

### Post by Zorael on 2008-05-07
Try booting up into recovery mode, pick 'root shell' (or something to that extent), open up **/etc/X11/xorg.conf**, find the videocard device section and add **Device "vesa"**.

Basically:
```
# sudo nano /etc/X11/xorg.conf
```
(Omit the hashmark, it's syntax convention to show it should be performed in a terminal as root.)
Scroll down to the part that looks like this, and add the line in bold.
```
Section "Device"
	Identifier	"Configured Video Device"
**	Driver		"vesa"**
EndSection
```
Save with Ctrl+O, exit with Ctrl+X.

Then enter **exit** and see what happens.

---

### Post by cerebellum on 2008-05-08
It works nicely, but somehow the ubuntu logo gets fuzzy for 1 second before the login screen appears.

And then I only have 1 screen resolution options, 1024x768 and that's all. My laptop has wide screen and supposed to be 1280x800 resolution.

Installed the ATI restricted drivers and still only 1 resolution options.

Please advice.

> **Zorael said:**
> Try booting up into recovery mode, pick 'root shell' (or something to that extent), open up **/etc/X11/xorg.conf**, find the videocard device section and add **Device "vesa"**.

Basically:
```
# sudo nano /etc/X11/xorg.conf
```
(Omit the hashmark, it's syntax convention to show it should be performed in a terminal as root.)
Scroll down to the part that looks like this, and add the line in bold.
```
Section "Device"
	Identifier	"Configured Video Device"
**	Driver		"vesa"**
EndSection
```
Save with Ctrl+O, exit with Ctrl+X.

Then enter **exit** and see what happens.

---

### Post by Zorael on 2008-05-08
If you replace "vesa" with "ati", you should get the open drivers running with which you may get your wanted resolution. From that point you can start over with trying to get the restricted drivers installed.

I don't know much about setting up ATI with fglrx, I'm afraid.

---

### Post by cerebellum on 2008-05-08
Ok.. I think I didn't enable the restricted driver just now. My bad.
But as I installed the ATI restricted driver and restarted, the system goes black after login.

found this thread: [http://ubuntuforums.org/showthread.php?p=4899862](http://ubuntuforums.org/showthread.php?p=4899862)

but managed to fixed it with luck ^_^ by restarting to recovery mode and select repair x server.

Thanks for the help. ^_^

---

