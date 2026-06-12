---
title: "Ubuntu 9.04 insatallation problem"
date: 2009-07-22
forum: Installation &amp; Upgrades
---

### Post by garotonoite on 2009-07-22
**Ubuntu 9.04 insatallation problem**                                                                             I am having problem intalling Ubuntu 9.04 over windows Vista. I have Windows Vista insatalled on main drive C: which is configured as RAID0. I also have 2 other SATA drive with drive letter D & E. I want to install Ubuntu 9.04 on my Windows Vista on Drive D wiht 30GB allocated. I was succesful until it ask for reboot which I did and then it gives me following message while booting into Ubuntu.
Busybox v1.10.2 (ubuntu 1:1.10.2-2ubuntu7) Built-in shell (ash)
Enter 'help" for a list of built-in commands
initramfs
I tried many times and the problem is persisting every time. I even tried the full insatllation alone with windows vista but still no sucess. 
 
Cen anyone help me with this issue. It' frustaiting.



Felipe Medeiros
-------------------------
Name: Felipe Medeiros
Status: Analyst JR
E-mail: [EMAIL="felipe.medeiros@weblocal.com.br"]felipe.medeiros@weblocal.com.br[/EMAIL]
Company: Weblocal [Hospedagem]("http://www.weblocal.com.br")
Hobby:[AdWords]("https://adwords.google.com.br/")

---

### Post by dstew on 2009-07-22
If your D: and E: partitions are on a RAID0, as your C: partition is, then you will have problems. The Ubuntu installer on the Live CD cannot access partitions on RAIDs. The installer will treat the disk partitions it sees as being un-RAIDed, and will install, but usually this destroys the RAID.

There is a method to try to install from a Live CD to a part-hardware, part-software RAID such as you have (also called a FakeRAID, to distinguish it from true hardware RAID, which is seldom used). The method is documented [here]("https://help.ubuntu.com/community/FakeRaidHowto"). It is not guarenteed to work, but you can try it if you want. Here is [another How-To]("http://bbossola.wordpress.com/2008/03/07/dmraid-on-ubuntu-with-sata-fakeraid/") of the same method.

There is some possibility that the [Alternate Install CD]("http://www.ubuntu.com/GetUbuntu/downloadmirrors#alternate") will be able to install to a FakeRAID, but I was unable to verify this. It will install to a software RAID though.

---

### Post by garotonoite on 2009-07-28
> **dstew said:**
> If your D: and E: partitions are on a RAID0, as your C: partition is, then you will have problems. The Ubuntu installer on the Live CD cannot access partitions on RAIDs. The installer will treat the disk partitions it sees as being un-RAIDed, and will install, but usually this destroys the RAID.

There is a method to try to install from a Live CD to a part-hardware, part-software RAID such as you have (also called a FakeRAID, to distinguish it from true hardware RAID, which is seldom used). The method is documented [here]("https://help.ubuntu.com/community/FakeRaidHowto"). It is not guarenteed to work, but you can try it if you want. Here is [another How-To]("http://bbossola.wordpress.com/2008/03/07/dmraid-on-ubuntu-with-sata-fakeraid/") of the same method.

There is some possibility that the [Alternate Install CD]("http://www.ubuntu.com/GetUbuntu/downloadmirrors#alternate") will be able to install to a FakeRAID, but I was unable to verify this. It will install to a software RAID though.


DSTEW, 

Thank you for your help, I sure appreciate it!




Felipe Medeiros
-------------------------
Name: Felipe Medeiros
Status: Analyst JR
E-mail: [email]felipe.medeiros@weblocal.com.br[/email]
Company: Weblocal [Hospedagem](http://www.weblocal.com.br)
Hobby: [AdWords](https://adwords.google.com.br/)

---

