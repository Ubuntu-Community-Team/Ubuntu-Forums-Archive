---
title: "How to copy old XP to new HDD migrating to Ubuntu?"
date: 2007-08-06
forum: Hardware &amp; Laptops
---

### Post by bliffle on 2007-08-06
I migrated from XP to Ubunto on this Thinkpad T40 2 months ago and I'm very happy with it. I installed a new 80gb HDD for ubuntu and put the old 30gb XP into an aluminum box with a USB cable so I can fetch old data at my convenience.

Now I want to convert my old TPs, like a couple 570s and a 600 I have laying around. I'm willing to buy new HDDs as necessary, since I roll forward to bigger HDDs as a backup strategy already.

The first XP 570 has become so slow and cranky it's almost unusable, but I do have to use it very infrequently when Only XP Will Do. So, I would like to have a dual-boot setup. I have 2 plans:

plan 1: make space on the existing HDD, partition and add Ubuntu. I hate this plan because I end up using the same old HDD and it's kinda small and it requires I do a disk de-frag before partitioning which will probably fail after running forever. So I prefer the next plan:

plan 2: copy old XP HDD to a rightsize partition on new HDD and then install ubuntu and dual-boot, etc. 

Problem is, I don't know what utility to use and what else I should know to copy the old XP to the new HDD and have it work. 

Also, I'm worried that the !$$#^ XP system is keyed to HDD (and CPU) serial numbers, or something, to prevent  copying for DRM reasons. 

So, to begin with, what do I use to copy the XP system from the old HDD to the new HDD in such a way that it will still run?

---

### Post by BoneKracker on 2007-08-06
I believe parted will create a new partition (with filesystem) from the contents of an existing partition (and filesystem).  However, I suspect this functionality does not extend to ntfs.

Generally, it's advisable to use the native tools of an os/environ for partitioning and filesystem operations.  In other words, don't go looking for a GNU/Linux tool to copy your Windows partition; look for a Windows tool.

Check to see if the built-in "disk management" tool (which does partitioning and what-not) can do this.  If not, look into popular Windows-based 3rd-party tools (partition magic, etc.).

Personally, I would simply back up the data files that I want from the Windows partition.  Nuke it.  Set up a clean install on the new drive/partition, restore data files, then install GNU/Linux.

---

### Post by bliffle on 2007-08-06
The XP utility is probably Norton GHost, which I had enormous problems with last time (probably MS DRM crap) so I don't want to use it.

My XP distro is an update so I first have to install the old W2K system, yuk. Unless I can get an XP non-update off bittorrent.

---

### Post by BoneKracker on 2007-08-06
You wouldn't be talking about something illegal, would you?

---

### Post by bliffle on 2007-08-06
> **BoneKracker said:**
> You wouldn't be talking about something illegal, would you?

My, my. What you must think of me!

But seriously, if the dang DRM stops me from upgrading the HDD on the computer that I paid to have the XP on, wouldn't I be justified? How does MS justify not allowing customers to upgrade an HDD?

---

### Post by tgalati4 on 2007-08-06
Yes.

Also, if your motherboard dies and you replace it, you have lost your Windows XP/Vista license.  It is keyed to the motherboard.

Open source software doesn't suffer from this problem.

---

### Post by HermanAB on 2007-08-06
OK, here is how to copy a HDD:

Get a live CD, eg. Knoppix.
Plug both the old and new disk drives into the system.
If SATA, the drives should be /dev/sda and /dev/sdb
If IDE, the drives should be /dev/hda, /dev/hdb, /dev/hdc, /dev/hdd
Click all the Knoppix disk drive icons to figure out which disk is which and write it down!

To copy the disk, use disk duplicate (dd). The destination disk must be the same size or larger than the source disk.  Do something like this:
sudo dd if=/dev/hda of=/dev/hdc bs=16k

Long wait...

If you get the inputfile and outputfile the wrong way around, then the result is going to be rather disappointing...

Cheers,

