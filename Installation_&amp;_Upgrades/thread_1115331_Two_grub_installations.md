---
title: "Two grub installations"
date: 2009-04-03
forum: Installation &amp; Upgrades
---

### Post by risingsun on 2009-04-03
After issues with debian (only booting 1/10 times due to some issuing mounting the / filesystem) I decided to switch to Ubuntu. :)

However, I had windows on sda and debian + grub on sdb. I cleared the sdb partitions and installed ubuntu instead on sdb. However it appears that ubuntu didn't replace the grub installation on sdb one but instead installed it on sda. Now this isn't giving me any issues, it just means that if i try to boot from the sdb drive instead of sda I get a grub error 15 since the files for that particular installation that it used to use are no longer where it expected them to be. (The grub on sda works fine.) 

This isn't a problem, I was just planning to try and keep sda as it was so I could boot direct to windows without issue if need be. I'm certainly not going to go messing around with the working grub installation though, too many experiences where I always manage to break something. :P

Is there any way I can clear this up (maybe point it to the files the working installation is using?) or should I just ignore it and stick to booting from sda?

---

### Post by Herman on 2009-04-03
It's entirely up to you, but let's think about what's going to be the easiest and most convenient for you.
If you decide to restore the MBR boot code in your first hard disk for pointing to the Windows boot loader, it'll be easier to boot Windows. 
But then when you want to boot Ubuntu you'll always have to do the extra work of watching for the opportunity to get into your BIOS boot menu as your computer is booting up and pressing whatever key it is at the right time before it's too late, and selecting hard disk 2.

I'd leave it as it is.

If you want to, (since Windows is a system that requires rebooting very many times when you try to use it), you can edit your /boot/grub/menu.lst file in Ubuntu to make Windows  be selected automatically to boot from GRUB, (if you're not watching), or you can even make it appear at the top of the boot list.
Here's a link that should help you do that, [default        0]("http://users.bigpond.net.au/hermanzone/p15.htm#osprefernc")

---

