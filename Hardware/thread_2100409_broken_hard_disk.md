---
title: "broken hard disk?"
date: 2013-01-01
forum: Hardware
---

### Post by mzrk7 on 2013-01-01
I've got an external hard disk, and I am having some trouble in rescuing its data. When I connect it to my pc, I can't access it through file manager, nor through gparted or testdisk. How can I tell if it's actually broken and there's nothing else to do? Do you have any suggestions, trying to "save" it?

---

### Post by ajgreeny on 2013-01-01
Show the output of ```
sudo fdisk -lu
``` with it attached.

---

### Post by mzrk7 on 2013-01-01
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x2b648ae0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   625138766   312568359+  83  Linux


(that's my internal hard disk)

---

### Post by ahallubuntu on 2013-01-01
Does it do anything when you plug it in?  Make noise? Lights come on?  If not, check the cabling and the connectors.  A bad USB cable would not be impossible.

If you still get no sound or lights, you could crack open the case and try attaching it to another computer or another USB enclosure in hopes that your problem isn't with the drive itself and is just with the enclosure.

If it's out of warranty you might crack it open anyway at this point if getting the data off is your primary goal.  Hard drives do die.

---

### Post by mzrk7 on 2013-01-01
I already tried to change the usb cable, but nothing changed. The drive front light, lights up (that's what makes me hope in something), and, as soon as I connect it, it makes a strange high tune sound that lasts 3 seconds. Then it suddendly stops, and the drive gets silent.
:s I know that they die... Just praying my own hasn't...

---

### Post by irv on 2013-01-01
First, I hope you had your data backed up. Yes, HD go bad. If you can't read it with gparted there is a good change it is bad. Try other USB ports and if you have a different USB cable try that. And if you have another computer to try it on do that also.
Even if it doesn't mount gparted should see it. Don't forget you need to switch between your internal HD to your external HD in gparted. I thought I would mention that in case you missed that.

---

### Post by ahallubuntu on 2013-01-01
See if it shows up in the list when you do "lsusb" as well.  If not, and you've tried it on another computer and the same thing happens, probably time to try cracking open the case and attaching it with another enclosure or directly to a desktop computer.

If you get the drive to show up anywhere, check its S.M.A.R.T. status.  Sometimes that can at least tell you if there's been a catastrophic failure or something.  If you have thousands of failed sectors or something, at least you know it's probably not worth wasting a lot of time on it at that point.

There are tools that will try to recover files by constantly trying to re-read the same sectors - perhaps over several days - if you are desperate to try to recover files from it without paying a lot of money for data recovery.  But you have to get the drive to show up at all first when attached to a computer.

---

### Post by mzrk7 on 2013-01-03
lsusb gave nothing. I opened it. It turned out that I couldn't connect it because it didn't have any port. No sata or ide. Just the usb. :cry: Do you think there are ways of connecting it before sending it to the cemetery? :-({|=

---

### Post by irv on 2013-01-03
I think you are trying to hang on to something that died. Maybe it is time to bury it.

---

### Post by ahallubuntu on 2013-01-03
> **mzrk7 said:**
> lsusb gave nothing. I opened it. It turned out that I couldn't connect it because it didn't have any port. No sata or ide. Just the usb. :cry: Do you think there are ways of connecting it before sending it to the cemetery? :-({|=

Inside the drive is almost certainly SATA or IDE.  Are you sure there isn't an adapter on top of the drive connector?  Can you read a drive label on the internal drive?  A part number?

---

### Post by mzrk7 on 2013-01-05
it is a samsung HN-M101XBB . I may be wrong, but there doesn't seem to be any sata or ide.

---

