---
title: "ubuntu server install - cannot see second HD"
date: 2009-06-08
forum: Installation &amp; Upgrades
---

### Post by dangerp on 2009-06-08
This is strange.  I just got a brand spanking new Dell tower server (PowerEdge T605 if that matters).  It came from the factory with two identical 500gb SATA hard drives.  The intention was to set up software RAID1.  I'm going through the install process, and everything is fine, except that the install process only sees one hard drive, not the second one.  If I continue, the rest of the install goes fine, and ubuntu server is installed on the first hard drive.  I tried using a gparted live CD to see if I can see the second hard drive, but no luck there either.

I confirmed that the machine sees the second hard drive using the BIOS.  I haven't tried to troubleshoot this type of issue before, and I don't even know where to start.  Any ideas on how I should proceed?  I am fine with doing another fresh install, or just modifying the current installation.

---

### Post by dangerp on 2009-06-08
Unexplainable.

After several reboots etc, I went into the BIOS and turned off the SATA controller altogether, then rebooted.  Then I went back into the BIOS and re-enabled the SATA controller.  Now all of a sudden it works.  No clue as to why...

---

### Post by vtex on 2009-06-10
[SIZE=3]I am having the same issue.  Brand new T605 - it cannot see the second hard drive in both Ubuntu or in Debian.  It appears that it may be a driver issue as the T605 uses the Broadcom HT1100 Chipset.  Talked with a Dell rep who pointed me to this page for a RHEL5 driver:

[http://support.dell.com/support/downloads/download.aspx?c=us&l=en&s=gen&SystemID=PWE_T605&os=RHEL5&osl=en&devlib=0&typecnt=0&vercnt=1&catid=-1&impid=-1&formatcnt=1&libid=27&fileid=237028](http://support.dell.com/support/downloads/download.aspx?c=us&l=en&s=gen&SystemID=PWE_T605&os=RHEL5&osl=en&devlib=0&typecnt=0&vercnt=1&catid=-1&impid=-1&formatcnt=1&libid=27&fileid=237028)

Have not yet tried it, but I will give an update if I find a solution to this issue.[/SIZE]

---

### Post by vtex on 2009-06-10
[SIZE=4]Well, this is very odd indeed.  It seems just "messing with it" as stated in the earlier post worked for me as well.  I was able to get Ubuntu to recognize the other drive by just switching the SATA port the drive was plugged in to.  *sigh*


[/SIZE]

---

### Post by dangerp on 2009-06-11
It defies reason, right?  Maybe the BIOS configuration is corrupted as shipped?  It doesn't make any sense to me either.  All I know is that I changed a setting, and then changed it back.  Didn't change other settings, didn't use proprietary drivers, didn't change the installation method.

Hopefully it helps someone else out.

---

