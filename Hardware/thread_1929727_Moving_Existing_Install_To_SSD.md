---
title: "Moving Existing Install To SSD"
date: 2012-02-22
forum: Hardware
---

### Post by justjustin on 2012-02-22
Not sure where to post this.

I have existing 10.04x64 studio install I would like to move to my new ssd (I will also be moving my Win7 install). I have read many posts on how to do this. I am familiar with most of the steps involved (moving home to separate partition, dual booting, cloning partitons etc) but unsure exactly how to approach the migration.

Here is fdisk without SSD(arriving tomorrow):

```

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xxxxxxxxxxx

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13      121602   976657408    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xxxxxxxx

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1          31      242688   83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sdb2              31        6596    52733953    5  Extended
/dev/sdb3            6596       60802   435405824    7  HPFS/NTFS
Partition 3 does not end on cylinder boundary.
/dev/sdb5            6110        6596     3905536   82  Linux swap / Solaris
/dev/sdb6              31        6110    48828416   83  Linux

Partition table entries are not in disk order

```

I know it's a bit messy. bios boots /sdb1 (grub), then /sdb6 (ubuntu) or /sda1 (winBootloader)
I intend on wiping sda clean and using it as my main linux/windows data(ntfs) partition after windows has been moved and is working correctly.
Data on sdb3 will be restored to the new sda data partition.
Ideally, I would like to move my /home to a new partition also, to save precious SSD space. I just don't want to mess it all up and have ubuntu looking for X @ Y that is now non-existent or anything like that.

Could anyone give me some advice please?
Thanks in advance

---

### Post by oldfred on 2012-02-22
I think there are two schools of thought, one clone or copy entire partition and the other is to do a new clean install and only copy the necessary settings.

If also installing Windows on SSD you may have to clone it, but I do not know about any hidden settings.

Often the issue of cloning from a hard drive to an SSD is that you want to go from a large drive to a smaller drive.

There are two active threads where users are cloning drives but having issues resetting UUIDs which requires editing fstab & reinstalling grub2's boot loader. Also some UUIDs or drive info needs to be updated if you clone.

If a new install you can then copy /home or keep /home on hard drive and use SSD just as boot drive.

I just installed a new  SSD, but have used gpt which is suggested by Arch for SSDs, but if using Windows on the SSD you have to stay with MBR. I created two 30GB partitions for Ubuntu on my SSD. I kept /home inside / (root) but have all data including some hidden data folders like the Firefox profile, kmymoney data and others also in my data partition on the hard drive. Very little other than user settings are in my /home so it easily fits inside root on the SSD and allows the SSD to fully boot without hard drive at all.

Full image backups
[http://clonezilla.org/](http://clonezilla.org/)
Free Imaging software - CloneZilla & PartImage - Tutorial 
[http://www.dedoimedo.com/computers/free_imaging_software.html](http://www.dedoimedo.com/computers/free_imaging_software.html)

My backup strategy is to do a new clean install and just backup settings and data I need to restore system.
Oldfred's list of stuff to backup May 2011:
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)

If you do not have a separate /home:
To move /home uses rsync  
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

Splitting home directory discussion:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)

---

### Post by justjustin on 2012-02-22
Wow, excellent reply, thanks a lot.
I intended to use clonezilla to clone my win7 install, thanks for link though. 
I have also moved /home before and used an existing /home partition on clean install.
I have now fully cleaned up my ubuntu partition and it comes to ~20Gb. As I have plenty of space available overall, there is no problem keeping this partition for the foreseeable future.

After your advice, I am now thinking:
Partition SSD leaving ~40GB for ubuntu at end.
Clone my Win7 to remaining 80GB.
Install clean ubuntu 10.04 and grub to SSD.

Now, is it possible to just copy and use the home and other settings/programs from my current install to my clean install?
I would be happy to keep /home on SSD considering it is quite small at the moment, possibly moving it to another drive in future.

Is that what you meant by:
"If a new install you can then copy /home or keep /home on hard drive and use SSD just as boot drive."

Basically, what I mean is: from my clean ubuntu install, copy all settings/programs and home from my existing "old" install without needing to backup and restore them?

---

### Post by oldfred on 2012-02-22
If /home is small you can just copy it into the SSD or if it also is a separate partition mount it as part of the install from the partition on the hard drive. 
Many suggest having it on the hard drive under the assumption it also has lots of data and is larger. I prefer, if possible to have the part of /home that has the user settings (most of the hidden or . files & folders) on the SSD as those are accessed more than the data. Then I keep the data part (Documents, Music, Video etc) of /home on the hard drive. I link both folders from my shared NTFS and data ext3 partitions.

