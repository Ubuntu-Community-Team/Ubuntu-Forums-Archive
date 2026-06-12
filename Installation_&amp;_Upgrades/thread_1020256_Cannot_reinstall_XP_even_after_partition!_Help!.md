---
title: "Cannot reinstall XP even after partition! Help!"
date: 2008-12-23
forum: Installation &amp; Upgrades
---

### Post by duffman1278 on 2008-12-23
I tried using gparted already to partition the HD and leave room to reinstall window XP. However when I go to install XP by putting in the disk, I get the following screen. I've been trying several times to get this and it doesn't seem to go through. I've tried searching and doing the guides provided but I got no luck so far:(

[IMG]http://farm4.static.flickr.com/3224/3132639574_e0294cd3c6.jpg?v=0[/IMG]

---

### Post by 2hot6ft2 on 2008-12-23
What did you partition it to? What format? Windows will not recognize a linux ext2, ext3, and the like you need to format it to ntfs for windows to see it. And it needs to be a primary partition.

---

### Post by duffman1278 on 2008-12-23
I did set it to NTFS and still nothing

---

### Post by 2hot6ft2 on 2008-12-24
Have you had any problems before this with the drive? Is it in the master position on the tape? Is the pin set to master on the drive (windows doesn't like being the slave)? It's looking like a hardware issue.

Might try this.
> [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
TestDisk is a powerful free data recovery software! It was primarily designed to help recover lost partitions and/or make non-booting disks bootable again when these symptoms are caused by faulty software, certain types of viruses or human error (such as accidentally deleting a Partition Table). Partition table recovery using TestDisk is really easy.

---

### Post by duffman1278 on 2008-12-24
Not sure what it's set to because this is on my laptop.

---

### Post by 2hot6ft2 on 2008-12-24
Then I seriously doubt it's been changed and I would try the recovery disc I linked to. I don't know if this will help but I just saw it.
> **Monotoko said:**
> Boot from the windows XP CD, press the "R" key in the setup in order to start the restoration console. Select your windows XP installation from the list, and enter the administrator password.
Enter the command: "FIXMBR" (without the quotes) at the input prompt and confirm the next question with a "Y" (without the quotes). Use exit to restore the computer.

That will fix XP right up :)

---

### Post by monkeyking on 2008-12-24
Check if your xp cd has sata drivers streamlined for your harddrive

---

### Post by duffman1278 on 2008-12-24
^^^ How would I do that?

---

### Post by logos34 on 2008-12-24
> **monkeyking said:**
> Check if your xp cd has sata drivers streamlined for your harddrive

If the OP is using a regular XP install CD, it won't.   

> **duffman1278 said:**
> ^^^ How would I do that?

Do you have a SATA drive?  Because if you do it could be XP can't recognize the disk because its in AHCI sata mode.  Check your Bios settings

---

### Post by duffman1278 on 2008-12-24
> **logos34 said:**
> If the OP is using a regular XP install CD, it won't.   



Do you have a SATA drive?  Because if you do it could be XP can't recognize the disk because its in AHCI sata mode.  Check your Bios settings

I'll go ahead and check that right now thanks. Yes this is just a regular XP cd.

---

### Post by duffman1278 on 2008-12-24
It seems like its SATA but the partition is giving me "hda7" which iirc isn't SATA.

---

### Post by logos34 on 2008-12-24
yes, hda probably means you have an IDE 

Post the output of this command:

sudo lshw -C disk

---

### Post by duffman1278 on 2008-12-24
[IMG]http://i5.photobucket.com/albums/y178/duffman1278/Screenshot.png[/IMG]

---

### Post by logos34 on 2008-12-24
no, looks like you do have sata (Sata 1.5 GB/s, that is)--two Seagate Momentus 100GB drives. (sda and sdb)

So the next thing to do is check the Bios settings to see if it's running in ahci mode...ubuntu kernel supports it, XP does not (natively)...the drivers need to be added at installation time on floppy (F6) or slipstreamed on the CD (some computer manufacturer CD's include the drivers, but not the OEM or retail versions AFAIK). Or else run in IDE compatibility mode (the only thing you would lose in your case I believe is hot-plug capability, and you'd have to switch the Bios mode every time you want to boot the other OS

---

### Post by duffman1278 on 2008-12-24
This is getting wierd now. I tried reinstalling ubuntu and redoing the partitons for NTFS and now i'm getting a message on the window XP install that says I now how NO HD. It looks like the blue screen I posted in my first post however it tells theres no drives. wtf:confused:

---

### Post by logos34 on 2008-12-24
> **duffman1278 said:**
> This is getting wierd now. I tried reinstalling ubuntu and redoing the partitons for NTFS and now i'm getting a message on the window XP install that says I now how NO HD. It looks like the blue screen I posted in my first post however it tells theres no drives. wtf:confused:

formatting ntfs partitions with gparted in linux (assuming that's what you mean) won't help us here...Sounds like the problem is that the sata mode in the Bios (check it) is set for AHCI rather than IDE emulation/compatibility/legacy mode...Vista and Linux kernel 2.6.x support it natively (i.e. include the sata drivers), XP doesn't.  You have to add them just before windows installation otherwise XP installer can't see the disks.  So you have a choice: either reinstall ubuntu in IDE compatibility mode, then add XP, or else slipstream the sata drivers into a custom XP install CD.  

Is this a laptop?  Post your make and model, system specs.  I can help track down the sata drivers if you want

---

### Post by duffman1278 on 2008-12-25
Yup, a laptop. I'll try what you said about the ubuntu reinstall.

Here's the specs:
 HP DV8000 
 200gigs HD
 1gb ram
 Intel Centrino

Upon reinstalling  Ubuntu  (trying to put it in IDE mode as you suggested) I noticed that it says here "SCSl3 (0,0,0)(sda) - 100GB ATA ST9100824AS) Dunno if that'll give you some info on the drives.

---

### Post by logos34 on 2008-12-25
> **duffman1278 said:**
> 
Upon reinstalling  Ubuntu  (trying to put it in IDE mode as you suggested) I noticed that it says here "SCSl3 (0,0,0)(sda) - 100GB ATA ST9100824AS) Dunno if that'll give you some info on the drives.

we already know the drives (see above). more [here]("http://www.seagate.com/ww/v/index.jsp?vgnextoid=f56d99f4fa74c010VgnVCM100000dd04090aRCRD&locale=en-US")

reinstalling both os in ide mode is the best option

---

### Post by duffman1278 on 2008-12-25
Got it! I ended up going into the BIOS settings and disabled the SATA Drive. After I did this it installed with no issues. Thanks!

---

