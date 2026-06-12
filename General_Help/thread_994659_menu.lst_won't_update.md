---
title: "menu.lst won't update"
date: 2008-11-27
forum: General Help
---

### Post by Girya on 2008-11-27
I upgraded to 8.10 and when I run cat /etc/issue I get the following so I assume I have 8.10

> 
Ubuntu 8.10 \n \l

then I run uname -a and I get

> Linux kevin-desktop 2.6.24-19-generic #1 SMP Wed Aug 20 22:56:21 UTC 2008 i686 GNU/Linux

Then I Checked menu.lst and my boot options are: 
> 
title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/vmlinuz-2.6.24-19-generic root=UUID=a4f5c078-1c65-41a4-9224-920f8a09e35d ro quiet splash
initrd		/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,0)
kernel		/vmlinuz-2.6.24-19-generic root=UUID=a4f5c078-1c65-41a4-9224-920f8a09e35d ro single
initrd		/initrd.img-2.6.24-19-generic

So apparently I have 8.10 but I can't boot it. 

Any help would greatly appreciated.

This all came about when I tried to install virtualbox and got an error about my kernal version so I started looking around and noticed these inconsistencies.

---

### Post by logos34 on 2008-11-27
you apparently have a separate /boot.  Run 

sudo [update-grub]("http://www.fifi.org/cgi-bin/man2html/usr/share/man/man8/update-grub.8.gz")

The 'groot' line in menu.lst should read (hd0,0)

Also check /etc/kernel-img.conf

You can also just manually add a 8.10 entry just above the current 8.04 one, pointing to the Intrepid vmlinuz- and initrd.img-

---

### Post by thestig_992 on 2008-11-27
haha i'd listen to someone who has 3 grub websites in their signature...XD

Anyway, shouldnt be too hard to work out how to manually add 8.10. just cut and paste the 8.04, change the title and the image

---

### Post by Xiong Chiamiov on 2008-11-27
The only part where 8.04 is specified in your menu.lst is in the title attribute, which only affects what you see in the grub menu.  You can change it to whatever you like, and it will not affect anything.

More important is your kernel, which you can see is 2.6.24-19-generic in both what you're running, and your menu.lst (although, of course, your menu.lst will change which kernel you boot, and thus the output of uname; I'm not sure what the most updated kernel for Intrepid is, though).

---

### Post by Girya on 2008-11-27
Thanks everyone for your sugeestions. We have company for Thanksgiving and   my wife has been monitoring my computer usage :) so I'll try your sugestions as soon as I get a spare moment. Gotta go mash the potatoes.

---

