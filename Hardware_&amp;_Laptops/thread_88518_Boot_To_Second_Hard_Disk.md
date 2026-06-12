---
title: "Boot To Second Hard Disk"
date: 2005-11-10
forum: Hardware &amp; Laptops
---

### Post by lexor on 2005-11-10
I am about to pick up a second hard drive and install it as slave on the IDE channel. I have ubuntu on the one and only hard drive that is installed at the moment and backed up the drive image on the network server.

When I get the other hard disk it will be installed as the slave drive "D:" and the other one will be master "C:" 

On C: I will put Windows XP as I need it for work reasons, and on "D:" I will restore the image of Ubuntu from the network server.

I would like Windows to boot from C and I am sure that will not be a problem once I install it and format the hard disk.

For Ubuntu I would like to boot it from a floppy disk only and not on the Windows MBR, I know I will have some issues here.

1) Will Ubuntu run on the new D: drive without any problems when I boot from the floppy disk.

2) Will I have to edit the boot menu file in Ubuntu.

3) Will the restore image work ok on the new hard drive as its from a different maker and is a bigger size of hard disk.

4) How to I make a Ubuntu boot disk and make it to look for the boot menu on the new drive slave and not the master.

5) Is there any benifit from spending £2 on ultra ide cables 80 wires rather than useing the old 40 wire IDE cables. I am sure my mother board and hard drives support it, but in the real world do it really matter.

Thanks for the info, I searched the forums for similar topics but they dont answer all my questions on the setup I am wanting to do.

---

### Post by Koybe on 2005-11-10
> **lexor]1) Will Ubuntu run on the new D: drive without any problems when I boot from the floppy disk.[/QUOTE]
I don't know why you want to boot from a floppy?
Anyway you'll have a problem as you're new HD will be /dev/hdb instead of /dev/hda. You'll have to modify your fstab and any file referencing to this.

[QUOTE=lexor]2) Will I have to edit the boot menu file in Ubuntu.[/QUOTE]
Yes for sure. Same reason as fort point one.

[QUOTE=lexor]3) Will the restore image work ok on the new hard drive as its from a different maker and is a bigger size of hard disk.[/QUOTE]
It shouldn't change anything to the restore pocess.

[QUOTE=lexor]4) How to I make a Ubuntu boot disk and make it to look for the boot menu on the new drive slave and not the master.[/QUOTE]
Use a live cd  said:**
> 5) Is there any benifit from spending &#163;2 on ultra ide cables 80 wires rather than useing the old 40 wire IDE cables. I am sure my mother board and hard drives support it, but in the real world do it really matter.
I have no idea for this.


Is you want to boot from your windows without installing grub on the MBR. Just do this :
dd if=/dev/hda1 bs=512 count=1 of=/mnt/floppy/linux.bin
Then copy the bin file to your windows c:\ and add this line to your boot.ini
c:\linux.bin="Ubuntu"

Then you'll get to grub through the windows multiboot instead of the grub one.

Good luck

---

