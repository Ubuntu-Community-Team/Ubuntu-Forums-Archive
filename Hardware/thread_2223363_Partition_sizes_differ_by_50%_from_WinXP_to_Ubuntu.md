---
title: "Partition sizes differ by 50% from WinXP to Ubuntu on 2.7TB-HDD"
date: 2014-05-10
forum: Hardware
---

### Post by frank54 on 2014-05-10
Hi,
I've got a strange problem with a brand new 2.7TB-WesternDigital-HDD. If I create partitions under WinXP, they are reported half the size in Ubuntus gParted. If I create them in Ubuntu, they are reported double size in WinXP. The total disk size of about 2.7TB is reported correct in both systems. I've never had that before. 

I create the partitions as basis for truecrypt device encryption. It doesn't matter, on which size a create the TC-device, formatted to NTFS. In both directions it cannot decrypted by the other TC, which is not surprisingly to me, since the basic partition is already wrong.

Anybody any idea how to fix that?

Regards
Frank

UBUNTU liveCD 14.04, WinXP SP 3, TC 7.1a

---

### Post by slooksterpsv on 2014-05-10
Is your Windows XP 32-bit or 64-bit. If it's 32-bit a lot of users have reported that the most they see in Windows is 2TB.

What are the sizes specifically? E.g. Ubuntu reports 2.5TB, XP reports 1.25TB or however you have them configured. Also are you using 32-bit or 64-bit Ubuntu? What are the specs of your machine as well?

---

### Post by oldfred on 2014-05-11
Any drive over 2TB needs gpt and XP does not work with gpt partitioning.

       GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)


 MBR tech details including 2TiB limit and GPT link
[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)

---

