---
title: "Problem Mounting Second External HDD"
date: 2009-12-16
forum: Hardware
---

### Post by cynicalcylon on 2009-12-16
I am trying to mount a second HDD, but it won't let me do it.
I'm not sure if it's trying to mount to the same place as the first HDD, or if it's just me being a ditz.

My first HDD mounted straight away, so I'm afraid that I only know the below ways to mount a volume.

This is the error message I got when I plugged it in, and when I tried right-click - Mount.

[IMG]http://i936.photobucket.com/albums/ad206/cynicalcylon/Misc/Mount1.jpg[/IMG]

---

### Post by bruno9779 on 2009-12-16
It looks like it is an NTFS partition, is that right?

---

### Post by DaVince21 on 2009-12-16
Well, did you try doing what it told you to do? Meaning - start Windows, properly shutdown Windows - try to mount again in Linux?

---

### Post by cynicalcylon on 2009-12-16
> **DaVince21 said:**
> Well, did you try doing what it told you to do? Meaning - start Windows, properly shutdown Windows - try to mount again in Linux?

Can I play the blonde card at this point??
Sorry, I'm really not sure.

---

### Post by cynicalcylon on 2009-12-16
> **DaVince21 said:**
> Well, did you try doing what it told you to do? Meaning - start Windows, properly shutdown Windows - try to mount again in Linux?

I don't have Windows on this machine.
Just took it out of the packaging & plugged it into this machine.

---

### Post by DaVince21 on 2009-12-16
Alright. Well, your external drive is probably formatted as NTFS, which has a special feature in it on Windows which basically locks the drive if it hadn't been disconnected/shut down properly. There are several solutions to fix this:

1. Find a Windows install, mount the drive and remove it "safely".
2. Backup the data, format the disk as FAT32 (widely supported) and copy all data back onto it.

Solution 1 will probably make the problem happen more often, especially if you plug out the disk without 'safely removing' (or unmounting) it on any Linux or Windows system first. The second solution is better, but you'll need to know how to format a disk and take the effort to actually do it.

---

### Post by cynicalcylon on 2009-12-17
Thanks much.
I'll see if I can borrow one of my housemate's computers for the tasks.

---

