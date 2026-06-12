---
title: "Wubi problem"
date: 2009-03-06
forum: Installation &amp; Upgrades
---

### Post by BlooSam on 2009-03-06
I installed ubuntu using wubi at work and it was fine on a windows xp machine, i downloaded the files, then it asked me to reboot and then it gave me the choice, windows xp or ubuntu at the boot menu..

I did the exact same thing on my vista laptop and the computer just loads vista, no choice or anything.

i can see ubuntu full installed on c:/ but it doesnt give me the option to boot it.


please help:(

---

### Post by lindsay7 on 2009-03-06
Install the "startup manager" using Synaptics. Run it and it should show you what the grub file has listed as os start ups. There is a way to do this thru the terminal too, but this is easy and you can harm anything this way. I am sure someone will tell you how to do this in the terminal. With the startup manager you can choose what the default startup will be.

---

### Post by lindsay7 on 2009-03-06
I found the info,

From within Ubuntu, open a Terminal. then:

sudo gedit /boot/grub/menu.lst

This is the file containing the boot order. Any line begiining with a hash (#) is a comment.

Towards the bottom, you will see the Windows boot instructions. Cut and past so that those instructions precede the boot instructions for your ubuntu. I don't mean put them at the top of the file, I mean relative to the other boot instructions.

Just keep in mind that there are several "sample" boot instructions, commented out.

Save the file, then you can reboot.

What if you made a terrible mistake, and bungled the editing? All is not lost. You can edit that file using something such as a live Linux distribution on a USB stick. Just keep in mind that you need to edit the menu.lst file on your hard drive, not the one within the live Linux distro.

---

