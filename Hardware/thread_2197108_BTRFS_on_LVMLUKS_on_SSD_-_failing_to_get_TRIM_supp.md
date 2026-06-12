---
title: "BTRFS on LVM/LUKS on SSD - failing to get TRIM support enabled"
date: 2014-01-02
forum: Hardware
---

### Post by SixedUp on 2014-01-02
I'm trying to set up 13.10 on a 250GB Samsung 840 EVO SSD in a Thinkpad x201. Because this machine is used for work, I need full disk encryption, so I'm using the traditional approach of a LUKS/LVM container for all partitions apart from /boot. To keep the SSD running well I'm keen to get Trim support working. And so far I'm failing, and need some help!

What I've been doing (because of the limitations of the GUI installer) is a manual partition and post-install tidy up:

So, from the Live USB, I install and run gdisk to create a GPT partition table on the SSD, and then a 1GB /boot partition (sda1, type 8300) aligned to 2048 sectors. Then the rest of the space is allocated to an LVM container (sda2, type 8e00).

I then issue:```

sudo cryptsetup luksFormat /dev/sda2
sudo cryptsetup luksOpen /dev/sda2 Ubuntu
sudo pvcreate /dev/mapper/Ubuntu
sudo vgcreate Ubuntu /dev/mapper/Ubuntu
sudo lvcreate -L 20G -n RootVol Ubuntu
sudo lvcreate -L 4G -n SwapVol Ubuntu
sudo lvcreate -l 100%FREE -n HomeVol Ubuntu
```

At this point I can run the GUI installer, pointing it at my partition layout, getting it to format the various partitions and install 13.10. When that completes, I stay in the Live USB, and:
```

sudo mount -t btrfs -o compress-force=zlib,discard,noatime,subvol=@ /dev/mapper/Ubuntu-RootVol /mnt
sudo mount /dev/sda1 /mnt/boot
sudo mount --bind /dev /mnt/dev
sudo chroot /mnt
> mount -t proc proc /proc
> mount -t sysfs sys /sys
> mount -t devpts devpts /dev/pts
```

I then create /etc/crypttab:```

# <target name> <source device> <key file> <options>
Ubuntu UUID=41ef7d4b-500c-4c83-a40a-9ef1c456653f none luks,discard
```

I then create /etc/initramfs-tools/conf.d/cryptroot:```

CRYPTROOT=target=Ubuntu,source=/dev/disk/by-uuid/41ef7d4b-500c-4c83-a40a-9ef1c456653f,discard
```

I then alter /etc/lvm/lvm.conf, changing the line that reads
```
issue_discards = 0
```
to 
```
issue_discards = 1
```

Next update my /etc/fstab to reflect the mount options I want:```

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
/dev/mapper/Ubuntu-RootVol /               btrfs   defaults,noatime,compress-force=zlib,discard,subvol=@ 0       1
# /boot was on /dev/sda1 during installation
UUID=d024ca5e-a8ba-45f3-9f46-e5949c84f125 /boot           ext3    defaults        0       2
/dev/mapper/Ubuntu-HomeVol /home           btrfs   defaults,noatime,compress-force=zlib,discard,subvol=@home 0       2
/dev/mapper/Ubuntu-SwapVol none            swap    sw              0       0
```

Finally, I update /etc/default/grub so the GRUB_CMDLINE_LINUX statement reads:```

GRUB_CMDLINE_LINUX="cryptopts=target=Ubuntu,source=/dev/disk/by-uuid/1f199eb6-b2ad-4014-9f8d-41954bf1a417,lvm=Ubuntu"
```

I then issue the commands:```

update-initramfs -k all -c
update-grub
```
and reboot.

The system comes up fine, but, when I try to run a trim on the SSD, I get:
```
> fstrim -v /home
fstrim: /home: FITRIM ioctl failed: Operation not supported.
```

