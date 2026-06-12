---
title: "WinXP boot does not get past loading drivers after Ubuntu is installed"
date: 2009-02-23
forum: Installation &amp; Upgrades
---

### Post by ssb22 on 2009-02-23
Hi, I installed Ubuntu 8 from DVD on an IBM-Lenovo ThinkPad Z61p, and chose to re-size the WinXP partition and install Ubuntu on free space.  Ubuntu now works but WinXP Pro no longer boots.  The Windows installation CD has been lost, but I re-installed an MS master boot record using ms-sys.sourceforge.net, however Windows still does not boot.  It does get as far as the "Windows was not properly shut down" message, and when I choose "boot in safe mode" it prints out a list of drivers that it's loading, the last one of which is BTHidMgr.sys, and then it immediately resets the computer (thus if left unattended it will go round in circles).  This behaviour happens regardless of whether grub or ms-sys is the main bootloader.

All I can find on Google is people having similar problems and suggesting installing an MS MBR, however I do not think the MBR is the issue here as it does not seem to have taken effect and anyway the Windows boot process seems to get further than it would if the MBR was the problem.  Does anyone know what else could have gone wrong?

By the way, I can mount the NTFS partition from Ubuntu without trouble, so it doesn't seem to be corruption there.  WINE can even run some Windows programs, but it is not able to access the real Windows registry (I'll need to get back into Windows to get the entries out).

Thanks.

Silas

---

### Post by Mark Phelps on 2009-02-23
When Windows no longer booted, if ubuntu booted OK, you could have come here and we would have told you how to modify your GRUB menu to add a Windows stanza, but since you're gone and overwritten your MBR, it's unlikely we can do anything here to repair an MS Windows-based MBR.

If you can boot into Safe Mode, try using command mode and see if you can do a fixboot and fixmbr.

Please don't take this as insulting -- but this is not really an MS Windows forum; it's an Ubuntu forum.  An excellent MS Windows forum is the NeoSmart forums.  They even have downloadable stuff and How-to's on fixing various MS Windows boot issues.

---

### Post by ssb22 on 2009-02-23
Sorry I didn't explain myself very well: I only *TEMPORARILY* restored the MS MBR.  When I saw that this did not solve the problem, I immediately re-installed Grub to the MBR (by booting from the Ubuntu CD, chrooting to the Ubuntu partition and running grub-install).  So at the moment I *do* have a Grub MBR.

What recipe for booting XP with Grub were you thinking of?  I do get an option to boot XP from Grub but it doesn't work.  (Could this be a limitation in the Ubuntu installer?  Is there a workaround?)

Thanks.

---

### Post by ssb22 on 2009-02-23
By the way this is what I got already:

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by Mark Phelps on 2009-02-23
> **ssb22 said:**
> 
What recipe for booting XP with Grub were you thinking of?  I do get an option to boot XP from Grub but it doesn't work.  (Could this be a limitation in the Ubuntu installer?  Is there a workaround?)

Thanks.
When you say it doesn't work, is that when it goes into SAFE mode and you don't get beyond the driver loading messages?

My guess is that your XP filesystem is corrupted somehow. SAFE mode boot provides (usually) the option to boot into a command line -- which will often work when other boot options don't.  

I don't know how to tell GRUB to tell Windows to boot into SAFE mode; all I can suggest is that as soon as you boot into Windows, start pressing the F8 key to try to force SAFE mode, and if you get a menu screen with options that allow command mode, select that and do the two fix commands.

Also, could try then running CHKDSK /F

---

### Post by ssb22 on 2009-02-24
No I can't get into Safe mode.  I can press F8 and I can get as far as the menu which offers normal start, safe mode, safe mode with command prompt, etc, but none of these options work.  They just load a few drivers and then reboot.  :-(

---

### Post by ssb22 on 2009-03-03
I borrowed somebody's XP Setup CD and tried the recovery console, but it wanted the administrator password, which has been forgotten.  So I tried pressing Enter to setup windows, F8 to accept license, select partition and press R to repair.  It checked the disk then wanted to restart as it had done "disk maintenance".  Windows still wouldn't boot, so back into the CD and let it copy files to Windows install folders, then it booted to a blank screen for a few minutes and said STOP 0x000000EA, infinite loop in framebuf.  Reboot got the same problem.  I tried F8 and Safe Mode and got "Windows XP setup cannot run under safe mode, setup will now restart".  And enabling VGA mode didn't help.

So apparently I should have used the setup CD that came with this particular laptop (which I don't have).  Borrowing somebody else's setup CD is not sufficient.

Well at least I got a good Ubuntu system .. but it's a shame that the Ubuntu installer's "NTFS resize" apparently rendered Windows unbootable, and it's a shame I haven't got any info that can be used to fix this.

---

