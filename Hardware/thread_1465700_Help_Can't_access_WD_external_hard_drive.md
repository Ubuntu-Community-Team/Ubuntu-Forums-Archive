---
title: "Help? Can't access WD external hard drive"
date: 2010-04-29
forum: Hardware
---

### Post by Kelci on 2010-04-29
I'm completely new to Linux, much less Ubuntu, so explain all your answers as if I'm dumb, please.

I have a WD SmartWare external hard drive that has all my files backed up from when my Windows Vista crashed. When I plug it in to my USB port, it pops up on my desktop, but when I go to open it, it just opens to a window that has pictures of how to plug in the external hard drive. This doesn't help at all.

This is strange because when I plug in my flash drive, it's accessed immediately and I can see my files. But when I plug in my WD external hard drive, it gives me unhelpful pictures and not the files I want. I want to solve this problem WITHOUT re-formatting the external hard drive, because I don't want to lose any of the files on it.

Could someone help me figure out how to access my stuff?

---

### Post by P4man on 2010-04-29
seems like the WD smartware comes with a special firmware that makes it act like a CD (containing those pointless images). 

It can be worked around though. Can you open a terminal (applications > accessories > terminal) and type in the following command:
```

sudo fdisk -l
```

(that is SUDO FDISK -L in *lower* case)

And copy paste the output here?

Then do the same with this command:

```
sudo blkid
```

---

### Post by Kelci on 2010-04-30
> **P4man said:**
> seems like the WD smartware comes with a special firmware that makes it act like a CD (containing those pointless images). 

It can be worked around though. Can you open a terminal (applications > accessories > terminal) and type in the following command:
```

sudo fdisk -l
```(that is SUDO FDISK -L in *lower* case)

And copy paste the output here?

Then do the same with this command:

```
sudo blkid
```

Ok, Here's what I got when I typed "sudo fdisk -1":

```
 [sudo] password for kelci: 

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xce5973cb

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14243   114406866   83  Linux
/dev/sda2           14244       14593     2811375    5  Extended
/dev/sda5           14244       14593     2811343+  82  Linux swap / Solaris
```

I had typed in my password when it prompted me to, and I got the above.

This is what happened when I typed in "sudo blkid":

```
 /dev/sda1: UUID="5c8c168c-c1b6-4eb5-902c-7c9b5e1e3b5f" TYPE="ext4" 
/dev/sda5: UUID="7b08ea46-520d-44ae-82e7-eaa70a42d691" TYPE="swap" 
```

Does any of this mean anything?

---

### Post by dino99 on 2010-04-30
install mountmanager from synaptic, then tweak as you need ( system admin mountmager: select into the left pane the device and set the settings in right pane)

---

### Post by P4man on 2010-04-30
Its not recognized as harddrive. Its presenting itself to the OS as a CD, requiring special software to access the data on the drive. I hate crap like that. its like U3 on usb sticks. Damn those manufacturers trying to make our life "easier".

Ive read somewhere you can work around that, but I cant find the link. 

For now, may I suggest you take the drive out of the enclosure and plug it straight in to a PC? That will avoid the firmware crap and hopefully make the drive just readable, assuming you did not encrypt it. If you did,, you got a problem.

Alternatively, remove the VCD crap/firmware using a windows machine and these instructions:

[http://www.wdc.com/wdproducts/updates/?family=wdsmartwareutilities](http://www.wdc.com/wdproducts/updates/?family=wdsmartwareutilities)

Im not sure if that destroys any data on it. Read more carefully than I did!

---

### Post by P4man on 2010-04-30
> **dino99 said:**
> install mountmanager from synaptic, then tweak as you need ( system admin mountmager: select into the left pane the device and set the settings in right pane)

thats great for harddisks. But this is no harddisk, at least not until the hdd is pulled out and the USB enclosure is driven over by a truck (my preference, but removing the factory installed malware may help too). Then it may become just a harddrive and something you can use. in which case you dont even need mountmanager.

---

### Post by Kelci on 2010-05-28
> **P4man said:**
> Its not recognized as harddrive. Its presenting itself to the OS as a CD, requiring special software to access the data on the drive. I hate crap like that. its like U3 on usb sticks. Damn those manufacturers trying to make our life "easier".

Ive read somewhere you can work around that, but I cant find the link. 

For now, may I suggest you take the drive out of the enclosure and plug it straight in to a PC? That will avoid the firmware crap and hopefully make the drive just readable, assuming you did not encrypt it. If you did,, you got a problem.

Alternatively, remove the VCD crap/firmware using a windows machine and these instructions:

[http://www.wdc.com/wdproducts/updates/?family=wdsmartwareutilities](http://www.wdc.com/wdproducts/updates/?family=wdsmartwareutilities)

Im not sure if that destroys any data on it. Read more carefully than I did!

What does encrypting it mean?

I know when I used this on my Vista, I had it password-protected. Is that what encrypted means?

---

