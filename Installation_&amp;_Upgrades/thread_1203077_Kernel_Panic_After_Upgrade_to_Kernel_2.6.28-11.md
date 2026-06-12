---
title: "Kernel Panic After Upgrade to Kernel 2.6.28-11"
date: 2009-07-02
forum: Installation &amp; Upgrades
---

### Post by SILLAT on 2009-07-02
I got some updates yesterday night, after installing the updates successfully i did some light browsing then shutdown and went to bed.
Tonight when i boot up an i get an error message: " Kernel Panic not syncing VFS: unable to mount root FS on unknown block 0,0 " and Ubuntu would not load up :mad:
I did a cold boot and when i reach the grub i press escape and saw that there was two kernel in the menu it had
[COLOR="Blue"]Ubuntu 9.04, Kernel 2.6.28-13 Generic and Ubuntu 9.04, Kernel 2.6.28-11 Generic
[/COLOR] i since booted into kernel 2.6.28-11 and everythings working jus fine i even see updates but i'm not installing them until i understand what has happened an whats the best move to make in the present situation.
How can i remove the new kernel (2.2.28-13) from the boot ? or set the old kernel (2.2.28-11) as the default ?
Whats the Next Best thing to do in a situation like this ? ?
Update: i just notice my initrd.img line is missing from menu.lst under kernel 2.2.28-13
here's how it looks:
title		Ubuntu 9.04, kernel 2.6.28-13-generic
uuid		4914717b-931b-443d-8597-07f41659783d
kernel		/vmlinuz-2.6.28-13-generic root=UUID=c52ec23c-d7d6-4f34-8025-17acaeaba76f ro quiet splash 
quiet

title		Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid		4914717b-931b-443d-8597-07f41659783d
kernel		/vmlinuz-2.6.28-13-generic root=UUID=c52ec23c-d7d6-4f34-8025-17acaeaba76f ro  single


If i get back/add my initrd.img line, will that fixit ??

---

### Post by mvaldez on 2009-07-03
Hi. I think you are not alone:

[https://bugs.launchpad.net/ubuntu/+bug/390984](https://bugs.launchpad.net/ubuntu/+bug/390984)


Regards,

MV

---

### Post by SILLAT on 2009-07-03
Since has no one can help me with this problem, and its happening to alota people; This is my fix for the problem:
I've set my Grub to boot the old kernel (2.2.28-11) by default since the new one (2.2.28-13) is not booting; also I'm ONLY gonna install security updates and NO kernel or initrd.img updates jus to keep my system stable until Ubuntu Karmic 9.10 comes out I'll do a clean install.

Cheers ;)

---

### Post by zipperback on 2009-09-19
I have the same problem.
I just updated on this computer and now it kernel panics on boot right when the screen shows the word GRUB. I can't even press escape in time before a kernel panic.

Right now I'm on the net using the live cd of 9.10 looking to see what happened. I see I am not alone.


- zipperback
:popcorn:

---

