---
title: "hdd problem, solutions point to windows fix, i only have linux"
date: 2010-12-21
forum: Hardware
---

### Post by shaunjohn007 on 2010-12-21
ive looked through many threads as to find out why my computer is giving me messages like     




(Error mounting: mount exited with exit code 13: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Failed to read NTFS $Bitmap: Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.)   


 and have been steered to threads that handle fixing this solution in windows...i have no access to a windows machine just a linux laptop and a mac every now and then

---

### Post by psusi on 2010-12-21
Why are you using a windows filesystem if you don't have windows?  Either the fs is corrupt and you need windows to fix it, or the disk may be failing, in which case it is time to replace it and restore from backup.

Open the disk utility and take a look at the SMART status of the disk to see if it is failing.

---

### Post by shaunjohn007 on 2010-12-21
the ntfs is because i initially used the external on windows 7....i got a new computer and put an open source os on it to cut costs

---

### Post by shaunjohn007 on 2010-12-21
it says smart system not supported

---

### Post by IcarusR on 2010-12-21
You don't need a windows install to fix, just a windows setup cd & use rescue console. Or maybe 'mini xp' that is on hirens boot cd.
Hirens has loads of useful tools on it. Very handy to have.

Link for d/l at bottom of this page

[http://www.hirensbootcd.org/download.html?start=8]("http://www.hirensbootcd.org/download.html?start=8")

---

### Post by psusi on 2010-12-21
You can't use SMART with USB enclosures.  You need to either connect it with esata instead, or remove the drive from the enclosure and plug it in internally if you want to run the SMART diagnostics.

---

### Post by shaunjohn007 on 2010-12-22
how would i go about that

---

### Post by psusi on 2010-12-22
If the enclosure has an esata port, use that instead of usb.  Otherwise, you open it up and remove the drive and install it internally.

---

### Post by shaunjohn007 on 2010-12-22
do i put it in then run hirens, cause it doesnt have a os....sorry for my ignorance, i thought i was computer knowledgeable, but apparently i have alot to learn

---

### Post by gradinaruvasile on 2010-12-22
Have you tried running ntfsfix on it?

---

### Post by shaunjohn007 on 2010-12-22
my terminal knowledge is basically cut and paste, kinda in need of specific directions, if you know what i mean :)

---

### Post by psusi on 2010-12-22
> **gradinaruvasile said:**
> Have you tried running ntfsfix on it?

That just sets the flag telling windows to chkdsk it.

Take a screwdriver and remove the drive from the enclosure, and plug it into an unused sata port on your motherboard.  Then boot up Ubuntu and start the disk utility and you should be able to get the SMART info from the drive.

If you don't have an unused sata port, or a spare sata cable, then disconnect the internal drive temporarily and plug the other drive in its place, then boot the ubuntu livecd and use the disk utility there.

---

### Post by shaunjohn007 on 2010-12-22
within the live cd disk utility show that smart isnt present

---

### Post by psusi on 2010-12-22
> **shaunjohn007 said:**
> within the live cd disk utility show that smart isnt present

Can you post a screen shot?

---

### Post by shaunjohn007 on 2010-12-22
could i show you with team viewer

---

