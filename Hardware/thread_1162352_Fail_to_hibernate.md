---
title: "Fail to hibernate"
date: 2009-05-17
forum: Hardware
---

### Post by MeisterLampe1 on 2009-05-17
My computer fails to hibernate. When I try, the screen just goes blank and that's it. Alt+Print+(R-E-I-S-U-B) restarts. I assume it has got something to do with my swap file. I installed Ubuntu without swap and configured a swap file per hand. It's a 4.1GB file (got 4GB RAM). The system uses it, I'm pretty sure about that. Now I tried the method described [here]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/340804"). That's when I found out that the /etc/initramfs-tools/conf.d/resume file is missing. I tried to reinstall the file with 
```
apt-get install --reinstall initramfs-tools
```
described [here]("https://lists.ubuntu.com/archives/ubuntu-users/2006-October/097823.html") but it didn't create the file. Now my question is: is this file in jaunty still in use, is it important to my problem or am I running in a completely wrong direction?

---

### Post by 67GTA on 2009-05-17
Yes, it is still used in Jaunty. The resume file contains the UUID of your swap partition. You could probably create it. Then add the UUID of your swap partition per ```
sudo blkid 
``` from a terminal. It would be similar to this, but with your swap UUID number:

```
RESUME=UUID=caa58837-13e0-4bca-b6c0-a64938d14dd0

```

Then run ```
sudo update-initramfs -u -k kernel-version
``` Replace "kernel-version" with yours. You can see it by running ```
uname-r
``` in a terminal.

---

### Post by MeisterLampe1 on 2009-05-17
```
sudo blkid
```

shows
```
/dev/sda1: UUID="B2AC022AAC01E9A5" LABEL="System Reserved" TYPE="ntfs" 
/dev/sda2: UUID="2EC013DAC013A75D" TYPE="ntfs" 
/dev/sda5: UUID="91458b3b-882f-4f14-b120-6fcabfed4c8c" TYPE="ext3" 

```

I guess it's because I have a swap file and not a partition. I just checked [this]("http://ubuntuforums.org/showthread.php?t=477091") thread, but ```
free | grep Swap
``` gives ```
Swap:      4198392          0    4198392
``` so I assume the swap works... I'm going to try to add just the filename where the UUID goes...

---

### Post by 67GTA on 2009-05-17
I didn't catch the "file" part in your first post. It won't work. You have to have a swap partition. That is why your resume file was missing.

---

### Post by MeisterLampe1 on 2009-05-17
made /etc/initramfs-tools/conf.d/resume with the content:

```
RESUME=/mnt/4gb.swap
```
then
```
sudo update-initramfs -u -k 2.6.28-12-generic
```, rebooted, went to hibernate --> same situation.. I wonder if hibernate works with a swapfile at all...
BUT:
I just read [this]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/252143") but report and found out, that my /boot/grub/menu.lst is missing this resume option. Where the guy from the bug report has got
```
title		Ubuntu 8.04.1, kernel 2.6.24-19-rt
root		(hd0,1)
kernel		/vmlinuz-2.6.24-19-rt root=/dev/mapper/tigris-root_crypt ro quiet splash resume=/dev/mapper/tigris-root_crypt resume_offset=126976
initrd		/initrd.img-2.6.24-19-rt
quiet

```

I've got:
```
title		Ubuntu 9.04, kernel 2.6.28-12-generic
uuid		91458b3b-882f-4f14-b120-6fcabfed4c8c
kernel		/boot/vmlinuz-2.6.28-12-generic root=UUID=91458b3b-882f-4f14-b120-6fcabfed4c8c ro quiet splash 
initrd		/boot/initrd.img-2.6.28-12-generic
```

You people think this might be the issue and if yes: what am I supposed to add?

---

### Post by MeisterLampe1 on 2009-05-17
> **67GTA said:**
> I didn't catch the "file" part in your first post. It won't work. You have to have a swap partition. That is why your resume file was missing.

Ok well, this settles it... Guess I have to repartition my system. Thanks for your help anyway.

---

### Post by 67GTA on 2009-05-17
Be sure to make your swap partition at least the same size as the amount of RAM you have. You still might have to maually set it up afterwards. You might also have to add the swap partition to /etc/fstab. I'm not sure if it will pick it up automatically afterwards. Post back if you have trouble.

---

### Post by MeisterLampe1 on 2009-05-18
For everyone who needs to do the same as me: I booted from the jaunty live-CD resized the linux ext3 partition and made a swap partition (via gksu gparted). Reboot -->
```
 swapoff /mnt/4gb.swap
swapon /dev/sda6
gksu gedit /etc/fstab
```
where I added the line:
```
/dev/sda6       none            swap    sw              0       0
```
then edited /boot/grub/menu.lst and added resume=... :

```
kernel		/boot/vmlinuz-2.6.28-12-generic root=UUID=91458b3b-882f-4f14-b120-6fcabfed4c8c resume=/dev/sda6 ro  single
```

finally edited /etc/initramfs-tools/conf.d/resume
which now has the content:
```
RESUME=UUID=71773c33-8da2-42ba-adfd-e530b705895c
```

rebooted (don't know if this is necessary) and it works like a charm. I now have Ubuntu and Windows 7 both in hibernation and can switch between the systems within seconds (depends mostly on the bios). I know it's not the place to say this but Windows 7 is actually pretty decent :)

---

