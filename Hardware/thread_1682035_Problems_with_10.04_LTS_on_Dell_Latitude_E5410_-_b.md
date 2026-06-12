---
title: "Problems with 10.04 LTS on Dell Latitude E5410 - blank screen"
date: 2011-02-05
forum: Hardware
---

### Post by partain on 2011-02-05
Greetings,

I've been fighting for a while with getting 10.04 installed on a Dell Latitude E5410 laptop.  The installation process goes without a hitch (I used the Alternate CD since I want to have the hard drive encrypted).  However, when I rebooted after installation, all I get is a blank / black screen.  I know that things are working since I can subsequently log in and hear the login melody :-)  However, the screen remains black.

I've found a number of threads on the forums that relate to this, but nothing I have found has helped.  I can't find anything in the X logs that indicate an error.  Nothing in /var/log/messages, either.

I'm kind of at a loss as to what I should look for.  Does anyone have any ideas?

Thanks.

David

---

### Post by mks113 on 2011-02-05
I remember a similar issue some years ago.  I don't recall the exact fix, but I do remember that it was something fairly obvious and simple when I connected an external monitor and could see what was going on.

---

### Post by partain on 2011-02-05
Hi,

A bit more digging and I found the answer right here:  [https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)

Turns out that I (1) used workaround B, (2) got the machine up and running so I could do something with it, (3) updated everything, (4) removed the VESA configuration, and (5) rebooted.

After doing so, everything worked as it should!

Thanks.

David

---

