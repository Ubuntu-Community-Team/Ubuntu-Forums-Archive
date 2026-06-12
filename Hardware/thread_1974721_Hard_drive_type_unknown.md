---
title: "Hard drive type: unknown"
date: 2012-05-06
forum: Hardware
---

### Post by joshwd36 on 2012-05-06
My computer won't boot from a hard drive, and when I go onto disk utility on the Ubuntu live CD it says the type of my Windows partition is unknown
[IMG]https://www.dropbox.com/s/2e5r3chtouewrfu/hard%20drive.png[/IMG] 
My Ubuntu partition is still intact, but it won't boot. How can I fix this?

---

### Post by ahallubuntu on 2012-05-06
What kind of system is it?  Dual-boot?  Windows on one drive, Ubuntu on another drive?   What version of Ubuntu?

If you have a Windows CD, it would help to boot it and run chkdsk /f on the Windows partition that you can now no longer access...

---

### Post by cmont899 on 2012-05-06
You will need to install ntfs support:

```
sudo apt-get install sudo ntfs-3g
```

You may need to load the module afterware or reboot:

```
sudo modprobe ntfs
```

---

### Post by joshwd36 on 2012-05-06
I have dual boot. They are both on one drive, but on different partitions. I have Ubuntu 11.10. 
I am running Ubuntu from the CD so I'm not sure any packages I install will stay.

---

### Post by ahallubuntu on 2012-05-06
A modern Ubuntu install or CD already has built-in NTFS support.  No need to install it.

Your picture shows two attached hard drives: a 120GB and a 160GB.  Are you saying the 160GB is the one with both operating system partitions on it?  Maybe your system is stuck trying to boot off the 120GB?  Did you change anything recently in your system?

According to that picture it appears the 160GB drive is S.M.A.R.T. healthy.  Good - that's the next thing I was going to ask you to check.

You might try re-installing Grub from the live CD as described here:

[https://help.ubuntu.com/community/Grub2#ChRoot](https://help.ubuntu.com/community/Grub2#ChRoot)

if you're just trying to get it to boot again.  But that doesn't solve the mystery of your Windows partition.  You might need to run the Windows chkdsk /f on the Windows partition by booting a Windows disc.

Note that to follow the instructions above, you need to make sure you know which drive has the Ubuntu partition on it.  Looks like that might be /dev/sdb in your case?  Or is it the 120GB /dev/sda ?

---

### Post by joshwd36 on 2012-05-06
It's the sdb drive. I have made sure it isn't trying to boot off the 120gb, but I will double check. Thanks.

---

### Post by joshwd36 on 2012-05-07
I ran chkdsk /f and it says
Cannot lock current drive
Windows cannot run disk checking because it is write protected.

---

### Post by ahallubuntu on 2012-05-07
How did you run chkdsk?  From a Windows CD?  What version of Windows is installed?  What type of Windows CD?

---

### Post by joshwd36 on 2012-05-07
I have Windows 7 and I ran it from the setup DVD. I went on repair windows, clicked command line and ran it from there

---

