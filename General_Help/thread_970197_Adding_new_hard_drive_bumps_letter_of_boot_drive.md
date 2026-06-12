---
title: "Adding new hard drive bumps letter of boot drive"
date: 2008-11-04
forum: General Help
---

### Post by Uaine on 2008-11-04
The drive that I have been booting from is /dev/sdd.  I am trying to add a drive (temporarily) to copy over some data.  However, after adding the new drive and booting, my boot drive gets bumped to /dev/sde.

Boot is not successful, and I get bounced to (initramfs) with the error "target filesystem doesn't have /sbin/init".

My /etc/fstab defines the boot drives by UUID.  However, my boot loader is Lilo, which I understand doesn't allow UUIDs.  So, my boot drive is defined by /dev/sdd in my lilo.conf.

So the question I arrive at is "How can I make sure that my boot drive will always be /dev/sdd?"  After doing some searching on the forums, I think I might need to make a udev rule. I'm not sure about this though; are udev rules imposed prior to Lilo?

I've played around with udev for several hours with no success, and would appreciate any guidance on this.

Note: I've considered just altering my fstab and lilo.conf to point to /dev/sde, but I don't want to do this every time I swap a new drive into or out of the computer.  There must be an easier way.

---

### Post by Erlander on 2008-11-04
Have you set the correct boot drive in the bios?

---

### Post by vanadium on 2008-11-04
> I don't want to do this every time I swap a new drive into or out of the computer. There must be an easier way.
this is not a usual situation. It is not normal to swap drives in and out of a computer system all the time, so it is not obvious that there would/should be an easier way.

The only drives you should be swapping in/out on a regular basis are external, removable drives.

---

### Post by geirha on 2008-11-04
If you switch which physical port the sdd and sde drives are connected to, they should also switch names.

---

### Post by KeyserSoze93 on 2008-11-04
If it's an IDE drive (which will be sdX on the new kernel), make sure the new one is set to slave.

---

### Post by Uaine on 2008-11-04
Thanks for the replies.  Let me add just a few details.

> this is not a usual situation. It is not normal to swap drives in and out of a computer system all the time, so it is not obvious that there would/should be an easier way.
I don't know, maybe I'm not doing this right.  But, I'm running a fileserver with some drives in a RAID and hot spares.  I'm going to be adding and reconfiguring storage as I grow the capacity of the server, and I'd prefer for my system not to be rendered unbootable every time I move some drives around. I imagine this is pretty rare stuff on a desktop machine, but I don't think it's too uncommon for a server.

Right now, I have
primary master: boot drive
third master: raid1
third slave: hot spare
fourth master: raid1
fourth slave: new drive

The primary master is still listed as the first drive in the bios, even after adding the new drive.  I never add anything to the primary slave.

Thanks for the suggestions so far.  It's not a bios problem as best as I can tell.  I'll keep searching for a solution to this, but if anyone has some ideas, I'd appreciate them.  Nobody really commented on the udev thing.  Am I correct to conclude that udev cannot help me?

---

### Post by caljohnsmith on 2008-11-04
Is there some particular reason you are using Lilo instead of Grub? Is it because of your RAID setup? Grub now can boot entirely by UUIDs, so if you can use Grub, I think it would solve your problem. Does Lilo have any startup menu editing capabilities like Grub? With Grub on start up, you can select an OS in the menu, press "e", and then temporarily edit the entry to suit your needs. Does Lilo have something like that? Or could you also just add some extra modified OS entries in your Lilo menu config file that will boot the OSes for the special case when you add your extra drive? Just some ideas.

---

### Post by Uaine on 2008-11-04
Grub may be the easiest resolution to this problem.  I'd been using Lilo just because it installed by default, and it hasn't given me any problems yet.  I've used Grub in the past, so I suppose I'll just switch.  I've never had to switch filesystems before (in the past, I've started with Grub), but from what I read, the process isn't much harder than just installing Grub.  I'll see how it goes.

---

