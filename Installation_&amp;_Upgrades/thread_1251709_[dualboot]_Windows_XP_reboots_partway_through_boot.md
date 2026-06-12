---
title: "[dualboot] Windows XP reboots partway through bootup"
date: 2009-08-28
forum: Installation &amp; Upgrades
---

### Post by Levviathor on 2009-08-28
I set up a dual boot with Ubuntu Jaunty and WinXP, XP first.  The installation went flawlessly, and Ubuntu runs fine.  Furthermore, I can access my files on the XP partition.

when I select XP from GRUB, it gives me the option of choosing Safe ode, Safe Mode With Networking, Safe Mode With Command Prompt, Boot With Last Good Configuration, and Start Windows Normally.

Start Windows Normally: it shows the XP splash screen for a few seconds, then flashes a blue screen with a few lines of white text for a fraction of a second, and reboots.

Any of the Safe Mode options: causes a bunch of text to scroll by, mostly loading drivers from /WINDOWS/system32/drivers/.  It reboots after a couple seconds of this.

Boot With Last Good Config: same as Boot Windows Normally.


Hardware:
495MB RAM
Celeron 1GHz
82.3GB HDD
(Can provide more if necessary)

---

### Post by oboedad55 on 2009-08-28
> **Levviathor said:**
> I set up a dual boot with Ubuntu Jaunty and WinXP, XP first.  The installation went flawlessly, and Ubuntu runs fine.  Furthermore, I can access my files on the XP partition.

when I select XP from GRUB, it gives me the option of choosing Safe ode, Safe Mode With Networking, Safe Mode With Command Prompt, Boot With Last Good Configuration, and Start Windows Normally.

Start Windows Normally: it shows the XP splash screen for a few seconds, then flashes a blue screen with a few lines of white text for a fraction of a second, and reboots.

Any of the Safe Mode options: causes a bunch of text to scroll by, mostly loading drivers from /WINDOWS/system32/drivers/.  It reboots after a couple seconds of this.

Boot With Last Good Config: same as Boot Windows Normally.


Hardware:
495MB RAM
Celeron 1GHz
82.3GB HDD
(Can provide more if necessary)

How did you handle the partitioning of your hd? Did you defrag your Windows partition before installing? Can you get to a command prompt in Windows and run chkdsk?

--Jon

---

### Post by Levviathor on 2009-08-29
I ran a defrag using XP's built-in defrag program, then shut it down.  I don't think anything occured between that and the installation.

I used the partitioner built into the LiveCD.

The partition is 20GBs.

I haven't been able to get to a prompt.
Short of using some sort of Windows restore CD, I don't think it would be possible.


It looks like perhaps someone did get onto the computer after the defrag, or else the defrag was incomplete, and there was an important file in the area that was overwritten by the Ubuntu partition.

---

### Post by epicoder on 2009-08-29
Sounds like you're getting a blue screen of death when you boot up Win XP. I'll need, more info before I can help you with anything, though.

---

### Post by presence1960 on 2009-08-29
That problem sounds like an unclean shutdown of windows may have occurred, or some type of system file corruption/loss. That is definitely a windows problem and has nothing to do with Ubuntu or GRUB. GRUB is pointing to the right partition for windows.

---

### Post by Levviathor on 2009-09-02
@sh228, what sort of info are you looking for?


@presence1960, I didn't think it was.  But the fact remains that XP is unbootable.


I'm going to dig around and see if I can find an XP restore disk, or something similar.  I'll post the results if possible.

---

### Post by Levviathor on 2009-12-04
I gave up and just deleted the XP partition.  Don't have the disks for it anyway.  Works decently.  Thanks guys.

---

### Post by efflandt on 2009-12-04
One thing that can trip up resizing Windows is Windows virtual memory, which it expects to find at a specific place in its partition, and cannot be moved with defrag.  If that got moved during partition resizing, that may have been the issue.

When I originally resized my 200 GB XP ntfs years ago with ntfsresize on a Linux rescue CD, I apparently had not done that or forgot to reboot after removing virtual memory, and could only free up 24 GB.  But after I recently disabled Windows virtual memory, rebooted, and defragged, gparted-live CD said I could shrink it to the amount of data on it if I wanted to.  But I just freed up 50 GB with enough room for a couple of Linux distros and swap.

I have resized ntfs and vfat partitions myself without issues.  But frankly I take precautions ahead of time, and would not trust any OS to automatically rearrange partitions.  I would rather set them up myself.  Even WinXP Pro 64 beta some years ago changed my partition table geometry when it installed itself (heads and cylinders) and could not boot itself or XP Home until I fixed the partition table from a Linux rescue CD.

---

