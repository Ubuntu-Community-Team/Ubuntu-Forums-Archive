---
title: "mouse smoothing is bad!"
date: 2005-03-31
forum: Hardware &amp; Laptops
---

### Post by 23meg on 2005-03-31
doesn't anyone have complaints about the overall mouse pointer action in Gnome? i like the way the pointer responds in the login screen, but as soon as Gnome launches it gets very slow and heavy to respond. people who dislike the "enhance pointer precision" option in windows xp will immediately get what i'm talking about  :) 

i can improve things a bit by putting 
```
xset m 2 2
```
in a startup script; it will speed up the movement, but that smoothing / heavy response is still present. i've also heard that putting the option "Resolution" with a high value in the input device section of the xorg.conf file helps, but it definitely doesn't help me.

as i've said elsewhere, Ubuntu is making my wrists ache!

---

### Post by 23meg on 2005-04-04
all xset combinations i've tried improve speed and make it easier to navigate long distances across the desktop but this time the pointer action becomes very jerky in short distance movements. i'm surprised that nobody else finds the overall mouse pointer action dissatisfactory...

---

### Post by WakkiTabakki on 2005-04-04
Are you using harware cursors? If not, this may be why your cursor is sluggish.

In the file /etc/X11/xorg.conf under the  [Device] section, make sure you've got
Option          "HWCursor"      "on"

Restart X (ctr-alt-backspace), and cross your fingers :)

/N

---

### Post by Buffalo Soldier on 2005-04-04
I have to say my mouse feels better with Hoary. When I was using Warty I needed to run [HOWTO: USB Logitech mouse and 800 cpi with udev](http://ubuntuforums.org/showthread.php?t=4357). But with Hoary the default settings are already good enough for me.

---

### Post by 23meg on 2005-04-04
[QUOTE=WakkiTabakki]Are you using harware cursors? If not, this may be why your cursor is sluggish.

In the file /etc/X11/xorg.conf under the  [Device] section, make sure you've got
Option          "HWCursor"      "on"

Restart X (ctr-alt-backspace), and cross your fingers :)

/N[/QUOTE]

are you sure this has to be in the [Device] section and not the [InputDevice] section?

---

### Post by J. S. Jackson on 2005-04-04
[QUOTE=23meg]i'm surprised that nobody else finds the overall mouse pointer action dissatisfactory...[/QUOTE]

Hmm.  My mouse has always been working fine in both Warty and Hoary.  I have a Microsoft optical mouse and everything is perfect...  and I'm a hardcore gamer, so I'm very sensitive to any mouse movement issues.

Well I'm sorry I can't help though.  Hope you get it sorted.

---

### Post by kudlaty82 on 2005-06-21
well... my mouse is jerky too  :|  and it's really annoying. i'm using creative desktop wireless 6000 - a set composed of wireless keyboard and mouse (optical). cursor movement is terrible, and after hours spent on looking up a solution in forums, i get totally pissed off  :-x
until now i've tried:
1. turning acpi off
2. reconfiguring xorg.conf in many ways
3. reinstalling hid related packages
4. and more - generally everything that can be googled

there is one important thing - after disconnecting my usb mouse+keyboard and connecting ps/2 ball mouse everything works totally fine

any suggestions or solutions??

---

### Post by scweble on 2005-08-25
*kick
I have the same problem..
Anyone an idea on how to fix it?

edit: yesterday I tried a logitech dual optical mouse(usb) and ik worked perfectly.

Problem solved by installing 2.6.12-7-686 :)

---

