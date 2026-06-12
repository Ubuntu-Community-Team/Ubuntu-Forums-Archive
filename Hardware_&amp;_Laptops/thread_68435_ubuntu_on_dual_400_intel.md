---
title: "ubuntu on dual 400 intel"
date: 2005-09-23
forum: Hardware &amp; Laptops
---

### Post by marks_linux on 2005-09-23
Getting a used and abused server today, with 2 400mhz intel processors, 1gig RAM and (I think) 2 x 18gig drives. Wanting to set this up as a personal web server for family (mysql,php and apache) and perhaps experiment with personal mail server.

I'm not overly familiar with dual proc systems and wondered if anyone could give me ok/not ok to run Ubunu on this.

---

### Post by varunus on 2005-09-23
This should be ok.  Just install the "smp" kernel package for your system (either linux-386-smp or linux-686-smp) and then reboot, choosing that kernel from the GRUB menu.  (It actually may give you the smp kernel by default.)  SMP = symmetric multi processor; install it to get the benefit of two processors.

---

### Post by marks_linux on 2005-09-30
Ok so got the server, best expectations - dual p2 1 gig and 512 ram.

Now the problems:

seems to have scsi disks + cd-rom attached to scsi controller. On boot up I get a continous beep from the scsi controller. I can't get the server to see a boot disk in the cd-rom device. first ventures into serverland so any advice welcome. Server seems to get past initial POST but won't see a boot device.
M

---

### Post by marks_linux on 2005-10-03
GOt it all working, removed the SCSI controller card and used the motherboard SCSI slots - now running ubuntu fine!

---

