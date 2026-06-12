---
title: "[raid0, laptop &amp; install] RAID me all you want, baby"
date: 2007-10-18
forum: Hardware &amp; Laptops
---

### Post by Yunabeco on 2007-10-18
(Short version: "ERROR: isw: Error finding disk table slot")

Good day/night/whatever, people.

Now happy owner of an Alienware m9750, and having a RAID0 array of two 200 GB hard drives, I wanted to break free of my chains (read: dual-boot XP Pro 32bit & Ubuntu) and soon found a little [documentation about FakeRaid](https://help.ubuntu.com/community/FakeRaidHowto). It goes all fine and stuff until I try to start up dmraid, then it claims that I have no RAID arrays. Well, might be an hardware incompatibility, but I just wanted to make sure.

Already installed Ubuntu on another comp, but this one had a single regular clean hard drive.

Courtesy of Windoz's hardware manager, I have a Intel(R) 82801GHM SATA RAID Controller with on it two 183 GB disks, if I remember correctly from the bios. I have a 2.33 GHz dual core processor (Intel Core 2 duo), if that matters.

Oh yeah, starting dmraid spouts me an error about disk table slots.
> root@ubuntu:~# dmraid -ay
ERROR: isw: Error finding disk table slot for /dev/sda
ERROR: isw: Error finding disk table slot for /dev/sdb
No RAID disks
root@ubuntu:~#

Help would be appreciated.
Thank you~!

Oh yeah, forgot to say. Tested that on Gutsy Gibbon and Edgy Eft.

---

### Post by Yunabeco on 2007-10-30
Oh well. I'll give up on Linux this time. :(

---

### Post by Alienwarem9750 on 2008-05-21
> **Yunabeco said:**
> Oh well. I'll give up on Linux this time. :(

Did you try out any of the howtos?

[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

[http://wiki.eyermonkey.com/My_Ubuntu_%287.10%29_Installation](http://wiki.eyermonkey.com/My_Ubuntu_%287.10%29_Installation)

---

