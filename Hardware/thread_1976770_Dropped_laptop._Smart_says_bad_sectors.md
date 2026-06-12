---
title: "Dropped laptop. Smart says bad sectors"
date: 2012-05-09
forum: Hardware
---

### Post by rockinruler on 2012-05-09
Hello,

I have Ubuntu and Win7 both installed on my laptop.

I was working on Windows when I dropped the laptop from about 3.5feet in air. Ever since, windows is unable to boot. But Ubuntu works just fine.

When I ran SMART, it shows me there are a few bad sectors. I'm attaching a screen shot of the report.

Can anyone suggest what must be done?

---

### Post by sudodus on 2012-05-09
- Do you have a recent backup of the windows partition?

- Are you thinking of getting a new internal HDD?

- Do you have an external drive with space enough to backup your personal files from Windows?

I would make a copy of the damaged drive with ***ddrescue***. This program is good at rescuing every readable bit from a damaged drive, and you need not worry that the damage will grow and make it impossible to recover the data. You should run ddrescue booted from another drive, for example an Ubuntu install CD or USB drive or some live rescue linux system.

If you are lucky, it might be possible to repair the drive. First run ```
chkdsk /r
``` then try to restore Windows to a restore point, or if you have a good backup, restore Windows from your backup. If you cannot even start a text interface (Windows or DOS), you can attach the drive to another windows computer and run chkdsk there, or use some other method that other people know better than I (also depending on what kind of Windows install/recover media you have).

---

### Post by mips on 2012-05-09
You damaged that drive when you dropped the laptop, might wanna look at getting a new one.

---

### Post by lucubrate on 2012-05-09
I had the same thing with my laptop. It started doing some strange stuff and crashing for about 6 months. I tried reformatting it, didn't work. Had to get a new drive.
Get them files out to another hard drive that hasn't been dropped. A hard drive will set you  £30 to £60 in UK.

---

### Post by zeljkojagust on 2012-05-09
Install smartmontools if not already installed and run the following command in terminal
```
sudo smartctl --test=long /dev/sdx
```where "x" is the letter assigned to your disk. You can check that by executing
```
sudo fdisk -l
```To check status and completion of test run the following:
```
sudo smartctl -a /dev/sdx
```If there will be no smart errors and the test result will be "Passed without errors" you still can safely backup up all your data and replace disk with new one. The disk should work for certain period of time. If you will get smart errors do the backup and replacement as soon as possible (yesterday!).

---

### Post by ahallubuntu on 2012-05-09
Most likely those three sectors have corrupted at least one file.  Even though Ubuntu still boots, there could be a Linux file corrupted as well just not accessed.  It may be difficult to find out which one if any.

However, it's possible the pending sectors are not in important files.

If you have an external drive, I would try imaging all of your partitions on this main drive with Clonezilla or Partimage.  (Try the Parted Magic Linux distro which has both of these included.)  If you get NO errors when copying partitions, maybe the bad sectors weren't in real files.  If you get errors, then try using ddrescue.

Then, I would do a clean erase (zero) of the whole drive with DBAN ([www.dban.org](www.dban.org)).  Then check S.M.A.R.T. again.  I have seen this completely clear all pending sector errors and make the drive completely usable again.  In fact, with one drive, it would not boot Windows at all - blue screen every time.  Simply clearing the drive and restoring allowed Windows to boot normally.  You may be so lucky.  At worst you'll have a few corrupted files and you might have to do a repair installation of Windows.

If zeroing the drive doesn't clear the pending sectors, time to get a replacement hard drive.

---

### Post by rockinruler on 2012-05-10
Thanks a lot for looking in guys, but right now I'm stuck with a new problem..

[http://ubuntuforums.org/showthread.php?p=11922589#post11922589](http://ubuntuforums.org/showthread.php?p=11922589#post11922589)

---

