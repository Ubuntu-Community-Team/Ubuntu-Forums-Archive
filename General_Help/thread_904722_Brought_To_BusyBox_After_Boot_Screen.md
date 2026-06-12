---
title: "Brought To BusyBox After Boot Screen"
date: 2008-08-29
forum: General Help
---

### Post by Kai001 on 2008-08-29
Hey everyone,

     It seems I ubruptly cannot get into my Ubuntu Hardy Heron 8.04 installation. It was working fine just the other day, and I did a soft shutdown as always. But now, when I try to boot normally, it brings me to the Ubuntu boot screen like it should, and then to a "busybox" terminal. If I try to go into rescue mode it does the same. Messages go by very fast, but I recall something about an NTFS error. But I end up being brought to the busybox terminal. :(

     I did increase my Wubi's root.disk's size, following the instructions on the official Wubi guide to do so, and after I increased the images size and rebooted everything seemed fine. Any idea as to why this is happening? :(

    I noticed that my "host" folder is no longer accessible. So mounting the root.disk file manually isn't an option.

     By the way, I probably should mention, I'm using the newest Wubi in Windows XP Pro SP2 to dual-boot with Ubuntu 8.04 Hardy Heron 32-bit.

Any help would be greatly appreciated! :D

---

### Post by ac1d6urn on 2008-08-29
Have you tried booting into windows xp and checking your drive for errors? Is it trying to go through a disk check on startup?  

Wubi creates a virtual drive with Ubuntu on top of Windows' NTFS drive, but if the main drive to be checked for errors first, virtual one may not be accessible.

---

### Post by Kai001 on 2008-08-29
Ya, I attempted to run "chkdsk /r", and since the drive was in use (Windows boots off of it) it asked if I wanted to run "chkdsk /r" on the next boot, and so I said yes. Now after rebooting I selected to go into Windows, and, now, I assume it's running chkdsk. Although, I can't see anything. But I suppose this is because I put "/NOGUIBOOT" in my boot.ini file to stop it from loading the boot screen in order to speed up my boot time. It's been working for 30-40 minutes now. My HD usage light's been on the whole time. Although, when I ran chkdsk before in the Windows XP recovery console on the same computer it didn't seem to take nearly this long, and I'm not sure if I can shutdown/reboot, since I'd suspect a hard shutdown/reboot while running something like chkdsk could cause problems. Right?

---

### Post by ac1d6urn on 2008-08-29
Hmm, give it a bit longer just in case if the usage light is still flashing...  Though it might be waiting for user input to continue but with CHKDSK text output disabled by /NOGUIBOOT you won't be able to.  Can you reboot to msdos/text mode and run chkdsk again?

---

### Post by Kai001 on 2008-08-29
Well, if I could reboot I could run chkdsk from the windows recovery console, or go back into Windows and turn off "/NOGUIBOOT". But since I'm running chkdsk "/r", it's supposedly recovering readable data, so I suppose it makes it even more dangerous to reboot/shutdown. Although, I do have my most valuable files backed up, I'd prefer to not have to reinstall unless nessicary. So I'm not sure about hard rebooting.. According to the error message I was able to read it told me to run "chkdsk /r" and then I should be able to boot back into Ubuntu just fine.

I probably should point out that I'm running with a 320GB SATAII HD that's about half full. :)

---

### Post by Crafty Kisses on 2008-08-29
Shutdown Windows XP correctly, just go to Start and logout, then try.

---

