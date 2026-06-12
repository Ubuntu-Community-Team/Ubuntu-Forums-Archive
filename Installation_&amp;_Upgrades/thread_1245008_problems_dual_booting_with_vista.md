---
title: "problems dual booting with vista"
date: 2009-08-20
forum: Installation &amp; Upgrades
---

### Post by latestsaint on 2009-08-20
hi... i am using ubuntu 9.04 jaunty.  i installed it on my first partition (25gigs out of 500).  i am trying to install vista on a second partition (around 150gigs) using this howto [http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm]("http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm")

i have just installed vista, booted into livecd, reactivated the grub bootloader, and booted back into ubuntu.  after adding the text into the menu.lst (making windows vista an option in the grub bl), i reboot and select vista, only to find this error:  "error 13 invalid or unsupported executable format"

this is the second time ive been through a windows installation *phew*  neways, i cant figure how to make vista load from grub.  any suggestions?  

or how to restore vista bootloader for that matter???  

thanks for any support :/

j the noob

---

### Post by tommcd on 2009-08-20
Post the output of:
```
sudo fdisk -l
```
and post the Vista part of your /boot/grub/menu.lst. If Vista is on the second partition the grub entry should be (hd0,1) as it says in that tutorial.

This would be much easier if you installed Vista first to the first primary partition. Just leave space for Ubuntu and install Ubuntu onto the free space. Then when grub is installed it should automatically pick up Vista and create a proper entry for it.

And welcome to the Ubuntu forums!

---

### Post by Mark Phelps on 2009-08-20
> **latestsaint said:**
> ... or how to restore vista bootloader for that matter??? 

You would do this by booting from the Visa DVD and running Startup Repair.  You DO have a Vista DVD, right?

---

### Post by Bartender on 2009-08-20
How many people have a Vista DVD?  I'm guessing not many.  Most of us are stuck with "recovery discs".  

That's assuming you made your recovery discs before doing anything dangerous to your computer...

---

### Post by Mark Phelps on 2009-08-20
> **Bartender said:**
> How many people have a Vista DVD?  I'm guessing not many.  Most of us are stuck with "recovery discs". 

Yep -- and  that's thanks to greedy PC suppliers who will gladly sell you $1000 or more work of PC -- but won't include 15-cents worth of plastic (i.e., Vista OEM DVD) with the box so you can recover from a corrupted boot loader situation.

---

### Post by presence1960 on 2009-08-20
> **Bartender said:**
> How many people have a Vista DVD?  I'm guessing not many.  Most of us are stuck with "recovery discs".  

That's assuming you made your recovery discs before doing anything dangerous to your computer...

go [here]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/") for an iso you can burn as image to disk which will give you only the repair function of a Vista disk, it will not install Vista. You can boot from it and run the repair console.

---

