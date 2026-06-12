---
title: "Can't Adjust brightness on Acer 5750 laptop"
date: 2012-02-07
forum: Hardware
---

### Post by Plasmah on 2012-02-07
I have an Acer 5750 i5 HD 3000 lappy
I could not for the life of me figure out how to get around that annoying adjust brightness issue. Till now!

Here's what worked for me:

Simply reboot and while your system is at the GRUB screen before you choose what OS to boot (make sure you hit one of the up/down arrows to stop timer first!) Now you can use the FN+arrow keys to change your brightness!

Out of all the fixes on this forum about this problem the above was the only one that worked for me.

Thanks whoever first posted this whoever you are. I was so excited I forgot to look at your name LOL ;)

---

### Post by jaceq on 2012-04-14
Hi,

To fix this for good do following:
Edit /etc/default/grub,
modify following line to look like this:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_backlight=vendor"
than save it and run sudo update-grub
Reboot.
Enjoy working brightness control.

---

### Post by killervenki on 2013-02-24
hey thanks buddy, it worked!!:popcorn:

---

