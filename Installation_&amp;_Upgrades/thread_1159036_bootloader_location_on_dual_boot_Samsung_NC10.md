---
title: "bootloader location on dual boot Samsung NC10"
date: 2009-05-14
forum: Installation &amp; Upgrades
---

### Post by roy20 on 2009-05-14
Hi All,
Please would someone advise me where is the best place for the boot loader for Ubuntu Linux to be located on a Samsung NC 10. I want to retain Windows XP on the first usable primary partition, bearing in mind that the first partition on the hard disk is reserved for Samsung's recovery routine but is invisible during regular use. I have set up an extended partition by shrinking the size of the second visible partition in Windows (the second visible partition is of course a natural fact the third primary) by making an extended partition in the fourth primary partition. This I have divided up into the Linux formatted EXT 2 and the smaller Linux Swap partition. So far so good.

Meanwhile I have readied the latest Linux distribution on a USB memory device so they can be installed from their when the BIOS has been adjusted to look for a USB boot device for first-time installation of Linux.

However before I begin installation I would like to know where to direct the Ubuntu boot loader to be installed -- am I correct in believing it is the root of the first visible partition in Windows i.e. the second primary partition on the hard disk? -- Am I correct in assuming this is HDA1 ? I cannot see that the boot loader could be installed on the emergency recover first hidden partition as I assume it would mark at the Samsung's recovery routine if it were to be used.

Thanks in anticipation, Roy

---

### Post by 3startuna on 2009-05-14
Dont do this until others chime in but

I would put the boot loader (grub) on the partition that linux is on. It will automatically detect the windows kernel and the recovery partition and add them as boot options. 

During the actual Ubuntu install process Grub should install itself on the correct partition automatically.

Second tip Grub sometimes doesnt name the partitions the same way that Linux does. 

For example it may call the third partition hd (0,2) where as linux will call it dev/sda3.

Just a heads up.

Thanks

---

### Post by roy20 on 2009-05-14
Thanks for the quick reply.

If the Grub bootloader gets put on my Linux partition (that will be on the first secondary partition, within the extended partition -- ie. within the extended partition located in the fourth primary) would be Master Boot Record be able to direct boot to the Linux boot loader? If I recall correctly I think I've always put it on the first primary partition in the past although in this case, for obvious reasons, this is not a possibility.

Thanks again, Roy

---

### Post by 3startuna on 2009-05-14
Thats why I said to wait until you got other responses, because i am not 100% sure.

It should still work and bring up grub. That how I had it setup on my computer if I remember correctly.

Worse case scenario it doesnt and you reboot it will start up Xp. Grub doesnt damage your computer far as I know.

All you have to do then is restart the computer under live CD run Grub from the terminal screen reinstall it on another partition.

wait for better responses though 

Thanks

---

### Post by roy20 on 2009-05-14
Thanks again !

---

