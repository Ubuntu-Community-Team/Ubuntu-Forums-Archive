---
title: "Kingston SSD Now V100"
date: 2011-03-28
forum: Hardware
---

### Post by oobayly on 2011-03-28
I'm running Maverick on a Kingston SSD Now V100 and am having issues getting trim to work, I've added **discard** to my /etc/fstab, but haven't been able to confirm that it's working (using the HowTo [HOWTO: Check If TRIM On Ext4...]("https://sites.google.com/site/lightrush/random-1/checkiftrimonext4isenabledandworking"))

The following output implies that TRIM should be working:
```

root@Tips-X100e:~# uname -a
Linux Tips-X100e 2.6.35-28-generic #49-Ubuntu SMP Tue Mar 1 14:39:03 UTC 2011 x86_64 GNU/Linux

root@Tips-X100e:~# hdparm -I /dev/sda | grep -i trim
	   *	Data Set Management TRIM supported

root@Tips-X100e:/var/tmp# hdparm -V
hdparm v9.27

```

I also tried skiping wiper and using hdparm --trim-sector-ranges (very carefully :-))
```

root@Tips-X100e:/var/tmp# dd if=/dev/urandom of=tempfile count=10 bs=1M
10+0 records in
10+0 records out
10485760 bytes (10 MB) copied, 2.90546 s, 3.6 MB/s

root@Tips-X100e:/var/tmp# hdparm --fibmap tempfile 
tempfile:
 filesystem blocksize 4096, begins at LBA 2048; assuming 512 byte sectors.
 byte_offset  begin_LBA    end_LBA    sectors
           0   57133056   57149439      16384
     8388608   57243648   57247743       4096

root@Tips-X100e:/var/tmp# rm tempfile; sync

root@Tips-X100e:/var/tmp# hdparm --read-sector 57133056 /dev/sda | head -n 10
/dev/sda:
reading sector 57133056: succeeded
ed46 95eb 2e78 ea9b 29d2 070e dc8d a893
00b4 3f23 b270 5f86 32f4 2c46 0fc8 2dac
fa7d 6c14 72b4 615d 1d03 d8aa 5dd9 facb
a555 4354 68c3 b64d 1a25 1507 d455 eed3
ee21 2c75 3cbe 9c23 ea11 8812 0580 612b
dc31 463f dcba 658b a604 2cc9 b48e 3d00
f4d6 5270 6037 7b9c 11ca 3198 1587 5617

root@Tips-X100e:/var/tmp# hdparm --please-destroy-my-drive --trim-sector-ranges 57133056:16384 /dev/sda
/dev/sda:
trimming 16384 sectors from 1 ranges
succeeded

root@Tips-X100e:/var/tmp# hdparm --read-sector 57133056 /dev/sda | head -n 10
/dev/sda:
reading sector 57133056: succeeded
ed46 95eb 2e78 ea9b 29d2 070e dc8d a893
00b4 3f23 b270 5f86 32f4 2c46 0fc8 2dac
fa7d 6c14 72b4 615d 1d03 d8aa 5dd9 facb
a555 4354 68c3 b64d 1a25 1507 d455 eed3
ee21 2c75 3cbe 9c23 ea11 8812 0580 612b
dc31 463f dcba 658b a604 2cc9 b48e 3d00
f4d6 5270 6037 7b9c 11ca 3198 1587 5617

```

I've also tried the above with and without the discard flag in fstab.

As you can see, the drive doesn't appear to be TRIMed, does anyone have any suggestions, or have I just lucked out and bought a drive that says it supports TRIM but doesn't really?

Thanks,
John

---

### Post by imac_89 on 2011-04-10
Oooo, looks like I am going to be having fun in the near future. I have a 64GB Kingston v100 on order for myself. 

I have been doing an awful lot of reading on alignment of SSDs, I am catching on a little, but not enough to help out. 

My use will be a small lightweight web-server, atom based, 2gb ram and this little gem.


What firmware are you using on your SSD?

According to [http://www.legitreviews.com/article/1556/2/](http://www.legitreviews.com/article/1556/2/), the controller does support TRIM.

---

