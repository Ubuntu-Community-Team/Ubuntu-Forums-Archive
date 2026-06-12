---
title: "Cannot use CD/DVD drive"
date: 2010-12-29
forum: Hardware
---

### Post by kiniyaloca1 on 2010-12-29
I am not able to mount my cd drive. I cant find it in my "places" tab under computer either. Im running maverick 64 bit and thats it. No other operating systems. Here's my fstab:

```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=8c316e20-5702-45dd-ba5a-1e4110f2dfec /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=eafabcc9-490a-4745-b7c7-3e82356555da none            swap    sw              0       0
```

---

### Post by kiniyaloca1 on 2010-12-29
Anyone...

---

### Post by pi/roman on 2010-12-30
You could try the disk mounter applet. Right click the menu bar, select "add to panel", scroll down to the disk mounter utility. Insert a disk and it should show up in the disk mounter applet. If that doesn't work check to see if your computer can see your cd drive with ```
wodim -devices
```

---

### Post by kiniyaloca1 on 2010-12-31
The disk mounter applet did not work. :/
Here's the ouput from the code you told me to try:

```
wodim: No such file or directory. 
Cannot open SCSI driver!
For possible targets try 'wodim --devices' or 'wodim -scanbus'.
For possible transport specifiers try 'wodim dev=help'.
For IDE/ATAPI devices configuration, see the file README.ATAPI.setup from
the wodim documentation.

```

---

### Post by pi/roman on 2011-01-02
Check in your bios settiings and see if your drive is detected there.

---

### Post by IWantFroyo on 2011-01-02
Check the drive. Make sure the little plastic tab is at the slave side of the master/slave switch.

---

### Post by kiniyaloca1 on 2011-01-02
Yeah i checked all of that and its ok. Randomly Ubuntu will mount the drive, but its nothing consistent and there is no pattern as to why its mounting.

---

