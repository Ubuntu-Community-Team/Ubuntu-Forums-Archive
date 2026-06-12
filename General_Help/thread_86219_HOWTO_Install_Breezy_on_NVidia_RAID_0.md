---
title: "HOWTO Install Breezy on NVidia RAID 0"
date: 2005-11-04
forum: General Help
---

### Post by MiddleBrooker on 2005-11-04
Hi to all,
after some experience in Gentoo installation I'm writing this HOWTO from my Ubuntu System installed in a Shuttle XPC with TWO Serial ATA Disk in RAID 0 Configuration.
Normally Ubuntu was not able to detect correctly the RAID Stripe from the BIOS so I've used an alternative method to install my favourite distro in my system without leave out the RAID 0 settings; now I'm happy to share my experience with all the members of the forum and I hope in some feedback or suggestion from user much more expert than me :smile:
PS: Sorry for my English!!
 
A special thanks to this [http://gentoo-wiki.com/HOWTO_Install_Gentoo_with_NVRAID_using_dmraid]("http://gentoo-wiki.com/HOWTO_Install_Gentoo_with_NVRAID_using_dmraid") HOWTO from the Gentoo Wiki.

OK, for install Ubuntu on our NVRAID 0 Stripe we need to:

1) Download the Gentoo LiveCD that is able to detect correctly the RAID 0 setup from the BIOS - Download it from here ---> [http://gentoo.osuosl.org/releases/]("http://gentoo.osuosl.org/releases/");

2) Preare an external USB disk or a normal IDE disk to install Ubuntu as the usual method;

My RAID disk have the first little partition as /boot and the second partition as / (ROOT).
```

#root@Mbrooker:~# ls /dev/mapper/
#control
#nvidia_bigjabae
#nvidia_bigjabae1
#nvidia_bigjabae2

```

We're going to install the basicall Ubuntu system into a normal USB or IDE disk and after that we'll copy all the installed system into our NVRAID Stripe (composed of both TWO SATA disks) by using the Gentoo LiveCD; after that we'll work on some system files to get GRUB - DMRAID etc... working correctly during the booting process.

I've installed Ubuntu as the usual method into the normal USB or IDE disk BUT REMEMBER TO DON'T INSTALL GRUB because this grub will not work with your RAID disk, after that I've made the boot with the Gentoo LiveCD and this command at the initial prompt:
```
#gentoo dodmraid
```

First of all be sure to have your internet connection working so run net-setup eth0 and follow the wizard to setup your ethernet card.
Now you should be able to see correctly your RAID partitons under /dev/mapper :
```
#ls /dev/mapper/
```

You should see something like: nvidia_bigjabaeX (nvraid) or sil_XXXXX, depend from your RAID controller.
We can partition the disk via the usual fdisk command:
```
#fdisk /dev/mapper/nvidia_bigjabae
```
[!!!] Please note that if you're partitioning for the first time you must reboot the system and re-run the Gentoo LiveCD for see the new partitions. [!!!]

After that we can mount both Ubuntu disk and the New RAID partition:
```

#mkdir /mnt/Ubuntu_IDE
#mkdir /mnt/Ubuntu_RAID
#mount /dev/hdX /mnt/Ubuntu_IDE
#mount /dev/mapper/nvidia_bigjabae2 /mnt/Ubuntu_RAID
#copy -r /mnt/Ubuntu_IDE/* /mnt/Ubuntu_RAID
#mount /dev/mapper/nvidia_bigjabae1 /mnt/Ubuntu_RAID/boot

```

Now we can remove the temporary IDE, USB and chroot the RAID Ubuntu, so start to tune it:
```
#chroot /mnt/Ubuntu_RAID /bin/bash
```

