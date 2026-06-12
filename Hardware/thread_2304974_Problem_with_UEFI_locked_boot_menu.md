---
title: "Problem with UEFI locked boot menu"
date: 2015-12-01
forum: Hardware
---

### Post by shk2 on 2015-12-01
have got into a very big trouble as i cannot change my boot order  and also not able to boot from any installations am making on my hard  disk.  Recently my harddisk was crashed and i gave it to service center they  replaced my HDD am not sure if they changed my default bios password  and kept custom but am very sure i have not touched it.Now in the novo  button menu if i select boot setup it asks me for PASSWORD which i have  never set.
  Now i have tried installing several times but it is not picking my  ubuntu installation.I have deleted all the drive data which was present  for my earlier Windows 7 and Ubuntu 12 version.Currently am able to use  only 64 bit LIVE USB v15 ubuntu.
  If you would like to have a look at boot repair report i am providing the URL. [http://paste.ubuntu.com/13587360/](http://paste.ubuntu.com/13587360/) [http://paste.ubuntu.com/13587215/](http://paste.ubuntu.com/13587215/)
  I would be really grateful if you can help me remove this UEFI locked  configuration without opening the box,removing CMOS battery did not  helped me.
  With Regards

---

### Post by oldfred on 2015-12-01
I do not know of a way to reset password, other than CMOS battery. And now with UEFI, it remembers some data even then.
You need to contact service center and see what they did.
In hindsite, you should have a good backup before letting anyone else touch system.

Your drive is now MBR(msdos) partitioned. Were your install(s) in UEFI mode as that would have had to have drive in gpt partitioning?

Or did you have an LVM or LVM with encryption. You show an ext2 partition as sda1 which is only standard with LVM type installs. 

No installs are shown.
Some partitions are NTFS, which you should only have if using Windows as you cannot run chkdsk from Linux and you may need that occasionally. Ubuntu runs fsck every 40 or 60 boots (or used to).

---

