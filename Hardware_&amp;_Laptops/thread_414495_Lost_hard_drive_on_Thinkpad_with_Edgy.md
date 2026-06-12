---
title: "Lost hard drive on Thinkpad with Edgy"
date: 2007-04-19
forum: Hardware &amp; Laptops
---

### Post by Mopana on 2007-04-19
So I'm pretty new to Ubuntu and Linux. I installed Edgy Eft on a Thinkpad T40p with Windows XP sp2 on its 40 gig hard drive. I wanted a dual booting system.

I initially made a small partition(~4 gigs) for Ubuntu and left the rest for Windows. Once Ubuntu successfully installed, however, I could not boot into Windows. I liked Ubuntu, so I used Gparted to repartition so Ubuntu had ~8 gigs. I ultimately needed Windows, so I decided to reinstall it on the other partition. 

During this installation, Windows demanded that I format the entire hard drive, both partitions, to NTFS. I decided just to format the whole thing and start fresh; I'd reinstall Ubuntu later. During this installation, however, file copying stalled and the installation failed. I restarted and tried to install again. This time Windows could not find the hard drive. This upset me, so I tried to install Ubuntu again, but I encountered the same problem. Neither Windows nor Ubuntu could recognize my hard drive. I eventually just bought a new one.

So, in conclusion, I repartitioned twice and formated to NTFS twice with Windows setup. Did I screw my hard drive up in this process? Is there some inherent danger in dual booting systems? Am I better off dual booting with two separate hard drives?

Additionally, is there any way to save my old hard drive? I don't need any data. I just want to use it.

Thanks for any help!

---

### Post by Mopana on 2007-04-20
Perhaps my first post was too vague.

I installed Edgy Eft over a previous Windows XP hard drive in the hopes of making a dual boot system. I repartitioned in Ubuntu setup. Ubuntu loaded fine, but Windows could never boot. I would get an error message "Disk error. Press Ctrl+Alt+Del to restart"

Throughout this entire time I could mount Windows in Ubuntu and read files. 

I repartitioned with Gparted to increase Ubuntu space and decrease Windows. 

Trying to reinstall Windows on the NTFS partition, I booted from the Windows setup CD and tried to format the NTFS space. Windows would not let me do this, but offered to format all partitions, including Ubuntu space. I did a normal NTFS format of the entire drive. File copying in setup immediately after this failed ~85% through. I restarted and booted from the Windows setup CD again, but this time my hard drive was not found.

I booted from the Ubuntu liveCD and tried to reinstall it, too. Again, Ubuntu could not find my hard drive.

Booting from the hard drive itself gives me the error message: "NTLDR is missing. Press Ctrl+Alt+Del to restart"

I know practically nothing about bootloaders, GRUB, NTLDR, or any such things.

Thanks.

---

### Post by Mopana on 2007-04-21
Found a solution.

In case any one else has this problem...

Simply boot from Windows setup CD and enter the recovery console. Type fixmbr. Once I did this, I could install both linux and Windows without problem.

I guess I corrupted both MBR and GRUB when I tried to format both partitions at once. I still don't understand why neither Windows nor Ubuntu setup could detect the hard drive. Once MBR was fixed everything seemed to be fine.

---

