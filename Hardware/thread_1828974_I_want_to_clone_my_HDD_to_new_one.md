---
title: "I want to clone my HDD to new one"
date: 2011-08-19
forum: Hardware
---

### Post by asel_ on 2011-08-19
Hi all, I've two laptops, one with ubuntu and another one from dell with windows vista.

The laptop with ubuntu is fine.But the another one, which contains vista is have a problem with hardisk and I want to replace it with new one. Now, I want to clone the HDD that contains the vista os to a new HDD, so that it keeps the same HDD patitions and os's that is in, such dell media direct partition and recovery partition. Is there any way to clone the HDD to a new one so that I keep same partition table and bootable windows vista beside the recovery partition and dell media direct partition under ubuntu?

Thank you in advance.

---

### Post by dandnsmith on 2011-08-20
If it's anything like the Dell desktops I've just been working on, you'd need to have a really good match for the new HDD, as the recovery stuff (for me) popped out messages about the boot block being different fom the original setup - so installing any other OS causes a problem, as well as any difference in sizes ...

Is the problem with the HDD severe, or just an annoyance?

As for tools, I use Acronis TrueImage under Windows, and partinmage for linux, but others recommend clonezilla (the writeup of which confused me as to what it really did - I like to know before I start a tricky manoeuvre)

HTH

---

### Post by sbraz on 2011-08-20
> **asel_ said:**
> Is there any way to clone the HDD to a new one 
to clone disks i use **dd**.

assuming that:
1. both disks are plugged on the same machine (it can be done over network too with netcat but i never tried);
2. the source disk doesn't have bad sectors (worth trying anyway);
3. the target disk is larger in size;
4. both disks doesn't have any mounted partitions (boot from cd/usb, any distro is okay);

either under root or with sudo you run:
```
dd if=/dev/sd[COLOR="Red"]X[/COLOR] of=/dev/sd[COLOR="red"]Y[/COLOR] bs=4M
```
and wait until it's done, no progress bars will be displayed.
X and Y are the drive's letter, in my case for example it's sda and sdb.

[COLOR="red"]**dd** is a powerful tool but can also destroy data if used the wrong way.[/COLOR]
to avoid that, i'd do this too:
```
man dd
```

---

### Post by asel_ on 2011-08-20
Hi, thank you for help !!

Dear dandnsmith, actually I want to clone my 250 GB to 320 GB. Because the the original one have a bad sectors. Now I don't know if it will success to clone the original one to the new 320 GB HDD to be able to use restore tool delivered from dell. Also it is a laptop not desktop. Anyway, I will try clonezilla as it is free.Thanks for them.


Dear sbraz, the HDD is have a bad sectors. Can I use the dd command?

Your help is really appreciated.

---

### Post by sbraz on 2011-08-21
> **asel_ said:**
> Dear sbraz, the HDD is have a bad sectors. Can I use the dd command?
well yes you can but there's no guarantee that the result will work (there might be other damaged sectors yet to be detected) or the dd command will even terminate its job. **it's worth trying anyway**...
keep in mind that it'll take some time copying the whole drive: empty sectors are copied in the process too. just check if it's done when the hdd-activity led stops blinking. ;)

the result is a drive with the exact same data, bootsector, bootloader, file fragmentation, recovery partitions, EVERYTHING as the source. it's called "cloning" for a reason. :)
as you are cloning to a bigger drive you will just have to resize the partitions to fill the additional space; don't touch any of the recovery partitions or they won't work anymore... not a problem for me, actually i think that NOT having a restore is a _good feature_ rather than a problem, but it might be a problem for you so be careful.

i've used this the first time when i swapped my netbook's crappy 5400rpm drive with a western digital scorpio black and it worked like a charm.

ah btw, here it's summer and it's very hot: during these lengthy tasks, the operative temperature of the drive might exceed safety levels, so since your old hdd is already failing try not to help it explode with your data in it: place a fan nearby as a precaution, any will do/don't overdo. :D

---

### Post by dandnsmith on 2011-08-21
If wanting to use, you might have a look at [ddrescue](http://www.garloff.de/kurt/linux/ddrescue/), as this can copy without the erroneous blocks.

---

### Post by asel_ on 2011-08-22
Well, first I have to say thank you for help.

Second, I used clonezella, booted from usd flash drive, connected the new HDD inside container, the clone process take about half hour, now I'm using the new HDD. But there is unused space about 60 GB in new HDD.

CLONEZELLA IS REALLY POWERFULL TOOL.

---

### Post by sbraz on 2011-08-23
you can reclaim those 60GB using your favourite partition editor tool:
you can find clonezilla and many other disk tools in a libe distro called PartedMagic, packed specifically for data rescue, clone, smart monitoring, partitioning and many other related things. :)

[http://sourceforge.net/projects/partedmagic/](http://sourceforge.net/projects/partedmagic/)

---

