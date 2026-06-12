---
title: "[SOLVED] Installed New Hard Drive Now Computer Wont Boot?"
date: 2008-10-07
forum: General Help
---

### Post by ChildOfMana on 2008-10-07
I'm running (or, more to the point, *was* running Hardy 8.04).

I installed a second HD today. After installing it I plugged the computer back in and fired it up. It booted fine. However, I couldn't see the new HD anywhere. "No problem" thought I, "I'll fire up a Live CD and use the Partition Manager to format the new drive to ext3".

Schoolboy error!

I formated said drive, shut down and removed the Live CD and re-booted the computer (changing the BIOS settings to boot from the 1st HD) but nothing happened. It won't boot.

I thought for one horrifying moment that I'd formatted the wrong drive so I  re-launched the Live CD to check. Thankfully all my data (including 35Gb of (legally obtained) music!!) was still in tact on the original drive.

I tried copying my music over to the new drive for safe keeping (now displaying as an ext3 formatted drive) but the *paste* option was grayed out.

Anyone know how I can; a) get my computer to boot again, and b) copy my music to the second drive just in case something goes wrong?

If it helps - my original drive has 3 separate partitions - a small /swap partition, a larger partition for / and the rest a dedicated /home partition.

Thanks.

---

### Post by arsham on 2008-10-07
Hi
Does the GRUB menu come up to choose the OS to boot?
If it does , is it saying it cannot boot from the partition?



> **ChildOfMana said:**
> I'm running (or, more to the point, *was* running Hardy 8.04).

I installed a second HD today. After installing it I plugged the computer back in and fired it up. It booted fine. However, I couldn't see the new HD anywhere. "No problem" thought I, "I'll fire up a Live CD and use the Partition Manager to format the new drive to ext3".

Schoolboy error!

I formated said drive, shut down and removed the Live CD and re-booted the computer (changing the BIOS settings to boot from the 1st HD) but nothing happened. It won't boot.

I thought for one horrifying moment that I'd formatted the wrong drive so I  re-launched the Live CD to check. Thankfully all my data (including 35Gb of (legally obtained) music!!) was still in tact on the original drive.

I tried copying my music over to the new drive for safe keeping (now displaying as an ext3 formatted drive) but the *paste* option was grayed out.

Anyone know how I can; a) get my computer to boot again, and b) copy my music to the second drive just in case something goes wrong?

If it helps - my original drive has 3 separate partitions - a small /swap partition, a larger partition for / and the rest a dedicated /home partition.

Thanks.

---

### Post by fballem on 2008-10-07
The following post: [http://ubuntuforums.org/showthread.php?t=908427](http://ubuntuforums.org/showthread.php?t=908427) contains information that may help.

I suspect that you have two issues - the first is to get the drive to mount, and the second is permissions.

Hopefully, the post will help.

Regards,

---

### Post by ChildOfMana on 2008-10-07
[QUOTE="arsham"]Does the GRUB menu come up to choose the OS to boot?[/QUOTE]

No, no GRUB menu at all.

---

### Post by ChildOfMana on 2008-10-07
[QUOTE="fballem"]I suspect that you have two issues - the first is to get the drive to mount, and the second is permissions.[/QUOTE]

Yeah looks that way. Thing is, I tried using a root terminal to copy the files but it still didn't work.

The disk has been mounted under /media by the Live CD.

---

### Post by fballem on 2008-10-07
> **ChildOfMana said:**
> Yeah looks that way. Thing is, I tried using a root terminal to copy the files but it still didn't work.

The disk has been mounted under /media by the Live CD.

Forgive me for asking, but are you a newbie? The reason I ask is that I don't want to insult you by asking basic questions.

If you are using GNOME (as opposed to KDE), then you may want to try the following:

1. In a terminal, type:

```
gksudo nautilus
```

This will open up nautilus in super user mode. Please be careful, you can do a lot of damage.

2. In nautilus, go to /media and find the mount point for the new drive.

3. Right click, which will open up a menu. Select Properties and please provide us with the permissions that you find there.

4. Close nautilus

Once we know this, then we can determine if it is a permissions problem, and advise you how to solve it.

By the way, I'm a relative newbie, but I did encounter this problem on one of my machines and was able to solve it. I find a step-by-step approach to be most helpful, and sometimes people who aren't now experiencing the problem can bring a different perspective.


Thanks,

---

### Post by ChildOfMana on 2008-10-07
Ah, I didn't think of using gksudo - apologies, I should have thought of that myself (I've used it in the past to get around similar problems). The files are copying as I type this.

I'm not new to Linux (which is really why I should have thought of using gksudo!!)- I've been using various distros for that last 2 or 3 years but when it comes to a problem I've not encountered before (such as not being able to boot my computer) I tend to flounder a bit.

Thanks for the help so far.

---

### Post by fballem on 2008-10-07
> **ChildOfMana said:**
> Ah, I didn't think of using gksudo - apologies, I should have thought of that myself (I've used it in the past to get around similar problems). The files are copying as I type this.

I'm not new to Linux (which is really why I should have thought of using gksudo!!)- I've been using various distros for that last 2 or 3 years but when it comes to a problem I've not encountered before (such as not being able to boot my computer) I tend to flounder a bit.

Thanks for the help so far.

Always glad to drop inspiring pearls of wisdom. Are you comfortable editing /etc/fstab, and do you know what you have to do there?

By the way, could you please explain what you mean when you say 'not being able to boot my computer'?

