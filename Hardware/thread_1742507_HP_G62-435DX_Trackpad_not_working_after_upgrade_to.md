---
title: "HP G62-435DX Trackpad not working after upgrade to 11.04"
date: 2011-04-28
forum: Hardware
---

### Post by alanray on 2011-04-28
I've been running 10.10 64bit on my HP G62-435DX laptop for a few months now. After upgrading to 11.04 using the LiveCD, when I boot up the trackpad no longer works. So I tried just logging in using the keyboard to see if it would recognize the trackpad after login, but still no luck. I even tried plugging in an external mouse, but it doesn't recognize that either... Any help?

EDIT
I managed to make it work on my laptop
Open terminal and type the following:

sudo gedit /etc/default/grub/

Note: If you get error stating Grub: File not found (missing)

sudo gedit &#65279;/boot/grub/grub.cfg

Edit the line

GRUB_CMDLINE_LINUX=&#8221; &#8220;

and add

GRUB_CMDLINE_LINUX=&#8221;i8042.nopnp&#8221;

Now run:

sudo update-grub

---

### Post by Bartcore3 on 2011-07-16
i did not find a solution to this problem.. i think they messed up trying to upgrade 10 to 11.. i tried everything but then i just deleted my ubuntu partition and reinstalled it.. 
It's not a solution but at least it's working now! :)

---

