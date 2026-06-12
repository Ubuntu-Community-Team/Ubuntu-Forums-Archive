---
title: "Installing SATA drive on an old Dimension"
date: 2009-02-18
forum: Hardware
---

### Post by ntuple on 2009-02-18
Hi everyone,

I have an old Dell Dimension 2350 that I installed Kubuntu 8.05 on with the ultimate goal of making a relatively inexpensive MCE box. 

I currently have a 40GB drive on the box so I bought a WD Caviar Blue drive only to find it came without a legacy power connector and the system board has no SATA controller.

The question is should I:

A. Buy a SATA controller that works with Linux (about $20) along with a power adapter cable ($5).
B. Forget this box and install the HD on my Windows box and try to make a dual boot so I can run Kubuntu and MCE on one partition.

My concern with A) is that the controller or drive may not be recognized by Kubuntu or the Dell meaning I'll waste the money along with $10 I spent last week on a bracket to get the HD into the box.  As usual with hardware, I find that unless I keep up with an area there's always some curve I didn't expect. 

If I go with B) I'm afraid I'm going to have to repartition that box and I like my Windows just the way it is. Also the MCE won't be running all the time so when I'm using Windows I'll lose the functionality of MCE. Meanwhile the Dimension would just be a box to putter around in but not be terribly useful.

Being new to Ubuntu would appreciate any thoughts from veterans on this forum.
Thanks for your help.

---

### Post by handy on 2009-02-19
Another option, is a PATA -> SATA converter that plugs directly into one of your motherboard's IDE sockets, instead of an IDE cable.

These converters allow you to install 2 drives & keep the Master/Slave thing going.

I tend to think that these cards are a safer choice than cards that go in PCI slots as far as Linux support is concerned.

I have not used one myself, but I don't believe there are any driver issues involved with them.

I have been looking into this stuff for my FreeNAS box which is based on FreeBSD. ;-)

---

### Post by ntuple on 2009-02-19
Thanks for the reply. As I only have on IDE slot on the system board, would I still be able to use the IDE drive I already have Linux installed on with this converter or must I reinstall on the new drive ?

> **handy said:**
> Another option, is a PATA -> SATA converter that plugs directly into one of your motherboard's IDE sockets, instead of an IDE cable.

These converters allow you to install 2 drives & keep the Master/Slave thing going.

I tend to think that these cards are a safer choice than cards that go in PCI slots as far as Linux support is concerned.

I have not used one myself, but I don't believe there are any driver issues involved with them.

I have been looking into this stuff for my FreeNAS box which is based on FreeBSD. ;-)

---

### Post by memilanuk on 2009-02-25
Bump due to similar dilemma :)

---

### Post by ntuple on 2009-03-14
Wow it worked!

For anyone wanting to do the same thing, first I bought a $10 metal adapter on ebay that allows the new drive to piggy back onto the HD case of the installed drive.

Then I found a SATA adapter on NewEgg that someone said works on 8.10 and the power & signal cable to go with it. Specifically:

* SYBA SD-SATA2-4IR PCI SATA II Controller Card RAID 0/1/5/10 JBOD
* BYTECC 18" Serial ATA-150/300 Cable w/Locking Latch Model SATA-118C
* Some $3 power adapter

I plugged them in and rebooted into GParted, The first time it said various things then went to black so I rebooted and ran GParted in safe mode. It ran fine, recognized the SATA controller and the WD Caviar Blue. 

I created a new partion and formatted the new drive to /ext3. Rebooting again into Kubuntu, I found the new drive had been mounted automatically as /media. THat's it !

No mount commands or driver installation needed. Wow, Kubuntu is actually newbie friendly. Now to do MCE :popcorn:

---

### Post by futts on 2009-04-29
Is this product fakeRAID?

---

