---
title: "USB drive read-only on 20.04 when mounted at boot; worked OK with 18.04"
date: 2022-03-10
forum: Hardware
---

### Post by stephen35 on 2022-03-10
Hi, I like to run my Linux boxes mostly from my Windows box via ssh.  I login at the Linux box itself only if I have no other option.  Some servers (e.g. media server) are run headless.

I like my connected drives to auto mount at boot.  This worked fine in 18.04.  Updated fstab and it just worked.  Since moving the computer to 20.04, the drive mounted at boot is set to read only.  I have another 20.04 box (a Raspberry Pi I use as a Plex media server) and that has no problems with mounting at boot.  Just as well as it headless!  I don't have the 18.04 any more as I replaced the disc and installed 20.04 on a fresh disc.  I guess I could fit the old disc again but not sure how that would help as I know if all works there!

If I log in at the terminal with default fstab then everything mounts and operates as writeable drives

I have been scouring forums for ideas for two days but so far nothing has worked.  Any suggestions would be greatly appreciated.  Thanks!

**FSTAB:**

# /etc/fstab: static file system information.
#
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda5 during installation
UUID=76fc74ce-5cd8-4224-9961-cb4af2b0b609 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
UUID=8AB6-23D0  /boot/efi       vfat    umask=0077      0       1
/swapfile                                 none            swap    sw              0       0
UUID=9A5A-95BF /home/username/USBdata/MyBook auto nosuid,nofail,x-gvfs-show 0 0

**FSTAB (that works on Raspberry Pi):**

LABEL=writable    /     ext4    defaults    0 1
LABEL=system-boot       /boot/firmware  vfat    defaults        0       1
UUID=6AFC8753FC871889 /media/external auto nosuid,nodev,nofail,x-gvfs-show 0 0

username@Leia:~$ ls -al /home/username/USBdata
total 12
drwxrwxr-x  3 username username 4096 Mar 10 10:57 .
drwxr-xr-x 22 username username 4096 Mar  9 17:00 ..
drwxrwxrwx  2 username username 4096 Mar  9 18:43 MyBook

After boot ownership of MyBook is changed to root.  

Thought about changing ownership of /dev/sdc1 to username but then thought that might cause some unpleasant side effects.  I do not know enough to try things like that.  

[B]FDISK -L
[/B]
username@Leia:~$ sudo fdisk -l
[sudo] password for username:

Disk /dev/sda: 1.84 TiB, 2000398934016 bytes, 3907029168 sectors
Disk model: ST2000DM008-2FR1
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0x67ce0d19

Device     Boot   Start        End    Sectors  Size Id Type
/dev/sda1  *       2048    1050623    1048576  512M  b W95 FAT32
/dev/sda2       1052670 3907028991 3905976322  1.8T  5 Extended
/dev/sda5       1052672 3907028991 3905976320  1.8T 83 Linux

Partition 2 does not start on physical sector boundary.

[SIZE=5]**(NOTE: these partitions were the DEFAULT choice made by the Ubuntu installation program)**[/SIZE]

Disk /dev/sdb: 4.56 TiB, 5000981073920 bytes, 1220942645 sectors
Disk model: Backup+  Desk
Units: sectors of 1 * 4096 = 4096 bytes
Sector size (logical/physical): 4096 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0x2d585bc0

Device     Boot Start        End    Sectors  Size Id Type
/dev/sdb1  *     2048 1220942644 1220940597  4.6T  7 HPFS/NTFS/exFAT


**Entry below refers to the USB disc I am trying to mount at boot**

Disk /dev/sdc: 5.47 TiB, 6001174511616 bytes, 11721043968 sectors
Disk model: My Book 25EE
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: 506E0F68-CF42-41C8-926D-0AA0EE024242

Device     Start         End     Sectors  Size Type
/dev/sdc1   2048 11721041919 11721039872  5.5T Microsoft basic data

---

### Post by TheFu on 2022-03-10
File system types matter.  Seems you have all non-Linux file systems, except for the boot drive.  That means that the mount command **must** include the owner and permissions for the entire non-Linux file system to work.  There are a number of clear fstab examples for this in these forums.  Search for 
"mount NTFS fstab uid=1000"
"mount FAT32 fstab uid=1000"
in these forums.

These days, there is little good reason to use FAT32 unless absolutely mandatory.  Mandatory means there is a specific hardware device that only works with FAT32 or it is an EFI partition.  For every other situation where a native Linux cannot or should not be used, either NTFS or exFAT should be used.

