---
title: "No Bootloader"
date: 2010-10-24
forum: Hardware
---

### Post by DemanRisu on 2010-10-24
Jeez. Where to begin?
First, there was Windows XP.
Then, in addition, there were two partitions with Windows 7.
Next came Ubuntu 9.10. I then proceeded to b0rk that. I only have the /usr partition from that now.
Next came Ubuntu 10.10. I b0rked that ten minutes ago by:
Finally, I installed Windows 7 again.

With Ubuntu 10.10, there was no extraneous boot menu - no GRUB, nothing.

When I installed 7, it nullified my ability to boot into 10.10 - a bad thing, since all my documents are contained within Ubuntu.

I then followed a tutorial on these forums to restore GRUB using a LiveUSB - I must have chosen the wrong partition, because now I can't boot into anything.

For what it's worth, I'm using an Eee PC 904HA.

My question: what do?

---

### Post by alexandari on 2010-10-24
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

this is what I suggest. Trust me,I've been there,and it helped me (Super Grub2 Disk)

You can always try the other two :> cheers

---

### Post by DemanRisu on 2010-10-24
What should I do after?

---

### Post by DemanRisu on 2010-10-24
Okay, I'm hoping someone can help me here.
After a lot of terminal majiggery, I now have a grub prompt when I boot up.
I've tried **multiple** times to install GRUB to pretty much any partition I can find - however, the only partition I'm remotely interested in getting to boot at the moment is /dev/sda5 or, in GRUB terms, (hd0,4).
If any of you Ubuntu wizards can help me, please do.

Oh, I'm running 10.10, for what it's worth. I also have multiple DE's installed (LXDE, Netbook, GNOME (my default one), and KDE).

Edit: Booting from a LiveUSB is what it looks like I'm going to be doing until I find a solution - and that'll work for however long I need to do it.

---

