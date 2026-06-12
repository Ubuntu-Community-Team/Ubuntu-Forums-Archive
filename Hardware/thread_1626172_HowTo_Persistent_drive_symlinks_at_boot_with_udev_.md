---
title: "HowTo: Persistent drive symlinks at boot with udev rules"
date: 2010-11-20
forum: Hardware
---

### Post by deconstrained on 2010-11-20
During boot, for varied reasons, sometimes the device files /etc/sd* or /etc/hd* will not always refer to the same physical drives. To unambiguously specify exactly which partition to mount at each mountpoint, it would suffice to use "UUID=[uuid]" in place of "/dev/sd[a-z]" as the device in /etc/fstab, and "/dev/disk/by-uuid/[uuid]" in crypttab, and then to rebuild the ramdisk. Another nice way is to make persistence rules that get passed to udev in the initial ramdisk at boot time and create reliable symlinks for each device that one can then use in place of /dev/sd*. As references I used the following pages:

[b][http://reactivated.net/writing_udev_rules.html](http://reactivated.net/writing_udev_rules.html)
[https://help.ubuntu.com/community/EncryptedFilesystemLVMHowto](https://help.ubuntu.com/community/EncryptedFilesystemLVMHowto)
[https://help.ubuntu.com/community/GutsyLUKSTwoFormFactor](https://help.ubuntu.com/community/GutsyLUKSTwoFormFactor)
[http://www.linuxfromscratch.org/lfs/view/6.3/chapter07/symlinks.html](http://www.linuxfromscratch.org/lfs/view/6.3/chapter07/symlinks.html)[/b]

In this example, there are three drives: an OCZ Agility-2 SSD with the root & swap inside an LVM2 group inside an encrypted one of its partitions, a 500 GB Western Digital, and a 1 TB Western Digital, which will be mapped to /dev/sda, /dev/sdb, and /dev/sdc, respectively. It will be assumed in this example that, because of the drive mapping problem, you are locked out of your system (with the error "cryptsetup: evms_activate is not available") and booted to a live disk.

[size=3]1. Mount the root filesystem & chroot;[/size]
Perform the following to open the root filesystem device (assuming the encrypted partition is /dev/sdb2, the boot partition is /dev/sdb1, the lvm2 volume group's name is 'crypt', and the logical volume on which the root filesystem is stored is named 'root'):
```
$ sudo -i
# for m in aes-generic dm-mod dm-crypt; do modprobe $m; done
# apt-get update; apt-get install -y lvm2 cryptsetup
# cryptsetup luksOpen /dev/sdb2 cryptlinux
# lvm vgimport crypt
# lvm lvchange -a y crypt
# fsck /dev/mapper/crypt-root
# mount /dev/mapper/crypt-root /mnt
# mount /dev/sdb1 /mnt/boot
```
Next, chroot;
```
# mount -o bind /dev /mnt/dev
# mount -t proc proc /mnt/proc
# mount -t sysfs sys /mnt/sys
# mount -t devpts devpts /mnt/dev/pts
# chroot /mnt
```

[size=3]2. Find device attributes unique to each drive and one of its parents[/size]
In order for the udev to properly match each device and apply the correct rule, you will need to find device properties that differ between the drives. Assuming you know which drive is which among /dev/sd*, once booted to the live disk (even if they settled incorrectly), use the following command for each drive to see its attributes (for example, in the case of /dev/sdb):
```
udevadm info -a -n /dev/sdb | less
```
If the drives are all different models, like in this example, you can easily use the 'model' attribute; the following appears in the output:
```
ATTRS{model}=="OCZ-AGILITY2    "
```
Note however that you should only be grabbing "KEY==VALUE" pairs from two devices: the block device and one of its parent devices (see ["Device hierarchy"](http://reactivated.net/writing_udev_rules.html#hierarchy)).

[size=3]3. Create the .rules file[/size]
Using your favorite command-line text editor, open/create a file in  '/etc/udev/rules.d/' named either '60-persistent-storage-dm.rules' or '55-dm.rules' (the reason will be explained later, and '60-persistent-storage-dm.rules' will be used in this example), to contain the udev rules. Rules are individual lines consisting of key/value pairs, separated by commas, that are either matches or assignments; 'KEY=="value"' is a match and 'KEY="value"' is an assignment (see [Rule Writing](http://reactivated.net/writing_udev_rules.html#syntax) for more details). To reiterate: you must, in order to avoid ambiguity, write match entries ONLY for the the device and ONE of its parent devices, as shown by the output of 'udevadm info'. Thus, to map the SSD correctly to /dev/sda using the model attribute to identify it, the rule could be:
```
SUBSYSTEM=="block", SUBSYSTEMS=="scsi", ATTRS{model}=="OCZ-AGILITY2    ", SYMLINK+="rootdisk%n"
```
This rule will create symlinks for /dev/sda (or wherever the SSD maps to) in /dev for the device and all of its partitions; they will be /dev/rootdisk, /dev/rootdisk1, etc.

Rules for the other two drives can be similarly added to the file, on separate lines;
```
SUBSYSTEM=="block", SUBSYSTEMS=="scsi", ATTRS{model}=="WDC WD5000AAKS-2", SYMLINK+="homedisk%n"
SUBSYSTEM=="block", SUBSYSTEMS=="scsi", ATTRS{model}=="WDC WD10EADS-00M", SYMLINK+="backup1disk%n"
```

[size=3]4. Test the udev rules[/size]
In a different, non-chrooted terminal, perform the following actions to test that the rules work properly:
```
# cp /mnt/etc/udev/rules.d/60-persistent-storage-dm.rules /etc/udev/rules.d/
# udevadm trigger
```
This should create the necessary symlinks in /dev.

[size=3]5. Modify configuration to reflect the changes[/size]
To take advantage of the changes, you must change device paths in /etc/fstab, /etc/crypttab (etc) to the new symlinks. 

[size=3]6. Rebuild the initial ramdisk[/size]
To ensure that these rules are applied on the next boot-up, [rebuild accordingly;](https://help.ubuntu.com/community/EncryptedFilesystemLVMHowto#Rebuild%20ramdisk)
```
# update-initramfs -k all -c
```
Next, double-check that the ramdisk is ready for booting;
```
# cd /tmp/ 
# mkdir ramdisk; cd ramdisk
# zcat /boot/initrd.img-$(uname -r)|cpio -iv
# cat conf/conf.d/cryptroot
# cat lib/udev/rules.d/60-persistent-storage-dm.rules
```
If 60-persistent-storage-dm.rules is not present, double-check the filename of the rules file and the contents of /etc/fstab and /etc/crypttab, and check that cryptsetup/lvm2 are installed. 

FYI: what will happen during the rebuilding of the initial ramdisk is that certain scripts in /usr/share/initramfs-tools/hooks/ will be automatically run based on the kind of system the kernel needs to expect when initializing, and some of these perform copying of udev rules. In the 'dmsetup' file, the relevant operation that performs the rule-copying is as follows:
```
for rules in 55-dm.rules 60-persistent-storage-dm.rules; do
        if   [ -e /etc/udev/rules.d/$rules ]; then
                cp -p /etc/udev/rules.d/$rules $DESTDIR/lib/udev/rules.d/
        elif [ -e /lib/udev/rules.d/$rules ]; then
                cp -p /lib/udev/rules.d/$rules $DESTDIR/lib/udev/rules.d/
        fi
done
```
Hence, one will need to use a filename that gets included based on the hooks that will be run during update-initramfs, and copy the contents of the original file (in /lib/udev/rules.d/) to the new one. To see which of the hooks are run for any given system, pass update-initramfs the '-v' flag; 
```
# update-initramfs -k all -c -v | grep hook
```

Good luck!

---

