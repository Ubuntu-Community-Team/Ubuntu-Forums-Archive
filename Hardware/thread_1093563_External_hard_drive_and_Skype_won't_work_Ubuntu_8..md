---
title: "External hard drive and Skype won't work Ubuntu 8.10 on"
date: 2009-03-11
forum: Hardware
---

### Post by senevene on 2009-03-11
Hello,

I am completely ignorant of computers (which means that I have absolutely no clue what the following texts that I am pasting in this message mean...yeah...too bad for me, I know) so hope to get some help. I have problems with Ubuntu not reading my external hard drive (Maxtor), where I have all the files I had before I installed Ubuntu. When I try, I get the following:

$LogFile indicates unclean shutdown (0,0) Failed to mount '/dev/sdb1': Operation not supported Mount is denied because NTFS is marked to be in use. Choose one action: Choice 1: If you have Windows then disconnect the external devices by clicking on the 'Safely Remove Hardware' icon in the Windows taskbar then shutdown windows cleanly. Choice 2: If you don't have Windows then you can use the 'force' option for    your own responsibility. For example type on the command line: mount -t ntfs-3g /dev/ sdb1 /media/disk -o force    Or add the option to the relevant row in the /etc/fstab file:    /dev/sdb1/media/disk ntfs-3g force 0 0


So I tried Choice 2 and this is what I get:

~$ mount -t ntfs-3g /dev/ sdb1 /media/disk -o force

mount: only root can do that


lsusb:

Bus 002 Device 005: ID 0d49:7410 Maxtor 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 046d:08af Logitech, Inc. QuickCam Easy/Cool
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Oh, yes, also my webcam is not working on Skype, it recognizes it but there is no video, only fuzzy colours appearing on the test miniscreen.

Any help please?

---

### Post by taurus on 2009-03-11
1.  You should connect that external drive to a windows machine and use the safely remove hardware (little icon at the bottom right) top unmount it first before you unplug it.

2.  Or install ntfsprogs and use ntfsfix to fix that.

```
sudo apt-get update
sudo apt-get install ntfsprogs
sudo ntfsfix /dev/sdb1
sudo mkdir /media/sdb1
sudo mount -t ntfs-3g /dev/sdb1 /media/sdb1
df -h
```

3.  Or use the force option to mount it with root privilege--sudo.

```
sudo mkdir /media/sdb1
sudo mount -t ntfs-3g /dev/sdb1 /media/sdb1 -o force
df -h
```

---

