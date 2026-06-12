---
title: "Create System Recovery Partition"
date: 2009-02-23
forum: Installation &amp; Upgrades
---

### Post by chrisx on 2009-02-23
Hello!

I have recently won a bid to provide about 70,000 computers.
I would very much like to install Ubuntu on each of them;
however, the region where I am selling has very few techs.

As a result, the buyer wants a recovery partition, ala HP/Dell.
I have looked on the forum and the Net, but I find little 
information.

How exactly does one go about creating a system recovery 
partition for Ubuntu?

Thank you so much for any help,

Chris

---

### Post by kidders on 2009-02-24
Hi there,

I suppose you could compress a clean root filesystem into a small partition on all of the hard disks. It's hard to know why you'd want to though ... there are comparatively few situations a recovery partition could rescue your users from. It might be better to put the replacement filesystem on a bootable CD/DVD, along with a quick shell script to automagically restore it (and/or reinstall the bootloader). That way, no matter what went wrong, the solution would always be the same, and would work without user intervention.

(I'm assuming the machines you're supplying will all have the same CPU architecture.)

---

### Post by chrisx on 2009-02-24
Thank you!

Yes, this is the track that I have been trying to follow with [partimage]("http://www.partimage.org/Main_Page"). I am trying to figure it all out, with partitions like so:

[FONT="Courier New"]
/dev/sda1 /recovery 5000 MB EXT2 - noatime, noauto, ro
/dev/sda2 /boot 150 MB EXT2 - noatime
/dev/sda3 SWAP 509 MB
/dev/sda4 / Remaining (~74 GB)  EXT3
[/FONT]

On sda1 I could add a small Linux installation and the image.
GRUB could display a menu item for recovery. On boot to the
recovery partition, I could call a script using at least
partimage to restore partitions 2, 3, and 4 to "factory."

> It's hard to know why you'd want to though ...

3rd world - the buyers state that there are almost no
technicians in their area, and they suppose that recovery 
partitions might help. They have no network, and the country
has no networking infrastructure other than POTS.
They will rely on the phone to give instructions to users.

> "there are comparatively few situations a recovery
> partition could rescue your users from."

Yes, and if the disk is bad, it won't help at all.

> It might be better to put the replacement filesystem on a
> bootable CD/DVD, along with a quick shell script to
> automagically restore it (and/or reinstall the bootloader).
> That way, no matter what went wrong, the solution would
> always be the same, and would work without user intervention.

That's a fine idea, and it is how I do want do it, also.

> I'm assuming the machines you're supplying will all have
> the same CPU architecture.

Yes. Two models, 80% are workstations and 20% laptops.
Gosh, great question. I had not thought about this yet.
I suppose this means I need to create two recovery solutions?

I feel as though I am trying to sysprep Windows without the
sysprep tool.

:)

---

### Post by kidders on 2009-02-24
That sounds quite neat, really. The biggest problem I'd have with your plan is that a botched bootloader is such a common issue, I'm not sure it's ideal for a recovery solution to depend on one. Still ... if that's what your client is insisting on, there's not a lot you can do, I suppose!

On the other hand, if the client is open to persuasion, it might also be worth pointing out that after restoring a computer, step two will invariably be "apt-get update && apt-get upgrade" (to kill off bugs & security issues) ... something which could take quite some time over a POTS. Deploying a disc-based recovery solution would allow you to update the images every few months to incorporate important updates (and possibly charge recurring support fees for doing so?).

Another suggestion I would make is to consider a single-partition install. Storing swap space & boot images in separate partitions creates extra failure points, and would make automated recoveries more complicated.

> **chrisx said:**
> I suppose this means I need to create two recovery solutions?Not necessarily ... you only need more than one recovery image if there are *significant* differences between your two operating environments (ie more than just the contents of a few files in /etc). Having to create two would be a real headache. :-(

---

### Post by gamhead on 2010-11-01
I agree that a botched bootloader is the biggest problem but surely this is the final piece of the puzzle that Ubuntu has consistently failed to address?

A decent recovery partition loaded with user friendly tools capable of inspecting and reconfiguring the bootloader - hence protecting the users from themselves is what is needed..

Im an experience programmer but have still managed to foul up my installations and get muddled when trying to resize my windows partition to make room for more ubuntu :(

---

### Post by kidders on 2010-11-01
Hi there,

> **gamhead said:**
> A decent recovery partition loaded with user friendly tools capable of inspecting and reconfiguring the bootloader - hence protecting the users from themselves is what is needed.:confused: Without a functioning bootloader, there'd be no way to access it.

---

### Post by gamhead on 2010-11-02
Yeah I hear ya, but isnt the problem that there are too many adhocs tools for managing this, and bootdiscs that let you get yourself in trouble?

If there was a recovery partition that could, by default, be installed onto a harddisk with an Ubuntu install with decent GUI tools to manage this stuff the users could be given a solution that is much harder to corrupt

---

### Post by timbott on 2011-03-02
I'm trying to solve a similar problem. This thread is marked as "solved" but I don't see an actual solution here yet. Chris would you be willing to share what you actually did to solve the problem and/or some of the scripts or steps?

your help would be much appreciated.

---

