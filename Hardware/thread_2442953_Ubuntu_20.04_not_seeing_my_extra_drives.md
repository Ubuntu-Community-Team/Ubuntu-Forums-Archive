---
title: "Ubuntu 20.04 not seeing my extra drives"
date: 2020-05-09
forum: Hardware
---

### Post by morcar on 2020-05-09
I have installed the all new version of Ubuntu 20.04 onto my SSD and I have 3 internal hard drives that I have games and other things on.

When I use Retroarch I am unable to see these other drives even though they are mounted.

Is there anything I can do to solve this?

Thanks

---

### Post by oldfred on 2020-05-09
What is RetroArch?

Post these.
cat /etc/fstab
lsblk -o name,mountpoint,label,size,fstype,uuid,partuuid | egrep -v "^loop"

---

### Post by CelticWarrior on 2020-05-09
So, from your description, it's *not* Ubuntu the OS that isn't seeing the extra drives - "*they are mounted*" - but Retroarch, the program not recognizing those drives?

If so then the likely explanation is because Retroarch is a snap app. Those by default have access to the user's home only.

---

### Post by morcar on 2020-05-09
RetroArch is a frontend to many cores for other systems

daddy@daddy-GA-78LMT-USB3-6-0:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sdc5 during installation
UUID=22de9529-1477-4cd2-9fee-8a2830f1ec27 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sdc1 during installation
UUID=5006-A861  /boot/efi       vfat    umask=0077      0       1
/swapfile                                 none            swap    sw              0       0


daddy@daddy-GA-78LMT-USB3-6-0:~$ lsblk -o name,mountpoint,label,size,fstype,uuid,partuuid | egrep -v "^loop"
NAME   MOUNTPOINT                   LABEL   SIZE FSTYPE   UUID                                 PARTUUID
sda                                       931.5G                                               
&#9492;&#9472;sda1                              Games 931.5G ntfs     4FDA2673701D22EE                     46bd197d-01
sdb                                       931.5G                                               
&#9492;&#9472;sdb1 /media/daddy/Roms1           Roms1 931.5G ntfs     655A767C261B7245                     fb644c9b-01
sdc                                       447.1G                                               
&#9500;&#9472;sdc1 /boot/efi                            512M vfat     5006-A861                            3ad89a31-01
&#9500;&#9472;sdc2                                        1K                                               3ad89a31-02
&#9492;&#9472;sdc5 /                                  446.6G ext4     22de9529-1477-4cd2-9fee-8a2830f1ec27 3ad89a31-05
sdd                                       931.5G                                               
&#9492;&#9472;sdd1                              Roms2 931.5G ntfs     294D426D3497F354                     8187bf6c-01
sr0                                        1024M

---

### Post by morcar on 2020-05-09
I will see what I can do about not using the snap app and post back in a moment.

thanks for the advice

---

### Post by CelticWarrior on 2020-05-09
If you installed via the app store then just search it and then you'll see a "permissions" button. Check that.

---

### Post by deadflowr on 2020-05-09
Open Software, or Ubuntu Software (whatever the app store is called) 
Click on  Installed (located up top)
Find Retroarch in the listings of the installed apps and click to open it's page, 
up in the top area click on Permissions and a pop up box will show.
In the popup box go down to where it says  allow read/write to removable media and toggle it to on.
(It will require your password to authenicate)

removable media only works for media mounted at either /mnt or the /media directories.

---

### Post by morcar on 2020-05-09
Ok so I removed the snap version and entered the ppa for retroarch and then installed the app

All drives are now seen :D

Thank you so much for help

---

