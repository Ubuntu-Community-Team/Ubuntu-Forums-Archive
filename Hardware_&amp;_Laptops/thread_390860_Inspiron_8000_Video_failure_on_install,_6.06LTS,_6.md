---
title: "Inspiron 8000: Video failure on install, 6.06LTS, 6.10 and Feisty Fawn"
date: 2007-03-22
forum: Hardware &amp; Laptops
---

### Post by K7AAY on 2007-03-22
Dell Inspiron 8100.

Knoppix 5 can recognize the video OK (1024x768), but no recent Ubuntu (6.06LTS, 6.10 and current Feisty Faun) can.

Video 's OK until about 1/3 of the way across the screen, where the rest of the screen is covered by another rendition of the first part of the screen. Can't read the dialog boxes to do an install. Booting with vga=771 does not work, either.

How can I get Ubuntu to recognize the video hardware?

Thank you in advance.
73s and best regards,
K7AAY

---

### Post by mikewhatever on 2007-03-22
If your hardware is unsupported by Ubuntu, there is really not too much you can do. Trying another distro, Knoppix for that matter, is a good idea. Perhaps Ultimate Ubuntu will work.

---

### Post by K7AAY on 2007-03-22
It HAD worked, when it was provided, with 6.06LTS; but, the user blew it away when they installed FreeDOS to support some ham programs. Now, I need to figure out how to get back to square one, but it DID work a month ago, so the hardware is not Unsupported.

---

### Post by mikewhatever on 2007-03-22
> **K7AAY said:**
> It HAD worked, when it was provided, with 6.06LTS; but, the user blew it away when they installed FreeDOS to support some ham programs. Now, I need to figure out how to get back to square one, but it DID work a month ago, so the hardware is not Unsupported.

Oh, I thought you were trying a clean install and not a fix. Sorry for misunderstanding.

---

### Post by K7AAY on 2007-03-22
> **mikewhatever said:**
> Oh, I thought you were trying a clean install and not a fix.
I DO want a clean re-install. 
The user wiped the ext3 and swap partitions, so I am starting over from scratch, which would be a clean install.

---

### Post by djpenguin on 2007-04-17
> **K7AAY said:**
> Dell Inspiron 8100.

Knoppix 5 can recognize the video OK (1024x768), but no recent Ubuntu (6.06LTS, 6.10 and current Feisty Faun) can.

Video 's OK until about 1/3 of the way across the screen, where the rest of the screen is covered by another rendition of the first part of the screen. Can't read the dialog boxes to do an install. Booting with vga=771 does not work, either.

How can I get Ubuntu to recognize the video hardware?

Thank you in advance.
73s and best regards,
K7AAY

I'm having the exact same problem with an Inspiron 8000 while trying to install 6.10.   Anybody know a solution/workaround for this?

---

### Post by lazlor on 2007-04-20
For some reason the HorizSync isn't detected for some LCDs on this guy.

When starting up I chose the 1400x1050 VGA option

After boot, I dropped to a shell ont tty1 and add:

HorizSync 28-100

to the Monitor Section of the /etc/X11/xorg.conf file.

Then go back to tty7 and ctrl-alt-backspace, should come up in full res.

Do the install. You might have to do this again after first boot into the OS. 

Haven't gotten there yet.

---

### Post by psyke83 on 2007-04-25
See: [http://ubuntuforums.org/showthread.php?t=167670](http://ubuntuforums.org/showthread.php?t=167670)

---

