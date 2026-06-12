---
title: "Fonts lost on upgrade of WUBI install to Karmic"
date: 2009-10-29
forum: Installation &amp; Upgrades
---

### Post by Terrycymru on 2009-10-29
I have done an upgrade to Karmic on a WUBI install of Jaunty. It booted OK but was unusable because I had squares instead of fonts in toolbars and menus etc. Even terminal had squares instead of fonts!

Fortunately, I always keep a copy of \ubuntu in case anything goes wrong so I have been able to go back to Jaunty.

Has anyone else had this problem upgrading a WUBI install to Karmic?

---

### Post by J V on 2009-10-29
You aren't supposed to upgrade on wubi...

Its a nice setup for those of us bound to crummy household rules but it lacks features (Fast harddrive, decent Vram, hibernation, version upgrade)

Save your ~, search through your synaptic logs for installed programs, write up a script, do fresh install (Dedicated partition?) run the script, paste your data, done...

---

### Post by Terrycymru on 2009-10-29
> **J V said:**
> You aren't supposed to upgrade on wubi...

Its a nice setup for those of us bound to crummy household rules but it lacks features (Fast harddrive, decent Vram, hibernation, version upgrade)

Save your ~, search through your synaptic logs for installed programs, write up a script, do fresh install (Dedicated partition?) run the script, paste your data, done...

But the WubiGuide says under Upgrade:

[I]Upgrading

Upgrading from 7.04 to 7.10 is NOT supported, due to the fundamental differences between 7.04 and 7.10. The best route is to uninstall and install Wubi-8.10 (you can save the old installation files and access them from 8.10) or move your 7.04 installation to a dedicated partition via LVPM, then upgrade using the standard upgrade-manager tool. 

Upgrading from 7.10 to 8.04 might work, but it has not been tested yet. 

Upgrading from 8.04 to 8.10 is supported.[/I]

I assumed that upgrading was supported from 9.04 to 9.10. The WubiGuide Wiki could do with updating!

---

### Post by J V on 2009-10-29
hmm... I must have misread then... In that case I have no idea whats wrong, but upgrading can give all sorts of trouble, a fresh install will fix it one way or the other...

---

### Post by Terrycymru on 2009-10-29
> **J V said:**
> hmm... I must have misread then... In that case I have no idea whats wrong, but upgrading can give all sorts of trouble, a fresh install will fix it one way or the other...

Thanks for the misinformation. Guess I'll have to wait until someone turns up who knows what they are talking about.

---

### Post by ShaneR on 2009-10-29
> **Terrycymru said:**
> Thanks for the misinformation. Guess I'll have to wait until someone turns up who knows what they are talking about.

Not many will be willing to help while you have an attitude like that.

---

### Post by Terrycymru on 2009-10-29
My original post asked if others had the same experience doing an upgrade of a WUBI install to Karmic. There is no point in commenting unless you have actually done it.

---

### Post by Terrycymru on 2009-10-31
I have reported this problem as Bug #466859.

---

### Post by Terrycymru on 2009-11-09
This problem was caused by the Karmic upgrade automatically removing the ttf-bitstream-vera fonts I was using in Jaunty. I went to Preferences>Appearance>Fonts and selected another available font.

---

### Post by garvinrick4 on 2009-11-09
A wubi upgrade is no different from any other upgrade. Wubi is just a folder inside
of Windows of what ever size you chose. It just uses the DOS4Grub instead of Grub2.
Host in file system is C: drive in Windows. Any thing you want in you personal files can
be transfered to Linux thru  host/users/your login/  and drag and drop to Ubuntu.

All fonts in Preferences/appearance/ fonts.
Also check browswers.

Have to reinstall third party in software sources. I believe you have to install
Ubuntu-restricted-extras to get your tt fonts and all your codecs. 

I know they disable on upgrade. 

Never had your problem, but I know WUBI.

---

