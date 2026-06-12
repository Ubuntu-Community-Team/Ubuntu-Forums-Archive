---
title: "dual boot windows 7 RC and ubuntu, i'm a newbie."
date: 2009-06-22
forum: Installation &amp; Upgrades
---

### Post by superflychick on 2009-06-22
Hi, 
 
Apologies in advance if this has been posted multiple times. I'm currently running windows 7, but am wanting to learn some linux... so I want to set my computer up to dual boot. I haven't found a lot of information online, but from what I've read, it seems like I am likely to run into problems. So I guess my first question is whether this will be a tricky install, or does the dual boot work well for most people with a few exceptions? 
 
Also, I am switching from win 7 beta to RC, so I plan on doing a clean install, and creating the partition for ubuntu during the windows install (instead of using the "shrink disk" tool... i already tried, and could not shrink enough despite having 70 gigs free.?..). I have a 90 gig hard drive, and am thinking of partitioning 60 gigs for windows, and 30 gigs for ubuntu? Would this be enough room, too much? I usually keep most of my files (music, pics) on an external. Also, I am a little unclear on how shared disc space for windows and ubuntu works? Do I only need to set aside space for ubuntu program files, and are my documents saved to a shared space with my windows documents? 
 
Also, I haven't done the installs yet, more fact finding, so I have less of a chance of f-in up the install. 
 
Any help would be appreciated. Links are fine too, if don't have room/time to explain. 
 
Thanks, KT

---

### Post by konqueror7 on 2009-06-22
i've had the experience of having a dual-boot windows7 and ubuntu, but mine was the other way around, ubuntu first, last windows7. i've had to restore my GRUB after that.

in your case, its a good thing that you will install windows(7) first. the dual-boot procedure is pretty much straightforward and is very similar to dual-booting vista & ubuntu.

about your partitions, usually some people like to separate their "home" directory (you can refer to your guide for that), but i usually have all in one partition.

a good thing also is, try ubuntu on the live-cd first, see if it works well for you, get the feel for it, then you can install it.

if any problems may occur, you can always come back to the forums. ;)

---

### Post by swerdna on 2009-06-22
Hi

> I have a 90 gig hard drive, and am thinking of partitioning 60 gigs for windows, and 30 gigs for ubuntu?
Looks good to me.
> I am a little unclear on how shared disc space for windows and ubuntu works? Do I only need to set aside space for ubuntu program filesYou need to have space for the /home territories where Linux users normally store personal files like documents, downloads, media etc etc. The /home/john directories are in every way like the "Docs and Settings"/john directory of windows.
> and are my documents saved to a shared space with my windows documents? No is the short answer. But you can access the windos NTFS directories with read-write access after the installation is over. You "mount" the NTFS partition in the Linux filesystem so it appears just like a normal directory.

So go ahead -- and ask questions as they occur during your new voyages. We're here to help you.

---

### Post by T.J. on 2009-06-22
If you are new to Linux and want to explore totally without fear, I'd use the Windows version of VirtualBox (totally free download from Sun Microsystems), and then install Linux as a guest operating system.

The reason I'm suggesting that is:

1) The regular Ubuntu disc is not very friendly when using Windows 7 or Vista.

The reason for this is complex, and not Linux's fault.  They changed the way that Windows boots with TPM.  Windows refuses to share, and wants to be the only OS on the drive. You cannot boot Windows 7 or Vista using the Ubuntu bootloader, and if you just take the defaults, Ubuntu may chew up the Windows MBR.  If it does, Windows will refuse to boot until you use the install disc to repair Windows.

2) If you decide Linux isn't for you, all that you would have to do is delete the  .VirtualBox folder in your Documents and uninstall VirtualBox.

3) You don't have to repartition.  VirtualBox puts itself between Windows and Linux, so that if you run a bad command, the worst thing that will happen is that you reinstall Linux.  Unless you share folders, Windows is safe if you make a mistake.
 
4) You don't need to worry out setting up the proper bootloader.


There are tradeoffs of course.  Running Linux under VirtualBox means it a bit slower, and it only has limited access to the hardware, but Linux really won't care.  

Video and 3D graphics will take a performance hit, but everything should run normally.

---

