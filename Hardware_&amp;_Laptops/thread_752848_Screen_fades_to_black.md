---
title: "Screen fades to black"
date: 2008-04-12
forum: Hardware &amp; Laptops
---

### Post by phidia on 2008-04-12
Something happened with the external drive gutsy install-on my laptop. The laptop went into suspend and it usually doesn't like that running from the external usb drive, but it did resume. I unplugged AC to move the computer and the screen started to dim a lot. Now when I log in to the install the display dims and goes to black immediately-it effects the display even through a reboot the screen remains dark. I can not get screen brightness back after this until I pull the battery for a few seconds to get it to return to normal. 

I can't login to failsafe gnome either as it happens there too. I created a test user who  can log in without the screen going black-the test user has no sudo privileges though. I can use windows install normally also.
I used a livecd to look at my user hidden files but I couldn't find anything there that might be effecting this.
I also read about DPMS settings in xorg-but not sure if that would be causing this.

Please help.

---

### Post by phidia on 2008-04-12
any ideas on this?

Ok here's what I did. I tried moving/backing up several of the x related hidden files in my home but that didn't solve this problem. 
I then backed up the entire user directory, created a new directory with the same name, chgown & chgrp to that user.
My permissions aren't quite right yet but I do have a usable desktop again-YAY!!

---

