---
title: "[SOLVED] keyboard - why tap apostrophe twice to display"
date: 2008-07-13
forum: General Help
---

### Post by charonred on 2008-07-13
minor problem - why do I have to tap the apostrophe **´** or **¨** twice in order for it to display in text ? do I have a setting wrong ?

---

### Post by geraldm on 2008-07-13
Some keyboard setups have dead keys.

[http://ubuntuforums.org/showthread.php?p=4176339#post4176339](http://ubuntuforums.org/showthread.php?p=4176339#post4176339)

Gerald

---

### Post by charonred on 2008-07-13
Brilliant, thanks for that, just changed keyboard to standard as per other post

i.e.
For "Keyboard model", "Generic 105-key (Intl) PC" is probably a safe choice, or you can pick your keyboard out of the list.
For "The origin of the keyboard", pick "U.S. English".
For "Keyboard layout", pick "U.S. English" -


:)

---

### Post by charonred on 2008-08-17
Actually, it´s still not right. 

Everytime I reboot the PC, the keyboard refuses to single click for the apostrophe - I try changing from one ´generic´ keyboard to another, the variations etc, even the ´Microsoft Internet Keyboard´ can´t make it work properly.

With all the typing I do maintaining and building websites, forums and email lists, this is fast becoming a big pain in the proverbial

Suggestions to fix appreciated.

---

### Post by charonred on 2008-08-17
OK, trawled though posts and found this earlier one from Jan '07

thanks to tonywhelan
[http://ubuntuforums.org/showthread.php?t=318491&highlight=fix+keyboard+apostrophe]("http://ubuntuforums.org/showthread.php?t=318491&highlight=fix+keyboard+apostrophe")


for convenience here's the solution (notice the apostrophe; and it only took one click)
> Here's how I fixed fix it:
(adapted with thanks from a post at [http://ubuntuforums.org/showthread.p...yboard+mapping](http://ubuntuforums.org/showthread.p...yboard+mapping) )

1. Make a backup of the xorg.conf file:
sudo cp /etc/X11/xorg.conf /etc/X11/xorg_conf_backup

2. Open the xorg.conf file in a text editor:
sudo gedit /etc/X11/xorg.conf

3. Find the following code:

Section "InputDevice"
Identifier "Generic Keyboard"
Driver "kbd"

4. Delete the "Xkbvariant" line:
Option "XkbVariant" "alt-intl"

5. Save the file.

6. Reboot the PC.
After logging in may get a window telling you that Gnome has a different keyboard config to what X has. You need to tell it to keep the X version. The response buttons in this window are a bit confusing, make sure you read the message carefully before you choose.

After reboot, the system didn't ask me to choose which keyboard config to use, it just worked  :)

---

### Post by samden on 2008-12-10
Same problem, that fixed it for me, thanks.
Note that you can just comment out that line in xorg.conf (place a # at the start of the line) if you are worried about messing it up, saves deleting something and realising later that you need it.

---

### Post by onekama_michigan on 2010-05-28
This same problem popped up on my machine after a recent update (tap apostrophe twice to get it to work).  Apostrophe is now acting like a dead key although my keyboard preferences do not reflect this.  Ubuntu 9.10.  No other config changes were made.  I will attempt key remap and modify keyboard preferences to see if it can be fixed that way.

---

### Post by eternalnoob on 2010-06-06
Hi I have the same problem since upgrading to 10.04
I have to hit the following keys twice ` ~ ^ ´ ¨
Keyboard layout USA Alternative international
Keyboard model Generic 105-key (Intl) PC
I tried switching keyboard layouts and models with no luck.
I also tried the xorg.conf fix recommended here but my xorg.conf did not contain XkbVariant and nor did any of the xorg.conf backups.

Any other suggestions

---

