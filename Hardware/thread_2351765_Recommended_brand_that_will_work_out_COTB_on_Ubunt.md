---
title: "Recommended brand that will work out COTB on Ubuntu - Network Attached Storage (NAS)"
date: 2017-02-06
forum: Hardware
---

### Post by edcompsci on 2017-02-06
I'm looking for a NAS device with at least 2 bays that will work with RAID 1 or higher and give me the least amount of issues when hooking up to my linksys router connected to to linux machines (1 machine is Linux Mint and the other dual boots CentOS and Ubuntu Studio).  I would like to use it for for my local file folder for Thunderbird email

I was about ready to click on and buy a Synology DS213 but then thought, what if it gives me problems?  Will Ubuntu find it on the network just like any storage device or will it give me issues, and are the issues easily solved?  

Can I get some advice on what brand will work better or any information?

maybe [http://lifehacker.com/5822590/turn-an-old-computer-into-a-networked-backup-streaming-or-torrenting-machine-with-freenas](http://lifehacker.com/5822590/turn-an-old-computer-into-a-networked-backup-streaming-or-torrenting-machine-with-freenas)

---

### Post by geeksmith on 2017-02-06
The protocols used for connecting to a NAS are pretty standard. For Ubuntu, you'll probably use NFS or Samba to connect shares served by the NAS. I'm confident that one or both are offered by all popular NAS products.

Using an old computer for a NAS is very compelling. I'm in the process of doing so myself, actually. The old computer must have a lot of RAM in order to be suitable, especially if you're going to use an advanced filesystem like ZFS (8GB is recommended minimum). The cool thing with using FreeNAS or NAS4Free is that the OS is installed on a USB flash drive, so all hard disks are available for network storage.

If you're going to buy a commercial appliance, just make sure it supports NFS or Samba (like I said, I'm pretty confident all do). Ubuntu will have no problem finding and using such an appliance.

If you have lots of free time and a penchant for hacking embedded systems, you can even put your own custom Linux on many commercial NAS appliances. That's probably beyond the scope of this forum, but there are other sites that offer information for this type of thing. Lot's of fun!!!

---

### Post by HonorableGoat on 2017-02-07
I have a Synology DS212j, which is a 2-bay, and don't have any issues when it comes to connecting to it from my laptop.  I'd be happy to try things out if you have any specific things you'd like to test out for compatibility purposes. I have a deja-dup backup running to it as a destination as we speak too :) The synology supports NFS, Samba and Mac Finder type connections.

I'd also like to give a +1 to FreeNAS, it's great.  Takes a bit more playing around to set it up though, but that's half the fun.

---

