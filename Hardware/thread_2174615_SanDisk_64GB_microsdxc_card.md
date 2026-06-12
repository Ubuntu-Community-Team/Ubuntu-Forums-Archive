---
title: "SanDisk 64GB microsdxc card"
date: 2013-09-15
forum: Hardware
---

### Post by davidmaxwaterman on 2013-09-15
Hi,

I just bought a SanDisk 64GB microsd card, but haven't been able to get it to work.

Can someone suggest how I might be able to determine if it is broken or if it is some driver error?

I'm getting these errors :

```
kernel: [  553.416039] mmc0: new high speed SDXC card at address e624
kernel: [  553.416463] mmcblk0: mmc0:e624 SU64G 59.4 GiB 
kernel: [  553.417920]  mmcblk0: p1
udisksd[2507]: Mounted /dev/mmcblk0p1 at /media/davidmaxwaterman/New Volume on behalf of uid 1000
kernel: [  589.212882] mmcblk0: error -84 transferring data, sector 72544, nr 85, cmd response 0x900, card status 0xc00
kernel: [  589.212968] blk_update_request: 123 callbacks suppressed
kernel: [  589.212971] end_request: I/O error, dev mmcblk0, sector 72566
kernel: [  589.212973] end_request: I/O error, dev mmcblk0, sector 72568
kernel: [  589.212975] end_request: I/O error, dev mmcblk0, sector 72576
kernel: [  589.212977] end_request: I/O error, dev mmcblk0, sector 72584
kernel: [  589.212979] end_request: I/O error, dev mmcblk0, sector 72592
kernel: [  589.212981] end_request: I/O error, dev mmcblk0, sector 72600
kernel: [  589.212983] end_request: I/O error, dev mmcblk0, sector 72608
kernel: [  589.212985] end_request: I/O error, dev mmcblk0, sector 72616
kernel: [  589.212987] end_request: I/O error, dev mmcblk0, sector 72624
kernel: [  589.214351] mmcblk0: error -84 transferring data, sector 2080, nr 3, cmd response 0x900, card status 0xc00
kernel: [  589.214432] end_request: I/O error, dev mmcblk0, sector 2080
kernel: [  589.214436] Buffer I/O error on device mmcblk0p1, logical block 32
kernel: [  589.214438] lost page write due to I/O error on mmcblk0p1
kernel: [  589.214441] Buffer I/O error on device mmcblk0p1, logical block 33
kernel: [  589.214443] lost page write due to I/O error on mmcblk0p1
kernel: [  589.214446] Buffer I/O error on device mmcblk0p1, logical block 34
kernel: [  589.214447] lost page write due to I/O error on mmcblk0p1
kernel: [  589.218446] mmcblk0: error -84 transferring data, sector 63008, nr 128, cmd response 0x900, card status 0xc00
kernel: [  589.218584] Buffer I/O error on device mmcblk0p1, logical block 60964
kernel: [  589.218588] lost page write due to I/O error on mmcblk0p1
kernel: [  589.218597] Buffer I/O error on device mmcblk0p1, logical block 60965
kernel: [  589.218600] lost page write due to I/O error on mmcblk0p1
kernel: [  589.218609] Buffer I/O error on device mmcblk0p1, logical block 60966
kernel: [  589.218612] lost page write due to I/O error on mmcblk0p1
kernel: [  589.218621] Buffer I/O error on device mmcblk0p1, logical block 60967
kernel: [  589.218624] lost page write due to I/O error on mmcblk0p1
kernel: [  589.218636] Buffer I/O error on device mmcblk0p1, logical block 60968
kernel: [  589.218639] lost page write due to I/O error on mmcblk0p1
kernel: [  589.218648] Buffer I/O error on device mmcblk0p1, logical block 60969
kernel: [  589.218651] lost page write due to I/O error on mmcblk0p1
kernel: [  589.218659] Buffer I/O error on device mmcblk0p1, logical block 60970
kernel: [  589.218663] lost page write due to I/O error on mmcblk0p1
kernel: [  589.223095] mmcblk0: error -84 transferring data, sector 63136, nr 128, cmd response 0x900, card status 0xc00
kernel: [  589.420296] mmcblk0: error -84 transferring data, sector 67488, nr 128, cmd response 0x900, card status 0xc00
kernel: [  589.438682] mmcblk0: error -84 transferring data, sector 68000, nr 128, cmd response 0x900, card status 0xc00
kernel: [  589.511931] mmcblk0: error -84 transferring data, sector 69920, nr 128, cmd response 0x900, card status 0xc00

```

My intention is to copy some music onto it and use it in my car (Audi A1)'s music system. I've tried formatting it as various filesystem types, all with similar results.

Thanks,

Max.
PS. DISTRIB_DESCRIPTION="Ubuntu 13.04"

---

### Post by davidmaxwaterman on 2013-09-28
FWIW, I formated it on Windows7 as fat32 (using some 3rd party tool since Microsoft tools won't do it) - fat32 because I have been lead to believe that my Audio A1's MMI won't read exFAT or NTFS; and then used scp to copy the files from my Ubuntu laptop onto the card on the Windows7 machine. The copy seemed to go without any error - though I don't know how to do the equivalent of 'tail -f /var/log/syslog' on Windows 7, so I can't be sure there were no errors. I can also play the audio files on Windows 7, apparently without any problem.

Anyway, it all *looks* ok when I put the card into my laptop, but when I try to compare the files by running md5sum on all the files, I still get errors in syslog.

I'm starting to think it's the card *reader* that's the problem :/

Max.

---