If I then examine the discard status of the block level devices, I get:```

> lsblk -D
NAME                        DISC-ALN DISC-GRAN DISC-MAX DISC-ZERO
sda                                0      512B       2G         0
&#9500;&#9472;sda1                             0      512B       2G         0
&#9492;&#9472;sda2                             0      512B       2G         0
  &#9492;&#9472;Ubuntu (dm-0)                  0      512B       2G         0
    &#9500;&#9472;Ubuntu-RootVol (dm-1)        0      512B       2G         0
    &#9500;&#9472;Ubuntu-SwapVol (dm-2)        0      512B       2G         0
    &#9492;&#9472;Ubuntu-HomeVol (dm-3)        0      512B       2G         0
```

Which seems to imply no TRIM support. But if I do:```

> hdparm -I /dev/sda | grep -i trim
    *    Data Set Management TRIM supported (limit 8 blocks)
```
... I can see that the drive does support TRIM.

So if I try to run the fstrim on the /boot partition (/dev/sda1) I get:```

> fstrim -v /boot
/boot: 933625856 bytes were trimmed
```
... which implies that drive support is OK, and so is the kernel support. Of course, /boot is ext3, not btrfs like the / and /home. 

But it looks more like this is a LUKS/LVM problem ... and I think that I can confirm that by:```

> cryptsetup status Ubuntu
/dev/mapper/Ubuntu is active and is in use.
  type:    LUKS1
  cipher:  aes-cbc-essiv:sha256
  keysize: 256 bits
  device:  /dev/sda2
  offset:  4096 sectors
  size:    486293839 sectors
  mode:    read/write
```
... which is missing the expected " flags: discards" at the end, indicating the TRIM passthrough is NOT enabled for some reason. I think.

I can further check this with:```

> dmsetup table
Ubuntu-SwapVol: 0 8388608 linear 252:0 41945088
Ubuntu-RootVol: 0 41943040 linear 252:0 2048
Ubuntu-HomeVol: 0 435953664 linear 252:0 50333696
Ubuntu: 0 486293839 crypt aes-cbc-essiv:sha256 0000000000000000000000000000000000000000000000000000000000000000 0 8:2 4096
```

Again, there is a lack of the expected " 1 allow_discards" on the Ubuntu entry.

So, has anyone actually got this working yet? I've tried with both Raring and Saucy 64bit, and both fail in exactly the same way, so its either a long standing shortcoming, or I'm making the same mistake repeatedly :-)  Any help much appreciated!

---

### Post by molson3 on 2014-01-08
Yeah, I'm having the exact same problem and have gone through exactly what you have as well. Did you ever figure this out?

---

### Post by SixedUp on 2014-01-17
No, I can't get it to work at all. I'm short on spare time at the moment, so I'm living with it for now.
If I don't come across a solution in the meantime I'll try a complete reinstall when 14.04 comes out.

---

### Post by esokrarkose on 2014-02-13
Affects me too ... Question would be if it is a bug, because it should work, I could not find any information that would indicate otherwise

---

### Post by linux4me on 2014-02-14
I may be missing the boat here, and I am not an expert, but to get TRIM to work on an LVM/LUKS encrypted SSD I just use the regular graphic installer, select encrypted with LUKS/LVM, and then once it's done follow the steps below to enable TRIM. I apologize for not crediting the site where I got these instructions; it's been a while and I don't have the link.

After doing the regular graphical install, the first step to enable TRIM is to add the discard parameter to the file system options of the encrypted LVM volume(s) in your /etc/fstab file. (If you want to reduce writes on your SSD, you can also add the “noatime” parameter too. The former makes the file system of your LVM partition aware that you want to use TRIM. The latter prevents the extra writes for logging the access time). Here is what my line for root looks like in /etc/fstab:
```
/dev/mapper/volumegroup-root    /    ext4    discard,noatime,nodiratime,errors=remount-ro    0    1
```

