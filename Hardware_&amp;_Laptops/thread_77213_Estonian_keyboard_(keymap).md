---
title: "Estonian keyboard (keymap)"
date: 2005-10-16
forum: Hardware &amp; Laptops
---

### Post by ebichu on 2005-10-16
Hi,
the problem is, that I can't use estonian keymap in ubuntu.
If I had choosen estonian keymap, when installing ubuntu, then it typed wrong letters, so I had to go with english.
I hoped, that i could repair it when installation is complete.
But no! I eaven chose estonian keymap from System->Preferences->Keyboard, but still the keymap is english.
If someone enderstood what I wrote, then please help me : )

---

### Post by cloudr on 2005-10-17
I have the same problem with Breezy.
Estonian keyboard remove dead keys is selected and the default keyboard but still just English keyboard so we are missing the 4 extra vowels (Estonian has 9 vowels instead of 5) very annoying.

Please can someone help us?:confused:

---

### Post by woosh on 2005-10-17
Same problem here... 

but in terminal there is estonian layout :confused:

---

### Post by ebichu on 2005-10-17
I solved the problem, found an answer from somwhere here, but can't find the topic : (
You need to download two deb files and install them, and the change your /etc/X11/xorg.conf in Module "Keyboard" (smthng like that) en to et.
And reboot or restart X and then, when gnome asks what keyboard to use, you say X.
Uploaded deb files to my server:
[http://www.jevx.com/deb](http://www.jevx.com/deb)

---

### Post by bigjoe on 2005-10-17
strange bug. i have it also, but hoary worked fine with estonian keyboard.. :(
and those two files helped out! big thanks!

---

### Post by mahfiaz on 2006-02-01
until upgrading everything works well, but after a lot of keys just miss in gnome and in kde, maybe someone should report this as a bug?

---

### Post by zeroconf on 2006-03-16
I used Edubuntu 5.10. I installed those *.deb files from [http://www.jevx.com/deb](http://www.jevx.com/deb) and got it work. I left /etc/X11/xorg.conf as it was (Option "XkbLayout" "us"). I even didn't needed to log out - after install I could write in Russian (Russian Typewriter), Estonian (Estonian Eliminate Dead Keys) and U.S. English letters - thanks for *.deb files. By the way, where these files are come from? Somewhere from Debian repositories? From where?
But still I couldn't change keyboard layout using left ALT+SHIFT as I set it up previously. Hopefully is this nasty bug fixed in next Ubuntu release

---

### Post by 1002285 on 2006-04-24
And what is the actual command in terminal to install the deb-files when I have downloaded them to my desktop?

---

