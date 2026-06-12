---
title: "New to Ubuntu and having problems"
date: 2006-02-09
forum: Installation &amp; Upgrades
---

### Post by headshot007 on 2006-02-09
Okay, i'm new to any Linux distros out there so if you could try to keep talk basic it would be helpful.

So what happens is, i've put Ubuntu 5.10 on my pc and now i want to put winXP back on, i was testing Ubuntu on this PC to see if i like it. 

Now what im trying to do is, is load the winxp installation cd and put winXP back on this PC but im receiving an error:
> [color=green]STOP: C0000221 Unknown Hard Error
\Systemroot\System32\ntdll.dll[/color]
It loads all the drivers etc it needs for setup and just before it goes to the next screen this error comes up and i cant do anything else.

I have searched other sites but they all have the same link: [http://support.microsoft.com/?kbid=314474](http://support.microsoft.com/?kbid=314474) and it seems no use to me. Is there anyway i can place a ntdll.dll file on my master drive and be able to format over the top of Ubuntu?

---

### Post by Greg2 on 2006-02-09
It ‘sounds’ like Windows is having problems with the existing Linux file system? So I would suggest you use a separate partitioning tool like the Gparted LiveCD:
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)
or Partition Magic if you have it, to make one primary FAT32 partition on your HDD. ‘Then’ use your WinXP CD to format your HDD with an NTFS file system and install XP.

---

### Post by shuttleworthwannabe on 2006-02-09
Do you still need the Linux installation; just my suggestions is if you do not then why not format the whole drive with winxp and create partitions using winxp install your winxp on the first partition, and format the rest at FAT32. When u install Linux choose the any one of the FAT32 partitions. Also when you parition with WinXp installation disc do not forget to create a small parition for swap in linux.

I am not sure if this is helpful or you tried this already?
best of luck,
s

---

