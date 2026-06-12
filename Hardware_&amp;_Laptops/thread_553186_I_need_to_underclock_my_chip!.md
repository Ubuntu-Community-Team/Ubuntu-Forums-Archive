---
title: "I need to underclock my chip!"
date: 2007-09-17
forum: Hardware &amp; Laptops
---

### Post by aztektum on 2007-09-17
I have a Thinkpad t41p with a 1.8P4-M and a ATI Mobility 9000.

In Windows AND Ubuntu I get weird video display problems on the internal LCD. On external monitor it's fine.

I noticed the bottom of the machine would get really hot, so I used ATITool in Windows to lower the clock speed of the chip and my problem went away (and I didn't have to drop it much.)

Is there a way to underclock the ATI chip in Ubuntu to see if that solves my issue there as well?

---

### Post by w4ett on 2007-09-17
What you are looking for is CPU Frequency Scaling....see:

[http://ubuntuforums.org/showthread.php?t=248867](http://ubuntuforums.org/showthread.php?t=248867)
[http://ubuntuforums.org/showthread.php?t=190921](http://ubuntuforums.org/showthread.php?t=190921)
[http://ubuntu.wordpress.com/2005/11/04/enabling-cpu-frequency-scaling/](http://ubuntu.wordpress.com/2005/11/04/enabling-cpu-frequency-scaling/)

---

### Post by aztektum on 2007-09-18
Nothing in those links addresses underclocking video chips, just main processors.

---

### Post by w4ett on 2007-09-18
Sorry about the misunderstanding.....

 No, Since your card (the 9000 series/RV250) is not supported by the AMD/ATI fglrx driver....to my knowledge,  the open source driver does not allow for over or underclocking.

Once again, sorry for the misunderstanding.

---

### Post by aztektum on 2007-09-18
no problem, but i found the answer on a goof

rovclock

it's in the repos too. w00t

---

