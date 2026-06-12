---
title: "fc10 to Ubuntu9.04"
date: 2009-06-26
forum: Installation &amp; Upgrades
---

### Post by flytape8490 on 2009-06-26
Ok, so I have fedora10 dualbooting on my laptop with vista, with vista on the main partition.
I'm sick of fedora and want to switch to ubuntu 9.04, or maybe debian 5 (that much hasn't been decided yet).

I'm just curious as to how I'm supposed to do that. I did some research and all I found were horror stories about problems relating to GRUB and the MBR when removing fedora, but no instructions as to how to circumvent these issues. These stories also come from the fedora docs themselves (which DO provide instructions, but I can't follow them because I don't have a Vista disk that has recovery console. I only have a factory image disk from HP.)

So, could you guys help me out with the best method to switch to ubuntu/debian, or at the very least remove fedora.

Help me out ppl!

Thanks

---

### Post by kilowattradio on 2009-06-26
> **flytape8490 said:**
> Ok, so I have fedora10 dualbooting on my laptop with vista, with vista on the main partition.
I'm sick of fedora and want to switch to ubuntu 9.04, or maybe debian 5 (that much hasn't been decided yet).

I'm just curious as to how I'm supposed to do that. I did some research and all I found were horror stories about problems relating to GRUB and the MBR when removing fedora, but no instructions as to how to circumvent these issues. These stories also come from the fedora docs themselves (which DO provide instructions, but I can't follow them because I don't have a Vista disk that has recovery console. I only have a factory image disk from HP.)

So, could you guys help me out with the best method to switch to ubuntu/debian, or at the very least remove fedora.

Help me out ppl!

Thanks

 You need to remove Grub from your boot device, see: 
[http://www.vistax64.com/vista-general/160505-re-fixing-mbr-after-removing-dual-boot-home-premium.html](http://www.vistax64.com/vista-general/160505-re-fixing-mbr-after-removing-dual-boot-home-premium.html)
Then you can simply run the Ubuntu CD-ROM to install Ubuntu over Fedora. 
 If you want to preserve any directories/folders you can use the commandline program tar to make a backup and transfer it to a USB device or directly save it to the USB device or burn it to CD-R or DVD-R.
Login as root
[b]su -
passwd: *****
cd /media/DEVICENAME 
tar cvfz backup.tgz /home/USERNAME[/b]
will create a backup of the directory with all files. 
Don't create the tar file in the same directory as 
you are creating the backup from! 
:P

---

### Post by flytape8490 on 2009-06-26
So by just straight installing ubuntu over fedora without any beforehand fiddling with grub shouldn't give me any issues with the MBR?

---

### Post by kilowattradio on 2009-06-27
> **flytape8490 said:**
> So by just straight installing ubuntu over fedora without any beforehand fiddling with grub shouldn't give me any issues with the MBR?

Just run the install cd-rom, select the option to format the fedora partition(s) and the swap partition and install. Ubuntu will overwrite and install the former MBR in the HDD.

---

