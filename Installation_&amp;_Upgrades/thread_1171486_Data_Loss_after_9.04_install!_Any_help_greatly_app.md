---
title: "Data Loss after 9.04 install! Any help greatly appreciated"
date: 2009-05-27
forum: Installation &amp; Upgrades
---

### Post by pandaconda on 2009-05-27
Ok, so here's the deal.  Big points to anyone who can sort this out, as I couldn't find a problem like this in any forum.  A week ago I had Vista running on a RAID 0 array (not exactly sure if it is fakeraid or whatever, but it is controlled by my mobo) with another HD for media files, etc.  I decided to install Ubuntu with a Wubi CD, but instead of doing an actual Wubi install, I decided to try to do a standard dual-boot setup wherein Ubuntu has its own partitions (this was my big newb mistake).  

Long story short, I tried at first to install to the RAID drive, not realizing that Linux doesn't recognize RAIDs the same way.  This didn't work with the GRUB OS chooser, so I installed it again on the stand-alone drive I have.  This also didn't work, so I was forced to simply unplug the RAID drives and boot in Ubuntu from the stand-alone.  

So now Ubuntu works flawlessly (and I love it).  But the problem is that my Windows install, along with all 600GB of data that is in the same partiton, is not inaccessible to me.  When I try to recover Vista, it says that everything is fine, so I suspect there is just the problem of the GRUB "hiding" windows or whatever.  When I try to boot from the RAID drives (with the other unplugged) I get a GRUB error.  I have deleted all the partitions I made for that first Ubuntu install (which I never actually was able to boot into) thinking that this would get rid of the GRUB as well.  I guess it didn't, and now my computer is as confused as me about where the Vista install is.  I've tried a super GRUB disk, too, but wasn't really able to figure out how that works.

All I'm trying to do here is boot back into Windows without having to completely wipe my 600GB of data.  I think this may involve completely wiping the GRUB so the Vista install can be found?  I want to do this so I can do an actual Wubi install within Windows directories and eventually make my life a lot easier.  I would just run Ubuntu exclusively, but I want the option of playing games from time to time and the ability to get all my files back.

Thank you so much for any help, and just let me know if you need any more info!

---

### Post by wkulecz on 2009-05-27
You need to boot your Vista CD and have it "reapir" the boot loader.  I don't use Vista but Grub overwrites the MBR. the Windows boot repair will overwrite Grub.

Since I don't use Vista beyond having installed the two RC downloads before it was released, I can't be more specific.

--wally.

---

### Post by ronparent on 2009-05-27
Excellent suggestion by wkulecz to get your windows up and running again. My follow up suggestion is to boot from the ubuntu live cd and start a terminal session (>Applications>Accessories>Terminal). From there enter **sudo grub** to start a grub session. At the grub prompt enter **find /boot/grub/stage1**. The output from this last command will tell you in grub terms where your ubuntu install is. Copy that the command root **(hdx,y**) (entering the actual numbers) followed by **setup (hdx)**. The ouput of this last command will indicate if you have successfully writen the grub bootloader to the mbr of the drive ubuntu is installed on. You should then set that drive as the boot drive in your bios. So set you can now boot to ubuntu. You will probably have to edit the /boot/grub/menu.lst to find windows since the boot order is now shuffled. I can't anticipate where windows will be located in grub terms except that it will probably be either (hd1,0) or (hd2,0). That being so you will probably have to add map commands to the windows boot up instructions in menu.lst so that a workably series of commands will tke the following form:

title <Windows whatever you want to call it>
rootnoverify (hdx,0)
map   (hd0)   (hdx)
map   (hdx)   (hd0)
chainloader   +1

Post here if you run into any trouble.

ps: with the windows mbr fixed you can access either operating system by setting the bios to boot from the drive it's installed on.

---

### Post by Mark Phelps on 2009-05-28
Your Vista "repair" will require booting from a Vista DVD and running Startup Repair -- not once, but several times -- until it finally works or you give up.  Evidently, it stops with the first error it finds, fixes that, and exits.  You have to keep running it again and again until it finds no more errors.

Yeah, I know, amazing utility this ... but that's what you get from MS.

---

