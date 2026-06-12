---
title: "ZFS Z2 pool 2.5 simultaneous failures, help me recover"
date: 2014-09-29
forum: Hardware
---

### Post by wesleykins on 2014-09-29
I have 8 3TiB Seagate ST3000DM001 drives in a Z2 Zpool.  (2 drives dedicated to parity)

I'm using [ZFSonLinux]("https://launchpad.net/~zfs-native/+archive/ubuntu/stable"), not ZFSFuse.

I recently noticed that one of the drives had a lot of reallocated sectors (thousands).  I check this regularly, and they just started to develop.

Between the time I ordered a new drive (Western Digital Red this time) TWO OTHER DRIVES DIED COMPLETELY.  Died as in "power on->click click->won't even spin up".

This leaves me with the drive with thousands of bad sectors as my only hope for recovering several TiB of data that I've spent years collecting.  Most of it can be re-ripped from my own personal media collection with a few months of effort, but some of it (home videos, pictures, etc.) is irreplaceable. 

I think there is a chance I can still read data off of this drive. It spins up and is "read-able", but keeps faulting due to read errors from bad sectors. The drives are plugged into a 3ware 9650 controller, but each drive is set up as a "single" unit, so it is presented to ZFS as if it were a normal drive.

I have 3 ideas to help:
1) how do I make the drive keep trying to read data from "bad" sectors for longer without kicking out and error
2) how do I keep the 3ware card from kicking the drive offline
3) how do I convince ZFS to keep trying to read the drive?

I have 3 replacement drives here.  Any suggestions as to how I can keep this drive alive long enough to read the data off of it?

Be a ZFS hero!  Help a man out.

PS  this makes FIVE failed ST3000DM001 drives out of my original 8 in less than 2 years.  Don't buy Seagate.

---

### Post by wesleykins on 2014-09-29
What happened to the formatting of my post?  It was nice and read-able when I clicked "submit"!

---

### Post by tgalati4 on 2014-09-29
You are in a bad situation.  I would get friendly with *hdparm* and see if you can change a few parameters to allow the disk to barf its data.

What was the SMART parameters of any of the failed disks?  It would be helpful to know exactly what failed.  That might help you in recovery.

```
man hdparm
```

and

```
sudo smartctl -a /dev/sda
```

Did you have power management features turned on with these drives?  I think you bought the wrong drives for this application.  These drives are only rated for 8 hours per day, 5 days per week:

> Support workload rate limits of 55TB/year in 8×5 environments

Of course an 8x5 environment could be an 8 foot by 5 foot cubicle.

---

### Post by wesleykins on 2014-09-30
> **tgalati4 said:**
> I would get friendly with *hdparm*...
Cool, thanks.  I'll try that and report back.

> **tgalati4 said:**
> What was the SMART parameters of any of the failed disks?  I
I'll post SMART info too.

> **tgalati4 said:**
> Of course an 8x5 environment could be an 8 foot by 5 foot cubicle.
Hah!  Nicely done.

These are definitely not "NAS" drives, but I still expected better than this.  I'm not constantly reading/writing to them.

I'll post updates here.

-Wes

---

### Post by tgalati4 on 2014-09-30
I would only use server-class/enterprise-class drives for a zfs array.  Cheap desktop drives are made of cat food.  How many power-on hours?

---

