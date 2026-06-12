---
title: "Boot from second partition without changing MBR"
date: 2008-10-23
forum: General Help
---

### Post by 5circles on 2008-10-23
Apologies if I'm using the wrong terminology - If I knew the right words I might already have found a solution.

I'm trying to set up Ubuntu on a laptop without running a dual boot system.  I've had various problems with dual boot in the past, and have some critical things going on in the Windows side right now.  But I wanted to install Ubuntu 8.04 on the partition that I already had set up.

I booted from the live CD, and went through the install process.  When asked installing Grub on HD0, I chose the alternative of installing on the partition with the Ubuntu installation.  [COLOR="Blue"]Was this dumb?[/COLOR]

Then I restarted.  I ran into a problem where the MBR seemed to have disappeared and I wasn't able to boot up at all.  For some reason this seemed to fix itself (perhaps after I booted from the Windows Recovery CD), and now I'm able to start Windows.  

But how can I start Ubuntu from the partition it is loaded on?  I tried loading the LiveCD, but didn't seem to have any option. Can I enter some commands to boot from sda6?  Or can I set up a Flash Drive to do this (I don't think I can boot from a Flash Drive - unless the laptop thinks it is a Floppy).

Thanks
Mike

---

### Post by TeXtonyx on 2008-10-24
If you actually installed grub to the Ubuntu boot partition then 
with Vista you can download Easybcd and add Ubuntu to your Vista
bootloader menu. OTOH, if you dual boot with XP you can download a
program called Bootpart. That copies the first 512 bytes of the
Ubuntu boot partition where you state you installed grub, to the
C:\ drive and writes a menu entry to boot Ubuntu in boot.ini.

Did you mean you installed grub to the Ubuntu boot partition in
Step 7, under Advanced? If yes, then the method above will work. 
If you don't mean grub but some empty partition, then you most
likely wrote grub by default to the MBR. Running the recovery cd
will reinstall the Windows MBR. But since you said grub, one of the
two methods above, Easybcd or Bootpart, free downloads, will work. 
Your description doesn't sound consistent to me.

---

### Post by 5circles on 2008-10-24
Sorry if the description was poor - yes I installed grub with the Step 7 Advanced options - I couldn't remember exactly.  

I installed EasyBCD and that did the trick.  

Thanks!

---