That change is not enough though. As long as LUKS is not aware that you want to use TRIM it will effectively block all TRIM operations coming from the LVM partition's file system. You must add the discard parameter to the cryptdevice options in /etc/crypttab to make LUKS accept the discard behavior of the LVM partition. Edit /etc/crypttab and add the ",discard" to the end of the line so it looks like this:
```
sda5_crypt UUID=e364d03f-[...]6cd7e none luks,discard
```

Next, rebuild your initramfs. The crypttab options are stored there and used on boot. Run the following command to save the changes:
```
sudo update-initramfs -c -k all
```

Finally, you need to restart.

To test the changes, run the following command, substituting the "sda5" for your particular install:
```
sudo dmsetup table /dev/mapper/sda5_crypt --showkeys
```

If the output of the command shows a result like the following ("1 allow_discards" at the end) you're all set:
```
0  77656056  crypt  aes-cbc-essiv:sha256  abc[...]c7a0c  0  8:5  2056  1  allow_discards
```

---

### Post by SixedUp on 2014-02-18
@esokrarkose:
I think it depends on how you choose to view it. The installer doesn't support complex partitioning schemes within the LUKS container, which one could argue is working as designed. However, that forces us to workaround it by doing a lot of the setup manually around the installer, which apparently results in a system that doesn't work properly. Hard to argue that's a bug in the installer, especially as @linux4me seems to have it working by just taking the default LUKS/simple ext4 partition route through the installer :-)

On the other hand, I think I pretty much followed all the documentation (using "man" extensively as I went) for all my manual steps, so maybe it's a documentation problem? Maybe some option has been silently renamed or missed out that I don't know about, but the installer does? Again, difficult to raise a bug on that basis. Or diagnose the problem, frankly.

@linux4me:
Yes, the graphical installer can cope if you accept it's default partitioning scheme within the LUKS container. Sadly I want separate root and home partitions, which the graphical installer seemed not able to do. I tried, and I ended up tied in knots! I also want options set on my BTRFS partitions at install time to enable compression, which again, the installer cannot cope with. In the end to get what I wanted I had to set up the partitions manually, fiddle with the mount command on the live USB image (to set the right options), and then trigger the installer to use my existing partitions. It works, and shouldn't affect the install, but it's a bit messy. 

At this point I'm starting to think that the graphical installer knows something about LUKS or LVM that I don't, and has set something up differently to get a working system. To try and diagnose that, please can you post the contents of your:
/etc/crypttab
/etc/initramfs-tools/conf.d/cryptroot
/etc/lvm/lvm.conf
/etc/fstab
and
/etc/default/grub
as together this will reveal (I hope!) what is different between your setup and ours? There shouldn't be anything security-sensitive in any of those.
Thanks!

---

### Post by SixedUp on 2014-02-20
I spent some time playing around with this again last night using the latest 14.04 nightly code. 

First comment: apparently the installer can't set up a GPT partition, which was a disappointment.

I then ran a quick "default" install in LUKS/LVM to see what it does. It creates a LUKS container, which it uses as an LVM pvgroup (name is based on the partition name), into which it puts a single volume group (Ubuntu), which it uses to create a pair of logical volumes, one for swap, and one root (/). The root volume is then formatted with ext4 before the actual install starts. At the end of the install, TRIM support is not enabled; fstrim fails, and checking with "cryptsetup status Ubuntu" shows that LUKS isnt trim-friendly. To enable it, all I had to do was add ",discard" to the end of the line in /etc/cryptsetup and reboot. At that point fstrim started working on all the partitions.

I checked what was in the configuration files I've been fighting with:
/etc/crypttab:
```

sda5_crypt UUID=ffbc9735-079b-426a-a215-a1822346478b none luks,discard

```

/etc/initramfs-tools/conf.d/cryptroot:
Didn't exist. The only file that did was "resume" which didn't contain anything of interest to this.

/etc/lvm/lvm.conf:
```

issue_discards = 1

```

