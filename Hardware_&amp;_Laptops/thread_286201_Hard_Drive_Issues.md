---
title: "Hard Drive Issues"
date: 2006-10-27
forum: Hardware &amp; Laptops
---

### Post by Stang70Fastback on 2006-10-27
Ok, here's my problem. I had an old hard drive, on which windows got corrupted. I bought a new hard drive, and planned to move all my files over and then reinstall windows. Problem is, one of the problems i was having was that Windows crashed any time I tried to use any file explorer, or anything, so I couldn't actually GET to the second HD to copy the files. So now I'm using this Linux on a LiveCD. I just want to use the Linux file explorer to pull up my old and new hard drives and copy files. Problem: Neither of my hard drives show up. They show up in the bios and the second hard drive is NEW as in like I just installed it, but it is identified. However, in the Linux explorer, all I see are the floppy, CD drive, and the 'filesystem' folder... HELP!?! Thanks!

---

### Post by SoggyCornflake on 2006-10-27
First, which LiveCD are you using?  One of the great benefits/pains of Linux is the huge variety of options availible at every level.

You may need to mount your hard drives.  If you aren't very experienced with Linux, that can be a bit tricky but basically what you need to do is enter something like this from the command line:
```
sudo mount /dev/hda1 -t vfat /mnt/OldDrive
```

Hears a breakdown of the above command
**sudo **is the command to tell the system for this command treat me like a superuser.
**mount **is the unix command to make drives readable by the system.  If you need more info on mount you can try googling the command by searching on **man mount**.
**/dev/hda1** is an IDE Hard Drive installed as the Master Drive on the first IDE bus.  The 1 refers to the partition number of the drive.  hdb is the slave
**-t vfat** is the formatting of that drive t for type and vfat is one of the possible formats you can use.
**/mnt/OldDrive** is where on your system you can find this hard drive.

You may have to do some poking around with different settings to get a hard drive mounted.

If you have a SCSI drive, the hda will probably be sda (or sdb et.)

I hope this helped.  If not, I'm sure somebody will have a better answer for you around here.

---

### Post by Stang70Fastback on 2006-10-27
When you talk about formatting the drive, do you mean I have to enter what it is formatted as? Or is that going to format the drive? Thanks for the help. I'm entirely new to Linux.

---

### Post by SoggyCornflake on 2006-10-30
> **Stang70Fastback said:**
> When you talk about formatting the drive, do you mean I have to enter what it is formatted as? Or is that going to format the drive? Thanks for the help. I'm entirely new to Linux.

First I applogize for not following up until now.

I don't mean that you should format your drive, I mean when you mount it, the computer needs to know the format your hard drive is already to be able read from it.

Essentially what I'm talking about having your computer and your hard drive agree on a language to allow communication.  That's what the -t flag is all about.

---

