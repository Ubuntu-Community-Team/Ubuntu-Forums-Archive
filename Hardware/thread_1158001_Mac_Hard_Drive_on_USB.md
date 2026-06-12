---
title: "Mac Hard Drive on USB"
date: 2009-05-13
forum: Hardware
---

### Post by F4rrari on 2009-05-13
Hi all,

My Mac G5 died, and I have pictures & Music on the Hard Drive that I plugged in to USB on Ubuntu. My questions is, how to I mount that hard Drive? Ubuntu sees it as USB Drive but can't mount it. Please help.:(

---

### Post by spacesamurai on 2009-05-13
If you have not touched your kernel, it might be that your box does not support the mac filesystem hfsplus. You can check this as follows:

```
$ cat /proc/filesystems  | grep hfsplus
```

If nothing shows up, then the filesystem is not supported. So te next step would be to install the module.

```
$ sudo apt-get install hfsplus
$ sudo modprobe hfsplus

```

After checking /proc/filesystems to see that it was installed, try to mount it again.

Hope this helps.

---

### Post by coffeecat on 2009-05-13
> **F4rrari said:**
> Hi all,

My Mac G5 died, and I have pictures & Music on the Hard Drive that I plugged in to USB on Ubuntu. My questions is, how to I mount that hard Drive? Ubuntu sees it as USB Drive but can't mount it. Please help.:(

Which version of Ubuntu are you using? In my experience Hardy, Intrepid and Jaunty will all automount a hfs+ (that's the Mac filesystem) usb drive read only without having to install any extra utilities. I've often done this to transfer large files from my Mac Mini to Ubuntu. However, you may encounter permissions problems navigating up through any folders because MacOS supports the same Unix permissions system as Linux and your UID in MacOS is almost certainly different from your Ubuntu UID.

That being said, if your Mac died and you can't read the drive in a USB enclosure in Ubuntu, then you need to make sure that either the drive hasn't died as well, or the filesystem hasn't been corrupted. What happened when the G5 died? Can you get access to another Mac to see if that will read your drive?

---

### Post by F4rrari on 2009-05-13
No Display on the Mac. I plug the hard drive on my buddy's macbook and it see my files. Anyway, I tried your instruction but not working. When I double click on USB Drive, it says unable to mount location. I am using Ubuntu 9.0. Any other suggestions? Btw , you talking to a newbie here.

Thanks

---

### Post by F4rrari on 2009-05-13
My /proc/filesystems  is blank. Did I miss something?

---

### Post by spacesamurai on 2009-05-14
I have being using intrepid and jaunty but don't seem to have the hfsplus filesystem. Is that just me?

Anyway the next step if your system is like mine is to install the hfsplus filesytem and try to mount it again. I listed the code above, but I will add it one more time just in case.

```

$ sudo apt-get install hfsplus
$ sudo modprobe hfsplus

```

If you finish entering the commands above, mount the USB again and see what happens.

Hope this helps.

---

### Post by coffeecat on 2009-05-14
> **spacesamurai said:**
> I have being using intrepid and jaunty but don't seem to have the hfsplus filesystem. Is that just me?

A default install of Jaunty doesn't include the hfsplus package - you're right - but the system will still automount a USB hfs+ filesystem and read it. That is/was true of Hardy and Intrepid in my experience. I believe the driver is compiled into the kernel, and I can't quite make out what the hfsplus package adds to a system which isn't already there.

I tried installing hfsplus, hfsprogs and hfsutils and now I can create hfs+ partitions in Gparted and write to them (which I couldn't before), but quite what each package did is also not clear.

But back to the OPs problem. I believe I may have realised why his system isn't automouting his G5 hard drive. The G5 came with the PPC processor and OSX 10.3 Panther (I believe), and sometime between then and the release of Intel based machines and later versions of OSX, Apple has changed the way it writes its partition table. I'm hazy about the details, but if you go into Disk Utility on a new(ish) Mac and try to create a partition, under 'options' it gives you three choices for the partition table type. If you try to install 10.5 (Leopard) to a HFS+ drive formatted the "wrong" way, it will refuse to install and insist on reformatting the drive. Furthermore - I once formatted a USB drive to hfs+ with a PPC machine running Panther and my Intel Leopard machine couldn't recognise or mount the drive - which rather surprised me. What I've said about Ubuntu mounting HFS+ formatted drives was with drives formatted with Leopard (Intel), so I wonder if Ubuntu can't mount the way F4rrari's drive is formatted because it was formatted the older way. Just a hypothesis. Perhaps if he installs the hfs* packages he may have more luck. I don't know.

** F4rrari**, if you're still following this thread, the only other suggestion I've got is to use your buddy's macbook to copy your files from the old HD to a flash drive or something formatted FAT32 which everything can read and write.

---

