---
title: "External Hard Drive problems"
date: 2008-11-30
forum: General Help
---

### Post by ToastyMallows on 2008-11-30
I'm having a problem getting Intrepid to even recognize my Tobisha External Hard Drive.  Is there something I'm missing?  I've searched the internet for my problem and haven't found anything.  Even though it's formatted in NTFS, shouldn't it still bring it up under Computer or even on my desktop?  If it doesn't do that automatically, is there anyway to mount it myself?

---

### Post by taurus on 2008-11-30
Do you know the name of that drive?  Is it something like /dev/sdb1?

```
sudo fdisk -l
```
You can try to mount it with

```
sudo mkdir /media/sdb1
sudo mount -t ntfs-3g /dev/sdb1 /media/sdb1
```

---

### Post by ToastyMallows on 2008-11-30
When I use fdisk -l all I get for results are the 2 internal hard drives and their partitions, nothing regarding the Toshiba usb External HDD.

I don't know the name of the harddrive, is there a way to find out?

---

### Post by taurus on 2008-11-30
Do you have windows on your machine?  Plug it in and see if windows automounted it.  Then, use the Safely Remove Hardware icon at the bottom right corner to unmount the drive before you unplug it.  Otherwise, just leave it plug in and reboot into Ubuntu and see if Ubuntu would detect it now

---

### Post by ToastyMallows on 2008-11-30
No windows on this computer, just linux.  I ran out of the number of times I could use XP, so that's why I joined the linux community.

---

### Post by ToastyMallows on 2008-12-02
Shameless self bump.  Still need help, any suggestions?

---

### Post by caljohnsmith on 2008-12-03
Have you checked whether your BIOS even detects the Toshiba drive? In other words, if you go into your BIOS, does it list it as an available drive? And if so, how do you have the drive configured in BIOS? Some of the HDD related settings you can look for in BIOS are "auto-detect", LBA, CHS, RAID, AHCI/HCI/EHCI vs. IDE, IDE-emulation, ACPI, DMA, etc. Also, is the Toshiba drive PATA/SATA/USB?

---

### Post by orlox on 2008-12-03
plug your hard drive to your computer (im guessing its via usb), and then run on a terminal the command dmesg. Even if it does not mount the disk, it should throw a couple of messeges regarding the newly connected device (dmesg will throw A LOT of messeges, only the last ones should be of interest).

On the other hand, don't you receive a messege when you connect your hard drive that said it wasn't possible to mount it??

---

### Post by ToastyMallows on 2008-12-03
> **orlox said:**
> On the other hand, don't you receive a messege when you connect your hard drive that said it wasn't possible to mount it??

No I don't and that's why I'm confused.

I connect it then use dmesg and the output I get at the end is

```
[  490.618470] sd 5:0:0:0: [sdg] Attached SCSI removable disk
[  490.618533] sd 5:0:0:0: Attached scsi generic sg7 type 0

```

> **caljohnsmith said:**
> Also, is the Toshiba drive PATA/SATA/USB?

The drive is usb and it's external, so shouldn't I not need to configure the BIOS if it's plug-and-play?

---

### Post by orlox on 2008-12-03
sdg??? thats weird....

Could you check if /dev/sdg exists??

---

### Post by ToastyMallows on 2008-12-03
Yes the file /dev/sdg does exist.  Along with sdg1 and sdg2

---

### Post by orlox on 2008-12-03
Are there any other files that start with sdg, like sdg1, sdg2 or something like that??

You could try to mount sdg to see if it works though:

sudo mkdir /media/sdg
sudo mount -t ntfs-3g /dev/sdg /media/sdg

---

### Post by ToastyMallows on 2008-12-03
> **orlox said:**
> Are there any other files that start with sdg, like sdg1, sdg2 or something like that??

You could try to mount sdg to see if it works though:

sudo mkdir /media/sdg
sudo mount -t ntfs-3g /dev/sdg /media/sdg

I tried that and I got an error of

```
Failed to access volume '/dev/sdg': No such file or directory
Please type '/sbin/mount.ntfs-3g --help' for more information.

```

I just tried to plug it in again now and dmesg isn't showing that it's even connected.

---

### Post by orlox on 2008-12-04
mmmm...

Did you see if in /dev/ there were things like sdg1, sdg2, etc...

Other thing you could try, is diskmounter:

[https://help.ubuntu.com/community/AutomaticallyMountPartitions]("https://help.ubuntu.com/community/AutomaticallyMountPartitions")

The last time I used it, it had some problems because (I think I remember wel...) the ntfs type was called ntfs-fuse instead of ntfs-3g. However, if the drive is connected and the computeer sees it, it should be able to put an entry into /etc/fstab that says what device corresponds to that drive...

(The thing about dmesg throwing nothing is actually pretty weird...Wonder if a reboot could fix it...)

---

### Post by ToastyMallows on 2008-12-07
I reboot more than a normal person should, believe me.

Now that I restared dev/sdg does not exist

I'm sooo confused.

---

### Post by Ber P on 2008-12-07
I'm having the same kind of trouble with an external Maxtor HD. When I plug it in, the 'active'-LED stays on. *fdisk -l* shows nothing and *dmesg | tail -n 10* shows this: ```
$ dmesg | tail -n 10
[ 7952.912190] sd 2:0:0:0: [sdb] Sense Key : No Sense [current] 
[ 7952.912204] sd 2:0:0:0: [sdb] Add. Sense: No additional sense information
[ 7953.834757] sd 2:0:0:0: [sdb] Sense Key : No Sense [current] 
[ 7953.834772] sd 2:0:0:0: [sdb] Add. Sense: No additional sense information
[ 7954.757325] sd 2:0:0:0: [sdb] Sense Key : No Sense [current] 
[ 7954.757339] sd 2:0:0:0: [sdb] Add. Sense: No additional sense information
[ 7955.920915] sd 2:0:0:0: [sdb] Sense Key : No Sense [current] 
[ 7955.920929] sd 2:0:0:0: [sdb] Add. Sense: No additional sense information
[ 7957.059625] sd 2:0:0:0: [sdb] Sense Key : No Sense [current] 
[ 7957.059640] sd 2:0:0:0: [sdb] Add. Sense: No additional sense information

```

I've mounted it in Windows, and made sure to "remove safely", so the NTFS journal should be ok also.

It worked perfectly under Gutsy, but I've been unable to connect it, since I made a fresh Ibex install. 

From searching ubuntuforums.org, I've found lots of threads regarding this - but no answers :(. 

So if anyone has the brain to crack this one - plz help us.....

---

