---
title: "Ubuntu 14.04. How to regain use of 2x2TB Expansion Drives"
date: 2016-03-16
forum: Hardware
---

### Post by RayArdia on 2016-03-16
I have 2 x 2TB Seagate Expansion Drives, previously 'of good behaviour' but_ now_ telling me I don't have permission needed to create and delete files.
Have looked at all relevant posts and tried to follow the arguments and coding but failed.
Here are some terminal outputs, perhaps someone would be so kind as to point me onwards. BTW tried to use Nautilus to change permissions but failed.

```
ray@ray-Aspire-5735:~$ sudo fdisk -l
[sudo] password for ray: 

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00001ec9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048   419559423   209778688   83  Linux
/dev/sda2   *   419559424   482252799    31346688    7  HPFS/NTFS/exFAT
/dev/sda3       482254846   488396799     3070977    5  Extended
/dev/sda5       482254848   488396799     3070976   82  Linux swap / Solaris
Note: sector size is 4096 (not 512)

Disk /dev/sdc: 2000.4 GB, 2000398929920 bytes
255 heads, 63 sectors/track, 30400 cylinders, total 488378645 sectors
Units = sectors of 1 * 4096 = 4096 bytes
Sector size (logical/physical): 4096 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xe9140063

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1            2048   488376319  1953497088    7  HPFS/NTFS/exFAT

Disk /dev/sdd: 2000.4 GB, 2000398933504 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029167 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000e3672

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1            2048  3907029163  1953513558    7  HPFS/NTFS/exFAT
```
```
ray@ray-Aspire-5735:~$ cd ..
ray@ray-Aspire-5735:/home$ cd ..
ray@ray-Aspire-5735:/$ ls
bin    dev   initrd.img      lost+found  opt   run   sys  var
boot   etc   initrd.img.old  media       proc  sbin  tmp  vmlinuz
cdrom  home  lib             mnt         root  srv   usr  vmlinuz.old
ray@ray-Aspire-5735:/$ cd media/ray
ray@ray-Aspire-5735:/media/ray$ ls
59C785F86AF71638  Seagate Expansion Drive
ray@ray-Aspire-5735:/media/ray$ gksudo nautilus
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


** (nautilus:2592): WARNING **: bookmark uri is file:///root/Desktop, but expected file:///root

(nautilus:2592): GLib-CRITICAL **: Source ID 97 was not found when attempting to remove it

(nautilus:2592): GLib-CRITICAL **: Source ID 98 was not found when attempting to remove it

(nautilus:2592): GLib-CRITICAL **: Source ID 99 was not found when attempting to remove it
```
```
ray@ray-Aspire-5735:/media/ray$ sudo mount
/dev/sda1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/cgroup type tmpfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
none on /sys/fs/pstore type pstore (rw)
systemd on /sys/fs/cgroup/systemd type cgroup (rw,noexec,nosuid,nodev,none,name=systemd)
gvfsd-fuse on /run/user/1000/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=ray)
/dev/sdc1 on /media/ray/Seagate Expansion Drive type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sdd1 on /media/ray/59C785F86AF71638 type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
```
```
ray@ray-Aspire-5735:/media/ray$ sudo fdisk -l

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00001ec9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048   419559423   209778688   83  Linux
/dev/sda2   *   419559424   482252799    31346688    7  HPFS/NTFS/exFAT
/dev/sda3       482254846   488396799     3070977    5  Extended
/dev/sda5       482254848   488396799     3070976   82  Linux swap / Solaris
Note: sector size is 4096 (not 512)

Disk /dev/sdc: 2000.4 GB, 2000398929920 bytes
255 heads, 63 sectors/track, 30400 cylinders, total 488378645 sectors
Units = sectors of 1 * 4096 = 4096 bytes
Sector size (logical/physical): 4096 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xe9140063

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1            2048   488376319  1953497088    7  HPFS/NTFS/exFAT

Disk /dev/sdd: 2000.4 GB, 2000398933504 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029167 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000e3672

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1            2048  3907029163  1953513558    7  HPFS/NTFS/exFAT
```
```
ray@ray-Aspire-5735:/media/ray$ sudo chown -R user:group /path/to/disk
chown: invalid user: ‘user:group’
ray@ray-Aspire-5735:/media/ray$ sudo chown -R ray:ray /Seagate Expansion Drive 
chown: cannot access ‘/Seagate’: No such file or directory
chown: cannot access ‘Expansion’: No such file or directory
chown: cannot access ‘Drive’: No such file or directory
ray@ray-Aspire-5735:/media/ray$ sudo chown -R ray:ray /Seagate_Expansion_Drive chown: cannot access ‘/Seagate_Expansion_Drive’: No such file or directory
ray@ray-Aspire-5735:/media/ray$ ^C
ray@ray-Aspire-5735:/media/ray$ 
```

