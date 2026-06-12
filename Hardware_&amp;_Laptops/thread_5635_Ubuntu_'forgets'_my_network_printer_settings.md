---
title: "Ubuntu 'forgets' my network printer settings?"
date: 2004-11-20
forum: Hardware &amp; Laptops
---

### Post by shad0w on 2004-11-20
Ubuntu appears to be 'forgetting' my network printer settings.

I had been fiddling with the wireless card itself and I put some reflectors on the wireless router to get rid of deadspots. Anyways, I had popped out and put back in the card quite a few times. This morning I was trying to print something, but it refused to work. I tried again and also tried fiddling with some network settings, try to see if my card was getting a good enough signal. That all checked out, but still, it refused to print. Finally, I opened up the gnome printer settings GUI. To my suprise, and extreme annoyance, all the fields in the network printer tab were empty! I tried putting back all the info and clicking 'close', but when I opened the printer settings up again, the fields were all empty again. I tried again, and this time it remembered all my SAMBA settings, except for the username and password. 

Now I'm stuck, and extremely pissed off, because I was trying to print an assignment for english and Ubuntu made me late :x

This look likes a serious bug to me, or am I just missing something?

---

### Post by shad0w on 2004-11-20
Anyone?

---

### Post by shad0w on 2004-11-21
Oh com'on. I make a thread that doesn't just read 'HELP!!!111!!! MY PRINTER BROKE!!!' and you ignore me :\ I really need help with this guys, and I think it's a serious bug.

---

### Post by Nomad on 2004-11-21
Same problem here until I found all the places for settings.

Computer>System Configuration>Printing>Edit  (just setting up your printer but check everything twice.

Same with File>Print (check Properties)

Open Office is the same but look at Printer settings

Anything you click you should go to another field and click to change the color of
the setting you changed?  I don't know why but this works for me.

---

### Post by mystery on 2005-01-03
I'm having a similar problem with a network printer attached to a DLink 704P router.  I'm trying to install an HP6122 which works OK from another computer (also using Ubuntu) on the same network.  Printer settings on the computer that works are:

UNIX printer (LPD)

Host:     192.168.0.1
Queue:  lp

On the computer that does not work the same print settings just disappear after clicking CLOSE.

I previously had SUSE 9.1 on this machine - detection was immediate with no problems.  I can also print using XP which is installed on the same machine. 

I can't get either computer to work with CUPS PRINTER (IPP).

Assistance would be greatly appreciated.

---

