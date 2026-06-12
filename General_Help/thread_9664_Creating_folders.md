---
title: "Creating folders ??"
date: 2004-12-30
forum: General Help
---

### Post by Bill888 on 2004-12-30
hi

I spent all morning downloaded the ubuntu LiveCD iso this morning to try out on my P3 desktop & Celeron notebook to see how it compares to MEPIS and Knoppix before deciding what is best to install to hard disk.

I'm new to Linux so forgive me if I am doing something real stupid.

I've come across some unusual issues.

1. From the GUI (Nautilus?), when I open a window to any folder, the File menu options to create a new folder are always greyed out on both desktop and notebook.   Surely this cannot be correct ?

2. On my Toshiba Satellite A10 notebook, I can use the menu options in ubuntu to set up my built in wireless network card (Agere minipci card - nickname 'Hermes I' according to iwconfig).  I can successfully ping known websites.

After configuring the wireless, I'm no longer able to launch any GUI based programs.  eg. Mozilla will appear to load as it appears on the taskbar at the bottom of the screen, then disappears.   Similar symptoms with Gaim and OpenOffice etc.     If I launch Mozilla before configuring the wireless network, Mozilla can surf the net but as soon as I shut it down and try to restart it, it fails to launch.



bill

---

### Post by khc on 2004-12-30
1) Any folder, including your home directory? I've not used the LiveCD, but I think it maps the home directory (and /tmp, etc) to some sort of RAM fs right?
2) Does the LiveCD allow you to log out and log back in? Try hitting ctrl+alt+backspace. This happens because your IP is changed after you configure your wireless, and X doesn''t like that.

---

### Post by Bill888 on 2004-12-30
1) ah Yes, turns out all of the folders I had tried were ReadOnly in RAM I guess.   I mistakenly thought I was logged in as Root.  As soon as I drilled down to the /home/warty folder, the GUI permitted me to create folders from the menus.

2)  Tried CTRL+ALT+Backspace on your suggestion.  Unfortunately all this did was cause ubuntu to shut down and restart the notebook.  (Live CD does not prompt to  login during boot up btw)

I might think about downloading and trying the regular version of ubuntu to try.

thanks for your suggestions.

---

### Post by nbliang on 2005-01-06
The LiveCD was running on the CD and RAM, and sometimes on your Swap partition in your hard disk (if available). You will not be able to create new folder(s) on it except you mount your hard disk.

---

### Post by tiiim on 2005-01-06
[QUOTE=Bill888]1) ah Yes, turns out all of the folders I had tried were ReadOnly in RAM I guess.   I mistakenly thought I was logged in as Root.  As soon as I drilled down to the /home/warty folder, the GUI permitted me to create folders from the menus.

2)  Tried CTRL+ALT+Backspace on your suggestion.  Unfortunately all this did was cause ubuntu to shut down and restart the notebook.  (Live CD does not prompt to  login during boot up btw)

I might think about downloading and trying the regular version of ubuntu to try.

thanks for your suggestions.[/QUOTE]
 also live cd at the current time does not match the quality of the real thing! there a few differnces so give Ubuntu a proper wurl and ur like it ;)

---