Any help gratefully received!
Ray

---

### Post by ajgreeny on 2016-03-16
I have attempted to clarify your post by adding code tags to the many and varied commands that you have used, but it is a little difficult to sort out exactly what you thought you were doing.

Have you formatted these external drives, and if so what filesystem do you believe you put on them, or are they now as they were when you first got them and they behaved as they should?

However for your information the command you used ```
ray@ray-Aspire-5735:/media/ray$ sudo chown -R ray:ray /Seagate Expansion Drive
``` will always show the error as spaces in file and folder names must be escaped either by using quotation marks around the pathway or by using a backslash (escape character) in front of the space, so your command needs to end with either **"/Seagate Expansion Drive"** or **/Seagate\ Expansion\ Drive**
Unfortunately, however, that will not work for a partition that is formatted as NTFS as that filesystem does not understand Linux permissions and will have to be mounted with options to make it read/write, probably in fstab.

---

### Post by RayArdia on 2016-03-16
Both Seagate drives are formatted NTFS, a single partition in each. Up until very recently I was able to use them without any restrictions - can't fathom what went wrong.
Very grateful for your reply, can you advise further please?
Ray

---

### Post by oldfred on 2016-03-16
What version of Windows?
Windows hibernation or Windows 8 or later versions with fast startup which is always on hibernation, leaves all NTFS partitions in effect mounted.
Linux NTFS driver cannot load hibernated or NTFS partitions needing chkdsk. If still mounted due to hibernation or not fully shutdown when disconnected and then now needing chkdsk from Windows will prevent Linux from mounting them.

Even a power flicker can be enough to corrupt a file system whether Windows or Linux and then either chkdsk or fsck if Linux ext4 repairs are needed.
Or good backups always required.

---

### Post by RayArdia on 2016-03-16
Hadn't used Windows for over 15 years, but about 2 years ago I dual-booted a Windows 7 OS at the same time as loading Ubuntu 14.04. I only did so because my grandson (an IT manager) suggested it as a 'fail-safe measure.
I did try, this morning, to see if Windows would give me access to the drives (as suggested in one of the Hardware posts). Windows was no help so back to good old Ubuntu!
Maybe your " If still mounted due to hibernation or not fully shutdown when disconnected and... " may be what is happening NOW, but still doesn't explain why it wouldn't work in Ubuntu.
Apologies for long-windedness.
Ray
Further to above I now find that the laptop will not go to 'suspend', nor will it shut down. The only way I can stop it is to hold the on/off switch down - I am aware that this is [U]not[U] recommended, but don't know what else to do.
I'm sure that a 'clean boot' with the latest 14.04 would solve these problems but of course to do that I need to save my Home folder, for which, ideally I would like to be able to access my Expansion Drives, so back to the beginning of this post!
Ray

---

### Post by RayArdia on 2016-03-18
In  desperation I  abandoned  hope of being able to use the Seagates with the Ubuntu 14.04 that I had installed. Rebooted and installed a fresh 14.04. NOW I can't open either drive and my Logitech USB mouse is not working.
Before I lose the will.... to continue with Ubuntu, can someone please mark out a way forward?

---

### Post by oldfred on 2016-03-18
To get USB devices to work, in BIOS settings, I often have had to either turn on keyboard & mouse settings to use USB ports or a USB port setting to allow devices or something similar.

I believe this is one of the settings that Seagate uses. It makes large drives more compatible with old systems but is not standard.
Sector size (logical/physical): 4096 bytes / 4096 bytes

