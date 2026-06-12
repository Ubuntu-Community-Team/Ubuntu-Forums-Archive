---
title: "Getting Rid of Vista in a Dual Ubuntu laptop"
date: 2009-06-17
forum: Installation &amp; Upgrades
---

### Post by jcadi001 on 2009-06-17
Guys, i need some help/advice with the following:
My laptop came with windows vista, i tried Wubi and liked it, i partioned my hard drive with EASEUS partition master, my hard drive has 230GB capacity, i partitioned 65GB for Ubuntu and left vista with 108GB , and a recovery partition for vista that came with the laptop. 
I installed Ubuntu following instructions from another source and worked well, i didnt GRUB take control of the boot manager,  i installed GRUB in /dev/sda2 , then i rebooted my PC but it automatically booted in Vista, then i downloaded EasyBCD( or something like that) and added a linux entry to the windows boot manager , the reason is that , i read that  in forums that if u let GRUB take control things could get messy.

now i want to get rid of Vista, can i just format the windows partitions to Ext3 so i can get that free space for my current 65GB Ext Ubuntu installation? 

what will happen to the boot manager if windows vista is gone, since i added the linux entry to the windows bootloader ??

is it better if i just do a clean install and let Ubuntu format everything?  but the thing is that i have configured my machine and installed variuous programs and dont want to loose those settings in Ubuntu. , can i make a backup of all my settings ? ( not files )

thanks in advance

-----
JC

---

### Post by dstew on 2009-06-17
> what will happen to the boot manager if windows vista is gone, since i added the linux entry to the windows bootloader ?If you delete the Windows partition, you will not be able to boot, because that is where the boot loader code is. You could try to retain just the root directory of Windows, maybe then it will boot. I don't know about Vista though, whether the boot loader uses code from places other than the root directory of its partition. Maybe better just to install grub.
> is it better if i just do a clean install and let Ubuntu format everything? but the thing is that i have configured my machine and installed variuous programs and dont want to loose those settings in UbuntuYou can delete the Windows partition, and then expand the Ubuntu partition so that it takes up the unallocated space. Then, your Ubuntu system will still have all its programs and configuration.

---

### Post by raymondh on 2009-06-17
For reference

[http://gparted.sourceforge.net/larry/resize/resizing.htm](http://gparted.sourceforge.net/larry/resize/resizing.htm)
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
[http://orgs.man.ac.uk/documentation/grub/grub_3.html#SEC9](http://orgs.man.ac.uk/documentation/grub/grub_3.html#SEC9)

On this link, at the page index, the last 3 would be interesting for your needs should you decide to re-install GRUB

[http://members.iinet.net.au/~herman546/p15.html#13](http://members.iinet.net.au/~herman546/p15.html#13)

Oh, and this too

[http://www.dewassoc.com/kbase/hard_drives/master_boot_record.htm](http://www.dewassoc.com/kbase/hard_drives/master_boot_record.htm)


Good luck.

---

### Post by Idefix82 on 2009-06-17
I'd also say, reinstall grub first, check that it works, then do as you proposed, namely formatting the Vista partition to ext3.

Alternatively, if you do want to reinstall Ubuntu, Create a separate partition for your /home folder and when you reinstall, tell Ubuntu to use that partition as /home and not to format it. This way you will keep your settings, although not the installed software.

---

