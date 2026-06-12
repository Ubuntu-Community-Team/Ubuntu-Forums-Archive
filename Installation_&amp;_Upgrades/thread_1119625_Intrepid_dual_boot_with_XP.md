---
title: "Intrepid dual boot with XP"
date: 2009-04-08
forum: Installation &amp; Upgrades
---

### Post by BangorOrBust on 2009-04-08
I'm currently running Intrepid on my Toshiba Satellite L355D-S7829 Laptop, and it works great.  However, I want to run some Windows programs and have gotten snagged on WINE and Crossover incompatibility issues which have lead me to once again run a Windows machine.  The problem with this is that when I try to install XP Pro I get a blue screen once windows tries to start its setup.  
I've tried a new hard drive with the same results.  The laptop is not old, only 6 months.  Any suggestions?

---

### Post by Spunkbubble on 2009-04-08
If Windows can't install even on a different hard drive, it sounds like it could be a problem with the installation disc. I'm no expert so I'd wait for an opinion from someone more experienced, but if this proves to be the case, AFAIK you can request another installation CD from Microsoft if you still have a valid key.

---

### Post by mhgsys on 2009-04-08
I guess you cannot install windows Xp true Wine, 
What you need is to set up a dual boot.

[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)

EDIT: maybe I misunderstood you, and you were not trying to install it true wine, anyway: The blue screen your talking about:

Remember that Windows can not read ext2/ext3 partitions, So the partition you want to install Xp in, has to be either Free 
Space, or NTFS
I'm pretty sure it will install when the space is recognized.

---

### Post by sdbrogan on 2009-04-08
An alternative you might want to consider is running XP as a virtual machine inside Ubuntu.  After not having much luck with WINE, I got VirtualBox OSE from the Ubuntu repositories & it was a lot easier than I thought it would be to set up an XP virtual machine & install Windows programs I needed.  Strangely, it seems to run faster than the hardware installation, despite having less RAM available. It also makes back-up/restore of XP hassle-free (copy/paste).

---

### Post by BangorOrBust on 2009-04-08
Well, thank you for the help.  I'm giving VirtualBox a shot right now.  I don't think its the disk unless my friends disk is bad as well.  I think it my have something to do with the sata drives that toshiba uses and having an early copy of XP though i'm not optimistic.  Also trying a RAM test to see if that is an issue which I also doubt since Intrepid is running impeccably on this laptop.  Any other suggestions or help would really be appreciated.

---

### Post by syfroyh on 2009-04-11
If it is the disks drivers, I'd suggest slipstreaming the SATA drivers into your XP CD.

I had an issue recognizing a SATA drive while installing XP Home to an NTFS partition a couple days ago.

Just go here for an extremely easy to do: [http://www.digitgeek.com/how-to-slipstream-sata-drivers-into-xp-cd/](http://www.digitgeek.com/how-to-slipstream-sata-drivers-into-xp-cd/)

Hope this does the job!

Cheers,
Marc

---

