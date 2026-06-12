---
title: "grub2: removing everything but host OS"
date: 2009-11-09
forum: Installation &amp; Upgrades
---

### Post by dijxtra on 2009-11-09
So Karmic has grub2. Nice, now I will finally force myself to learn this new and miraculous grand unified bootloader.

But before I find time to wrestle through documentation, can somebody please tell me how to remove everything but host OS entries from my menu? I have a dedicated (legacy) grub partition which chainloads zillion OSes I have on my box. So I want that zillion entries out of my Karmic grub2 menu.

I spent 10 minutes jostling through tutorials and documentation and what I found out is that I have to edit /etc/grub.d/xx_whatever files which are not plaint menu.lst stuff but real sh scripts which is all extremely cool and everything. I could hardcode my Karmic kernel(s), but then upgrade-grup2 wouldn't add new ones to the list, right? So hardcoding kernels is out of the question. So, can anybody tell me how to leave the kernels of the host OS but remove all the other stuff? Would appreciate it a lot.

Thanks in advance.

---

### Post by Ginsu543 on 2009-11-10
I believe you can easily do what you want by changing the permission bit on the 30_os-prober file in /etc/grub.d. Try the following:

1) Open Terminal and navigate to /etc/grub.d
2) Run "sudo chmod -x 30_os-prober" (without quotes)
3) Run "sudo update-grub" (without quotes)

That should get grub2 to recognize your main kernel and OS without probing for other OSes present on your system.

---

