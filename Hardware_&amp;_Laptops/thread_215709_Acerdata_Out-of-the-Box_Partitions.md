---
title: "Acerdata Out-of-the-Box Partitions"
date: 2006-07-14
forum: Hardware &amp; Laptops
---

### Post by tonyr1988 on 2006-07-14
I just got an Acer Aspire 5672WLMI (I love it!)

It came pre-installed with XP (who would've guessed?), and the following partitions:

PQSERVICE - FAT - 4 Gig
ACER - FAT32 - 55 Gig
ACERDATA - FAT32 - 55 Gig

ACER has Windows installed in it. PQSERVICE (I've read on other forums) holds system restore data. PQSERVICE is small enough to not bother me. But ACERDATA sucks up half my hard drive, and it has the following stuff:

MSOCache (hidden folder) with a bunch of files (a lot of CABs) and a ton of other junk.
Recycle Bin
System Volume Information (hidden folder) with some files I don't recognize.
msvci70.dll

Some questions:

1) Why did they do that?

2) I'm preparing to dual-boot with Ubuntu. Can I move the files into ACER and still have it work?

3) I thought Windows system files needed NTFS to work. I guess not. The last time I installed WinXP Pro on my desktop, I swear it said I needed NTFS (there's no way M$ would lie to me...)

4) The PQSERVICE is at the beginning. Will that mess up GRUB or anything if I install Ubuntu?

5) I was thinking about these partitions (assuming I can get rid of ACERDATA):

PQSERVICE - 4 Gig
ACER (WinXP) (FAT32) - 40 Gig
UBUNTU (ext3) - 40 Gig
SHARED (FAT32) - 25 Gig
Swap - 3-4 GB (should that be enough?)

Wow - too many questions at once. :P If anyone can help with any of those, it would be great. What did the rest of you Acer dual-booters do?

Thanks

---

### Post by PvSinNL on 2006-07-16
I think the idea behind the "ACERDATA" partition is that the user can store his/her data, documents, etc. there. If/when you'd need to do a full reinstall of XP, you could safely wipe the system partition and still have your documents. (This doesn't make regular backups redundant, obviously, but that's another story...)

In response to (some of) your other questions:

- No, XP doesn't strictly need NTFS. It runs fine on FAT32. It's easy to convert an existing FAT32 partition to NTFS, though.

- On my Acer laptop, I just reduced the size of the ACERDATA partition to make space for a new Ubuntu (+ swap) partition, using the partition manager on the Breezy install cd. (Keep in mind that you can have 4 primary partitions at most.) I also decided to install Grub onto the Ubuntu partition instead of the MBR, and boot it from the Windows XP boot menu. The way to do this is detailed [here]("http://www.geocities.com/epark/linux/grub-w2k-HOWTO.html").

- I think that, under most circumstances, 3 or 4 GB of swap would be more than enough. I've got 723 MB (and 512 MB of RAM) on my Aspire 2012WLMi, and my system hardly ever seems to use any swap.

---

### Post by tiger015 on 2006-07-16
I have Acer Travelmate 4502 with 80 G hard disk. The AcerData partition was around 37.5 G when I bought the laptop. I got rid of it and installed Ubuntu on that.

Windows does not need NTFS though Microsoft says it is preferred.

PQService at the beginning should not mess up GRUB.

SWAP size of 2-4 G is enough.

---

### Post by tonyr1988 on 2006-07-17
I ended up merging ACER and ACERDATA into one partition with no problems.

When installing Ubuntu, I partitioned it this way:

PQSERVICE (primary) (fat32)
ACER (primary) (fat32)
SHARED (primary) (fat32)
EXTENSION:
   UBUNTU (ext3) (logical)
   SWAP (logical)

For some reason, I couldn't get the partitioner to let me put my Shared partition as logical instead of primary, so I wouldn't have to use extended. Is that supposed to be like that?

Anyways, I put GRUB into the MBR and used the above partitioning. Everything works beautifully. No problems at all. :) Thanks for all the help.

---

