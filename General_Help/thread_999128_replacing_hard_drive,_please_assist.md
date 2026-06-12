---
title: "replacing hard drive, please assist"
date: 2008-12-01
forum: General Help
---

### Post by BlueAngel-CPT on 2008-12-01
Hi,

I have 2 IDE hard drives in my Ubuntu Intrepid machine (one for booting, other for storage (this one is also shared across the network).

The main problem is that the storage drive has started giving problems (intermittently it sounds like a head failure). I've managed to copy everything I need off it, and I bought a new 320Gb IDE drive (the motherboard doesn't support SATA, sadly) which I want to use to replace the current drive with.

I found the very helpful tutorial on installing a new hard drive ([https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)) which helps me half way.

My question is this -> if I replace the hard drive with the new one and boot up the computer, is Ubuntu going to complain about the drive being unformatted / unpartitioned? Ideally I would like a step-by-step to avoid problems. (i.e. do I comment out the entry in fstab and the share in samba before shutting down to do the swop, then boot up, do the partitioning and put it all back?

Some pointers from someone who's had to do this would be appreciated.

---

### Post by cubeist on 2008-12-01
perhaps I am over-thinking this, but the way I would do it is place both the old storage HDD and the new HDD in the computer, then boot from a live cd and clone the contents of the old HDD to the new HDD.  This way you will have an exact duplicate of the old hard drive.  Then when you are finished copying put the boot hard drive back in and everything should work aok.

---

### Post by BlueAngel-CPT on 2008-12-02
Thanks for your reply cubeist, but perhaps I should have specified that the drive that has failed is not the boot drive, but the secondary. Maybe if I replace that drive and boot up without any modifications there won't be any problems but what has happened a few times is when I boot up the machine with the failing drive in, is that it spews out loads of disk read errors and is unable to boot. I'm just afraid that if I put in the new drive (or with no secondary drive in) without any config changes, it won't be able to boot and I'll be stuck.

Maybe I'm over-thinking things?

---

### Post by PocketDog on 2008-12-02
As long as the jumpers are set in the slave position (assuming the boot HD is master) I don't see a problem. Else how would anyone fit new secondary drives in the first place? Just plug it in, switch on, and watch the pretty boot screen ;-)

---

### Post by BlueAngel-CPT on 2008-12-02
At the moment the secondary drive is auto-mounted with an enty in fstab, wont I need to comment that out before swopping out the drives?

---

### Post by Elfy on 2008-12-02
yes - it will complain and fsck will fail with exit status 8 - you will be able toresume boot withh Ctrl+D

Once it's booted you can edit fstab with the new information, alternatively you could do so from the livecd - a little more work, but only a little :)

You could edit fstab before you reboot and install and have no errors - just comment it out with #

---

### Post by flyingbrass on 2008-12-02
Since the drive is IDE, make sure it is jumpered correctly for your situation (master, slave or cable select).

When you boot it will be detected, but you need to partition and format it before it can hold any data.  A simple GUI for the task is gparted.  

sudo apt-get install gparted
gksu gparted

Select your new drive from the dropdown menu in the upper right.  Create your partitions (can be only one), then your filesystem(s).  All done.

You'll need to add it to /etc/fstab.

---

### Post by BlueAngel-CPT on 2008-12-02
Thank you very much, guys. This more than answered my question. I have gparted installed (used it when I added the failed drive in the first place) and I know about the jumper setups. Will do this when I get home later.

---

