---
title: "Edited FSTAB, can't boot now, file system is read only"
date: 2009-08-18
forum: Installation &amp; Upgrades
---

### Post by Fox5 on 2009-08-18
So I edited my /etc/fstab file to change some of the mount options, but now when I boot I get:
EXT4-fs: cannot change data mode on remount

One of the data options I changed was from ordered to writeback, but I can't seem to unmount the read-only filesystem, or remount it as writable.  I don't have a cd drive on this laptop, so it would be difficult to get access to a live cd, how can I remount the filesystem and fix this?

---

### Post by afroman10496 on 2009-08-18
OK... you use ext4, right

---

### Post by afroman10496 on 2009-08-18
How can you boot to recovery mode?

---

### Post by Fox5 on 2009-08-18
Well, it starts to boot, and even the ubuntu load screen comes up and the bar fully loads, but then it errors out and drops me to a terminal. Alternatively, I can choose the recovery option prior to booting and boot into that, but the file system is still mounted as read only.

I am unable to unmount or remount the filesystem due to the error, and I'm hoping there's some command to force it to remount anyway. Or perhaps manually specifying all mount options so it skips what's in fstab?

---

### Post by afroman10496 on 2009-08-18
sorry it took so long i was thinking... how about 
```
*[I]*[/I]sudo chmod /
```

---

### Post by afroman10496 on 2009-08-18
how about, this is only a guess: 
```
sudo apt-get install lilo
sudo apt-get remove grub
```
*or*
```
sudo apt-get install grub2
```

---

### Post by miegiel on 2009-08-18
> **Fox5 said:**
> ...
I don't have a cd drive on this laptop, so it would be difficult to get access to a live cd, how can I remount the filesystem and fix this?

Assuming you have a 2nd running machine with ubuntu, you can make a live USB (instead of a live CD) with *System > Administration > USB Startup Disk Creator* and the ubuntu iso. If it's not installed you can install it with.
```
sudo apt-get install usb-creator
```

---

### Post by Fox5 on 2009-08-18
sudo chmod / gives
chmod: missing operadand after '/'

And I can't install or remove any packages because the file system is mounted read only.

---

### Post by afroman10496 on 2009-08-18
```
sudo chmod +x /
``` will make it executable... try chmod +r  or +w or +a through z /

---

### Post by miegiel on 2009-08-18
Have you tried mounting it twice, I maen monting it automatically as you boot and then manually in /media or so?

What I would do (but I've got to much old spare hardware) is pull out the disk and stick it in another *nix box, edit /etc/fstab there and stick the disk back.

---

### Post by xyepblra on 2009-10-21
Finally I found the thread my help request it would be proper to post to.
I followed the instructions from maketecheasier.com/how-to-upgrade-from-ext3-to-ext4-without-formatting-the-hard-disk/2009/04/21#more-4157 and I manually moified /etc/fstab by replacing ext3 with ext4 for the boot volume. Now I am being prompted with read only file system error on boot. Need help badly.

---

### Post by stlsaint on 2009-10-21
i replied to your thread:
[http://ubuntuforums.org/showthread.php?t=1297054](http://ubuntuforums.org/showthread.php?t=1297054)

---

### Post by xyepblra on 2009-10-22
Thank you, stlsaint, I'm fine by now, because e2fsck has fixed my /.

---

### Post by humidity on 2010-02-10
Hi Fox5, did you manage to get a solution to the problem for this tread? I am inthe same dilemma.

---

### Post by humidity on 2010-02-10
Hi there, I found out a solution to the Read Only issue. The trick is to edit into the kernel, change RO to RW, Ctrl-X to reboot and then gedit fstab. After that, reboot and the grub kernel revert back to RO. All fixed! :p

---

### Post by WylieE on 2010-04-12
> **humidity said:**
> Hi there, I found out a solution to the Read Only issue. The trick is to edit into the kernel, change RO to RW, Ctrl-X to reboot and then gedit fstab. After that, reboot and the grub kernel revert back to RO. All fixed! :p

Can you explain this in a little more detail, I am having a similar problem (mine is specifically with RAID 0 I believe) and have been unable to apply the suggestions in other threads because of the Read Only problem.
Thanks,
Colleen

---

### Post by miegiel on 2010-04-12
> **WylieE said:**
> Can you explain this in a little more detail, I am having a similar problem (mine is specifically with RAID 0 I believe) and have been unable to apply the suggestions in other threads because of the Read Only problem.
Thanks,
Colleen

He means [this way to change the kernel parameters when booting]("https://help.ubuntu.com/community/Grub2#Editing Menus During Boot").

I'm not sure if it will solve your problem though, good luck.

---

### Post by WylieE on 2010-04-14
Thanks, Miegiel.
I ended up reinstalling 9.04.

---

### Post by blur xc on 2010-04-14
I think the less to learn here is - don't edit existing lines in your fstab.  Copy/paste the line you want to change, comment out the original untouched line, make edits to your new line.  If you blow it, boot up a live cd and put it back.

BM

---

### Post by jdowdell on 2012-07-06
I had the same issue adding datamode=writeback in fstab, not realizing / is mounted earlier and the system complains that it can't change the datamode on remount.

Solution is, during boot, when grub comes up, edit the boot options.  Where it says "quiet splash", add in "rootflags=data=writeback", and then you'll boot fine.

---

### Post by howefield on 2012-07-07
Old thread closed.

---

