---
title: "Challenge accessing 4TB NTFS partition using Ubuntu 14.04"
date: 2015-08-09
forum: Hardware
---

### Post by darts2 on 2015-08-09
Hi Everyone,

I have purchased a WD 4TB hard drive and partitioned it as NTFS using MiniTool Partition Wizard ([http://www.minitool.com/partition-manager/partition-wizard-home.html](http://www.minitool.com/partition-manager/partition-wizard-home.html)).

Now when I connect the hard drive to my Ubuntu box I am not seeing it in File Manager. If I run the 'lsblk' command at the terminal I see the drive at sda but with no mount point, as shown below.

[IMG]http://i58.tinypic.com/ranfvk.jpg[/IMG]

How can I go about mounting this drive?

Any help will be greatly appreciated.

Kind Regards,

Davo

---

### Post by weatherman2 on 2015-08-10
What's the output of:

```
sudo parted -l /dev/sda
```

?

---

### Post by oldfred on 2015-08-10
Since over 2TiB, you have to use gpt partitioning.
       MBR tech details including 2TiB limit and GPT link
[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)
[http://en.wikipedia.org/wiki/GUID_Partition_Table](http://en.wikipedia.org/wiki/GUID_Partition_Table)

 GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr](http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr)

---

### Post by darts2 on 2015-08-10
Hi weatherman2,

Thank you for responding to my post. I left the computer (off) over night, then this morning when I booted up I was able to see the disk in File Manager. I am not sure of why the drive was not available yesterday.

Kind Regards,

Davo

---

