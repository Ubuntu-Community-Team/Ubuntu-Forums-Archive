---
title: "going crazy...help please"
date: 2006-01-03
forum: Installation &amp; Upgrades
---

### Post by yep_it's_me on 2006-01-03
I've been going nuts for the last few days searching the net in trying to solve this problem.

I have a dual P3 1000Mhz Abit VP6 and want to make use of it using Ubuntu.

After Ubuntu installation, and while booting, I get this:

ide: failed opcode was: unknown
end_request: I/O error, dev hda, sector 215
Buffer I/o Error on device hda1, logical block 19
hda: dma_intr: status=0x51 { DriveReady SeekComplete DataRequest Error }
hda: dma_intr: error=0x40 { Uncorrectable Error }, LBAsect = 215

ide: failed opcode was: unknown
end_request: I/O error, dev hda, sector 215
Buffer I/o Error on device hda1, logical block 19
Error reading block 6 {Attempt to read block from filesystem results in short read}

RUN fsck MANUALLY

I get maybe about ten of these on boot and then stops, going to a command line.

Could anyone help?

I don't know how to edit or retrieve files while it is doing this since I don't know the commands (I am DOS compedent, though).

Thanks!

---

### Post by kanem on 2006-01-03
Sounds to me like something went wrong with the installation. Maybe while it was formatting the hard drive or while copying files to the drive. Errors like that sound like the system is having a hard time reading the filesystem.

I'm not an expert though. Hopefully someone with more knowledge of corrupt filesystems will be able to be more specific. You might want to try googling those error codes.

Or just re-install. If you do this you might want to check the MD5 sum of the disk first to make it wasn't the problem.

Ever had problems with this hard drive before?

---

### Post by dickohead on 2006-01-03
I installed ubuntu (5.10 beta) on a dual P2-350mhz machine a while back, on issue i had was that it did not initially pick up both CPU's and would keep locking up.... I reinstalled with a newly burnt disc (5.10) and eveything works great!

If you have pressed CD's i suggest a reinstall, otherwise try and burn the cd again and run an md5 check on it.

---

### Post by yep_it's_me on 2006-01-03
Thanks for the quick responses guys.

I just ran Maxtor's disk utility and it said my drive was failing.  I just found out what the 0x40 code is: failing disk drive.

I think that is my problem.  What I am going to do is swap drives around and see if that does the trick.  I'm not sure why the drive is bad...it previously had XP on it???

I'll reply back to close it out.

Thanks!

---