/etc/fstab:
```

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
/dev/mapper/ubuntu--vg-root /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=20843742-62ba-4944-b5c2-8a59ac349252 /boot           ext2    defaults        0       2
/dev/mapper/ubuntu--vg-swap_1 none            swap    sw              0       0

```

/etc/default/grub:
```

GRUB_CMDLINE_LINUX=""

```

Next I checked if it was possible to get BTRFS into a LUKS/LVM container using the installer. It isn't. If you specify manual partitioning, and add a LUKS container, then when the container is opened, the installer automatically adds LVM and gives all the space to an ext4 partition for "/" and won't let you change it in any way. Not terribly "manual".

Next I'll take a shot at manually working around the installer again, but not supplying an /etc/initramfs-tools/conf.d/cryptroot, or making any changes to /etc/default/grub ... though at the moment I don't see how that will even boot ...

---

### Post by linux4me on 2014-02-20
> **SixedUp said:**
> 
@linux4me:
Yes, the graphical installer can cope if you accept it's default partitioning scheme within the LUKS container. Sadly I want separate root and home partitions, which the graphical installer seemed not able to do. I tried, and I ended up tied in knots! I also want options set on my BTRFS partitions at install time to enable compression, which again, the installer cannot cope with. In the end to get what I wanted I had to set up the partitions manually, fiddle with the mount command on the live USB image (to set the right options), and then trigger the installer to use my existing partitions. It works, and shouldn't affect the install, but it's a bit messy. 

At this point I'm starting to think that the graphical installer knows something about LUKS or LVM that I don't, and has set something up differently to get a working system. To try and diagnose that, please can you post the contents of your:
/etc/crypttab
/etc/initramfs-tools/conf.d/cryptroot
/etc/lvm/lvm.conf
/etc/fstab
and
/etc/default/grub
as together this will reveal (I hope!) what is different between your setup and ours? There shouldn't be anything security-sensitive in any of those.
Thanks!

The machine I did that LUKS/LVM SSD install on is actually not mine, and I can't get my hands on it at the moment. Sorry! I would like to help. If I can get that info, I will post it.

---

### Post by SixedUp on 2014-02-20
> **linux4me said:**
> The machine I did that LUKS/LVM SSD install on is actually not mine, and I can't get my hands on it at the moment. Sorry! I would like to help. If I can get that info, I will post it.
Don't worry, I think I finally have it solved. I will post how I got it working next :-)

---

### Post by linux4me on 2014-02-20
Okay, great. I'm glad you got it.

---

### Post by SixedUp on 2014-02-20
So I now have this working, admittedly on a nightly build of 14.04, but I think the same procedure would work just as well on 13.04 or 13.10. There are two problems that we're trying to overcome with this method:
(a) is that the Ubuntu installer won't let you put anything other than (a single) ext4 partition and swap into a LUKS/LVM container, and
(b) is that the Ubuntu installer won't let you specify any mount options for the filesystems that it creates as part of its partitioning, making it difficult to install with compression.

What I want to achieve is a small standalone /boot partition (ext4), and swap, / (btrfs) and /home (btrfs) partitions in a LUKS/LVM container. I also want to make sure that the install is done with the partitions mounted with options of my choosing, to ensure that compression is used on the drive.

To achieve that I did a lot of reading ... everything in this post comes from information, hints, tips and advice from around the net. I just tried to pull it all together.

I installed my blank SSD into my system, and booted from a live Ubuntu installer.
When the system booted, I selected "Try Ubuntu", and brought up a command line (CTL-ALT-T)
Got to root ("sudo su")
Started gdisk against my SSD ... in my case that was "gdisk /dev/sda"
Used "o" to install a new GUID Partition Table, at an optimal alignment for the best performance of my SSD
Used "n" to create my first (/boot) partition. I took the default starting sector, "+1G" for the length, and the default "8300" Linux Partition type.
Used "n" again to create my luks partition. I took the default starting sector, ending sector, but changed the Linux Partition Type to "8e00", LVM
Used "w" to write the partition table to the disk.