OK, now we are into the RAID Ubuntu system by the Gentoo LiveCD Kernel; the next part of the HOWTO will let you know how to install Grub and boot the system into your RAID disk.
We need a correctly compiled kernel, so download and build it.
Be sure to add STATICALLY (not as Module) into the kernel configuration all the necessary for your RAID controller and for the RAID support:
```

#
# SCSI device support
#
CONFIG_SCSI=y
# CONFIG_SCSI_PROC_FS is not set

#
# SCSI support type (disk, tape, CD-ROM)
#
CONFIG_BLK_DEV_SD=y
# CONFIG_CHR_DEV_ST is not set
# CONFIG_CHR_DEV_OSST is not set
# CONFIG_BLK_DEV_SR is not set
CONFIG_CHR_DEV_SG=y
# CONFIG_CHR_DEV_SCH is not set

#
# SCSI low-level drivers
#
CONFIG_SCSI_SATA=y
# CONFIG_SCSI_SATA_AHCI is not set
# CONFIG_SCSI_SATA_SVW is not set
# CONFIG_SCSI_ATA_PIIX is not set
CONFIG_SCSI_SATA_NV=y
# CONFIG_SCSI_SATA_PROMISE is not set
# CONFIG_SCSI_SATA_QSTOR is not set
# CONFIG_SCSI_SATA_SX4 is not set
# CONFIG_SCSI_SATA_SIL is not set
# CONFIG_SCSI_SATA_SIS is not set
# CONFIG_SCSI_SATA_ULI is not set
# CONFIG_SCSI_SATA_VIA is not set
# CONFIG_SCSI_SATA_VITESSE is not set

#
# Multi-device support (RAID and LVM)
#
CONFIG_MD=y
CONFIG_BLK_DEV_MD=y
# CONFIG_MD_LINEAR is not set
CONFIG_MD_RAID0=y
# CONFIG_MD_RAID1 is not set
# CONFIG_MD_RAID10 is not set
# CONFIG_MD_RAID5 is not set
# CONFIG_MD_RAID6 is not set
# CONFIG_MD_MULTIPATH is not set
# CONFIG_MD_FAULTY is not set
CONFIG_BLK_DEV_DM=y
CONFIG_DM_CRYPT=y
CONFIG_DM_SNAPSHOT=y
CONFIG_DM_MIRROR=y
CONFIG_DM_ZERO=y
CONFIG_DM_MULTIPATH=y
CONFIG_DM_MULTIPATH_EMC=y

```

Using the chrooted system you'll be able to install via apt-get all the necessary packages to build your kernel via dpkg-buildpackage.
To do this remember to set your internet connection via the Gentoo LiveCD.
After that install the kernel package and don't reboot the system.

Install Grub
```

#apt-get install grub

```

Now I've attached to this thread the dmraidinitrd script (from the gentoo Wiki) to create an image for boot correctly the system.
I've edited it because one link is missing and the package is no longer available (remove the .txt extension from it).
```

apt-get install libselinux1 libselinux1-dev
#wget http://tienstra4.flatnet.tudelft.nl/~gerte/gen2dmraid/linuxrc
#chmod +x dmraidinitrd
#./dmraidinitrd linuxrc initrd
#cp linuxrc /boot
#cp initrd /boot

```

Now make sure you have the kernel image into the /boot directory or the classic vmlinuz link, so lets go to grub configuration:
```

#vi /boot/grub/grub.conf

```

```

title Ubuntu
root (hd0,0)
kernel /vmlinuz-2.6.12 root=/dev/ram0 init=/linuxrc real_root=/dev/mapper/nvidia_bigjabae2
initrd (hd0,0)/initrd

```
[!!!]Remember to append the real_root option to specify your real root device from the device mapper[!!!]

We can install grub as reported in the Gentoo wiki page:
Do not run grub-install! It will not work properly, and will probably detect the sda1, etc. instead of your actual raid. Make also sure not to start grub inside of an chroot enviroment like you propably do if you install from the Gentoo LiveCD and do it like described in the installation manual of gentoo.org. It doesn't know about /dev/mapper so you would get some errors with grub. In this case just jump into another terminal with ALT+F2. Start grub and make sure that it's pointing to /dev/null as a device map.
```

#grub --device-map=/dev/null

```

