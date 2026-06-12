---
title: "Corrupt USB Drive"
date: 2008-08-22
forum: General Help
---

### Post by chaosrl on 2008-08-22
Hey,

I have a USB drive that completely died while I was in Windows. Vista locked up while reading from it, and after restarting, the drive can no longer be used. In Windows, the error says "No media inserted in Disk F", though it does show up as a drive. In Ubuntu, in my Computer folder, it shows up as "USB Drive", but then when I mount it, it says "Unable to mount location. No media in the drive."

It doesn't show up in gparted, and Windows fails to format it. Am I SOL? Or is this drive still savable? I don't need any of the data on the drive, I'd just like the drive to be working again. Thanks!

---

### Post by Gondee on 2008-08-22
If the drive is older than 5 years then i think its most likly dead for good. 

When did you get it? What type is it? How much do you use it?

---

### Post by chaosrl on 2008-08-22
It's pretty much brand new. I got it from Newegg about 3 months ago, and since then, I've used it sparingly. Just moving files from here to there occasionally. It's a Super Talent PicoC drive.

---

### Post by Patb on 2008-08-22
Chaos, you might try using gparted to delete the existing partitions and repartition the drive. That **might** work but I wouldn't get too much hope up. Good luck. 

Cheers, Pat

---

### Post by caljohnsmith on 2008-08-22
If it's a near-new HDD, I wouldn't give up on it just yet. If you want to recover data off of it, try using "testdisk":
```
sudo testdisk
```
Another great program for recovering files is "photorec", and you can find some info on using it at [this website]("http://www.google.com/url?sa=t&ct=res&cd=1&url=http%3A%2F%2Fwww.users.bigpond.net.au%2Fhermanzone%2Fp21.html&ei=acWuSJ7NM4LMtQP0oa2FAQ&usg=AFQjCNGcHjQMwCtG2uSlI4hu49igNJT23w&sig2=P_ILDTcK8QEqqcBTZG7f_g") (for example). 

It could be something as simple as your HDD's partition table got corrupted, which testdisk can often help you repair. But if you don't have anything important on that USB HDD, then +1 for what PatB said; I would just wipe it clean and start over. But, I would definitely run some HDD diagnostic tests on it to check its health; if you don't have a diagnostics test CD that came with the drive, you could always download the [Ultimate Boot CD,]("http://www.ultimatebootcd.com") which has a bunch of HDD tests you can run. Good luck.

---

### Post by chaosrl on 2008-08-24
Hey, sorry for the late reply. To Patb and caljohnsmith: it doesn't show up in gparted at all. I'm unable to mount it, period. It just shows up as "disk" in My Computer, and I can't open it, as it says "Disk can not be mounted."

And sorry if I wasn't clearer earlier, but it's a 4gb flash drive, not an HDD. I'm not terribly worried about the data on it, I might have to end up getting another one it seems, as I do need something of this sort in college. But if there was a way to salvage it, that'd be fantastic!

Again, thanks for your help!

---

### Post by caljohnsmith on 2008-08-25
> **chaosrl said:**
> Hey, sorry for the late reply. To Patb and caljohnsmith: it doesn't show up in gparted at all. I'm unable to mount it, period. It just shows up as "disk" in My Computer, and I can't open it, as it says "Disk can not be mounted."

And sorry if I wasn't clearer earlier, but it's a 4gb flash drive, not an HDD. I'm not terribly worried about the data on it, I might have to end up getting another one it seems, as I do need something of this sort in college. But if there was a way to salvage it, that'd be fantastic!

Again, thanks for your help!
Thanks for clarifying, I misunderstood you and should have read your first post more carefully. :) In case you want to try and recover any data off of it, I would give the testdisk/photorec programs a try; but if you don't really need anything off that flash drive, then I think Patb had the best suggestion in that you should just wipe the drive clean and start over. You can then repartition it with gparted.

---

### Post by chaosrl on 2008-08-25
I'm not sure how to follow through with Patb's suggestion, though I don't need any data off the drive. When I open up gparted, in the upper right hand corner, I can select the different drives (I only have /dev/sda right now), and when I have my flash drive in, it doesn't show up there. Before (when it did work) I just used that to select the drive; is there another way to get to the drive?

---

### Post by caljohnsmith on 2008-08-25
First, if you don't happen to know the device name for the flash disk, do:
```
sudo fdisk -lu
```
And find the /dev/<device> for your flash drive. Next, try formatting the drive to ext3 with:
```
sudo mkfs.ext3 -L "flash drive" /dev/<flash device>
```
[COLOR="Blue"]Just make sure you get the /dev/<flash device> name correct or you could accidentally format your HDD.[/COLOR] Hopefully that will at least make your flash drive recognizable to gparted, which you can then use to repartition it and reformat the partitions any way you like.

---

### Post by chaosrl on 2008-08-26
Thanks caljohnsmith, but fdisk doesn't show the flash drive either. ```
jeff@lenovomon:~$ sudo fdisk -lu

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x95f3457a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    13213695     6605824   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *    13213696    99982176    43384240+   7  HPFS/NTFS
/dev/sda3        99982239   234435599    67226680+   5  Extended
Partition 3 does not end on cylinder boundary.
/dev/sda5        99982240   102906006     1461883+  82  Linux swap / Solaris
/dev/sda6       102906783   234435599    65764408+  83  Linux

```

That's all that shows up, which is my HDD. It's looking more and more as if this drive is gone for good :(.

---

### Post by caljohnsmith on 2008-08-26
> **chaosrl said:**
> Thanks caljohnsmith, but fdisk doesn't show the flash drive either. 
...
That's all that shows up, which is my HDD. It's looking more and more as if this drive is gone for good :(.
Unfortunately, I would have to agree with you; I think you're going to need to invest in a new flash drive. At least they're relatively inexpensive these days. Good luck. :)

---

### Post by chaosrl on 2008-08-27
Yeah, thank goodness. Thanks for all your help though, much appreciated!

---

### Post by iztok.jeras on 2008-11-25
Hi,

I destroyed two Super Talent PICO-C flash drives since I upgraded to Intrepid, I received a new one from the shop where I bought the first and it stoped working the third time I used it. The USB controller is detected but the drive does not respond to partitioning or formating or ... requests.

Iztok

---

