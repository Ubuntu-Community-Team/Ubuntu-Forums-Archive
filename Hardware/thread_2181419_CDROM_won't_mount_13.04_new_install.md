---
title: "CDROM won't mount 13.04 new install"
date: 2013-10-17
forum: Hardware
---

### Post by Bhakti108 on 2013-10-17
G'day all

I am installing Ubuntu for a friend on their acer laptop. I tried 12.04 and found that after install the os doesn't see the cdrom. (it works fine in win 7) I decided to do a new install of 13.04 and see if that fixed it, but no it doesn't. I have scoured the net but can't find anything that works. 

I used disk utility in 12.04 and found the drive listed as dev/sr0 but in 13.04 using the replacelement program "disks" all I see is the total hard drive size and nothing else??

So my question is, please can someone give me the step by step commands / process to mount the cdrom at boot time automatically. 

Thanks

EDIT -- SOLVED -- after hours of searching and trying all sorts of commands etc, finally I came acrosss the answer and it is so easy, so for others who might have this issue, and it seems to be a common one.

1) on boot access your BIOS 
2) change the drive order of boot devices so that the cdrom is after HDD 
3) Save and exit the BIOS 

continue to Ubuntu login, and you will find your cdrom /dvd is now mounted and usable. Problem Solved  :)

---

