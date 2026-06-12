---
title: "some help before i go mad please. thanks :)"
date: 2006-09-13
forum: Hardware &amp; Laptops
---

### Post by sal on 2006-09-13
so i bought two items recently. a logitech clicksmart 510 which i only want for the digital camera aspect and an Olympus camedia usb reader/writer model MAUSB-10.

what i am trying to get help with is how i can get the pictures off of the smartmedia card that is in the mausb-10 and plugged in to the pc's usb port.

hopefully someone here can guide me in the right direction.

thanks in advance,
sal

---

### Post by meng on 2006-09-13
I assume from your post that there is no automounting of the card in the card reader. That is to say, no icon appears on the desktop and it doesn't appear under the Places menu.

---

### Post by sal on 2006-09-13
> **meng said:**
> I assume from your post that there is no automounting of the card in the card reader. That is to say, no icon appears on the desktop and it doesn't appear under the Places menu.

yes, you are correct. this is driving me crazy.

---

### Post by meng on 2006-09-13
Yes I heard you the first time! What is the output of
lsusb
EDIT: screw that, what is the output of
cat /proc/scsi/scsi

---

### Post by sal on 2006-09-13
> **meng said:**
> Yes I heard you the first time! What is the output of
lsusb
EDIT: screw that, what is the output of
cat /proc/scsi/scsi

the output of cat /proc/scsi/scsi:
Attached devices:

the output of lsusb:
Bus 002 Device 002: ID 03f0:6004 Hewlett-Packard DeskJet 5550
Bus 002 Device 003: ID 051d:0002 American Power Conversion Back-UPS Pro 500/1000/1500
Bus 002 Device 001: ID 0000:0000
Bus 004 Device 003: ID 07b4:010a Olympus Optical Co., Ltd <---| thats the device
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000

---

### Post by meng on 2006-09-13
What about
fdisk -l

---

### Post by sal on 2006-09-13
> **meng said:**
> What about
fdisk -l

sudo fdisk -l fgives:
Disk /dev/hda: 20.4 GB, 20416757760 bytes
255 heads, 63 sectors/track, 2482 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1         243     1951866   82  Linux swap / Solaris
/dev/hda2             244        1337     8787555   83  Linux
/dev/hda3            1338        2482     9197212+  83  Linux

Disk /dev/hdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       14593   117218241   83  Linux

---

### Post by sal on 2006-09-14
bump, please help :)

---

### Post by John.Michael.Kane on 2006-09-14
sal cat /proc/scsi/scsi: shows that the item can be seen. let me ask you can you use g-thumb to see if see's the device?


Also you may have to just edit the fstab file and it to it. 


I did a search of the forum,and there seems to be only one other post in reguards to this peice of hardware. so this issue seems very obscure.

---

### Post by sal on 2006-09-15
> **SD-Plissken said:**
> sal cat /proc/scsi/scsi: shows that the item can be seen. let me ask you can you use g-thumb to see if see's the device?


Also you may have to just edit the fstab file and it to it. 


I did a search of the forum,and there seems to be only one other post in reguards to this peice of hardware. so this issue seems very obscure.

no i tried g-thumb and it dose not see the device. it's driving me crazy because the thing is i am using the usb card reader to read a smartmedia card that is in a logitech clicksmart 510 that dose not work with linux. right now i'm having to revert back to the windows box to get things off the camera but i don't want to have to do that. if you or anyone for that matter can get this card reader working for me i would be so grateful.TIA

---

### Post by sal on 2006-09-18
bump....anyone know what i should try on this?
TIA

---

### Post by John.Michael.Kane on 2006-09-18
Have you tried testing this device under edgy knot3?

---

### Post by sal on 2006-09-18
> **SD-Plissken said:**
> Have you tried testing this device under edgy knot3?

im running edgy knot 3 and i have tried it on both knot2 and now since the other day knot3 and nothing.

---

### Post by John.Michael.Kane on 2006-09-18
According to this theres driver support for the device in 2.16 kernel 
[http://alauda.sourceforge.net/wikka.php?wakka=HomePage](http://alauda.sourceforge.net/wikka.php?wakka=HomePage)

i'm not sure as to why your having issues.

---

### Post by sal on 2006-09-18
> **SD-Plissken said:**
> According to this theres driver support for the device in 2.16 kernel 
[http://alauda.sourceforge.net/wikka.php?wakka=HomePage](http://alauda.sourceforge.net/wikka.php?wakka=HomePage)

i'm not sure as to why your having issues.

yes i saw that page when i was researching the device. the problem im having is how do i mount the device and get the pictures/movies off of my smartmedia card. if i can do that somehow ill be a happy camper.

---

### Post by John.Michael.Kane on 2006-09-18
You could try this [http://ubuntuforums.org/showthread.php?t=259864&highlight=edit+fstab](http://ubuntuforums.org/showthread.php?t=259864&highlight=edit+fstab) edit the device labels to match your usb reader,and it should be mounted at boot.

---

### Post by sal on 2006-09-18
> **SD-Plissken said:**
> You could try this [http://ubuntuforums.org/showthread.php?t=259864&highlight=edit+fstab](http://ubuntuforums.org/showthread.php?t=259864&highlight=edit+fstab) edit the device labels to match your usb reader,and it should be mounted at boot.

no go. did not work. know anything els i could try with this friggin device?

---

### Post by WillFull on 2006-11-06
Sal,

something tells me we're going to have to bite the bullet and compile the driver into the kernel ourselves. :(

---

