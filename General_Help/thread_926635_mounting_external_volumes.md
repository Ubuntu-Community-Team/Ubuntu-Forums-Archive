---
title: "mounting external volumes"
date: 2008-09-22
forum: General Help
---

### Post by guest_user on 2008-09-22
Everytime I plug in an external volume, NTFS or FAT32, it gives me an error, I know I need to add the entries into the fstab file but the problem is that quite a number of my external storage are named /dev/sdb1, I remember there was some other way of referring to the specific device in hand, was it the UUID? anyway how do I find out the specific address of the device and refer to it in the fstab file?

Additionally, my FAT32 volume isn't even found using fdisk -l on hardy heron ubuntu, but it mounts ok on kubuntu fiesty fawn, what gives?

---

### Post by stickmangumby on 2008-09-22
What is the specific error you are getting when you plug in FAT32 and NTFS external volumes?

You can specify a UUID in /etc/fstab instead of say /dev/sda1. You can find a volume's UUID by running: 

```

sudo vol_id --uuid /dev/sda1

```

Where /dev/sda1 is the device you want to know about.

---

### Post by vanadium on 2008-09-22
> I know I need to add the entries into the fstab file
That is wrong knowledge. External drives are automounted in Ubuntu. In prehistorical times, you would announce (but not mount) them in /etc/fstab and then mount them manually after plugging in.

For removable drives to automatically have a name of your choosing, it suffices to label the volume: see [https://help.ubuntu.com/community/RenameUSBDrive](https://help.ubuntu.com/community/RenameUSBDrive)

---

### Post by guest_user on 2008-09-22
> **vanadium said:**
> That is wrong knowledge. External drives are automounted in Ubuntu. In prehistorical times, you would announce (but not mount) them in /etc/fstab and then mount them manually after plugging in.


I see, however, my FAT32 drive is still not detected by hardy heron but fiesty fawn automounts it. hardy didn't give me any visible error messages, in fact, as mentioned, sudo fdisk -l does not show it either. What should I do?

---

### Post by vanadium on 2008-09-22
Are you really sure it is not in the output of "sudo fdisk -l"? Is it a hard drive or an USB? Sure the power is connected? Did you try a different USB connection and/or a different cable? A drive not being recognized by the system suggests hardware issues. You might want to take a look at the output of "dmesg" after you connected the drive.

---

### Post by guest_user on 2008-09-22
> **vanadium said:**
> Are you really sure it is not in the output of "sudo fdisk -l"? Is it a hard drive or an USB? Sure the power is connected? Did you try a different USB connection and/or a different cable? A drive not being recognized by the system suggests hardware issues. You might want to take a look at the output of "dmesg" after you connected the drive.

Its not in the output of fdisk -l, tried 2 different USB ports, same result, for power, its a portable USB HDD so it draws power from the usb connection. I'll take a look at the results of dmesg later. If it's hardware issue, why is it that it is recognized and mounted automatically by fiesty fawn? :(

---

