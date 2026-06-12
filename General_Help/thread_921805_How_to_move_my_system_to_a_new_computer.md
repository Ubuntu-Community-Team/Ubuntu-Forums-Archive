---
title: "How to move my system to a new computer?"
date: 2008-09-16
forum: General Help
---

### Post by CaptSaltyJack on 2008-09-16
I'm curious, if I wanted to take my existing Ubuntu setup and move it to a totally different computer, how would that work out?  One issue is getting the data moved, but the other is that the motherboard and CPU would be different, so I'm not so sure I can just copy files over and boot up and expect it to work.

How do I go about doing this?

---

### Post by rjack on 2008-09-16
Did you customize your kernel?

If you are using the standard (= generic) kernel that comes with the distribution there are no issues at all, just make sure that the target machine has the same architecture of the source machine (e.g. I think you can't move a AMD64 installation to a x86 machine -- but I can be wrong).

Probably xorg will fail to load on the new machine because the ubuntu installation configured xorg.conf for the source machine's video card.

Just run ```
sudo dpkg-reconfigure xserver-xorg
``` if this happens.

---

### Post by Peter Frank on 2008-09-16
Here is a comprehensive guide about how to move a Linux system:
[http://beans.seartipy.com/2006/09/24/moving-a-gnulinux-installation-to-a-different-partition/](http://beans.seartipy.com/2006/09/24/moving-a-gnulinux-installation-to-a-different-partition/)

Basically you need to use 'cp -a' in copying, to preserve symlink etc.,and you might need to edit "/etc/fstab" and "/boot/grub/menu.lst".

Something important which is not mentioned in the website: you should move /boot first, and the rest of the stuff on your filesystem afterwards, to ensure that the /boot folder is at the first 8G of the new partition, otherwise Grub might fail.

I once moved my Ubuntu into a USB hard disk and it did work on another computer, although X need to be reconfigured.

---

