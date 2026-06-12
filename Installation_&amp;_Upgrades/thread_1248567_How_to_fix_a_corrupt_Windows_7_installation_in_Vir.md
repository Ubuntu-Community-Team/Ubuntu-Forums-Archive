---
title: "How to fix a corrupt Windows 7 installation in Virtualbox"
date: 2009-08-24
forum: Installation &amp; Upgrades
---

### Post by nanonils on 2009-08-24
This simple guide will allow users to recover a corrupt Win7 in a Virtualbox installation that refuses to do checkdisk repairs but has licensed legacy applications on it.

**Setup:** Win7 32 bit Ultimate in 3.0.4 Virtualbox 
**Problem:** Hard reset corrupted Win7 where it will only boot in "safe mode" but is unable to run checkdisk because of some missing files. No restore point made.
**At stake: **university licensed Adobe Acrobat Prof 9, Office 2007 Prof, Endnote X2, downloaded Unbox Amazon movie. Applications cannot be reinstalled as they are locked to exactly this Windows SN.
**Solution:** Install a second Win7 in Virtualbox, mount to this Win7 corrupt installation hard disk as the IDE Primary Slave in Virtualbox's "Hard Disks" window then run a checkdisk with repair. Then unmount HD from new Win7 and mount as Primary Master to previously corrupt Win7. If the first boot doesn't work, try again after rebooting. It probably depends on what files are gone but it worked well in my case. Now I'm making a restore point always.

**Background:** Like other Firefox 3.X users I have experienced frequent system freezes where everything stops (including mouse and Xorg reset keys) while the harddrive ramps up to maximum activity for >30 minutes (would wait any longer). I had to hard reset the two computers (System76 WildDog quad core and Lenovo T61 core duo with identical software configuration on 9.04 64bit ext4) several times a day revoking "blue screen of death" Windows memories... This post here solved my FF problem: [http://ubuntuforums.org/showthread.php?t=1141507&highlight=firefox+freezes](http://ubuntuforums.org/showthread.php?t=1141507&highlight=firefox+freezes)

Note: Yes, I shouldn't use those legacy applications, thank you, but tell that to my collaborators who are not using OO3, Bibus and PDFtk. Also PDF file commenting and sharing of those files is still in infancy with anything but Adobe Acrobat.

---

### Post by shreeseva.it on 2010-08-08
Thanks for your help. I got the same problem for windows xp VM on Fedora. I tried to recover the VM by various ways, but nothing worked. But using your tricks I created a new VM for ubuntu, then installed guest additions and used a shared folder. Also added old corrupted windows VM as a slave disk and recovered the development files I needed.

Thanks for the trick.

CPK

---

### Post by nanonils on 2010-08-12
Nice to see it worked for you! I'm always amazed how well soluions can be exchanged in these forums.

---

### Post by hundycougar on 2010-09-30
Thank you thank you thank you thank you!! Thank you thank you thank you thank you!!Thank you thank you thank you thank you!!Thank you thank you thank you thank you!!Thank you thank you thank you thank you!!

This process saved my kiester!! I had an XP image that was on a host that was hard powered down (without a proper shutdown) and would boot half way into XP )(displayed the logo and everything) but would blue screen and reboot.  None of the safe modes would work, and when I tried to launch the XP CD to see if I could repair or if need to install into the Windows2 directory to try to recover it, it wouldn't recognize the drive.

Mounted it into anothe Guest I had, booted, repaired and chkdsk, rebooted and it worked!!!!!

Thank you!!!!

---