Now I prepare the LUKS/LVM partitions:
```

cryptsetup luksFormat /dev/sda2
cryptsetup luksOpen /dev/sda2 Laptop
pvcreate /dev/mapper/Laptop
vgcreate Ubuntu /dev/mapper/Laptop
lvcreate -L 20G -n RootVol Ubuntu
lvcreate -L 4G -n SwapVol Ubuntu
lvcreate -l 100%FREE -n HomeVol Ubuntu

```

At this point I have the partition layout on disk that I want:
/dev/sda1 - /boot
/dev/mapper/Ubuntu-RootVol - /
/dev/mapper/Ubuntu-HomeVol - /home
/dev/mapper/Ubuntu-SwapVol - swap

It's just a matter of making the installer use it, which we can do by using the "something else" option in the partitioning part of the install. However, the installer remounts and reformats the partitions as part of the install process. So I need to make the installer mount the BTRFS partitions with the options I want (in my case, "compress-force=zlib,discard,noatime"). The trick to this is to wrap the live CD "mount" command with a script. 

So:
mv /bin/mount /bin/mount.bin
Then I paste this into a new /bin/mount:
```

#!/bin/sh  
if echo $@ | grep "btrfs" >/dev/null; then  
    /bin/mount.bin $@ -o defaults,compress-force=zlib,discard,noatime  
else  
    /bin/mount.bin $@  
fi

```
And then I make it executable with "chmod 755 /bin/mount"

Now I invoke the GUI installer, and when I get to the partitioning section, select the "something else" option. Now I select the various partitions that I have created for Ubuntu, formatting them to the appropriate filesystems. I then let the installation complete. But, when I get to the end of the installation I DO NOT REBOOT. Back in the command line, I do the following:
```

mount -t btrfs -o compress-force=zlib,discard,noatime,subvol=@ /dev/mapper/Ubuntu-RootVol /mnt
mount /dev/sda1 /mnt/boot
mount --bind /dev /mnt/dev
chroot /mnt
mount -t proc proc /proc
mount -t sysfs sys /sys
mount -t devpts devpts /dev/pts

```

Then I get the UUID of the LUKS container with "blkid /dev/sda2" ... say 1111xxx1111

I then create /etc/crypttab:
```

Laptop    UUID=1111xxx1111    none   luks,discard

```

I make sure that "issue_discards = 1" in /etc/lvm/lvm.conf (seems to be the default in 14.04, but not before that)

I then update /etc/fstab with the mount options that I want for my BTRFS partitions. In my case, since I intend to use fstrim rather than have the filesystem continually sending trim requests for every deletion, the options I want are "defaults,noatime,compress-force=zlib" plus the appropriate subvol mount information that should already be there. No need for "discard" here for me.

Then I can issue "update-initramfs -c -k all" and "reboot" ... apparently no need to mess with grub. Indeed, doing so may be why this didn't originally work for me. When the system comes back up I am now able to successfully issue "sudo fstrim -v" commands against all my partitions.

Hope this helps someone else.

---

### Post by Strike0 on 2014-03-16
Hi Richard, 

great guide that you put together, it all being quite an effort! I am very certain this will help a lot of other users. 

I just read it and want to jot a couple of thoughts: First, I am wondering whether the hack you do with "mount.bin" is required. It should not be - in fact you should be able to turn on/off trim via a reboot by editing crypttab/fstab options (and likely updating initramfs afterwards). So you should be able to follow your install procedure without that step and just add trim later That is standard behaviour. I would suspect that the main reason lies in the 14.04 packages/installer. 

I checked launchpad on the issue and want to add a reference: In [https://blueprints.launchpad.net/ubuntu/+spec/core-1311-ssd-trimming](https://blueprints.launchpad.net/ubuntu/+spec/core-1311-ssd-trimming)
the Ubuntu team is tracking advances to trim for 14.04. Maybe you want to track that and/or add a link to your test install experiences, as it might help them! 

That blueprint is triggered by: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1244504](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1244504)

