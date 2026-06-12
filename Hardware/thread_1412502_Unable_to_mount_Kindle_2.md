---
title: "Unable to mount Kindle 2"
date: 2010-02-21
forum: Hardware
---

### Post by hellinger on 2010-02-21
I am having trouble mounting the file system on my Kindle 2. Despite Amazon not explicitly declaring the compatibility of the Kindle with Linux distros, I figure it should be possible to mount it as a USB mass storage device - the device is running Linux after all!

When I connect the device it begins to charge and enters "USB Drive Mode" on the Kindle. However it is not auto-detected in Ubuntu and is not mounted in **/media/**.

```
dmesg
``` yields this
> [15979.152038] usb 1-4: new high speed USB device using ehci_hcd and address 2
[15979.296145] usb 1-4: configuration #1 chosen from 1 choice
```

lsusb
``` shows
> Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 1949:0002 Lab126 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

**How can I mount the Kindle as a USB mass storage device?**
Since I cannot mount nor unmount the Kindle, when I disconnect it - it crashes and I have to do a 15 second reset to bring it back.

Many thanks

Hellinger

---

### Post by bhold on 2010-03-29
I came across this thread because I am having trouble getting my kindle2 to automount. In other threads it seems like some people are not having this problem. But until I figure this out, I manually mount the kindle following these instructions:
[https://help.ubuntu.com/community/Mount/USB](https://help.ubuntu.com/community/Mount/USB)

(I am running 9.10 desktop in case it matters.)

---

### Post by bhold on 2010-03-29
I tried booting into 8.04 Ubuntu and connected the kindle2. The automount works fine, it is only on 9.10 that I must manually mount the kindle2. On 9.10 my usb backup drive automounts ok just like it always has. So whats the problem with kindle2 on 9.10, any suggestions?

---

### Post by hellinger on 2010-06-03
Finally worked this one out last night!
 
The Kindle 2 uses the Microsoft Media Transfer Protocol (MTP) as opposed to the more common Mass Storage Device Class (MSC) to facilitate the transfer of media files and associated metadata to and from devices.
 
To get it to mount on Ubuntu Karmic I had to install the ***mtpfs*** package. Type the following command in the Terminal.
 
```
 
sudo apt-get install mtpfs

```
 
After that, plug the Kindle 2 into USB and, hey presto, it auto mounts!

---

