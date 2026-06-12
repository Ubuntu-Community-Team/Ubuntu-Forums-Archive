---
title: "Ubuntu corrupted my XP Master File Table!"
date: 2009-11-10
forum: Hardware
---

### Post by frogitts on 2009-11-10
Here's the background:

I have two hard drives, one (SATA) with XP on it and another (EIDE) with an NTFS partition and Ubuntu on an ext2 (I think, or ext3, I can never remember which one's right). I also have an external hard drive (EIDE) that's completely NTFS.

My power supply failed, and so while I was waiting I switched the XP HD with my external so that I could access it from my laptop. I got the power supply back and plugged everything back in, and hooked up my external HD as an internal, because I was never using as an external anyway and wanted faster transfer speeds.

Here's the kicker, which makes me want to ditch Ubuntu altogether:
When I hooked all three drives up, I started XP and after the Windows logo with the progress bar appeared, I got a BSOD (Blue Screen of Death). It flashed for an instant (no chance to read it at all) and then restarted the computer.


I immediately took the main HD out and mounted in my external again, accessing it through my laptop running Karmic. I used the disk utility to see what was happening, because it wasn't mounting.

This is it:
My EIDE with Ubuntu on it was 160GB, while my SATA with XP on it was 750GB. Ubuntu's Disk Utility reported the drive as containing **_160GB_** of space in an unknown format and the rest as empty space.

So my question: Did having an Ubuntu partition somehow make GRUB copy the MFT from the EIDE with Ubuntu on it to the SATA with XP on it? I don't know how this would happen, it seems like magic to me. All I know is, this isn't the first time this has happened. A year ago I got this new hard drive (SATA) and installed XP on it with Ubuntu already installed on a second drive. When that second drive was attached, I always got a BSOD and a corrupted MFT that seemed to have been copied from the Ubuntu drive. I threw that HD out, and never had a problem with my SATA again. Until now.

The only other thing I can think of is that using a bootable drive as an external somehow screwed things up by not writing correctly to the MFT, since it was a XP bootable drive and i was using it as an external drive in an Ubuntu environment.
[B]
Can anyone shed some light on this and help me recover my files/trust in Linux?[/B]

---

### Post by frogitts on 2009-11-10
Here's a picture of the BSOD: Turns out it's an UNMOUNTABLE_BOOT_VOLUME error.
[http://www.humyo.com/F/3591551-183476919]("http://www.humyo.com/F/3591551-183476919")
[IMG]http://www.humyo.com/F/3591551-183476919[/IMG]

---

### Post by frogitts on 2009-11-11
All right, so I've connected my two main hard drives and I can boot into GRUB and therefore I can boot into Ubuntu on the 160GB EIDE. I've installed and run testdisk, which seems like a nice utility with the crappiest documentation in the universe. No one seems to have any clue how to use this thing, so I'm calling for help yet again. I'm using version 6.10 of testdisk (I downloaded 6.11.3, but whatever) and it seems like even the official documentation is for an older version.

It can see the 160GB partition on a quick search. Once it's located that, I can see my entire (700GB) file structure, but a good portion of the files have a filesize of 0 (as in CHS: 0 0 0). Upon doing a deeper search it locates a partition with the correct size (700GB) but it says "Can't open filesystem. Filesystem seems damaged."

So I have two choices: (1) Correct size, no files or (2) incorrect size, complete file structure, partial files. **Can anyone help me figure out a better solution?**



Oh, and BTW: The files that I want to backup are the ones that have a file size of zero. And I tried adding a partition - it doesn't work. Here's my partition list:

Disk /dev/sda - 750 GB / 698 GiB - CHS 91201 255 63
     Partition               Start        End    Size in sectors
D HPFS - NTFS              0   1  1 19457 254 63  312592707
D HPFS - NTFS              0   1  1 91199 254 63 1465127937

I tried adding a partition using "0   1  1 91199 254 63" and "0   0  1 91199 254 63." This partition should be listed as "*" (Primary Bootable).

---

### Post by frogitts on 2009-11-11
Ok, more progress and info. I could still use some help if anyone out there knows how to use testdisk!!!

I did a quick scan again, found the partition with an incorrect size but the right file structure. I chose "Add partition" and added a partition with the correct size. I can now see the file structure on this new, correctly sized partition.

Here's the problem now: a number of the files are listed as having a file size of "0" still (CHS: 0 0 0). If I rewrite the MFT with testdisk now, does that mean these files will permanently be of size 0 (i.e., lost)?

I'm trying to use photorec to recover my important files, but I have more important files than I have good, free HD space right now, so this might take a while. Even if I do manage to correct my MFT, who knows how many system files will have a file size of 0? I guess, if this is the case, I need to look for a different solution such as formatting, which is no fun. I really don't feel like setting this system up all over again.






[on another note, I think I know what caused this: each time this has happened to me, I've had two DVD drives hooked up to one IDE channel, two hard drives hooked up to a second IDE channel (1 master, 1 slave) and an SATA master being run in IDE mode on IDE channel 3. Seems like my system can't handle 3 masters or 3 IDE channels, right?]

---

