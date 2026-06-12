---
title: "Fn-F2 not working - Asus A8HeAS"
date: 2008-04-04
forum: Hardware &amp; Laptops
---

### Post by madscience on 2008-04-04
I've just installed 8.04 beta and I noticed that all of my Fn-Fx keys work great!  I get a nice OSD for my volume up/down/mute, Fn-F1 puts the machine to sleep, Fn-F5 and Fn-F6 change the LCD brightness.  The only problem I'm having is that Fn-F2 does not toggle WiFi, and the LED status indicator does not respond.  I looked at the scripts in /etc/acpi, but I'm not knowledgeable enough to know what I need to change.  I noticed that the script seems to be looking for:
ATKD 0000005f - for wifi off
ATKD 0000005e - for wifi on

but on my machine, I see that Fn-F2 sends 0000005d every time the key is pressed.  Is there a fix to get this key to toggle WiFi and the status LED?

I've checked Launchpad, and it seems like the latest versions of the ACPI scripts were written for Asus machines which actually toggle the key value.

Thanks in advance.

---

### Post by madscience on 2008-04-08
upon further inspection, it looks like asus-wireless should work (as opposed to asus-wireless2).  Can anyone tell my how to get acpid to use one or the other?

---

