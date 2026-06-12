---
title: "[SOLVED] mounting trouble"
date: 2008-11-22
forum: General Help
---

### Post by Bigneil on 2008-11-22
hi there, is it possible to mount a disk drive that is being shown as SCSI ?

  it was my main operating system drive (master), with a second drive as a storage volume (slave). 

  After stupidly mincing up the main drive i swapped them over and installed a dual boot on what was the storage volume. and i have made the 'problem' disk drive, the slave now but cannot mount it.

  Windows XP does not recognise it in 'My computer' but, if i go to 'manage' and look at the disk drives it is shown as 'Unallocated'.

  In Ubuntu, it is recognised and shown in 'computer' as SCSI and i am struggling to mount it, i am a noob to ubuntu. and i have no computer training what so ever. i just muddle through best i can. All i tried to do so far, is to copy and paste into terminal from other similar threads, trying to substitute where appropriate. I also tried the drive in an external case on another pc running XP and 'Unallocated' was the conclusion there too.

  The drive originally contained a dual xp/ubuntu boot i think the problem began when i tried to re-install the ubuntu after loosing the ability to dual boot. i attempted to re-install the ubuntu, but the disk partitioner tool would not recognise windows on the master drive, and was determined that i should patition the storage volume.     Sooo,

  I used Partition magic in XP to extend the windows partion from 40 gb to 80 gb and thus, fill the drive back up with the ntfs windows partion.
i did this by re-formatting the ubuntu partition to ntfs, then merged the two. 

  The ubuntu partitioner on the live cd was still determined that i should partition the storage volume instead of the main one.

  At this point i decided to give up and go back to windows, and give up on the dual boot. but found that i could no longer boot up windows either.

The good news is that i have now used what was the storage volume and created a brand new installation of xp and ubuntu, and it is running really nicely:):)

if any body knows how to mount the problem drive i would really appreciate some guidance.

Thanks for reading.

---

### Post by whollycow on 2008-11-22
[http://www.linuxforums.org/forum/peripherals-hardware/46891-how-do-i-mount-scsi-tape-drive.html](http://www.linuxforums.org/forum/peripherals-hardware/46891-how-do-i-mount-scsi-tape-drive.html)

Looks like according to this forum posting it's not possible to mount as you would other drives.  Not much of an answer, but hopefully this puts you on the right track.  Good luck.

---

### Post by Bigneil on 2008-11-22
perhaps it would be possible to run a recovery of xp on it and then see it it would be bootable into xp agan ??

or i have heard talk of a program that can pull files out of a formatted drive??

---

### Post by Bigneil on 2008-11-22
> **whollycow said:**
> [http://www.linuxforums.org/forum/peripherals-hardware/46891-how-do-i-mount-scsi-tape-drive.html](http://www.linuxforums.org/forum/peripherals-hardware/46891-how-do-i-mount-scsi-tape-drive.html)

Looks like according to this forum posting it's not possible to mount as you would other drives.  Not much of an answer, but hopefully this puts you on the right track.  Good luck.


It may well help, i'll have a close read up and have a few goes at it,.....
I'm just a bit paranoid that i might do more damage and completely loose any retrievable data on the disk

thanks for your help

---

### Post by Bigneil on 2008-11-23
I have run a 'testdisk' on the drive. and it is recognising the partitions on it:guitar:

but i don't really know what to do next.

If i can restore the partion for my XP i could boot it up and retrieve my files that way.???

HELP !



Here is a screen shot.-->

---

### Post by Bigneil on 2008-11-23
Ok, it states that, partition could not be restored.:(

Would photorec be my next step??

---

### Post by Bigneil on 2008-11-23
ok, i dove in at the deep end and ran photorec and recovered loads of files:guitar:

I still have to trawl through them and weed out the important files.

---

