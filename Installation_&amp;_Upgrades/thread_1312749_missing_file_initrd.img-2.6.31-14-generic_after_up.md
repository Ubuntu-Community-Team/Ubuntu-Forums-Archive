---
title: "missing file initrd.img-2.6.31-14-generic after update from 9.4 to 9.10"
date: 2009-11-03
forum: Installation &amp; Upgrades
---

### Post by Pierre92 on 2009-11-03
Hello,

I have just automaticly updated my Ubuntu 9.4 to 9.10.
On reboot the system stops with the following messages :

init : mountall main process (763) terminated with status 1
General error mounting filesystems.
A maintenance shell will now be started.
CONTROL-D will terminate this shell and re-try.
Give root password for maintenance
(or type Control-D to continue):

if I type Control-D the logo Ubuntu appears, then it turns white
with the message :
***something unreadable *** 478f-9275-ce01b8bc057c
/tmp waiting for (null
swap: waiting for UUID=fa8d0147-c541-45a1-8765-3906e17878f1

I searched different forums and found that the grub menu.lst file is inadequate. But I also found that the file /boot/initrd.img-2.6.31-14-generic is missing.

Any idea ?

---