Part of my reason for having /home on the SSD is that I try to configure each hard drive as a fully bootable drive. All system partitions including /home (which I leave in /) are on one drive. But almost all data is on various drives and mounted in each install. I have at least one copy of Ubuntu on every drive except my old XP drive. I used to rotate current install of Ubuntu from drive to drive. I could easily find an old setting and add it to the new version or reboot into old version. Also good for testing next version separately.

I mount my data partition in /mnt/data so it is not seen in Nautilus but link all the data folders back into /home. Others suggest bind as a better way but linking has worked for me.
Another way to share:
Morbius1 uses bind, now:
[http://ubuntuforums.org/showthread.php?t=1896695](http://ubuntuforums.org/showthread.php?t=1896695)
kansasnoob's sharing and Morbius1 use of bindfs older
[http://ubuntuforums.org/showthread.php?t=1495798](http://ubuntuforums.org/showthread.php?t=1495798)
Advantages of bind post 16 - Morbius1
[http://ubuntuforums.org/showthread.php?t=1896695](http://ubuntuforums.org/showthread.php?t=1896695)

---

### Post by justjustin on 2012-02-22
Ok, thanks again.

"If /home is small you can just copy it into the SSD"

So, this is what I would like to do.

In my clean install I can just copy over my home folder and /etc and upon rebooting I should be able to login as my "old" user?

But, it is not possible to somehow (easily) copy over all installed packages. I will need to build a list of currently installed packages and download and install them in my clean install. 
> 
dpkg --get-selections > ~/my-packages
sudo dpkg --set-selections < my-packages && sudo apt-get dselect-upgrade


Do I have this right?

As I said I will be keeping existing install until I have everything on SSD working as it should, so no real fear of anything going too wrong, only that I could be wasting time going about it with the wrong idea.

Thanks for all the help/info so far and hope I'm not wasting _your_ time ;)

---

### Post by oldfred on 2012-02-22
I have used dpkg many times on new installs. From my history:

  431  dpkg --set-selections < ubuntu-filesport2010Mar
  432  sudo dpkg --set-selections < ubuntu-filesport2010Mar
  434  sudo apt-get -y update
  435  sudo apt-get update
  436  sudo apt-get dselect-upgrade
  437  history

If reinstalling exactly the same version and have not housecleaned you can copy the debs. I am normally installing to a new version.
Location of downloaded debs
/var/cache/apt/archives/
sudo apt-get install --no-download <package name>

Again if the same version you can copy /etc but if any different you have to be careful as new version may also have changes that you want or old settings are not required with a new verison. I try to copy any system file I edit into my /home so I only backup /home and have system modify settings I might need.

More detail on /etc files to backup - post #3:
[http://ubuntuforums.org/showthread.php?t=1500559](http://ubuntuforums.org/showthread.php?t=1500559)

Files to include or exclude from full system backup.
[http://ubuntuforums.org/showthread.php?t=1903085](http://ubuntuforums.org/showthread.php?t=1903085)

Some files to exclude from /home:
[http://ubuntuforums.org/showthread.php?t=1883834](http://ubuntuforums.org/showthread.php?t=1883834)
/home/*/.cache
/home/*/.dbus
/home/*/.dropbox
/home/*/.gvfs
/home/*/.local/share/Trash
/home/*/.mozilla/firefox/*.default/Cache/**
/home/*/.qt
/home/*/.thumbnails
/home/*/Examples
/home/.ecryptfs
/home/lost+found

---

### Post by justjustin on 2012-02-22
Great, yes, it will be exact same version, 10.04 studio LTS. You almost gave me too much info earlier I had trouble making out exactly what was relevant to the way I decided to do it but I have a very clear idea now, thanks.
I apt-clean'd a good while back so will use whatever is there now, should save a bit of dl'ing.
Should be getting SSD in morning so will probably get straight into it and will let you know how it goes.

Thanks a million for your time

---

### Post by justjustin on 2012-03-03
Just to report back, all went smoothly when SSD finally arrived.
Only hitch was Win7 which I ended up clean-installing, no harm.

I just partitioned as normal, install Win7 then Ubuntu and grub.
Installed all packages from package list, saved 2.5GB download by keeping /var/cache/apt/archives.
Then copied my old /home and /etc to new system, excluding suggested files.

Left /home on SSD, all Data Folders on 1TB drive and linked to both Ubuntu and Win7, mounted at /media for convenience. 
All Data folders, /home, /etc, and /var/cache/apt/archives/ are rsynced to an ntfs and ext4 partition on 500GB, mounted at /mnt and hidden in nautilus.

Everything running great (and fast) too.

Thanks for the help, you made this so easy.

---

### Post by oldfred on 2012-03-03
Glad it worked. :)

---

