---
title: "How to install if you have the 100MB partition?"
date: 2009-10-30
forum: Installation &amp; Upgrades
---

### Post by Frostmint on 2009-10-30
Ok so I did what I thought was a good idea and manually partitioned Windows 7 so that I had some extra gigs to install Ubuntu on. 

Unfortunately Windows 7 put the bootloader on the hidden 100MB partition, and from what I have heard, installing Ubuntu on a setup such as this will completely wreck Windows.

Is that correct? Anything I can do besides reinstalling Windows?

thanks       :D

---

### Post by Sigma47 on 2009-10-30
I just did this and am still working out the kinks although Win and Ubuntu both boot my setup is slightly unideal. What I did: Make a recovery disk in Win7 then load a live a cd and open Gparted and delete the 100 MB (unless you can do it from diskmgr in Win but I couldn't). Then use your recovery cd and make a dir in Win Partition C:\boot and copy the boot directory on the recovery cd to the newly created C:\boot directory. then copy the bootmgr file to "C:\". Then run bcdedit /fixmbr and then bcdedit /fixboot. Now you should be able to boot Win. I then installed U9.10 on a partition right after my win install but Grub loaded to the old drive where the 100 MB partition was loaded so I don't think I corrected the MBR problem and am working on that now. Its not too big of a deal its just that GRUB loads on my data drive and then starts the sys drive regardless of boot because both OS's are located there. However I am annoyed by this lack of order and am interested in moving my GRUB/MBR to my sys drive. Hope that helps I got some links if you want em.

---

### Post by Frostmint on 2009-10-30
> **Sigma47 said:**
> I just did this and am still working out the kinks although Win and Ubuntu both boot my setup is slightly unideal. What I did: Make a recovery disk in Win7 then load a live a cd and open Gparted and delete the 100 MB (unless you can do it from diskmgr in Win but I couldn't). Then use your recovery cd and make a dir in Win Partition C:\boot and copy the boot directory on the recovery cd to the newly created C:\boot directory. then copy the bootmgr file to "C:\". Then run bcdedit /fixmbr and then bcdedit /fixboot. Now you should be able to boot Win. I then installed U9.10 on a partition right after my win install but Grub loaded to the old drive where the 100 MB partition was loaded so I don't think I corrected the MBR problem and am working on that now. Its not too big of a deal its just that GRUB loads on my data drive and then starts the sys drive regardless of boot because both OS's are located there. However I am annoyed by this lack of order and am interested in moving my GRUB/MBR to my sys drive. Hope that helps I got some links if you want em.Thanks for the info. It might be more practical if I just reinstall 7...I really wonder what Microsoft's motive was for doing this...:frown: However, since I am only using one drive I might be able to install Ubuntu without experiencing the problems you have.

---

### Post by moe_syzlak on 2009-10-30
> **Frostmint said:**
> Ok so I did what I thought was a good idea and manually partitioned Windows 7 so that I had some extra gigs to install Ubuntu on. 

Unfortunately Windows 7 put the bootloader on the hidden 100MB partition, and from what I have heard, installing Ubuntu on a setup such as this will completely wreck Windows.

Is that correct? Anything I can do besides reinstalling Windows?

thanks       :D

You can do a test on your own. Backup all data just in case the system nukes if Windows 7 and Koala kollide.

---

### Post by Sigma47 on 2009-11-01
If you only have one drive your golden, I don't think it would be a problem try it!!!

---

### Post by Mark Phelps on 2009-11-01
> **Frostmint said:**
> ...I really wonder what Microsoft's motive was for doing this...

Contrary to what all the Vista-bashers and MS-haters will contend, MS's motive for "doing this" has nothing whatsoever to do with Linux.

They actually did it to HELP people!!

A common complaint with Vista, which was NOT MS's fault, was that the preinstalled versions nearly always came WITHOUT a recovery CD -- thus, if anything happened that corrupted your Vista OS installation (like, for example, using Linux utilities to shrink the Vista OS partition), you had no way to recover from that.

MS provided an alternative, known as WinRE (Windows Recovery Environment), but burning such a CD required the download and installation of the Windows Automated Installation Kit (WAIK), the creation of a custom Window image, and the hand-creation of a recovery CD -- a LOT to expect anyone to do, let alone most MS Windows users.

So, with Windows 7, on a clean drive, it installs a small Recovery partition at the beginning of the drive which contains not only the boot loader files, but also the repair and recovery tools.  It also provides a built-in capability to burn your own Recovery CD -- without all the hassles of downloading or installing anything.

If this new environment no longer works with the new GRUB (i.e., GRUB2), or with Wubi, that's hardly MS's fault.

---

