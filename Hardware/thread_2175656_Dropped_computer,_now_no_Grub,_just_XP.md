---
title: "Dropped computer, now no Grub, just XP"
date: 2013-09-20
forum: Hardware
---

### Post by dyers2 on 2013-09-20
My German Shepherd uses her nose to move things around to get at what  she wants. This time, she wanted me to scratch her face. When she tried  to get at me from the side of my desk, she decided my dual boot (Ubuntu,  XP) laptop was in her way, and she nosed it off the edge of the desk to  the floor. When I picked it up, it was still running, and I was  relieved. When I rebooted, that looked good at first, too, but then it  opened to Windows boot menu. I rebooted again, but no Grub. What might  be my next coarse of action look like?

Peace,

Dave

---

### Post by oldfred on 2013-09-20
Drives are not made for that unless you have one of the Toughbooks.

Sometimes it may be chkdsk on NTFS from a Windows repairCD and fsck on ext partitions from a Linux live DVD or Flash drive. If grub in MBR cannot read partition then it gives that type of error. 

From live installer in live mode does hard drive show up. If not does BIOS show drive.

From Disks or Disk Utility does Smart Data show passed?

       #From liveCD so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

---

### Post by dyers2 on 2013-09-20
No, they aren't made for that at all.  :sad:

Thanks  for your reply. I should have told you I'm only about a month into  using any Linux distro, so I'm a little shy of experience at this  point.  I can boot into Windows, no problem. I ran Error Checking on the  Windows drive (same physical drive as Linux) with no errors found nor  repairs made.

We had a difficult time installing Ubuntu on this  old machine because it's CD-ROM wouldn't burn the disc properly, and the  BIOS don't have an option to boot from USB. With help, and advice from  this forum, we did eventually get 12.04 installed, and from there, I  upgraded to 13.10. The truth is that I just don't know enough yet to  understand your directions; I'm sorry.

---

### Post by oldfred on 2013-09-20
Can you boot your install CD? If so then go to terminal and run those commands.
If you do not know which partitions are ext4 run this first and then use any ext4 partitions in the e2fsck commands. You can copy & paste commands from here, and edit sdb1 in example to what parted command shows.

sudo parted -l

---

### Post by dyers2 on 2013-09-20
Thank you again; now I have a better idea of what you meant. 

I discovered a little while ago that my external hdd is no longer being detected.  Though it was not involved with the fall directly, the USB connection was abruptly yanked loose when the computer fell. The computer saw the enclosure as new hardware, and installed drivers for it, but only the one time.  Still, the partitions aren't displaying in my file browser. Tried another USB cable, but unfortunately it didn't help, either. Interestingly, the Windows tones play when I connect the ext. hdd to the machine, or disconnect it.

I need to regain access to that drive before anything else can be done with this, so as soon as I've implemented your suggestions, I'll be back to let you know.

---