Most systems are 512/4096

---

### Post by RayArdia on 2016-03-18
Sorry to say Oldfred, your post doesn't mean a lot to me, though the bit "Sector size (logical/physical): 4096 bytes / 4096 bytes" rings a bell, I think my drives have such sectors.
If it is of any help I now get this Error message:-
Error mounting /dev/sdd1 at /media/ray/59C785F86AF71638: Command-line `mount -t "ntfs" -o "uhelper=udisks2,nodev,nosuid,uid=1000,gid=1000,dmask=0077,fmask=0177" "/dev/sdd1" "/media/ray/59C785F86AF71638"' exited with non-zero exit status 13: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Failed to read NTFS $Bitmap: Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.
This too seems to 'think' I'm using Windows and I'm not; I have now only got Ubuntu 14.04 on the machine.
Ray

---

### Post by oldfred on 2016-03-19
It also could be if you left Windows hibernated when external drives were plugged in. All NTFS partitions then are in hibernated state and cannot be default mounted read/write in Linux. You may be able to force mount in read only mode.

 Force mount, read only (ro), example with sda3, use one of your drives/partitions:
sudo mkdir /media/windows
sudo mount -t ntfs-3g -o ro /dev/sda3 /media/windows 

Some issues with Acer and USB ports in this thread, see last few posts.
[http://ubuntuforums.org/showthread.php?t=2285694](http://ubuntuforums.org/showthread.php?t=2285694)

More info on 4K drives:
 [http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/)

---

### Post by RayArdia on 2016-03-22
> **oldfred said:**
> It also could be if you left Windows hibernated when external drives were plugged in. All NTFS partitions then are in hibernated state and cannot be default mounted read/write in Linux. You may be able to force mount in read only mode.

 Force mount, read only (ro), example with sda3, use one of your drives/partitions:
sudo mkdir /media/windows
sudo mount -t ntfs-3g -o ro /dev/sda3 /media/windows 

Some issues with Acer and USB ports in this thread, see last few posts.
[http://ubuntuforums.org/showthread.php?t=2285694](http://ubuntuforums.org/showthread.php?t=2285694)

More info on 4K drives:
 [http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/)

I'm so sorry to be so thick, but I don't understand the kind replies so far received.
Re. [QUOTE=oldfred;13457678]It also could be if you left Windows hibernated when external drives were plugged in. All NTFS partitions then are in hibernated state and cannot be default mounted read/write in Linux. You may be able to force mount in read only mode.
As I understand Oldfred's comment the reason why I can't access the two Seagate drives is because they were hibernated when I (foolishly) tried to follow an old post in Hardware which suggested trying to change the drives' permissions using Windows.
At present I can't even get the two drives to show up either in Nautilus or in Terminal. The should be at /media/ray/..... but 'ls' shows nothing at all.
Do you think I could un-inhibit them by connecting to a Windows PC? I must admit to being terrified of losing the data on these drives and Oldfred's suggestion:-

 Force mount, read only (ro), example with sda3, use one of your drives/partitions:
sudo mkdir /media/windows
sudo mount -t ntfs-3g -o ro /dev/sda3 /media/windows '
makes me worry that  I&#8217;ll get it wrong and go and delete the lot!

I'll be 80 soon and I'd really like to get things working again before then!

Afternote:- Now the two drives do _sometimes_ appear in Launcher when they are switched on, but still have no write access. Am very worried that two folders which were previously full of data now show content as 'nothing' in Properties; is this just some sort of 'glitch' (ie a false report) or can the content have disappeared?

Can someone please help me sort things out?

---

### Post by oldfred on 2016-03-22
Yes, you should be able to connect to a Windows computer.

Then make sure fast start up or always on hibernation is totally off.
       Fast Startup off (always on hibernation)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.htmlold](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.htmlold)

---

### Post by RayArdia on 2016-03-31
In complete desperation I downloaded the latest version of Ubuntu 16.04 and installed it. MAGIC! Everything works as it should; can 'see' my two Seagate drives and Permissions allow me to Read/Write.
I now consider my problem solved - perhaps others who are having similar problems should try this, after suitably backing-up Home and anything else of importance?

---