Herman

---

### Post by bliffle on 2007-08-06
> **tgalati4 said:**
> Yes.

Also, if your motherboard dies and you replace it, you have lost your Windows XP/Vista license.  It is keyed to the motherboard.

Open source software doesn't suffer from this problem.

I replaced the MB on this very T40, so I guess this XP (which is now in the box) is invalidated. Good thing I'm running ubuntu, whiich has no such goofy restriction.

---

### Post by bliffle on 2007-08-06
> **HermanAB said:**
> OK, here is how to copy a HDD:

Get a live CD, eg. Knoppix.

I have the liveCD for feisty, and I'm gueSounds like  THAT should work.ssing that willl do.
> 
Plug both the old and new disk drives into the system.
If SATA, the drives should be /dev/sda and /dev/sdb
If IDE, the drives should be /dev/hda, /dev/hdb, /dev/hdc, /dev/hdd
Click all the Knoppix disk drive icons to figure out which disk is which and write it down!

To copy the disk, use disk duplicate (dd). The destination disk must be the same size or larger than the source disk.  Do something like this:
sudo dd if=/dev/hda of=/dev/hdc bs=16k
...


I have a dock for the 570, so I can put the new big HDD in the dock bay and run linux from a liveCD in the CD player at the USB port. Then 'dd' the old HDD to the one in the dock bay. 

After that I guess I Run parted from the CD , or do I do that before I copy the old XP system disk?

---

### Post by BoneKracker on 2007-08-06
dd doesn't stand for "duplicate disk"

I've used dd to copy partitions from one disk to another before.  But I was under the impression that if you used dd to copy an actual disk (e.g., /dev/hda), you would also be copying the disk label (including geometry and partition table entries).  

So, if your first disk is say, a 20 GB IBM DeskStar and your new disk is a 80 GB Western Digitital Raptor, after the operation your new disk is also going to show up as a 20 GB IBM DeskStar (in addition to quite possibly not functioning properly).

---

### Post by HermanAB on 2007-08-06
First copy the old small disk to the new big disk.  After that, XP should boot if you install the new disk properly - Windoze will be non the wizer.  

If at this point you run gparted, you will see the XP NTFS partition and a ton of empty space.  You can create a partition for Ubuntu in the empty space, or you can simply run the Ubuntu installer, since it should look around and offer to install into the empty space and add Windows to the boot menu, to make the system dual boot Windows/Linux.

Hope that helps!

Herman

---

### Post by HermanAB on 2007-08-06
Indeed, some people believe dd means ``Destroy Disk'' or ``Delete Data''...

---

### Post by bliffle on 2007-08-06
I've been told to use 'pcopy' instead of 'dd', but it has to come from Synaptic.

---

### Post by bliffle on 2007-08-07
So my general strategy is to copy the old XP to the big HDD then employ parted and install Feisty.

The question is, what do I use to copy XP? It seems as though "dd" is both dangerous and unreliable. So I'm planning to use "pcopy", which I have on this T40. Then I can connect the old and new HDDs to the 2 USB ports and have the T40 pcopy the system disk. Then I'll try the new HDD in the 570 and see if it works. If it does I can use the 7.04 livecd to partition and install Feisty.

I just worry that pcopy wil not copy correctly or completely the XP and I'll have an XP on the new HDD that won't come up.

---

### Post by bliffle on 2007-08-08
I've noticed that some people allocate a 'swap'  partition of about 3gb. Is that for swapping data between XP and ubuntu? Or is it for swapping RAM in and out of virtual storage, or is it for hibernation?

---

### Post by HermanAB on 2007-08-08
The swap partition should be at least two times the amount of RAM you have.  Swap is used in an emergency - when Linux runs out of memory, it will move dead stuff to swap so it can keep running instead of grinding to a halt.  If you have 1GB or RAM, swap will almost never be used, but it is important to have it.  On laptops it is also used to save a RAM image for the hibernate/suspend feature.

---

