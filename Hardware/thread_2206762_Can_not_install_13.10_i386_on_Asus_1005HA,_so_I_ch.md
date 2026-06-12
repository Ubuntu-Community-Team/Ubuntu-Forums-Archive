---
title: "Can not install 13.10 i386 on Asus 1005HA, so I cheated!"
date: 2014-02-20
forum: Hardware
---

### Post by sdenham on 2014-02-20
Ubuntu Team,

My adventure began when I decided to create my own web server with a spare netbook I had laying around (Server with built in UPS!!).  I was playing around with the 13.10 LiveCD and decided that it was a bit too laggy.  I then downloaded 14.04 Alpha 2 and installed it.  Everything went fine.  Spent a few days with it and decided that the GUI was still a bit laggy and not needed for a headless server.  So I wiped it and decided to install Server 13.10 i386.  I get through the partition manager, it copies system files, downloads some files, and then the step where it would confirm writing GRUB to the MBR causes an MCE Hardware Error.  Hours upon hours of web crawling/trial and error had me thinking my little netbook had seen it's last days.  I even tried a couple other Debian based distros to the same effect (and same spot).  Tried new RAM, new HDD (not easy), new BIOS, and still had the same problem.  It just bugged me that I could install Windows just fine and it run stable.  I could use the LiveCD just fine.  I atleast narrowed it down to writing GRUB to the MBR...

I have been using Virtual Box a ton lately for testing pfSense configurations and I had a Greek epiphany.  Why not install Server on a 40GB VBox with LVM and then do a HDD clone to my netbook?  Seemed a bit crazy.  I wasn't even sure it would work from behind a virtualized system.  With nothing to lose and a netbook to gain/keep, I tried it. 

Step 1:
Create VBox with my external HDD as a shared folder.
Install Ubuntu Server 13.10, apt-get update, upgrade, and dist-upgrade.

Step 2:  Install VBox Guest Additions
Attach the install iso (under Devices menu in VBox)

```

sudo apt-get install build-essential dkms linux-headers-`uname -r` pv
sudo mount /dev/cdrom /media/cdrom
sudo sh /media/cdrom/VBoxLinuxAdditions.run
sudo usermod -G vboxsf [username]
sudo shutdown -r now

```

**Note** The 'pv' package is optional.

Step 3:  Create disk image

Since I wanted to see a progress bar on the disk clone, I installed a package called 'pv'.  In order to get an accurate time measurement on how long the copy would take, I needed to know exactly how large the image was going to be.  So I got the size of the disk like this:

```

user@ubuntu:~$ sudo parted
(parted) unit B
(parted) print
Model: ATA Blahblahblah (scsi)
Disk /dev/sda: 1234567890B           <---- This is the size of the drive in bytes, I later realized mine was exactly 40GB
Sector size (logical/physical): 512B/512B
...

(parted) quit

```

You can use bytes, kilobytes, etc with pv.  I ended up using '40g' for 40GB. Now to create the image! **Note** I used an external drive formatted to NTFS.  You can not use FAT32 if your disk image is over 4GB in size!  Not a problem in my case since the LiveCD can mount NTFS just fine.
```

sudo dd if=/dev/sda | pv -s 40g | dd of=/media/sf_ExternalDrive/ubuntu-server.img bs=1M conv=notrunc,noerror

#Without pv:
sudo dd if=/dev/sda of=/media/sf_ExternalDrive/ubuntu-server.img bs=1M conv=notrunc,noerror

```

Or for a much much smaller file (came out to about 1GB compressed for me) and only takes a few more minutes:
```

sudo dd if=/dev/sda | pv -s 40g | gzip -c /media/sf_ExternalDrive/ubuntu-server.img.gz bs=1M conv=notrunc,noerror

#Store HDD Geometry just in case:
sudo fdisk -l /dev/sda > /media/sf_ExternalDrive/sda_fdisk.info

#Without pv:
sudo dd if=/dev/sda | gzip -c /media/sf_ExternalDrive/ubuntu-server.img.gz bs=1M conv=notrunc,noerror

```

Step 4: Extract the image on my netbook
I booted into my LiveUSB, installed pv, and connected my external drive.  Once the drive was detected, I issued one command in the terminal and went to go have a cup of joe.
```

sudo apt-get install pv

#If you didn't use GZip:
sudo dd if=/media/UUIDofMyExternalDrive/ubuntu-server.img | pv -s 40g | dd of=/dev/sda bs=1M conv=notrunc,noerror

#Without pv:
sudo dd if=/media/UUIDofMyExternalDrive/ubuntu-server.img of=/dev/sda bs=1M conv=notrunc,noerror

#If you used GZip:
sudo gunzip -c /media/UUIDofMyExtDrive/ubuntu-server.img.gz | pv -s 40g | dd of=/dev/sda

#Without pv:
sudo gunzip -c /media/UUIDofMyExtDrive/ubuntu-server.img.gz | dd of=/dev/sda

```

Then I unmounted my External Drive, removed my LiveUSB, and rebooted into a fresh install of Ubuntu Server i386 with current patches. :D  I have no idea why I couldn't install from CD, DVD, or LiveUSB on my netbook, but there's more than one way to do things.  I grabbed all this information over 2-3 days of searching Google.  I don't remember all site sites I visited for this knowledge but I would like to give some thanks to the ArchLinux Wiki for the good tips with "dd".  I hope this might help someone else in the future.

If there is anything critical I missed, please don't hesitate to point it out.  I'm still rather new to this and not sure how safe this proceedure is going to be for my web server.  Luckily it's not a business site, so I'm not too concerned if it crashes and burns.

Regards,
Steve

---

