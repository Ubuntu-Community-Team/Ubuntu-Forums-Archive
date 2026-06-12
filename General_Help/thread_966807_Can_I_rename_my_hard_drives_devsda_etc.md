---
title: "Can I rename my hard drives? /dev/sda etc?"
date: 2008-11-01
forum: General Help
---

### Post by Roasted on 2008-11-01
I have 4 drives... 

They are arranged in this series in my computer case.
1 - 500gb (Vista, Ubuntu Intrepid)
2 - 500gb (Backup of drive A)
3 - 250gb (Samba network drive)
4 - 250gb (Samba backup drive)

Despite the fact drive 1 is the first drive with my OS's, it's listed as /dev/sdb while my 2nd drive is /dev/sda. I'd like to switch them.

Is that possible? I'd just like to keep things consistent and have my main drive be /dev/sda.

Note - In my BIOS, the drives have identical tags, however one has a 0 with it and the other has a 1. I understand the 0 = 1 and 1 is actually equivilent to number 2 in computer language, and the computer with the "1" tag is the one I boot to with my operating systems on it. So my BIOS as well recognizes my first drive as drive 2. Not a big deal, it's just a tag. But I have a mount and backup script in Ubuntu which would make changing dev/sda etc easier.

---

### Post by geirha on 2008-11-01
As far as I know, you can't. Though each file system has a unique identifier called UUID, and you can also give them labels. To see the UUIDs and LABELs of all filesystems, run ```
sudo blkid
```

So for your back-up script, whatever it does that need to know the devicenode, instead of using /dev/sda1 etc, use /dev/disk/by-uuid/*the-uuid* or /dev/disk/by-label/*the-label*.

---

### Post by Roasted on 2008-11-01
All right, I see what I did.

I ended up just switching my two 500gb drives, physically. Like I took each one out and hooked them up to the opposing SATA connections.

Now, everything in my BIOS is lined up, and when I boot into Ubuntu, everything (Vista and Ubuntu) is on my sda drive. Is that normal that Ubuntu changes tags like that if I switch drives around? I thought each drive got like... hard coded, or something, to the /dev/sda tag that it was assigned to.

My confusion started with the motherboard. I didn't realize the way the SATA controllers were numbered. Turns out the top drive was actually plugged into port 2, whereas the second drive was plugged into port 1. That's why my "main" drive came through as drive 1, when my "backup" drive came through as drive 0 (which is actually the first drive, since 0 is really 1 and 1 is really 2 in the BIOS world)

It's hard to understand without seeing it, but everything is fine now. I just had everything backwards from the get-go, but now everything is squared away.

But my question remains about the /dev/sda tags. I thought Ubuntu like hard coded each drive to the tag? I didn't think the tags would change according to which SATA slot they are plugged into.

---

### Post by geirha on 2008-11-01
They get the /dev/sda, /dev/sdb names based on the order they are connected. This has caused a bit of problems earlier as adding a new disk may cause the drives' names to get "shuffled". That's why UUID and LABEL was introduced, to have a fixed name for each file system, regardless of which order they are connected.

---

### Post by scouser73 on 2008-11-01
> **Roasted said:**
> I have 4 drives... 

They are arranged in this series in my computer case.
1 - 500gb (Vista, Ubuntu Intrepid)
2 - 500gb (Backup of drive A)
3 - 250gb (Samba network drive)
4 - 250gb (Samba backup drive)

Despite the fact drive 1 is the first drive with my OS's, it's listed as /dev/sdb while my 2nd drive is /dev/sda. I'd like to switch them.

Is that possible? I'd just like to keep things consistent and have my main drive be /dev/sda.

Note - In my BIOS, the drives have identical tags, however one has a 0 with it and the other has a 1. I understand the 0 = 1 and 1 is actually equivilent to number 2 in computer language, and the computer with the "1" tag is the one I boot to with my operating systems on it. So my BIOS as well recognizes my first drive as drive 2. Not a big deal, it's just a tag. But I have a mount and backup script in Ubuntu which would make changing dev/sda etc easier.

Try this; [https://help.ubuntu.com/community/RenameUSBDrive]("https://help.ubuntu.com/community/RenameUSBDrive")

---

