---
title: "Intel 855 - Ubuntu 10.10 Graphics Issues"
date: 2011-03-04
forum: Hardware
---

### Post by talonthegeek on 2011-03-04
Hey Guys,

I've been using 9.10 for a while and have decided to make the jump to 10.10 on my Dell Inspiron 710m. It all seems to work except for the fact that my laptop isn't displaying a picture. I've read on other forums that I have to edit my xorg.conf and somehow access a command line. Can someone please give me some step by step instructions to do this? Sorry in advance for my n00bishness :lolflag:

talonthegeek

---

### Post by Handssolow on 2011-03-06
First thing to try is booting with i915.modeset=1
During the boot process keep the shift key depressed which should take you into Grub2. Press e to edit and add i915.modeset=1 before quiet splash.
Press Ctrl+X to boot and test this configuration.

If this works you'll need to make the change permanent.
sudo nano /etc/default/grub

Then run update Grub
sudo update-grub

There's more but get this working first.

---

### Post by talonthegeek on 2011-04-15
Sorry it took me so long to respond, I had a lot of school stuff and a move to get through. I will try tonight with 10.10 and will post back.

---

