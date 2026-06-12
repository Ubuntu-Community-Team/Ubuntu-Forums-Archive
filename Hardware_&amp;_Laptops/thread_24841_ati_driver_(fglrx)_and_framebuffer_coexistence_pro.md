---
title: "ati driver (fglrx) and framebuffer coexistence problem"
date: 2005-04-08
forum: Hardware &amp; Laptops
---

### Post by n2024 on 2005-04-08
I've just installed without too many problem fglrx driver for my ati 9600 mobility on my medion laptop.
I have 2100 fps on glxgears So that's ok!

But I have a 2.6.10 custom kernel with vesafb activated
here's my grub line

kernel /boot/vmlinuz-2.6.10 root=/dev/hda1 ro video=vasafb:ywrap,mtrr,1200x800 quiet splash

And each time I switch to console (CTRL + ALT + F1) and switch then back to X (CTRL-F7), the screen is corrupted and the only thing to do is to kill and relaunch gdm.

I'searched accrosss the web and found some post saying that there was problems with fglrx drivers and radeon framebuffer. They say that the solution is to use vesafb framebuffer.
In fact I noticed that when I disactivate framebuffer everything is OK! But I really need it!
 
My questions : 
I'm not using radeonfb but vesafb. But vesafb (for me) needs the radeon framebuffer being activated in kernel. When I disactivate it in the kernel , I have no more framebuffer! Is it normal or am I missing something?  

I searched the web about that problem and find out that there wasn't lots of people talking about this problem! Is there someone with some ati cards and framebuffer not having this problem?

Thanks for response!

Ciao

---

### Post by KraXooR on 2007-07-20
kernel /boot/vmlinuz-2.6.10 root=/dev/hda1 ro video=**vasafb**:ywrap,mtrr,1200x800 quiet splash
speeling typo??
correct-->
kernel /boot/vmlinuz-2.6.10 root=/dev/hda1 ro video=**vesafb**:ywrap,mtrr,1200x800 quiet splash
Also ATI have their own framebuffer support e.g **intelfb**

plus i dont think that resolution is supported under the VIDEO statement.?

D.

---

