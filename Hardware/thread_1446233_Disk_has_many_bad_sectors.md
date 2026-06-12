---
title: "Disk has many bad sectors"
date: 2010-04-03
forum: Hardware
---

### Post by mongoose_za on 2010-04-03
hi there,

I'm getting this message constantly about the hard drive that Ubuntu is installed on. Message: *'Disk has many bad sectors'*. I've screenshot to make it clearer.



I'd like to mark the bad sectors and fix or remove them if possible so I tried to boot off the cd and

```
sudo fsck -pcfv /dev/sdb
```

I then get the error message about superblock missing etc. I should rather try > sudo e2fsck -b 8193 /dev/sdb however that does nothing..

*note: I ran scandisk on the hard drive in windows. A thorough scan which came out as 100% ok :/*

Any suggestions would be greatly appreciated.
Thanks in advance

---

### Post by Revolutionary101 on 2010-04-03
1. Bad sectors are a physical problem with the hard drive, mostly caused by the ageing of the hard drive. Thus these bad sectors can't be fixed by software means. (at least that I know of)

2. As for the Windows scan, the scan most likely only scanned the Windows partition and not the Linux Mint one. If the bad sectors are only located on the Linux Mint partition, the Windows scan would not have detected them.

I hope these answers may have enlightened you about your problem. If you have any more questions just ask.

---

### Post by mongoose_za on 2010-04-03
Hi Rev,

The hard drive is quite old (4years). It doesn't seem to be causing any issues so I'll just keep using it as is.

Oh and when I scanned the drive originally it was NTFS. I only formatted it during the install process. I wasn't clear about that in my post sorry.

I also found that when clicking on the drive in Palimpsest you can click 'More information". Then in that tab you can check 'Don't warn me if the disk is failing'. Probably not recommended but it's gotten rid of that irritating message alert.

---

### Post by Revolutionary101 on 2010-04-03
Yes its not a big problem. I too have the same problem with my hard drive. Just make sure that you backup your hard drive occasionally.

---

### Post by Mark Phelps on 2010-04-05
Unfortunately, 9.10 has developed a bad reputation for reporting "false positives" regarding hard disk problems.

You would do better going to the website of the manufacturer of your hard drive, and downloading any disk checking utility they have -- and running that instead.

I encountered the same problems with my WDC drive, downloaded their utility, ran it -- and it found NO errors!  That was months ago and I've not had any problems with the drive at all.

---

### Post by Revolutionary101 on 2010-04-05
> **Mark Phelps said:**
> Unfortunately, 9.10 has developed a bad reputation for reporting "false positives" regarding hard disk problems.

You would do better going to the website of the manufacturer of your hard drive, and downloading any disk checking utility they have -- and running that instead.

I encountered the same problems with my WDC drive, downloaded their utility, ran it -- and it found NO errors!  That was months ago and I've not had any problems with the drive at all.

Wow thanks for that info. I thought my HDD was going to fail soon. Well anyways it doesn't hurt to backup my HDD from time to time, its a good habit to get into.

Do you know if the false positives are going to be fixed in 10.04? I sure hope they fix it.

---

### Post by paulisdead on 2010-04-05
> **Mark Phelps said:**
> Unfortunately, 9.10 has developed a bad reputation for reporting "false positives" regarding hard disk problems.

You would do better going to the website of the manufacturer of your hard drive, and downloading any disk checking utility they have -- and running that instead.

I encountered the same problems with my WDC drive, downloaded their utility, ran it -- and it found NO errors!  That was months ago and I've not had any problems with the drive at all.

I'll second that.  I've got a samsung drive in my Dell D430 that is known to have compatibility problems with Palimpsest.

With 10.04, it's definitely not fixed for my drive.  I still had to disable the notifications.  I've had the alpha/beta running on that laptop for a few weeks.  I'm sure the drive's fine, since I tested it with both Dell and Samsung's tools the first time I saw that error and freaked out.

---

### Post by mongoose_za on 2010-04-06
Alrighty, it's good to know that this seems to be reasonably common. As Rev said though it's not bad practice to backup just in case :D

---

