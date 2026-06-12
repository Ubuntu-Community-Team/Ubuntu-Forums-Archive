---
title: "USB stick read only"
date: 2022-02-11
forum: Hardware
---

### Post by eliyahu22 on 2022-02-11
My USB sticks are read only, I cannot delete anything from them, and I cannot write on them.   Is there a solution for this? 

I use Ubuntu 20.04 LTS.

---

### Post by SeijiSensei on 2022-02-11
Some USB sticks have write-protect switches. Make sure they are turned off.

---

### Post by TheFu on 2022-02-11
> **eliyahu22 said:**
> My USB sticks are read only, I cannot delete anything from them, and I cannot write on them.   Is there a solution for this? 

I use Ubuntu 20.04 LTS.

Some things to consider.
* Flash storage wears out.
* If an ISO file has been "burned" onto the flash storage, the entire device is read-only until it gets reformatted.
* Not all flash drives work with all USB ports. Try a different port.  Try a different stick.

If there isn't any hardware issue, use **gparted** to completely wipe and put a new partition table onto the device. 
Then add at least 1 partition and format it as ext4.  Connect that to your Linux system and mount it.  
One last thing. By default, the storage will be owned by root:root so your userid cannot write to it.  Change the owner to your userid on the top level directory and from that point forward, you'll be able to write to the disk. This will survive reboots, unplug/replug, whatever.

You may not want to use ext4, since it isn't exactly friendly for flash storage.  There is a Linux compatible file system, f2fs, which **is** friendly for flash storage and fast. Install f2fs-tools (that's the package name in the repos) and then it should be possible to format, mount and access the storage using that file system. 

File system choice matters.  If you use any non-Linux file system, all the rules change.

---

### Post by eliyahu22 on 2022-02-14
> **TheFu said:**
> Some things to consider.
* Flash storage wears out.
* If an ISO file has been "burned" onto the flash storage, the entire device is read-only until it gets reformatted.
* Not all flash drives work with all USB ports. Try a different port.  Try a different stick.

If there isn't any hardware issue, use **gparted** to completely wipe and put a new partition table onto the device. 
Then add at least 1 partition and format it as ext4.  Connect that to your Linux system and mount it.  
One last thing. By default, the storage will be owned by root:root so your userid cannot write to it.  Change the owner to your userid on the top level directory and from that point forward, you'll be able to write to the disk. This will survive reboots, unplug/replug, whatever.

You may not want to use ext4, since it isn't exactly friendly for flash storage.  There is a Linux compatible file system, f2fs, which **is** friendly for flash storage and fast. Install f2fs-tools (that's the package name in the repos) and then it should be possible to format, mount and access the storage using that file system. 

File system choice matters.  If you use any non-Linux file system, all the rules change.

I don't get anywhere with gparted.  Tried it, but nothing.    I have a laptop,  when I plug in the USB port a USB stick, or a wireless mouse, he murders them immediately.  Could my desktop have the same problem now?

---

### Post by TheFu on 2022-02-14
Try a different USB port.  If the issue follows a device from computer to computer, I'd bet the issue is with the device, not both computers, unless they are using exactly the same USB controllers. Then it could easily be a USB controller incompatibility.

I'd still think the flash storage as worn out, as my best idea.

---

