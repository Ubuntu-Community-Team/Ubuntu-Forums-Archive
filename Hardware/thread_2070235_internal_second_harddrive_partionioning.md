---
title: "internal second harddrive partionioning"
date: 2012-10-12
forum: Hardware
---

### Post by fernansha on 2012-10-12
hi guys, 
i have two hardrives built in, where as an ssd and a 750gb hdd, 
i did the root, home , tmp, swap in the ssd and i am not sure wat should i do for the second one i have, and its not showinf up in the list as well, 
and i want to use that as my /transfer drive .

any suggestions how to do it. thanks.

---

### Post by cjhabs on 2012-10-12
You should use "sudo fdisk -l" to list the drives that the system can see. You can also use fdisk to partition the drive - if it a second drive, not the OS drive, then the simplest is to make it a single data partition. If it does not show up in the fdisk list I assume it is a driver issue.

---

### Post by fernansha on 2012-10-12
thanks for the quick reply cjhabs, the fdisk lists the second hardisk, 
in wat format i should partition it and wat should be the name for it, 

for eg, when installing we assignd, /,home etc.. like wat should give this ?

---

### Post by ALinuxWindowsBalance on 2012-10-12
> **fernansha said:**
> thanks for the quick reply cjhabs, the fdisk lists the second hardisk, 
in wat format i should partition it and wat should be the name for it, 

for eg, when installing we assignd, /,home etc.. like wat should give this ?

You probably shouldn't use it. What is the size of the SSD?
If it's something huge like 3TB you're obviously fine.
But /transfer? I haven't seen that before. Are you going to install another operating system? Because if you are, it's fine to keep /transfer on the SSD. You can just navigate to it from Windows, or whatever.

---

### Post by fernansha on 2012-10-12
i am not going to use windows, 
i have an ssd size of 80gb and the second hardisk is 750gb this is were i am confused.. coz almost separated the ssd perfectly how i need.

/transfer is wat i had at workplace, coz the home folder was is server and /tranfer was the hdd in the machine. thats why i mentioned /transfer..
nothing specific

---

### Post by ALinuxWindowsBalance on 2012-10-12
> **fernansha said:**
> i am not going to use windows, 
i have an ssd size of 80gb and the second hardisk is 750gb this is were i am confused.. coz almost separated the ssd perfectly how i need.

/transfer is wat i had at workplace, coz the home folder was is server and /tranfer was the hdd in the machine. thats why i mentioned /transfer..
nothing specific
**LOOK AT THE PICTURES FIRST**
When one of my disks don't show up(i had this problem once) Try setting the pins on the actual drive, the 750-er(that means taking off the computer's cover, the HDD enclosure, and unplugging the drive.) On the back you'll see pins(the pictures are attached) which are called jumpers. Remove all the 'jumpers' and **KEEP THEM SAFE.** They are very small and are very important. On the cover your hard drive should have instructions for setting C5, Master, and Slave. Allign the jumpers to the pins, per the Drive's instructions for SLAVE. Try it now.

---

### Post by fernansha on 2012-10-12
thanks for the info, i was aware of it too, but i am using a netbook. 
now i see the hardrive in terminal. with fdisk, i just want to make sure wat format it should be and how to make it visible in the actual gnome. 

i am guessing i should go with ext4 and leave the partion type be logical..

---

### Post by ALinuxWindowsBalance on 2012-10-12
> **fernansha said:**
> thanks for the info, i was aware of it too, but i am using a netbook. 
now i see the hardrive in terminal. with fdisk, i just want to make sure wat format it should be and how to make it visible in the actual gnome. 

i am guessing i should go with ext4 and leave the partion type be logical..

Is there another partition on the 750GB?

---

### Post by cjhabs on 2012-10-12
Logical is fine. ext4 is good for Linux. You could use NTFS if at some point you decide to move it to a windows machine as a data drive. You can use /transfer as the mount point - that is not a problem. You will need to add it to /etc/fstab to mount it at boot time. Removable drives get mounted under /media when they are recognized - I am not sure if the internal drive would get automatically mounted there without an entry in /etc/fstab - you try that first.

---

### Post by fernansha on 2012-10-12
> **cjhabs said:**
> Logical is fine. ext4 is good for Linux. You could use NTFS if at some point you decide to move it to a windows machine as a data drive. You can use /transfer as the mount point - that is not a problem. You will need to add it to /etc/fstab to mount it at boot time. Removable drives get mounted under /media when they are recognized - I am not sure if the internal drive would get automatically mounted there without an entry in /etc/fstab - you try that first.

i dont have any partition on the 750gb HDD

thanks for the reply guys! i am doing that now! will post the results pretty soon, hope it works.

---

### Post by oldfred on 2012-10-12
I use /mnt/data or /mnt/shared, but with Linux you can use just about anything you want. If you mount it in fstab into /home or /media it will appear in the left panel of naulitus. Other locations will not. I then use links to show the folders in my /home.

You also will need to set ownership and permissions so you can use your new data partition.

Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)

from Morbius1-----------------------------------------------------
[http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
suggest using templates instead. Post #6
For ntfs UUID shown is example only see below:
UUID=DA9056C19056A3B3 /media/WinD ntfs defaults,nls=utf8,umask=000,uid=1000,windows_names 0 0
Window_names prevents the use of invalid windows characters:
(which are the nine characters ” * / : < > ? \ | and those whose code is less than 0×20) 
uid=1000 should fix the trash problems as well:

For ext4:
UUID=076426af-cbc5-4966-8cd4-af0f5c879646 /media/Data ext4 defaults,noatime 0 2
** To find the correct UUID for your partitions:
sudo blkid -c /dev/null -o list
** You will have to create the mount point yourself, for example:
sudo mkdir /media/WinD
and/or 
sudo mkdir /media/Data
** Then add the template with the correct UUID and mount point to fstab:
sudo cp /etc/fstab /etc/fstab.backup
gksu gedit /etc/fstab
** And when you are done editing fstab and saving it run the following command to test for errors and mount the partitions without requiring a reboot. You will know before you reboot if something is amiss. :
sudo mount -a

---