```

grub> device (hd0,0) /dev/mapper/nvidia_bigjabae1
grub> device (hd0) /dev/mapper/nvidia_bigjabae
grub> root (hd0,0)
grub> setup (hd0)
grub> quit

```


FINISH!!!
You should be able to reboot and select the Ubuntu System installed into your RAID disk, it should be boot up correctly and you can enjoy your RAID 0 system.

Please send to me via this thread some feedbacks or opinions regarding this HOWOT I'll be very happy to have any other suggestion!
Regards,

MiddleBrooker

---

### Post by poptones on 2005-11-04
FWIW, installing an operating system (and making your primary operating partition) a RAID0 drive is a seriously bad idea if you care AT ALL about your data. RAID0 *doubles* your chances of losing data to a hard drive falure.

after losing gigabyte after gigabyte I went to a RAID5 solution and couldn't be happier. In fact, my NEW Seagate started acting up a couple weeks ago and is now off at the repair shop as I type this, yet I still have access to all my data becuase it was one disk of three. So long as I don't have a SECOND disk fail in the next couple of days...

If I had been using a RAID0, I would have essentially lost everything on *all* the drives as soon as that one failed.

---

### Post by MiddleBrooker on 2005-11-04
[QUOTE=poptones]FWIW, installing an operating system (and making your primary operating partition) a RAID0 drive is a seriously bad idea if you care AT ALL about your data. RAID0 *doubles* your chances of losing data to a hard drive falure.

after losing gigabyte after gigabyte I went to a RAID5 solution and couldn't be happier. In fact, my NEW Seagate started acting up a couple weeks ago and is now off at the repair shop as I type this, yet I still have access to all my data becuase it was one disk of three. So long as I don't have a SECOND disk fail in the next couple of days...

If I had been using a RAID0, I would have essentially lost everything on *all* the drives as soon as that one failed.[/QUOTE]

Hi,
I know all the risk and the various RAID Mode, I've always used RAID 0 without lose any datas, maybe I'm lucky because I know that the failure of only one disk cause the loosing of all the datas, but actually I can only make a Stripe or a Mirror with only two disk.
Tha RAID 5 Mode require a minimum of three disks and one complete disk will be take for data security, of course is much more safely of the RAID 0.
In my modest opinion is simply a choice and I think that the installation method proposed in this thread can be applied to a RAID 5 Mode too.

Are you using Ubuntu into your sistem, if yes I would like to know how do you have installed it into the RAID 5 ?

Thank you very much.

---

### Post by poptones on 2005-11-04
I do not have the system itself on a RAID, however I do **encrypt** just about everything. I do not use a /boot partition, I just install everything into a small (2GB) partition and then use a larger (presently 3GB, though that will revert to 10GB when my failed drive returns) partition for everything above /

My install process goes thusly:

During install, tell the system to install to TWO partitions. One is /, the other is mount to /usr

Once system is up and running, install cryptsetup from synaptic (this really should be on the CD)

init 2 (go to single user command line mode)

fuser -k /usr - kill all processes still linked to /usr
umount /usr

