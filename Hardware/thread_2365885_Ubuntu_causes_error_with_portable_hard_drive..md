---
title: "Ubuntu causes error with portable hard drive."
date: 2017-07-11
forum: Hardware
---

### Post by holthaunt on 2017-07-11
I am using Ubuntu 16.04 LTS and have had the following problem a few times. I believe Ubuntu is causing issues/error with my portable Sata hard drive. I will plug in and find that my NTFS partition and data is gone. The drive is seen as an unallocated NTFS. I have not been able to recover the partition or data. The first time this happened it was on a drive that was questionable, so I figured that the drive went bad, but I found that I could wipe data then reformat the drive-worked fine after that. The second time, on a different drive, this happened I have not been able to find the drive at all-in any recovery software. Then yesterday I was transferring about 40gb of files on to a third drive and received a copy error. I didn't think much of it because I was done with work for the day, so I unplugged drive and shut down computer. Then today I plug in drive and found unallocated NTFS. That when it hit me. Each time I had a failure I had been copying large amounts of data to a drive and received a copy error. Then next time I plugged in drive I had issues. I don't remember the full error message, but I believe it had to do with not finding drive to copy data.

Does anyone have any idea what is cause this and what I can do about it?  Thanks.

---

### Post by Autodave on 2017-07-11
One thing that I can think of: are you using a USB 2.0 or 3.0 drive? If USB 2.0, are you plugging it into a USB 3.0 port? I have seen that cause an issue similar to what you are experiencing.

---

### Post by holthaunt on 2017-07-11
No just 2.0. I forgot to mention that I use the drive in both Ubuntu/Win10 OS. I just read a new post about someone having this problem with usb pen drive, who also had a similar problem.

---

### Post by efflandt on 2017-07-13
If the drive is only powered from USB, maybe it is not quite getting enough power for long file copy operations. Portable drives often include a cable with 2 USB plugs because USB 2.0 is only required to provide 500 mA and the drive may require more power than that. You may want to try a powered USB hub, especially if doing that with a laptop. Although, some laptops have one specific USB port that can provide up to 2 A (2000 mA).

If you connect one of the failed drives to Windows does it mount with a drive letter? If it does, you could try repairing it with chkdsk /f with that drive letter and colon. But I don't know if Windows can fix a drive that does not mount (other than reformatting it).

You should always make sure that a drive is NOT mounted before unplugging it by either clicking on the eject button next to it in File Manager, or using umount (or sudo umount) in a terminal, to make sure that any writing to the drive has completed. Otherwise you risk corrupting it.

---

