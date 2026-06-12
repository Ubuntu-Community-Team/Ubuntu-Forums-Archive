---
title: "cdrom speedup"
date: 2005-11-09
forum: Hardware &amp; Laptops
---

### Post by missmoondog on 2005-11-09
Guess this is somewhat of a hardware issue.
Saw this on the howto page about speeding up cdrom,

Q: How to speed up CD/DVD-ROM?

   1. Read General Notes
   2.

e.g. Assumed that /dev/cdrom is the location of CD/DVD-ROM

   3.

sudo hdparm -d1 /dev/cdrom
sudo cp /etc/hdparm.conf /etc/hdparm.conf_backup
sudo gedit /etc/hdparm.conf

   4. Append the following lines at the end of file

/dev/cdrom {
       dma = on
}

that wouldn't have any effect on being able to burn cd's faster than 12x without errors, would it?

thank you

---

### Post by Leif on 2005-11-09
yes, it would. you need to turn dma on to speed things up.

---

### Post by missmoondog on 2005-11-10
heck! didn't even see the last line of that (dma on). it is.

duh!!

thanks

---

