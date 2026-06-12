---
title: "master boot record gone MBR boot-repair"
date: 2022-01-31
forum: Hardware
---

### Post by b49P23TIvg on 2022-01-31
[https://pastebin.ubuntu.com/p/psMzTVbGk3/](https://pastebin.ubuntu.com/p/psMzTVbGk3/)  expires on 2022-02-24.

Following 
***a command that deleted the entire system***
the master boot record was destroyed.  I had a 'new' system and I thought to start out learning about disk partitioning and other experiments.

I installed an SSD, and LTS 20.04, and am using the mechanical media as storage space.

Goal: make the computer dual boot (which it did before the experiment gone wrong) with windows 10 because I have a job to make a PulseBlaster board work in linux whereas it does work in window.  It would be great to see how the board should perform.  Anyway, I've been unable to install windows 10 alongside ubuntu on the SSD.  (The SSD has  EFI, ext3 partitions in first half, and ntfs in the other half.)

Nice work this post, I've invoked at least two possibly unrelated issues.

Thanks for your assistance, David Lambert

---

### Post by yancek on 2022-02-01
The command you used deleted the entire system and you can see in boot repair that there is no OS installed.  Check what a command does before running it.  The link below is the official Ubuntu documentation on dual booting with windows.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by tea for one on 2022-02-01
> **b49P23TIvg said:**
> Following 
sudo rm -r /
the master boot record was destroyed.

For new users of Ubuntu or, indeed, any flavour of a Linux OS, do not copy this command just to see what happens.
[COLOR="#0000FF"]yancek[/COLOR] has already described what happened. 

If curious, please read this [https://ubuntuforums.org/announcement.php?f=326](https://ubuntuforums.org/announcement.php?f=326)

---

