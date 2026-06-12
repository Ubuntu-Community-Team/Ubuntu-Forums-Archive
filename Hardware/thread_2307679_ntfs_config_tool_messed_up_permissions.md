---
title: "ntfs config tool messed up permissions"
date: 2015-12-27
forum: Hardware
---

### Post by cafeledavid on 2015-12-27
I am new to Ubuntu, I wanted to use plex media server but it was unable to see any video files on my external drive. I googled around and someone suggested to use a ntfs config program, so i went to the application center and downloaded ntfs configuration tool (i should have listened to the only rating of do not use!) and now i can still get into the drive and open/create files however i can no longer delete unless i right click and select delete though it permanatley deletes the file/folder instead of going to the trash like it used to. i tried to change the permissions through the program but no luck, i removed it now. i also tried gksu nautilus but it wont take my changes

i checked the permissions and now all of my permissions are set to user root and group root, i googled again and only found these solutions to use sudo chown -R me:me /dir/. but no luck i also tried chmod - i get no errors but still have this dilemma
here is my fstab file:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>


#Entry for /dev/sda1 :
UUID=bb17e668-62dc-4ec1-871d-b3dcb3a67621    /    ext4    errors=remount-ro    0    1
#Entry for /dev/sdb1 :
THIS IS MY EXT HDD --->     UUID=B86CB0626CB01CD6    /media/david/B86CB0626CB01CD6    ntfs-3g    defaults,nosuid,nodev,locale=en_US.UTF-8    0    0
#Entry for /dev/sda5 :
UUID=5d0d5d4a-22fd-49ed-8f6a-0a08acbe4c43    none    swap    sw    0    0

i tried to use my vmware win7 box and reset permissions, i changed the owner to the windows admin username, removed all linux usernames, and gave permissions to everyone/read only and to myself full access but now i cant unmount/mount the drive when i put i back to the ubuntu box, only remove it, then i have to power cycle it or replug the usb cable :\

i checked and the permissions still say only root has access but i can still read/write but when i delete i still have to right click and it does it permanately instead of going to the trash like it used to

just rebooted and same thing help please :(

-.-

i am going to format it and start again, luckily i have a 4tb drive as a backup of my active 2tb drive, just imaged my system too just in case, already had to reinstall linux due to installing 32 bit prior to 64 bit, seems some apps like cairo dock dont work well with it and i cant use any of my vm apps since they are 64 bit as well, lost 1 day doing that :\

---

### Post by ajgreeny on 2015-12-27
You will need to make sure the permissions for the mountpoint of the USB drive allow it to be used by the user plex.

I have done this by firstly adding my user to the plex group and also adding the user plex to the group of my username.

Secondly I make a folder in my home named **Plex/USB** and then mount the USB disk, a flash drive in my case formatted to fat32, to that folder in my home, not where it mounts automatically to /media/username.

As USB disks always mount as /dev/sdf, I do this with an alias, using command **usb** for simplicity, which really runs the command ```
sudo umount /dev/sdf1 && sudo mount /dev/sdf1 /home/username/Plex/USB/
``` to firstly unmount it from /media/username and then mount it in that home folder.

Finally to be sure it works, I change the permissions of the /Plex/USB folder in my home to ensure both that it is mine with ```
sudo chown username:username /home/username/Plex/USB
``` and then make it read/write for both users and groups with ```
chmod 775 Plex/USB
```That final chown command may be unnecessary for you so test it first.

---

### Post by cafeledavid on 2015-12-27
thanks yeah i will try that on a usb flash drive later, right now i am copying everything from one ext hdd to the other (19 hours to go...) by the way i formatted via windows vmware just in case the permissions did not reset correctly

the movie files were in /media/user/subfolder/subfolder not at the root of the media folder if that helps

---

### Post by oldfred on 2015-12-27
If you are using NTFS, you cannot change permissions or ownership. Defaults are only set with the mounting.
Normally external drives are not mounted with fstab, as drive may not be present when rebooting, especially cold boot, or may not come up to speed in time to be correctly mounted with fstab.

 Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.
HOWTO: Mount NTFS partitions with specific ownership/permissions - WorMzy
[http://ubuntuforums.org/showthread.php?t=1604251](http://ubuntuforums.org/showthread.php?t=1604251)
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)

---

### Post by cafeledavid on 2015-12-27
thanks for the info

---

### Post by cafeledavid on 2016-01-02
i tried this and now it shows up in plex however it gave root the permissions after i did the last step chmod 775 plex/usb

so i cannot do anything but read the contents, i tried to revert the permissions to myself but i am getting this error

Operation not permitted

i also tried using sudo su to change the permission but didnt work

i used a test usb flash drive because i really dont want to have to copy 1tb over 20 hours again by formatting by ext hdd again :\

any ideas? i am going to format this now sigh


> **ajgreeny said:**
> You will need to make sure the permissions for the mountpoint of the USB drive allow it to be used by the user plex.

I have done this by firstly adding my user to the plex group and also adding the user plex to the group of my username.

Secondly I make a folder in my home named **Plex/USB** and then mount the USB disk, a flash drive in my case formatted to fat32, to that folder in my home, not where it mounts automatically to /media/username.

As USB disks always mount as /dev/sdf, I do this with an alias, using command **usb** for simplicity, which really runs the command ```
sudo umount /dev/sdf1 && sudo mount /dev/sdf1 /home/username/Plex/USB/
``` to firstly unmount it from /media/username and then mount it in that home folder.

Finally to be sure it works, I change the permissions of the /Plex/USB folder in my home to ensure both that it is mine with ```
sudo chown username:username /home/username/Plex/USB
``` and then make it read/write for both users and groups with ```
chmod 775 Plex/USB
```That final chown command may be unnecessary for you so test it first.

---

### Post by cafeledavid on 2016-01-05
anyone?

---