And, anecdotal, when I searched I also saw: [https://bugs.launchpad.net/ubuntu/+source/debian-installer/+bug/988542](https://bugs.launchpad.net/ubuntu/+source/debian-installer/+bug/988542)
where "TRIM" is put to wishlist by Mark Shuttleworth himself stating it should be default. So you're in good company! 

Thanks. 

Regards,
Strike0

---

### Post by SixedUp on 2014-03-21
> **Strike0 said:**
> Hi Richard, 
great guide that you put together, it all being quite an effort! I am very certain this will help a lot of other users. 

Thanks :-)

> 
I just read it and want to jot a couple of thoughts: First, I am wondering whether the hack you do with "mount.bin" is required. It should not be - in fact you should be able to turn on/off trim via a reboot by editing crypttab/fstab options (and likely updating initramfs afterwards). So you should be able to follow your install procedure without that step and just add trim later That is standard behaviour. I would suspect that the main reason lies in the 14.04 packages/installer. 

You don't need the mount hack for the Trim support; what I needed it for was to get the installer to mount the BTRFS partitions with compression enabled. It saves me a few GB in the root partition at the time of installation. I suspect I could add compression afterwards, but this seemed to be the "simple" way to achieve what I wanted.

> 
I checked launchpad on the issue and want to add a reference: In [https://blueprints.launchpad.net/ubuntu/+spec/core-1311-ssd-trimming](https://blueprints.launchpad.net/ubuntu/+spec/core-1311-ssd-trimming)
the Ubuntu team is tracking advances to trim for 14.04. Maybe you want to track that and/or add a link to your test install experiences, as it might help them! 

Thanks for the pointer. I will take a look.

> 
That blueprint is triggered by: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1244504](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1244504)

And, anecdotal, when I searched I also saw: [https://bugs.launchpad.net/ubuntu/+source/debian-installer/+bug/988542](https://bugs.launchpad.net/ubuntu/+source/debian-installer/+bug/988542)
where "TRIM" is put to wishlist by Mark Shuttleworth himself stating it should be default. So you're in good company! 
Thanks. 
Regards,
Strike0

Interesting. The problem with making it the default is what default do you choose? To allow the filesystem to issue TRIM on each delete (permanent but hopefully small performance hit) or set up some sort of background cron job to issue occasional fstrim commands, that will potentially cause infrequent but unpredictably large performance hits? No simple answers until we get a queueable ATA TRIM command in SATA 3.1 I suspect.

Still it would be nice to get the underpinnings in place so there is minimal effort for the user to choose one or the other approach themselves in the meantime.

---

### Post by Strike0 on 2014-03-31
> **SixedUp said:**
> The problem with making it the default is what default do you choose? To allow the filesystem to issue TRIM on each delete (permanent but hopefully small performance hit) or set up some sort of background cron job to issue occasional fstrim commands, that will potentially cause infrequent but unpredictably large performance hits? No simple answers until we get a queueable ATA TRIM command in SATA 3.1 I suspect.
To my understanding the way you set it up should be the preferred for now anyway. First of all the actual TRIM (and overhead), triggered by the filesystem mount options or fstrim, is done by the drive's firmware anyway. Having a cron job would only make sense on a server to my understanding. Simply because the drive does not keep a table of already trimmed blocks. So what happens when you use fstrim manually is that the drive zeroes empty space. But if you reboot, that information mapping is gone. Hence, when a cron job jumpstarts fstrim again after a reboot, all empty space has to be re-considered. It is easy to verify, just execute something like ```
# time fstrim -v /home
```note the number of blocks it trimmed, reboot and time it again. By using it as a mount option, on the contrary, each block gets trimmed once it gets freed up. Hence, no double effort after a reboot. 

Regards, 
Strike0

---

### Post by K.R.O.N.I.K on 2014-11-05
[deleted]

---