As an aside .... all the 'loop' devices in the output above are useless. We never, ever, need to see them when discussing storage.  They are artifacts from the snap package subsystem. Above, they just cruft up the information. *It would be kind to edit the post and remove all loop device output sections.*  Very kind.

[Https://ubuntuforums.org/showthread.php?t=2459633&p=14027843#post14027843](Https://ubuntuforums.org/showthread.php?t=2459633&p=14027843#post14027843) is something I wrote about fstab stuff. I don't think it has an example for FAT32. Sorry. The search terms posted above should find what you seek.

---

### Post by stephen35 on 2022-03-11
> **TheFu said:**
> File system types matter.  Seems you have all non-Linux file systems, except for the boot drive.  That means that the mount command **must** include the owner and permissions for the entire non-Linux file system to work.  There are a number of clear fstab examples for this in these forums.  Search for 
"mount NTFS fstab uid=1000"
"mount FAT32 fstab uid=1000"
in these forums.

Thanks for those suggestions.  I have deleted all reference to the loops.  Yes they are all non Linux as they have their default file systems when purchased and they were used on Windows previously.  If the file system in an issue, why does Ubuntu mount them successfully as writeable drives when I log in at the terminal?  They mounted at boot on 18.04.  Has Ubuntu become more pernickety on this point?

---

### Post by TheFu on 2022-03-11
> **stephen35 said:**
>  If the file system in an issue, why does Ubuntu mount them successfully as writeable drives when I log in at the terminal?  They mounted at boot on 18.04.  Has Ubuntu become more pernickety on this point?

I don't know. It doesn't work that way on **any** of my systems and I don't go out of my way to configure it .... except in a file manager (which I seldom use), I disable automatic mounting.

Automatic mounts are security issues as far as I'm concerned. The power to mount is the power to destroy. That's 100% true. I want to manually control all mounts on my systems.  The distro people have decided to go for ease of use over security.  There are differing opinions about this.  Allowing a random, unknown, storage device, inserted into a USB port to do anything on your system is crazy to me. 

For storage devices we know about, adding 1 line to the /etc/fstab seems like a minimal hassle to make access easy, yet 100% controlled.

BTW, I don't have any 20.04 systems running directly on real hardware. On real hardware, I'm still using 18.04, but plan to move to 20.04 real-soon-now. I have a year.

---

### Post by stephen35 on 2022-03-11
[QUOTE=TheFu;14085285]File system types matter.  Seems you have all non-Linux file systems, except for the boot drive.  That means that the mount command **must** include the owner and permissions for the entire non-Linux file system to work.  There are a number of clear fstab examples for this in these forums.  Search for 
"mount NTFS fstab uid=1000"
"mount FAT32 fstab uid=1000"
in these forums./QUOTE]

Thank you VERY MUCH for your assistance.  i have now made it work.  In the end, all I needed to do was add "user,uid=1000" to my fstab parameters.  I checked my uid with* mount | grep username *and then plugged it into the fstab.  I guess in this case "auto" correctly identified the type of drive.

---

### Post by stephen35 on 2022-03-11
> **TheFu said:**
> I don't know. It doesn't work that way on **any** of my systems and I don't go out of my way to configure it .... except in a file manager (which I seldom use), I disable automatic mounting.

Automatic mounts are security issues as far as I'm concerned

I get that.  In future I will preface questions with the disclosure that this is a home network, so the security implications of auto mount are not something i am particularly concerned about.

---

### Post by vidtek on 2022-03-11
> **TheFu said:**
> I don't know. It doesn't work that way on **any** of my systems and I don't go out of my way to configure it .... except in a file manager (which I seldom use), I disable automatic mounting.

Automatic mounts are security issues as far as I'm concerned. The power to mount is the power to destroy. That's 100% true. I want to manually control all mounts on my systems.  The distro people have decided to go for ease of use over security.  There are differing opinions about this.  Allowing a random, unknown, storage device, inserted into a USB port to do anything on your system is crazy to me. 

For storage devices we know about, adding 1 line to the /etc/fstab seems like a minimal hassle to make access easy, yet 100% controlled.

BTW, I don't have any 20.04 systems running directly on real hardware. On real hardware, I'm still using 18.04, but plan to move to 20.04 real-soon-now. I have a year.

I totally get your point on security on commercial, company and public set-ups.

I wouldn't mind betting that most (I would guess at least 80%) linux users are more like me, with a couple of boxes physically in view in private residences.   The physical security implications of a random USB stick in most of these circumstances is of little concern, whereas usability for the average user probably carries more weight in the developer's minds. 

Cheers Tony.

---

