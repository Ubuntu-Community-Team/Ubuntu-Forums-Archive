---
title: "Newbie Install Questions"
date: 2005-01-18
forum: Installation &amp; Upgrades
---

### Post by midnightfxgt on 2005-01-18
Hey guys!

Just checking out the sites, as I am interested in learning some more linux.  This will be my first real install, and wanted to make sure I am all set.  I have install Linux about a year ago at school, on a school machine, so I am a bit rusty :)

HDD Layout:

10GB NTFS drive with WinXP installed
60GB NTFS drive for Windows Apps/storage

10GB that will be added via an IDE Controller (Promise brand).

My questions:

Can I simply install Ubuntu on the 10GB empty drive and expect all to boot well?  Does Ubuntu have a loader that will allow the option to boot between Windows and Ubuntu?  Also, when partitioning the drive what are some good default partitions, and sizes.  Things like /var, /home etc etc.

TIA!
~JOHN

---

### Post by wallijonn on 2005-01-18
With just 10G I wouldn't even think of setting up different partitions (like /usr, /var, etc) ans would just take the defaults.

I would disconnect your WXP HD from the system, set the new 10G as Master and try to install Ubuntu; it may have a problem with Promise Controllers.

If everything worked fine under Ubuntu I would make the new 10G drive a Slave and connect both HDs up and use the BIOS to select which HD to boot into or create a GRUB boot floppy and set the BIOS to boot from the WXP drive unless the floppy was inserted. 

No fuss, no mess.

---

### Post by midnightfxgt on 2005-01-18
[QUOTE=wallijonn]With just 10G I wouldn't even think of setting up different partitions (like /usr, /var, etc) ans would just take the defaults.

I would disconnect your WXP HD from the system, set the new 10G as Master and try to install Ubuntu; it may have a problem with Promise Controllers.

If everything worked fine under Ubuntu I would make the new 10G drive a Slave and connect both HDs up and use the BIOS to select which HD to boot into or create a GRUB boot floppy and set the BIOS to boot from the WXP drive unless the floppy was inserted. 

No fuss, no mess.[/QUOTE]
 OK.... Maybe I will Have the WINXP as master (what it is now), and put the "Storage" drive onto the controller.  Then the "Ubuntu" HDD can be a slave drive, and I can install from there.

Is there any easy was to have a boot loader come up with the option between Windows and Linux?  I can make a boot disc easy enough i suppose, but would rather the option.

Thanks again
~JOHN

---

### Post by Umachines on 2005-01-18
Well, some bios let you choose between boot devices by just pressing certain key at post. I used to have a machine with dual boot this way.

---