cryptsetup create -y usr /dev/**usrpartition**
*enter password*
*enter password again to confirm*

dd if=/dev/**usrpartition** of=/dev/mapper/usr bs=1024k

*wait....*

/usr is now encrypted. 

mount -t reiserfs /dev/mapper/usr /usr

This is the fun part...

mv /home /usr
mv /root /usr
mv /opt /usr
mv /srv /usr
mv /tmp /usr
mv /var /usr

Now everything above the root level is in the encrpypted /usr partition...

ln -s /usr/var /var
ln -s /usr/home /home
ln -s /usr/root /root
ln -s /usr/opt /opt
ln -s /usr/srv /srv
ln -s /usr/tmp /tmp

Now edit /etc/fstab and change the /dev/**usrpartition** entry to /dev/mapper/usr and tell /etc/crypttab to mount /dev/**usrpartition**

echo "usr /dev/**usrpartition**" > /etc/crypttab

All userspace data is now encrypted. All that remains is swap. I used to use a separate swap partition, but because swap is used so little I now just make a swap partition in a loopback file

This will make a 255MB file called "swap.img" in root

dd if=/dev/zero of=/swap.img bs=1024k count=255

Then tell /etc/crypttab to mount it on boot using a random encryption key...

echo "swap /swap.img /dev/urandom swap" > /etc/crypttab

And tell fstab to mount it...

echo "/dev/mapper/swap swap swap" > /etc/fstab

The RAID5, once installed and setup, is detected *automatically* on every reinstall. There's nothing to do after the initial creation. It is created using mdadm tools, and these tools put information on the discs themselves about membership in a RAID. So every time I rebuild the system using ubuntu, even without doing anything at all, on the first boot I see information passing by "RAID5 /dev/md0 mounted using 2 discs out of 3." When all the discs are in place, of course, I get "3 discs out of 3" and I do not mount it read-only (you can mount a degraded raid5 r/w, but better safe than sorry).

```

$ cat /proc/mdstat
Personalities : [raid5]
md0 : active raid5 hda1[1] hdb1[2]
      295001344 blocks level 5, 128k chunk, algorithm 2 [3/2] [_UU]

unused devices: <none>

```

Because this is built into the kernel, if you are using ubuntu I suspect there would be nothing at all to installing directly to this raid. I haven't tried it, but I know the raid is there even in the installer if I select it from the list of options. Because it is there at install time, one would only have to point the installer there and go. Of course you would still need a /boot partition somewhere.

Creating the RAID5 was pretty easy. Just create equally sized partitions on the three drives, make sure the partition type is "fd," tell mdadm to look for them and tell it the kind of raid you want...

mdadm --create /dev/md0 --level=5 --raid-devices=3 /dev/hd[acd]1

Create /dev/md0 as a raid5 using /dev/hda1, hdc1, and hdd1

So far as I know, you could even do this from the live cd - ie fdisk 3 drives, leave only a small 100MB /boot space free on them, use the command above to make them a raid, then reboot from the install cd and there you go. The other two small 100MB partitions on the other (non /boot) drives could be used to stripe 200MB of swap space. A better way would, of course, be to partition the cluster into multiple md arrays - so you could have a /dev/md0 of maybe 2GB (one GB on each disk), a /usr space of 8GB (4GB on each disk), and partition the rest for general purpose storage. Once they're created they will persist (at least to ubuntu) so long as you never overwrite their partition info. 

All the HOWTOs out there are really complicated and use raidtools then they start talking about mdadm. Most of that stuff is not needed - mdadm does quite a lot automatically and has been rock sold for me for many months. All that remains is to see how it behaves when my failed drive returns and I get to add it back...

---

### Post by poptones on 2005-11-04
BTW thanks for this discussion. While I don't use the RAID the way you describe, I now will be strongly considering repartitioning my drives when the failed one returns and installing the whole system on RAID5 partitions. I was using the failed Seagate as my "system disk" before it failed and having the system on that one drive when it started going bad caused me all sorts of headaches. So, if you *really* want to know how it goes, remind me here in about two weeks and I'll let you know :)

---

### Post by MiddleBrooker on 2005-11-05
[QUOTE=poptones]BTW thanks for this discussion. While I don't use the RAID the way you describe, I now will be strongly considering repartitioning my drives when the failed one returns and installing the whole system on RAID5 partitions. I was using the failed Seagate as my "system disk" before it failed and having the system on that one drive when it started going bad caused me all sorts of headaches. So, if you *really* want to know how it goes, remind me here in about two weeks and I'll let you know :)[/QUOTE]

Thanks for your comments but from your first post I've understood that your system is based on a RAID Controller that can be the RAID 5 Mode too; I know that with your setup there's no problems during the installation and a final good data security level, but I think that the performace are lowest than a RAID 5 setup owned by a dedicated hardaware controller, please post your:

```
hdparm -tT
```

result.

I've made the HOWTO just for help in the Ubuntu installation on a physical RAID controller , the mirroring, striping or both with RAID 5 or other levels is not important because I think that with this method is possible to install gentoo on these hardware configuration.

Thank you very much.
Regards,

MiddleBrooker

---

### Post by poptones on 2005-11-05
My posting those tests would tell you nothing. You d not know what types of hard drives I have, what sort of controller or even what kinds of cables I am using in my system, all of which will affect throughput.

I also cannot run an hdparm on my raid right now because, as I said, it is presently degraded while the missing disk is at seagate's warranty shop. Not only would the test not be accurate, I am not going to run a read/write test on a degraded array.

A RAID0 has absolutely zero reliability when compared to a RAID5, and RAID5 hardware controllers are still substantially more complex - that's why your motherboard only support 0 and 1 - so comparing my numbers to yours would be completely apples and oranges. Also, as I pointed out I am using *encrypted* partitions and with an AMD cpu and that encryption has its own performance hit that is substantially greater than the simple XOR operations required by a RAID5 process. I will point out, however, that I have never maxed out my CPU while performing large file copies between RAID arrays, even when I was copying from (encrypted) RAID5 to (encrypted) RAID0. The test reports I have seen over the years have almost always shown software RAID5 controllers to beat all but the most expensive hardware controllers - there's a lot of horsepower in today's CPUs and those dedicated controllers are usually based on some low power embedded risc chip. 

My goal has been security and reliability. I have lost far too much time and date over the years to unreliable configurations and I trust a software RAID far more than I would trust essentially proprietary algorithms embedded in hardware controllers. I can put my disks in any system running a 2.6 kernel and mdadm and not have to worry about compatability... or about losing all my data because of a single drive failure.

I'm sure your howto will be appreciated. I'm only making the point that trusting your data to a raid0 array is actually WORSE than just putting it on two large drives without the interleave. If you need the performance for video capture or something that's understandable, but most folks here aren't going to be doing that - and it sucks terribly to lose a few years worth of MP3s. Raid1 is better but uses twice the power and generates twice the heat; making a raid5 from 3 or 4 discs is a convenient, relatively low power, and reliable tradeoff.

---

### Post by Silverblade on 2006-03-20
Hi, i found your guide very usefull, but i have a problem in the steps.
i arrive here:

Now I've attached to this thread the dmraidinitrd script (from the gentoo Wiki) to create an image for boot correctly the system.
I've edited it because one link is missing and the package is no longer available (remove the .txt extension from it).

Because the link is broken:
#wget [http://tienstra4.flatnet.tudelft.nl/~gerte/gen2dmraid/linuxrc](http://tienstra4.flatnet.tudelft.nl/~gerte/gen2dmraid/linuxrc)

Can you help me?
bye

---

### Post by MiddleBrooker on 2006-03-20
Hi,
if the script fail, I suggest you to install the Gentoo Grub by making the steps that you can find here: []("http://gentoo-wiki.com/HOWTO_Install_Gentoo_with_NVRAID_using_dmraid")

So you'll have a working grub, please note that you have to install the basic Gentoo for doing this, the operation should not be so long!

After that you can safely format the Gentoo partition and copy the Ubuntu files according to the previous howto.

Basically I'm using the gentoo Grub with Ubuntu, I've already tested this, for me 100% working.

Please let me know if you have any problems.

Hope this help.
Regards,

MB

---

### Post by Silverblade on 2006-03-31
Hi


We can install grub as reported in the Gentoo wiki page:
Do not run grub-install! It will not work properly, and will probably detect the sda1, etc. instead of your actual raid. Make also sure not to start grub inside of an chroot enviroment like you propably do if you install from the Gentoo LiveCD and do it like described in the installation manual of gentoo.org. It doesn't know about /dev/mapper so you would get some errors with grub. In this case just jump into another terminal with ALT+F2. Start grub and make sure that it's pointing to /dev/null as a device map.
Code:

#grub --device-map=/dev/null



I don't understand this step and i have problem when using 
#grub --device-map=/dev/null
so that bash grub say that the string is not legal

---

### Post by MiddleBrooker on 2006-04-02
[QUOTE=Silverblade]Hi


We can install grub as reported in the Gentoo wiki page:
Do not run grub-install! It will not work properly, and will probably detect the sda1, etc. instead of your actual raid. Make also sure not to start grub inside of an chroot enviroment like you propably do if you install from the Gentoo LiveCD and do it like described in the installation manual of gentoo.org. It doesn't know about /dev/mapper so you would get some errors with grub. In this case just jump into another terminal with ALT+F2. Start grub and make sure that it's pointing to /dev/null as a device map.
Code:

#grub --device-map=/dev/null



I don't understand this step and i have problem when using 
#grub --device-map=/dev/null
so that bash grub say that the string is not legal[/QUOTE]

Sorry SilverBlade for the dealy in reply, I've saw only now that my previous post don't have the link address, this one [http://gentoo-wiki.com/HOWTO_Install_Gentoo_with_NVRAID_using_dmraid](http://gentoo-wiki.com/HOWTO_Install_Gentoo_with_NVRAID_using_dmraid)

I suggest to install grub via Gentoo if the script fail becuase this method is 100% working and after that the gentoo partition can be safely deleted or content replaced with the ubuntu files as I've described into the first post.

Are you working on SATA raid0 now?

Regards,

MB

---

### Post by Khannie on 2006-05-16
Just wanted to say thanks to the OP for posting this. Mods: Maybe move this to the [installation forum](http://www.ubuntuforums.org/forumdisplay.php?f=94)? I searched in there and couldn't find anything similar (and ended up posting [this](http://www.ubuntuforums.org/showthread.php?t=177337) thread).

---

### Post by Eddy5 on 2006-05-19
I'm really struggling to get this to work (I'm a but of a Linux newbie anyway).
I've managed to get to running the dmraidinitrd script but it keeps falling over because all the package names have changed because they've been updated. I've updated the names in for busybox and dmraid in the top of the dmraidinitrd script to reflect the 1.01 release of busybox and the rc10 version of dmraid, but it just keeps falling over because I think some other files are using the old links. I have no clue which ones these are yet.
Also I'm not sure what to do with the code snipper listing all the SCSI devices.

Has anyone done this installation recently?
I am trying to install Kubuntu, could this have a bearing on my issues?
Any help would be most appreciated.

---

### Post by kosharj on 2006-05-21
[QUOTE=poptones]FWIW, installing an operating system (and making your primary operating partition) a RAID0 drive is a seriously bad idea if you care AT ALL about your data. RAID0 *doubles* your chances of losing data to a hard drive falure.

after losing gigabyte after gigabyte I went to a RAID5 solution and couldn't be happier. In fact, my NEW Seagate started acting up a couple weeks ago and is now off at the repair shop as I type this, yet I still have access to all my data becuase it was one disk of three. So long as I don't have a SECOND disk fail in the next couple of days...

If I had been using a RAID0, I would have essentially lost everything on *all* the drives as soon as that one failed.[/QUOTE]

The *data* drive is where you might need, or benefit from, raid1+.  I've always found that raid 0 is much more satisfying for the price for operating systems.  Raid 1 over raid 0?  Why sacrifice 1/2 or you drive space and 1/3 speed?  An operating system is so static and it so often, for whatever reason, may need to be reinstalled anyway (Windows or, yes, Linux, too). 

I typically get my operating system installed, and then create and burn an image of it immediately.  As I find programs I like, or configuration changes I want, I maintain a list of todo for the next image.  Then at some point, I take my pristine image, restore it, install/change what I want, and then immediately burn an image of the new improved system.  This means you always have a clean image (ever free of malware) with all configuration changes and software already installed.

Save the Raid0,5,kitchen sink for the data drives.  Run the OS off of Raid 0 SATA.:-)  You're sacrificing speed and space for an event that is likely not to happen more than once in 5 years in which time you are more likely to install/reinstall your operating system 3 times because it's so much fun(or because you own Windows.

---

### Post by JimMurple on 2006-05-30
Hi all,

Does this procedure valid to install Ubuntu in the following configuration ???

MB A7N8X Deluxe :

2 80Go DD in Raid 0 mode with Sil3112a controller (yes Fake Hardware Raid I know but it works correctly with Windows) so 160Go Raid 0 with.

Part 1 : 40 Go NTFS with Windows XP installed

Part 2 : 120 Go NTFS => to be broken to welcome Ubuntu partition (/, /home and swap).

Note : I'm totally newbie in Linux environment. 

I look information up to install Linux as describe above but no solution. I feel that it will not possible.

Will the next version of Ubuntu recognize Hard/Soft Raid 0 controlers ?????

Thanks in advance and best regards. 

:confused:  :confused: :confused: :confused: :confused:

---

### Post by BoneKracker on 2006-06-01
Have you looked at the HowTo that already exists?
[https://wiki.ubuntu.com/FakeRaidHowto](https://wiki.ubuntu.com/FakeRaidHowto)

That approach:
- does not require a CD from another distribution
- does not require an additional disk outside the RAID
- does not require kernel configuration and compiling

I'm sure it could be greatly improved, and I don't know if it works with 6.06 (people say it does), but maybe combining your knowledge with what's there, and improving that HowTo would be the most useful thing for people.

---

### Post by DJMatty on 2007-03-22
Hi

I have been trying for the last week or so to get Ubuntu installed on my 680i mobo with nvraid... unsuccessfully :(

Tried all combinations of the how-tos and posts I have found, I am using feisty though as I did read that there were issues with some of the other chipset features.

I have managed to get a working install on a regular SATA drive in my PC (although for some reason it only booted if it was at the start of the partition list on my drive, I had originally got 3 small partitions for booting xp vista and other stuff, and ubuntu would just not boot properly, after numerous attempts from live cd and alt)

However I had recently found another how-to that I was trying, and also just found your post. Now I have a working install I think I will attempt to copy it from SATA to raid...

I am a n00b at Linux, so can someone confirm, will I just need to modify the fstab file to list my /dev/mapper partitions instead of the /dev/sda ones? Or is there more to it than this?

Thanks

Matt

---

### Post by DJMatty on 2007-03-22
Well i have found out there is more to it than that... there's all that security stuff to think about...

Darn!

Is there any way to move over the users and also the owners of the files that have been copied?

Matt

---

### Post by BoneKracker on 2007-03-23
I haven't done an nvraid install with Ubuntu since I last contributed to that wiki article, so everything I know that's of any value is in there.

---

### Post by DJMatty on 2007-03-23
OK thanks...

I guess it's not specifically about nvraid anymore, that bit is working fine, I can boot from my raid array to the copied system, it just doesn't work because there are no users in the system, and the files owners and attribs aren't set up properly.

I'll post a question in the install bit about this.

Thanks

Matt

---

### Post by DJMatty on 2007-03-23
After looking at the man pages for 'cp' I am wondering if the -a switch would allow the copy of the root to the new drive to keep all the owner and attrib information?

I'll give it a try tonight and see what happens.

is the 'copy' command different to 'cp'? The original how-to says to use the 'copy -r' to copy the files from the IDE to the RAID drives, i used 'cp -r' last night to do this and when it boots it moans about owners of files not being right.

Also do you think I would need to chroot to the just copied raid root and make new users in there or would the copy preserve the ones from the IDE install?


Matt

---

