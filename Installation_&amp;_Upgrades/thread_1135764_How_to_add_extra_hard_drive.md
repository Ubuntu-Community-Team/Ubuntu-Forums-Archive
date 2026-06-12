---
title: "How to add extra hard drive ?"
date: 2009-04-24
forum: Installation &amp; Upgrades
---

### Post by Julian David Pitt on 2009-04-24
I am looking to add an extra hard drive to a system but when I try to boot it up I find the drive designations have changed and the system won't boot. Is there a way I can prevent this from happening, ie hda not becoming hdb when the second drive is added. Thanks a lot.

---

### Post by Therion on 2009-04-24
Do you check your BIOS settings after installing the slave-drive?

I know that when I'm playing with drives or adding a new slave, I usually have to reset the boot-order to keep things from borking.  The fact that you can't boot when adding the slave drive tells me your system is trying to boot from it instead of the primary drive (with the OS installed on it).  

Install the slave drive, reboot, check your BIOS settings and see if you don't need to change the boot-order back to the proper drive.

---

### Post by drs305 on 2009-04-24
Once you have the order set in BIOS, you can make sure a device gets mounted the same each time by giving it a label or mounting it in fstab with a UUID. Designating it in fstab via label or UUID is more consistent than using "/dev/sdXX".

Labels:
For ext3:
```
sudo tune2fs -L *labelname* /dev/sdXX

```
Example: sudo tune2fs -L mydata /dev/sda2

For NTFS:
```

ntfslabel /dev/sdXX mydata  # install *ntfsprogs* to have this capability

```

In fstab, you would replace the start of the line "/dev/sdXX" with "LABEL="
So an entry for ext3 might look like this:
> 
LABEL=mydata /media/mydata ext3 defaults 0 2


---

### Post by Julian David Pitt on 2009-04-27
> Do you check your BIOS settings after installing the slave-drive?

It seems to install ok as I get a BIOS message saying the configuration has changed and now showing two drives with the original as the master and teh new as the slave. Ubuntu then tries to boot and I see the splash screen before it drops to a console and I get the alert "/dev/disk/by-uuid does not exist". I have the bios set to boot from the hard drive first, but am not able to differentiate between the two drives. If I select the options at the grub loading screen it shows (hd0,4), with or without the second drive fitted. The label idea for the hard drive sounds good but can I do that if I cannot boot into the OS. Your help is much appreciated.

---

### Post by Julian David Pitt on 2009-04-29
```
sudo tune2fs -L labelname /dev/sdXX
```
If I run the command above to label my first hard drive, and then boot from it, will that prevent grub from not finding the boot partition when I add the second drive back to the system. If that would work ok it would solve the issue I am having. Thanks in advance.

---

