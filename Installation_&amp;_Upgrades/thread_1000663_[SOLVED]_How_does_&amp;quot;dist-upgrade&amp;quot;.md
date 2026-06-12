---
title: "[SOLVED] How does &amp;quot;dist-upgrade&amp;quot; find the intial grub menu.lst options?"
date: 2008-12-03
forum: Installation &amp; Upgrades
---

### Post by littlebat on 2008-12-03
I am using Xubuntu8.04, below is the part content of menu.lst which generated when installed system initially:
> 
root (hd1,0)
kernel /vmlinuz-2.6.24-19-generic root=/dev/md0


Later, I moved my system to another place and edited the menu.lst manually like below:
> 
root (hd0,0)
kernel /vmlinuz-2.6.24-19-generic root=/dev/sda3


When I executed "sudo apt-get dist-upgrade" to upgrade the system, kernel 2.6.24-22-generic was installed newly, when upgrade tool updated "menu.lst", there are some options, the first is "install the package maintainer's version", the second is "keep the local version currently installed", I selected the first option, upgrade tool generated menu.lst come with the options when I installed system initially, like below:
> 
root (hd1,0)
kernel /vmlinuz-2.6.24-19-generic root=/dev/md0


How does dist-upgrade find the menu.lst options of the system installed initally? Where is the system to keep the information of the menu.lst when system was installed initially? 

I guess a bug I reported maybe related with this. This bug is ("Segmentation fault" after "apt-get dist-upgrade" for Hardy) [https://bugs.launchpad.net/ubuntu/+bug/297546](https://bugs.launchpad.net/ubuntu/+bug/297546) . But, I can't reproduce this bug and can't find the crux of the problem. Maybe, bug "https://bugs.launchpad.net/ubuntu/+bug/297546" isn't a bug, it was produced by my mistake.

Thanks.

---

### Post by littlebat on 2008-12-05
Hi, if anyone have run into the same situation?
I have tried my best to look for the answer, but I failed.

If I didn't express my meaning clearly? Please tell me. My english is a bit poor.

---

### Post by confused57 on 2008-12-05
If I understand your problem correctly, you may need to change the line beginning with kopt in your menu.lst:
[http://users.bigpond.net.au/hermanzone/p15.htm#kopt](http://users.bigpond.net.au/hermanzone/p15.htm#kopt)

---

### Post by littlebat on 2008-12-06
> **confused57 said:**
> If I understand your problem correctly, you may need to change the line beginning with kopt in your menu.lst:
[http://users.bigpond.net.au/hermanzone/p15.htm#kopt](http://users.bigpond.net.au/hermanzone/p15.htm#kopt)

Thanks. I think you have answered my question. It is the time I learn GRUB deeply now.:)

---

