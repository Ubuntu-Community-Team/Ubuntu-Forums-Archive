---
title: "HP Pavillion has too many Partitions"
date: 2012-05-27
forum: Hardware
---

### Post by Kaninepete on 2012-05-27
I haven't changed my partitions at since I bought this laptop.

I'm trying to install ubuntu alongside windows 7, but it seems that I can't have more than 4 partitions.

If anyone could tell me for sure which one to delete, I will gladly do so, and move forward.

Please help me out?

---

### Post by madverb on 2012-05-27
Where are the partitions mounted in Windows? C: D: etc... What size are each of the partitions?
You can only have 4 primary partitions. You can remove one of the partitions and create an extended partition and then you can create as many as you need.

---

### Post by ahallubuntu on 2012-05-27
I wouldn't automatically delete ANY partition.  I'd want to know what each one is first.

Likely, two of them are probably the Windows C: (main) partition, an HP recovery partition (to do a factory restore if Windows gets messed up), and then maybe a diagnostic partition, a Windows boot partition...a backup partition?

Could you go into Disk Management in Windows and display what the partitions are currently?  You might already have an extended partition (you can create as many logical partitions as you wish inside of an extended partition, which is kind of a "container" for  logical partitions).  But maybe the Ubuntu installer can't re-jigger any free space from shrinking the Windows C: partition and move it into the Extended partition (where it could then create partitions for installing Ubuntu).  This could perhaps be done manually without deleting ANY partition, using a boot CD like Parted Magic but it could be a bit timing consuming and tricky.  Again, depends on your existing partition scheme.

---

### Post by Kaninepete on 2012-05-27
[http://imgur.com/fCb1j](http://imgur.com/fCb1j)

This is what Windows shows me.

---

### Post by madverb on 2012-05-28
It would be a bit difficult to modify that set up.
You would have to shrink the C: partition and create an extended partition.
The main problem is that it is using 4 primary partitions, so you wouldn't be able to create an extended partition. You could remove the HP Tools partition as that isn't really needed (I'm not sure though).

---

### Post by ts3 on 2012-05-28
> **madverb said:**
> You could remove the HP Tools partition as that isn't really needed (I'm not sure though).

That's what most people do, after making a back-up copy of W7, on dvd or USB. It contains HP recovery tools but nothing that's critical.  The other partitions are the main W7 partition, the W7 recovery and the bootloader and you'll probably need them if you want to dual-boot.  

You can google HP Tools partition removal, there's a lot of info online, including on these forums.  Personally, I have only linux on my hp laptop (deleted all four partitions that came with the laptop)  and have lived without HP Tools for months now without any ill effects :)

---

### Post by ahallubuntu on 2012-05-28
I would make an IMAGE backup of the HP tools partition and all the other partitions, actually, before deleting any partitions, though erasing the HP tools partitions and shrinking/moving the other partitions is probably what I'd do too.  I use True Image from Acronis in Windows for such things (you can boot a rescue CD without booting Windows and have most of the functionality).  Clonezilla has the ability to do it too.  In any case, I'd probably backup everything before messing with the partitions at all.  Shrinking partitions always involves some risk that something will go wrong, though Gparted has proven pretty reliable for me.  Better safe than sorry.

To be honest, I'd almost find it easier just to buy a new laptop hard drive and clone the Windows part to it - that would make it much easier to re-configure stuff and also avoid the risk of losing anything.  Hard drives are starting to fall in price again.  I've seen some of those Seagate hybrid 750GB laptop drives recently for around $130 or so - with the SSD cache that would add a nice performance boost as well.

---

### Post by Mark Phelps on 2012-05-28
Looks like you already have a 500GB drive -- which really is plenty of room.  You don't need to go out and buy a 1TB drive -- and deal with all the hassle of migrating your partitions to it.

What I would do is the following:
1) Copy the files and folders in the HP Tools partition into your Win7 OS partition (C).
2) Use ONLY the Win7 Disk Management utility to shrink the Win7 OS partition to create some room.
3) Once the Win7 partition is shrunk, reboot into Win7 a couple of times to allow it to do filesystem adjustments.
4) Download and install the FREE version of Macrium Reflect to your PC.
5) Hook up an external drive and using Macrium, image off your System Reserved partition and your Win7 OS partition.
6) Use the Macrium option to create and burn a Linux Boot CD.

NOW, you have what's needed to restore Win7 on your PC.

Now, you can mess around with doing a dual-boot install.

---

