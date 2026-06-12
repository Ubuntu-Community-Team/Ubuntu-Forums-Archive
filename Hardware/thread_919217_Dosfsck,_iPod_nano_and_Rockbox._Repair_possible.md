---
title: "Dosfsck, iPod nano and Rockbox. Repair possible?"
date: 2008-09-13
forum: Hardware
---

### Post by DirtDawg on 2008-09-13
After deleting a large number of files from my ipod 1st generation, 2 gig nano, it stopped mounting automatically. When trying to mount manually, I would get an error about the iPod not being a block device. From what I've read, this might mean my Rockbox partition has somehow become corrupted.

I tried repairing with "dosfsck -r /dev/sdc2" (sdc2 is the Rockbox partition). I have not used dosfsck before. I got this in return:
```
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
There are differences between boot sector and its backup.
Differences: (offset:original/backup)
  65:03/00
1) Copy original to backup
2) Copy backup to original
3) No action
? 1
FSINFO sector has bad magic number(s):
  Offset 0: 0x00059601 != expected 0x41615252
  Offset 484: 0x0005b67a != expected 0x61417272
  Offset 510: 0x0005 != expected 0xaa55
1) Correct
2) Don't correct (FSINFO invalid then)
? 1
Got 1409024 bytes instead of 1907992 at 16384
```
As you can see, I answered '1' to both, though I'm not sure what question 1 is even asking.

After running dosfsck, I can manually mount the ipod, but it no longer mounts automatically and I can't get any kind of readout about the space left on the iPod's hard drive. When I rerun dosfsck, I get exactly the same response, so I'm not sure anything is actually being repaired.

Is dosfsck capable of repairing the problems I'm having? I'm starting to think I may need to use Apples' iPod recovery tool and reinstall Rockbox from scratch. Something I don't mind doing as long as it's safe.

I should mention the ipod has failed to mount automatically on 3 separate Ubuntu boxes and when plugged into my Windows box, a dialog box tells me iTunes needs to reformat and restore the entire iPod.

Any insight would be appreciated. I'm a little worried about doing something wrong and giving my iPod the old 'brick syndrome'.

Thanks.

---

### Post by DoctorMO on 2008-09-14
Have you tried repartitioning it using gnome partition manager?

---

### Post by DirtDawg on 2008-09-14
> **DoctorMO said:**
> Have you tried repartitioning it using gnome partition manager?

Thank you for your response. I have not tried reformatting yet. I was thinking about doing just that, but probably on the Windows box with the idea that iTunes could reformat and recover the iPod, then I could reinstall Rockbox, as mentioned above.

However, as of now, when I transfer files I often get an input/output error (though not consistently). I read elsewhere that error sometimes indicates a hard drive going bad. But could that error also be a result of a failed partition?

I'm concerned that if I reformat and try to reinstall the Apple firmware (and Rockbox) and the hard drive is going south, the hard drive might error out in the middle of the process, reducing my iPod to brick status. For now at least it works, although it's pretty rocky going.

---

### Post by DirtDawg on 2008-10-28
Follow up for the curious: I used Windows iTunes to reformat my ipod, then reinstalled rockbox and everything was fine. :KS

---

