---
title: "Setting up RAID 5 system on ubuntu 12.04lts"
date: 2012-07-05
forum: Hardware
---

### Post by JacoSWD on 2012-07-05
hi everyone

ive got a question, hope this is in the right place , but here goes, i recently built a brand new computer and transfered my old pc's harrdrives with ubuntu on to the new pc and they booted up first time. now my question is this, ive bought 3x 2TB seagate harddrives to use as a raid 5 system, and ive setup the raid 5 array in the bios and its setup fine, but when i boot ubuntu it still sees the drives as seperate drives instead of a raid 5 drive.

but when i boot it with a live usb ubuntu version it sees the three drives as a raid drive as it should.

ive got ubuntu 12.04 lts on and use the onboard sata , and onboard raid , motherboard is gigabyte ga-z77-d3h

any help would be appreciated

---

### Post by mut3d87 on 2012-07-05
it maybe a shot in the dark here but if you have just moved the hdds from your old computer are you using your old install if you are maybe you could try a fresh install on your raid array backing up everything you want on the old hdds and set the old hdds to slaves

---

### Post by JacoSWD on 2012-07-05
yes its still running with old install, and the raid array is basically for storage only , will still use one or two of the old drives for the operating system

---

### Post by mut3d87 on 2012-07-05
ahh i see can pleaseshow the output of

```
cat /proc/mdstat
```

---

### Post by JacoSWD on 2012-07-05
im not currently at the pc, any other suggestions?

---

### Post by mut3d87 on 2012-07-05
well we need to see if your computer recognizes the raid array if not we may need to set it up

---

### Post by JacoSWD on 2012-07-05
well if i boot from a live ubuntu usb drive it recognises the raid array as it should, it says one raid drive with 4TB capacity in ubuntu's device manager, but when booted with normal installation it shows 3 seperate drives..

 also the pc is not mine but a clients pc, so at the moment i dont have access to it

---

### Post by JacoSWD on 2012-07-05
also would it help if i installed a seperate raid pci adapter and connect the drives to the adapter and configure raid from there?

---

### Post by steeldriver on 2012-07-05
There ARE some RAID experts on here (rubylaser, darkod...) I'm not one of them unfortunately but I would think the first thing you should check that the previously installed system even has the dmraid package on it (by default the desktop install doesn't iirc) - not mdadm, that's only for software RAID afaik

I have the UD3H board and I played briefly with the on-board RAID setup but decided it was horrible and opted for software RAID instead

---

