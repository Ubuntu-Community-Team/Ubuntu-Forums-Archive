---
title: "Boot error"
date: 2016-03-10
forum: Hardware
---

### Post by steve246 on 2016-03-10
Boot error now solved. Turns out it was faulty ssd. Been running on old hdd with no problems.

---

### Post by weatherman2 on 2016-03-10
I'm not familiar with this exact error message, but I did a quick search on it.

Can we guess that this is running on older hardware?  if not, what kind of system are you running in?  Is it a single boot or dual boot system (with Windows?).

It seems that you may be getting this message due to a BIOS issue.  Grub may be having trouble accessing the Linux partition to boot it.  One solution I've seen that makes sense is to make a separate, small /boot partition (maybe 500MB, not very big), and make sure that boot partition is FIRST on your drive.  It would be easiest to wipe and re-install this way from scratch.  It is possible to retrofit it after that fact but it's a bit of work.

You can create the separate /boot during install by choosing the "something else" option when you get to choosing the disk and partitions.  You can then create partitions you want to use manually.  You would probably create three partitions (unless you want others for something else - say Windows).  The three partitions would be:  /boot (about 500MB), swap (choose the size based on how much RAM you have; I usually choose the swap size to be the same as my RAM so I can use hibernation if need be), and then the rest of the space for the / partition.  Make sure /boot is the first partition.

If you have Windows on the same drive, it's a bit more complicated...

---

### Post by weatherman2 on 2016-03-10
Another thought: if there is a newer BIOS available for your system, consider installing it if you can do so safely.  (Sometimes harder to do without Windows.)  Just be aware that flashing a new BIOS can be risky so be careful.  Don't interrupt a BIOS flash, make sure you have reliable AC power, etc.

---

### Post by oldfred on 2016-03-10
Is BIOS set for AHCI mode for drives, not IDE nor RAID?

And best not to do hard reset unless nothing else works. But at grub error, you may have to do hard reset.
Hard resets can corrupt file system and then you have to run fsck to repair it.

       #From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1


 Never force shutdown your system. Use Alt+SysRq R-E-I-S-U-B instead. (For newer laptops they don't bother adding the SysRq print to the key, but it's the same as the PrtScr key) 
   Holding down Ctrl+Alt and SysRq (which is the Print Screen key) while slowly typing REISUB
R-E-I-S-U-B to force shutdown
A good way to remember it is.
Raising Skinny Elephants Is Utterly Boring ...or
Reboot System Even If Ultimately Broken ...LOL.
[https://en.wikipedia.org/wiki/Magic_SysRq_key](https://en.wikipedia.org/wiki/Magic_SysRq_key)
[http://kember.net/articles/reisub-the-gentle-linux-restart/](http://kember.net/articles/reisub-the-gentle-linux-restart/)

---

### Post by steve246 on 2016-03-11
Thanks for response. System is not that old...3 years maybe. Running Pentium Dual Core E5800 @ 3.2ghz x2.    2.8G ram. Not using Windows, just 14.04. When I set it up, I used the "Something Else" method and created the following: Swap 3Gb, /root 20Gb and /home using the rest (SSD drive, 128Gb total size). What I don't understand is why it boots OK at the first attempt one day and I get the error the next time and so on. I also cleared the drive before starting the install using a live USB of GParted.

---

