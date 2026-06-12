---
title: "Windows 7 Panic"
date: 2009-11-08
forum: Installation &amp; Upgrades
---

### Post by devi59 on 2009-11-08
I am having the worst luck with this new Karmic then I have ever had. I started trying to install using Wubi and it broke half my system, but it was recoverable on the windows side. Now I installed without Wubi and my system lost my windows side and i just have ubuntu. This would be all bad if I wasnt a remote worker for a telecom company and I need windows to run our software. I have reinstalled Grub2 (6th time at least) and got linux back again after trying Windows Recovery. Of course, the recovery just removes Grub2 and the ability to boot back into ubuntu so I have to boot off the livecd, reinstall Grub2 and I get ubuntu back, then I upgrade grub to add windows back into grub, but it when I boot windows, it shows the windows 7 flag coming together with the 4 colored balls. Before they come together as a full flag, a BSOD flashes for about half a second which I can't read full info on and it reboots. I'm at my wits end, I missed work today and I ABSOLUTELY NEED my windows back. I have tried everything I can think of and I'm about to try Hirens Boot CD to see if it has any luck. Any ideas PLEASE reply!

---

### Post by Intel91 on 2009-11-08
Have you tried viewing your HDDs with a partition editor to see if your original window partition and file system is still intact? If it isn't then there really isn't anything you can do except completely reinstall windows. If it is intact, go to [http://www.matthewjmiller.net/howtos/dual-boot-linux-and-windows/](http://www.matthewjmiller.net/howtos/dual-boot-linux-and-windows/) and refer to Part 2 Steps 4-10.

---

### Post by devi59 on 2009-11-08
> **Intel91 said:**
> Have you tried viewing your HDDs with a partition editor to see if your original window partition and file system is still intact? If it isn't then there really isn't anything you can do except completely reinstall windows. If it is intact, go to [http://www.matthewjmiller.net/howtos/dual-boot-linux-and-windows/](http://www.matthewjmiller.net/howtos/dual-boot-linux-and-windows/) and refer to Part 2 Steps 4-10.

My partitions are running smooth. In fact I can mount all of my partitions in Ubuntu fine (Storage, Recovery, Windows7) and see all my files just hanging out staring me in the face. I don't think it has anything to do with grub now, it is something with Windows not seeing a boot area somewhere or something. I have been trying to fix it using Hirens and I can't load the DOS stuff because of a CD driver or something. I can load Mini XP off the disk, but the Win tools are much more stripped. I am trying to run like a chkdsk on my partitions but even Windows Recovery can't find any valid windows installs.

---

### Post by devi59 on 2009-11-08
I think this is the longest I have ever delt with an issue and not been able to resolve it. At this point I believe I have pinpointed a LARGE problem. I know when I wanted to install Ubuntu it wouldn't let me make a new partition because of the 4 partition limit. I moved all the recovery off the recovery partition and deleted it. I have a feeling that it is possible that that specific partition actually held the SATA drivers for my hard drive because I can NOT get windows to recognize I have my sata drive in my laptop. I have been spending HOURS trying to extract the drivers from the SOFTPAQ that I obtained from HP's website with the SATA drivers. Unfortunately though, even though I FINALLY got them on a USB drive and tried usng both Recovery AND installing fresh it doesn't see the hard drive at ALL for Windows. I believe this is my problem. I have deleted the 100MB system reserved that Windows used, moved that to the windows partition changed GRUB and BCD to recognize that it has been moved to that partition and it STILL won't work. I am tryign to resize right now to remake a partition but I have a good feeling its not going to work because of the way my luck has been going for this weekend.

---

### Post by Mark Phelps on 2009-11-08
The 100MB partition you removed contained the Windows Recovery Environmnent files you needed to fix the Windows 7 boot problem.

If you really do need your Windows 7, your best bet at this point (presuming that you can't reinstall Windos 7 yourself), is to contact HP and see if they will provide you a recovery CD that does not need the recovery partition to restore your Windows 7 install.

However ... your Windows 7 installation just might be salvageable.  Go to the NeoSmart Technology forums, check their EasyBCD support subforums, and you will find links there where you can download and burn a Windows 7 Recovery CD containing much the same recovery files as the partition you destroyed.  Follow instructions in their forums for using that CD to do Startup Repair on your Windows 7 install ... and if you luck out, you might just get your Win7 running again without having to completely reinstall it from scratch.

And THE NEXT TIME, before you go charging ahead trashing things right and left, take the time to search these forums for information about what you're trying to do.  If you had done that, you would have seen post after post after post about folks complaining bitterly about how Wubi, Ubuntu 9.10, and Windows 7 do NOT work well together.

---

### Post by Intel91 on 2009-11-08
It might be worth noting for the community which Windows 7 doesn't work with 9.10 and WUBI, the pre-release or actual release. I had no problems using WUBI on my Windows 7, which at the time was an official late beta.

---

### Post by devi59 on 2009-11-08
Well a couple of hours later, a long wait of EASUS Partition Magic doing its thing and I can actually install windows sort of. It errored right before the end of doing it's thing but at least now windows install can actually see the hard drive. I already moved all the recovery stuff over and changed my boot so it was fine to remove that obnoxius waste of 100mb. I removed it, moved my remaining partitions (storage, win 7 and ubuntu) using EASUS and now I have a functioning HD, now I just need to reinstall windows and cry about losing my data. At least my storage had most of my stuff.

---

### Post by devi59 on 2009-11-09
Well it is solved. I moved my partitions and then it re-wrote the partition table. I lost my windows partition during the move for one reason or another but it wasn't a complete loss. Then I was able to install Windows 7 again and boot from the livecd to reinstall grub back as the bootloader then did a grub-update and it saw the windows partition and all is well with the world again. Too bad I didn't get help on my threads.

---

