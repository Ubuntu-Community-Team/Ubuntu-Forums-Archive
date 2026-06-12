---
title: "IDE drives - tertiary &amp; quaternary controllers"
date: 2005-06-19
forum: Hardware &amp; Laptops
---

### Post by jafa on 2005-06-19
Hi guys,

My system has the following drives:
SCSI - main boot drive, ubuntu install.
IDE Primary (motherboard) Master = cdrom
IDE Tertiary (Promise card) Master = ide hard drive 1 - data only.
IDE Quaternary (Promise card) Master = ide hard drive 2 - data only.
There is no seconard controller.

My first attempt at installing ubuntu wouldn't boot. I suspect it tried to install GRUB on on of the non bootable IDE drives... I went through this problem with a previous Fedora install.

I unplugged the two IDE drives and ubuntu installed ok on the SCSI.

Now that ubuntu is working, how do I get it to detect the IDE drives? With Fedora they came up as /dev/hde and /dev/hdg.

Also in the device manager ubuntu does not report the IDE card... I am guessing it should.

Is there such a thing as "autodetect new hardware"?

Thanks,

Nick

---

### Post by blind0wl on 2005-06-20
Try punching in the make and model of your IDE controller into search and see if there has been other issues with that particular model, and can you post the output of:

```
lspci
```

Cheers

Blindy

---

### Post by wookie on 2005-07-15
[QUOTE=blind0wl]Try punching in the make and model of your IDE controller into search and see if there has been other issues with that particular model, and can you post the output of:

```
lspci
```

Cheers

Blindy[/QUOTE]
 My card is detected by lspci, but I have no /dev/hd* devices.  Any idea how to get them ?

Cheers, J/.

---

