---
title: "SSD recognized as HDD"
date: 2015-06-11
forum: Hardware
---

### Post by guenther4 on 2015-06-11
Hi all,

I have 14.04 LTS Server on a RAID1 of Samsung SSDs. I tried to check if trim is working using fstrim but it failed:

```
~$ sudo fstrim / 
fstrim: /: FITRIM ioctl failed: Inappropriate ioctl for device
```

So I checked if my SSD is recognized as such:
```
~$ cat /sys/block/sda/queue/rotational
1
```

Which means HDD but not SSD ([https://wiki.debian.org/SSDOptimization](https://wiki.debian.org/SSDOptimization))

And I tried 
```
~$ cat /proc/scsi/scsi
Attached devices:
Host: scsi0 Channel: 02 Id: 00 Lun: 00
  Vendor: LSI      Model: MR SAS 6G 1GB    Rev: 3.22
  Type:   Direct-Access                    ANSI  SCSI revision: 05
Host: scsi1 Channel: 00 Id: 00 Lun: 00
  Vendor: TSSTcorp Model: CDDVDW SN-208FB  Rev: FT01
  Type:   CD-ROM                           ANSI  SCSI revision: 05
```

So how can I tell Ubuntu that there are SSDs connected and to get weekly trims working?

Thanks in advance
Günther

---

### Post by efflandt on 2015-06-12
Unless something changed, TRIM did not work on RAID SSDs before. It works from 14.04 on a non-raid SSD (in my case a backup Linux system on sdb1):```
efflandt@XPS-8100-1404:~$ sudo fstrim /media/efflandt/1b68a308-8400-41fc-a1f1-0197397f37b7/
efflandt@XPS-8100-1404:~$
```

---

### Post by guenther4 on 2015-06-15
> **efflandt said:**
> Unless something changed, TRIM did not work on RAID SSDs before. It works from 14.04 on a non-raid SSD (in my case a backup Linux system on sdb1)

Thank you for your reply.

Hm... that leaves me with 2 questions:


[LIST=1]
[*]How important is trimming to keep system's performance on a high level
[*]Can I add some packages to enable TRIM in 14.04 with RAID SSD?
[/LIST]

Regards,

Günther

---

### Post by kryten35 on 2015-06-15
Are you using LVM or encryption? If yes,then you have to activate trim for them.
[URL="http://blog.neutrino.es/2013/howto-properly-activate-trim-for-your-ssd-on-linux-fstrim-lvm-and-dmcrypt/"]
http://blog.neutrino.es/2013/howto-properly-activate-trim-for-your-ssd-on-linux-fstrim-lvm-and-dmcrypt/[/URL]

---

### Post by guenther4 on 2015-06-16
> **kryten35 said:**
> Are you using LVM or encryption? If yes,then you have to activate trim for them.

No, I don't use eighter of them.

---

### Post by dino99 on 2015-06-16
some related links  [http://askubuntu.com/questions/461808/does-ubuntu-14-04-support-ssd-trim-on-software-raid](http://askubuntu.com/questions/461808/does-ubuntu-14-04-support-ssd-trim-on-software-raid)

---

### Post by guenther4 on 2015-06-16
Thanks for the links. I am confused now. So should I use discard in fstab or is this useless? Will discard work even if fstrim won't?

---

### Post by dino99 on 2015-06-16
'discard' explanations with many cases [https://wiki.debian.org/SSDOptimization](https://wiki.debian.org/SSDOptimization)

---

