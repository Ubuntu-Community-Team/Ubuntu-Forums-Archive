---
title: "Don't automount Samsung device"
date: 2014-04-04
forum: Hardware
---

### Post by Azyx on 2014-04-04
Hi. I have a Samsung Galaxy Tab 3 7.0 and as I understand it; Kies does not work well in Wine, so I have activade a vbox VM machine with Windos7 and installed Kies there. My host-os is Ubuntu 12.04 LTS. I have manage to sometimes let the vbox machine mount the Samsung device, but every time Ubuntu try to mount with bad results (Mouted in Nautilus, but it say it could not mount) so every time I need to unmount the device... I have found how I can turn of automount i Nautilus, but I only what it for the Samsung Galaxy Tab device there I have filtered it to be the only USB-device to mount i Vbox.

Is it possible to not automount 1 specific device in Nautilus.

---

### Post by Kris_Spencer on 2014-04-05
Hello. The best way I can think to do that is to add the device to your fstab. That's a file that is in charge of mounting devices. You will need to first determine the UUID of the tablet. So, plug it in and let it mount. Keep it mounted and run this command:
  
```

sudo blkid

```

This will list all your partitions system wide. So open 'disks' or it may be 'disk manager' in 12.04, and look for the device identifier for you tablet. Find you tablet and note if it's, /dev/sdb1 or /dev/sdc1. Whatever it is. Look back to the terminal output and find that device identifier. In the same like of output, it'll have the UUID. Let's say that it was /dev/sdc1:

```

			 				/dev/sda1: LABEL="Ubuntu0" UUID="5e2f35bf-4894-4586-ad64-8da2ca9c61bd" TYPE="ext4" 
/dev/sda5: UUID="4bde0f88-f4a2-4405-b895-d16c06e01764" TYPE="swap" 
/dev/sdb1: LABEL="VideoHD" UUID="1d278a93-d076-4f66-9d75-d559b9398df5" SEC_TYPE="ext2" TYPE="ext3" 
***/dev/sdc1***: LABEL="Tablet" _***UUID=***"***641b027f-a8c8-4153-a70f-9f5e77490e2e***_" TYPE="ext4" 			 		

```
  	 	 	 	   
I know, this is a long explanation. Almost done, I promise. Copy, or write down the UUID=blah part, without the quotes. Also note the TYPE above. This is the filesystem. I am assuming that the tablet is formated in fat32. Now do this:

  
```

sudo cp /etc/fstab /etc/fstab.bkp
sudo nano /etc/fstab

```

At the bottom, add this line:

UUID=the number        /mnt                  vfat     noauto,nofail,defaults            0 0

Replace the vfat part with whatever filesystem it is, unless it is fat32. vfat is for fat32. The option noauto will keep it from mounting. The option nofail will keep the system from requiring that the tablet is plugged in on boot. 

I hope that this isn't too confusing and it helps out.

---

### Post by Azyx on 2014-04-05
Thanx for the tip :)
But the SAMSUNG_Android devices (2 partitions, memory card and internal memory) does not appear, more than in Launcher and in the side panel in Nautilus (As mounted). A strange thing is that all folders are empty. The partitions does not be shown in Disk-utilities or blkid. The device is shown in lsusb as:
```
Bus 002 Device 021: ID 04e8:6860 Samsung Electronics Co., Ltd GT-I9100 Phone [Galaxy S II]
```

As a Galaxy S II device, not Galaxy Tab 3 7.0/SM-T210

/Cheers

---

### Post by Kris_Spencer on 2014-04-06
I see. I tried this with my phone just now and I got the same result. I didn't realize that the Galaxy devices would behave in such a way. I guess that solution won't work then...

---

### Post by Azyx on 2014-04-06
Probably an Applefication thing :( No, you need ther f*cking Keis application to transfer files. The same thing happend in early ipods by Apple, lock down normal filemanagement and need specific app to access files. It's probably an Applefication thing they have done. I think I never gonna by Samsung again.

Or is it a Android-thing? No problem with ZTE skate and Android 2.3

---

### Post by Mark Phelps on 2014-04-06
>  It's probably an Applefication thing they have done.

Have no idea what that means -- but I can mount my Samsung Galaxy S3 in Ubuntu 13.10 -- and access it without problems.  So, it's not any kind of "lock down" or the need to use a "specific app".  And ... I can mount it and transfer files just fine in MS Windows, as well, without the need for Kies.

---