Regards,

---

### Post by ChildOfMana on 2008-10-07
[QUOTE="fballem"]Always glad to drop inspiring pearls of wisdom. Are you comfortable editing /etc/fstab, and do you know what you have to do there?

By the way, could you please explain what you mean when you say 'not being able to boot my computer'?[/QUOTE]

Yes I'm comfortable editing /etc/fstab but no I don't know what I'm supposed to do there. **Edit:* I mean that, although I don't know what I'm supposed to do, I'm certainly comfortable trying.

When I say I can't boot my computer I mean I can't boot from the HD. I can boot from a Live CD (which I'm currently using) but if I remove the CD and change the BIOS settings to boot from 1st HD then nothing happens. It gets to the point where GRUB would normally (briefly) pop up and just stops there. No error messages, no GRUB menu - just a flashing white cursor.

Could it be a problem with the MBR?

---

### Post by fballem on 2008-10-07
> **ChildOfMana said:**
> Yes I'm comfortable editing /etc/fstab but no I don't know what I'm supposed to do there. **Edit:* I mean that, although I don't know what I'm supposed to do, I'm certainly comfortable trying.

When I say I can't boot my computer I mean I can't boot from the HD. I can boot from a Live CD (which I'm currently using) but if I remove the CD and change the BIOS settings to boot from 1st HD then nothing happens. It gets to the point where GRUB would normally (briefly) pop up and just stops there. No error messages, no GRUB menu - just a flashing white cursor.

Could it be a problem with the MBR?

Actually, I am wondering if it's an even more basic problem.

I'm going on distant memory, but is it possible that when you installed the new hard drive, the new hard drive has been identified as the bootable drive. This might be as simple as having physically connected the cable from the old hard drive to the new hard drive.

The reason that I'm suggesting this is that your computer should still be able to boot from the old drive.

Before you take your computer apart, do a cold boot and go into the BIOS at boot up. Each computer is different, but common keys will be either the Delete key or the F12 key when you are booting. Once there, check out the characteristics of the hard drives that are attached.

Just a thought!

---

### Post by ChildOfMana on 2008-10-07
Yeah I though that as well. The thing is though, I didn't disconnect the original drive. The original drive is connected to SATA_II port 2 and the new one to SATA_II port 3 (the optical drive is on port 1).

Still, something has obviously gone wrong somewhere.

I'll go have a look through the BIOS now and if I see anything untoward I'll let you know.

Short of that though I can't feasibly delve inside the computer until tomorrow evening now.

Either way though I'll post back here and let you know what I find.

Thanks.

---

### Post by fballem on 2008-10-07
I'll look forward to the updates. Although you may not have changed the cables, I wonder if you loosened the cable for the old drive.

---

### Post by ChildOfMana on 2008-10-07
Okay so both drives appear to be as they should in the BIOS - the old drive is on SATA_II 2 and the new one on SATA_II 3. Both are being detected properly - make, model, size etc info is all correct.

I don't think I've disturbed a cable as the original drive is being detected and mounted by the Live CD and I can access (and copy) all the files on it. Also, the computer booted as normal after I'd fitted the new drive - it was only after I'd formatted the new drive that it ceased to boot.

I would venture then, that it was something to do with the act of formatting the new drive that caused the problem.

---

### Post by philidox on 2008-10-07
Its sounds like your computer is booting to the wrong hard drive.  Thats the simplest thing I can think of.  If it was giving you some type of error in linux then I would say its the os but if your not getting anything then that sounds like a bios issues, specifically the boot priority.  I hate to insult your intelligence but sometimes its the simple stuff that gets ya.  Check the bios and see if its set to OLD HARD DRIVE to boot.  Some bios don't let you choose a specific hard drive so you have to switch the cables around to ensure the old hard drive is booted from first.  To rule out whether its your hard drive or bios just simply remove the new hard drive an see if it boots like normal.  Post back on what you get.

---

### Post by fballem on 2008-10-07
> **philidox said:**
> Its sounds like your computer is booting to the wrong hard drive.  Thats the simplest thing I can think of.  If it was giving you some type of error in linux then I would say its the os but if your not getting anything then that sounds like a bios issues, specifically the boot priority.  I hate to insult your intelligence but sometimes its the simple stuff that gets ya.  Check the bios and see if its set to OLD HARD DRIVE to boot.  Some bios don't let you choose a specific hard drive so you have to switch the cables around to ensure the old hard drive is booted from first.  To rule out whether its your hard drive or bios just simply remove the new hard drive an see if it boots like normal.  Post back on what you get.

Or just remove the cable on the new drive instead of removing it.

---

### Post by ChildOfMana on 2008-10-07
The BIOS reports the 1st boot device as the old HD.

Still, I'll try disconnecting the new drive and see what happens.

Unfortunately I can't do it until tomorrow evening but I'll post back here when I do and let you know how I get on.

Thank you for your help so far, its very much appreciated.

---

### Post by ChildOfMana on 2008-10-09
Figured it out - I'd inadvertently swapped the SATA ports for the original HD and the Optical Drive. Duh!

The thing that threw me off though was that the computer booted as normal even after I'd installed the second drive - it was only after I'd formatted it that it stopped booting. That was why I didn't look immediately to the obvious. I just figured it was something to do with formatting the new drive that had caused problems.

Ah well - you live, you learn!

Thanks for the input guys, and sorry to have wasted your time!

Cheers.

---

