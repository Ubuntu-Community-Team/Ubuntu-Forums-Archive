---
title: "Change back to Intrepid"
date: 2009-03-12
forum: Installation &amp; Upgrades
---

### Post by matthewpopester on 2009-03-12
I was recently informed by my computer that I had about 1000 updates to install, and I ran them, and now I have Jaunty instead of Intrepid.  Which I didn't want.

Is there an easy way to roll back an "update" such as this?

Oh, and I tried putting in my Intrepid disk, but it seemed to only be able to do a fresh install.

---

### Post by lisati on 2009-03-12
The only way I know of is to back up your data and then do a fresh install. Anyone else?

---

### Post by mick222 on 2009-03-12
If jaunty is running ok leavr it as the new release will be out soon. Also open software sources go to the updates tag and disable distribution upgrades,or do as the above poster says and back up data and do a reinstall.

---

### Post by Partyboi2 on 2009-03-12
> **lisati said:**
> the only way i know of is to back up your data and then do a fresh install. Anyone else?
+1

---

### Post by matthewpopester on 2009-03-12
I looked into doing a fresh install because I have all my data stored on another drive anyway.  When I went to install it, the partitioner started up, and it was going to do something like this

|---- WIN XP ---------|----- Intrepid ------|----- Jaunty ----|

How do I get it to just overwrite Jaunty?

---

### Post by Partyboi2 on 2009-03-12
At the partitioning stage choose "manual" then select the Jaunty partition and tick the box to format it and then set the mount point to /

To make sure you change the correct partition  open a terminal (Applications>Accessories>Terminal)  from the live cd and type
```
sudo fdisk -l
``` to find out what partition number jaunty is using so you know which one to edit when you choose the "manual"  partitioning option.

---

