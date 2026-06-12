---
title: "Help with Extending Kubuntu partition"
date: 2009-08-10
forum: Installation &amp; Upgrades
---

### Post by BigCityCat on 2009-08-10
When I installed Kubuntu I only used 32 gigs. Afterwards I decided I wanted to use more. So I went into windows and shrank the windows partition, so I have 86 gigs of unallocated space. Windows will not allow me to extend the Linux partition as far as I can tell. I checked to install Parted in Kubuntu but it's already there. I just don't know where it is or how to use it. I have Kubuntu and Windows Seven Rc installed. I want to use the unallocated space for Kubuntu.If someone could help it would be greatly appreciated thanks.

---

### Post by Elfy on 2009-08-10
You will have to do the resizing with a livecd - either your kubuntu one or a partition editor such as PartedMagic.

Once you have the editor open you will likely need to turn off swap - depends on how your partitions are laid out - a default install will cretae an extended with swap and / partitions.

To get the unallocated space you will need to resize the extended first and then move the unallocated or / so that they are contiguous.

If however you installed inside windows with wubi then you can look here - [https://wiki.ubuntu.com/WubiGuide#How](https://wiki.ubuntu.com/WubiGuide#How) do I resize the virtual disks?

---

### Post by BigCityCat on 2009-08-10
Ok I think I see what you are saying. I have the Kubuntu cd. So your saying boot with that and do it that way. 

My partitions actually are out of order. By that I mean it goes Kubuntu, I guess the boot partition, Windows and the unallocated. So if that is going to be too difficult I could just extend over windows and use the entire disc.

---

### Post by BigCityCat on 2009-08-10
I think I am just going to extend over the windows partition. My only concern is that I paid 50 dollars for a pre order of win7 so will I be able to resize Kubuntu in the future and install win 7 or should I call them and cancel my order? Because I do not want to lose this Kubuntu install. I had help setting up the wireless. I don't think I can set it up myself again and I REALLY LIKE KDE 4.3.

---

### Post by Elfy on 2009-08-10
Don;t overwrite windows if you don;t want to ;)

Run this command from a terminal and paste the output here - should be able to see what needs to be done from that.

```
sudo fdisk -l
```

---

### Post by BigCityCat on 2009-08-10
Thanks, cause I put the disc in and I didn't see any thing to partition with.

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x99972ac3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        4179    33567786    5  Extended
/dev/sda2   *        4180       19115   119967744    7  HPFS/NTFS
/dev/sda5               1        4001    32137969+  83  Linux
/dev/sda6            4002        4179     1429753+  82  Linux swap / Solaris

---

### Post by BigCityCat on 2009-08-10
Well parted magic wont let me move or extend the kubuntu partition. Was waiting for you to come back, or someone else.

---

### Post by zkriesse on 2009-08-10
To use the Live Cd to do what you want to accomplish you probably have to re-install the cd...then it should give you the partition option....I personally use Ubuntu so it might be a little different but I think it should work. Let me know.

---

### Post by merlinus on 2009-08-10
Linux is in a logical partition within an extended one, and windows is in a primary. Therefore the 86G of space you freed by shrinking windows resides in what is/was a primary partition. 

So you will first have to grow the extended to encompass that space, and then add it to linux.

---

### Post by Elfy on 2009-08-11
Turn the swap off - ```
sudo swapoff -a
```

You won;t be able to do anything to the extended with swap on.

---

### Post by BigCityCat on 2009-08-11
Thanks Guys. I screwed it up with Gparted so I said the hell with it and reinstalled Kubuntu over the entire disc. I want to just use KDE from now on. No more windows, but my wireless is now back to square one. I need to see if I can get Chili to help me with that again. It had something to do with adding a WL to the end of a file and changing how KDE is looking at fb4 or something like that. It's broadcom and it can work. I know that much. Right now it sees no wireless at all. Do you guys know where a tutorial or something that can help me with this? Thanks

---

