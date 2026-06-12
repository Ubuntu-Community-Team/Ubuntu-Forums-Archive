---
title: "Missing space after increasing ext3 over NTFS using gparted"
date: 2008-11-02
forum: General Help
---

### Post by HappyUser123 on 2008-11-02
For a while I dual-booted XP/Ubuntu 8.04 with my partitions as so:

/super small fat16
/~40GB NTFS (~20GB used)
/~40GB ext3 (~20GB used)
/~2GB linux swap

I decided that I wanted Ubuntu to control everything. I put in the 8.04 LiveCD and started gparted. I told it to delete the NTFS partition and increase ext3 over the space. After I "applied" the change, it deleted the NTFS partition, apparently resized the ext3 partition, "copied files left".

Unfortunately it didn't fully complete, I think it failed some kind of check. However gparted showed my system as

/super small fat16
/~80GB ext3
/~2GB linux swap

I tried to do a "Check" on the filesystem. It shows:

Calibrate <linux /dev>
Check & Fix
     e2fsck -f -y -v <linux /dev>
Grow filesystem
     resize2fs
           error: run e2fsck -f <linux /dev> first

Weird. Anyway, hoping for the best, I rebooted to the HDD into Ubuntu. Surprisingly I am able to get into Ubuntu and every appears to work. Except...I'm getting weird conflicts about how much space I have. For example df -h says my filesystem is ~40GB with about ~20GB used. On the other hand Disk Usage Analyzer shows about ~70GB in the system with about ~42GB used. 

Anyway I'm stumped. How can I recover the missing space? Should I be worried about something being subtly corrupt in my existing system? I feel certain the problem is just with a configuration issue somewhere and not the data itself, as I said I am able to boot into Ubuntu and everything looks fine. I would really, really prefer not to have to format and reinstall, but if I can't fix it may have to. 

Any ideas welcome, thanks!

---

### Post by Herman on 2008-11-02
:) So it's telling you to run e2fsck -f <linux /dev> first right after you did just finish running e2fsck -f -y -v eh?

First of course you already have your files backed up right?

I would simply try repeating the 'check' once or twice again from Gnome Partition Editor in the Live CD or GParted.

Or maybe try running e2fsck again but from the terminal in the Live CD so you can use slightly different options to see if that will help. 

I usually try running e2fsck with the -p option before I resort to using -y.
The '-p' is short for 'preen', and is much gentler than '-y' means 'yes', (I agree to unlink files to the Lost+found if necessary, without any further consultation). 
```
sudo e2fsck -C0 -p -f -v /dev/sda2 <linux /dev>
```I don't know for sure if running e2fsck with -p will really do anything more than the command built into Gnome Partition Editor, and it may do less.  I'm just hoping it'll do something different. This was the command GParted used for the e2fsck 'check' originally.

Regards, Herman :)

---

### Post by HappyUser123 on 2008-11-02
Thank you for responding Herman. 

I decided to just wipe everything and start again. I figured that, wiping it or no, I probably had a few hours of messing around with the system ahead of me. At least by wiping I could be reasonably sure that the problem would be fixed after those few hours :)

---

