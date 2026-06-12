---
title: "Mounting an LVM file system"
date: 2008-10-04
forum: General Help
---

### Post by awd-s on 2008-10-04
This might be helpful to anyone who wants to recover data from a hard disk drive extracted from a failed computer.

My primary computer developed a hardware failure that wasn't worth repairing. I extracted the hard disk, set it aside, and discarded the failed hardware. I bought a replacement computer. To recover the data on the old hard drive, I bought a Manhattan high speed USB 2.0 SATA/IDE adapter with power supply, using it to connect the old hard drive to the USB port of the new computer.

The old hard drive mounted, but only the boot partition. The data partition was marked as "LVM" and unrecognizable by the mount command. This is what I did to mount the LVM and extract my data with the help of this thread:

[http://ubuntuforums.org/showthread.php?t=428292]("http://ubuntuforums.org/showthread.php?t=428292")

and by executing these commands from the command line:

```
sudo apt-get install lvm2
```
Installs the Logical Volume Manager utilities.

```
sudo lvdisplay
```
Displays the logical volumes by logical volume name. In my case, I was interested in the logical volume named: /dev/Ubuntu/root

```
sudo modprobe dm-mod
```
Load the modules.

```
sudo vgchange -ay
```
Activate all volume groups visible to the system.

```
sudo mount /dev/Ubuntu/root /home/awds/Pavilion-HD
```
Mounts the logical volume named "/dev/Ubuntu/root" to the mount-point "/home/awds/Pavilion-HD"

At this point, I was able to copy the data on my old external hard drive via the USB port to a new location on the hard drive internal to my new computer.

Having copied the data, I unmounted the external drive using this command:

```
sudo umount /dev/Ubuntu/root
```

Lastly, I changed ownership of the recovered data from root to my username using this command:

```
sudo chown -R awds:awds /home/awds/NewLocation/
```

where "awds" is my user and group name and the pathname is the new location of my just recovered data.

I hope this helps. Good luck!

---

