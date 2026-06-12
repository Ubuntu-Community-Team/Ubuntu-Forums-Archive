---
title: "Vista, XP, and Ubuntu: multiboot help!"
date: 2009-04-12
forum: Installation &amp; Upgrades
---

### Post by russet_wolf on 2009-04-12
I'm working on gtting my father's computerto be able to booth these three OSes. Vista was nstalled first, then Ubuntu 8.10 and last, Vista. I reintalled the GRUB loader, and I have no problem booting into Ubuntu and XP, but I can't figure out how to get Vista to be bootable from GRUB as well. Any help appreciated!

---

### Post by ispyamoose on 2009-04-12
I would check your boot.ini file in XP.

I have had all three operating systems installed at the same time, so I know it works. I had XP installed first, then Vista, then Ubuntu.

---

### Post by lisati on 2009-04-12
> **ispyamoose said:**
> I would check your boot.ini file in XP.

I have had all three operating systems installed at the same time, so I know it works. I had XP installed first, then Vista, then Ubuntu.

The order ispyamoose suggests can sometimes make it easier: Windows first then Ubuntu. Part of the reason for this is that the Ubuntu installer copes better with another OS being on the system than Windows.

---

### Post by meierfra. on 2009-04-12
> Vista was installed first, then Ubuntu 8.10 and last, Vista.

???  Did you install XP last?   Then  XP  would have overwritten the Vista boot loader. You can restore the Vista boot loader with EascBCD:

[http://neosmart.net/wiki/display/EBCD/Installing+XP+After+Vista](http://neosmart.net/wiki/display/EBCD/Installing+XP+After+Vista)

---

### Post by ispyamoose on 2009-04-12
> **lisati said:**
> The order ispyamoose suggests can sometimes make it easier: Windows first then Ubuntu. Part of the reason for this is that the Ubuntu installer copes better with another OS being on the system than Windows.

What you said is certainly true. 

Vista uses a different file for its "boot.ini." Rather than using that, it uses BCDEDIT. That could be part of the problem.

---

### Post by russet_wolf on 2009-04-13
I've tried the EasyBCD method, but it only restores the Vista bootloader, overwriting the one for XP. This doesn't solve my problem, since I want to be able to boot both XP and Vista. 

As for installation order, I have to install Vista first because the CD that came with he computer is stubbornly just a "recovery" disk and reformats and partitions the hard drive to the factory defaults, installing Vista, and wiping everything else. should I reinstall in the order: Vista, XP, Ubuntu? Will it make a difference from the current order of Vista, Ubuntu, XP?

---

### Post by rage9 on 2009-04-13
I'm working on the same thing, I had vista first, then linux.  All was good.  Added XP, XP over wrote grub.  Reinstalled linux, but now when trying to boot into vista it instead loads XP.

---

### Post by meierfra. on 2009-04-13
russet_wolf:

> but it only restores the Vista bootloader,

???
EasyBCD lets you add XP to the Vista boot loader.
Did you do this part of the instructions: 

> 5.  Once that's done, head on to the "Add/Remove Entries" page and select "Windows NT/2k/XP/2003" from the drop-down list, give it a name, then press "Add Entry" to finish.


rage9:  Try EasyBCD:

[http://neosmart.net/wiki/display/EBC...XP+After+Vista](http://neosmart.net/wiki/display/EBC...XP+After+Vista)

---

### Post by russet_wolf on 2009-04-13
Yes, I followed those instructions to the dot, mierfra. Everything went smoothly until I got to the Vista bootloader. It gave me both Vista and XP options to boot, and Vista worked fine, but when I tried XP it told me that it could not boot. (I don't recall the exact message, though if it would help I could do it all again and scribe it here.)

I'm not sure if my grasp of the problem i correct, but I think if I could just install the Vista bootloder on the Vista partition and the XP bootloader on the XP partition, and then direct GRUB to the correct location, it could solve my problem. However, I have no idea how to do that.

---

### Post by meierfra. on 2009-04-13
> I don't recall the exact message, though if it would help I could do it all again and scribe it here.)

You don't have to do it all again. Just the very last part. What error error messages to  you get when you try to boot XP from the Vista boot menu.

> I could just install the Vista bootloder on the Vista partition and the XP bootloader on the XP partition, 
That should work and I can show you how to do that, but I would like to see that error message first.

---

