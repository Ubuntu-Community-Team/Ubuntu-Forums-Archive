---
title: "Moving from extended to primary"
date: 2008-11-10
forum: General Help
---

### Post by epqr on 2008-11-10
Ok so im going to make on big partion for all my documents and a common home partion for all my distroes. so i have 25gb unallocated on my primary drive (and a windows drive). i also have 10gb on my extended part which i would also like to use on the one big partion. is there any way to move it from the extended partion to the primary, or maybe the other way arround?

---

### Post by epqr on 2008-11-10
Not possible ?

---

### Post by logos34 on 2008-11-10
post output of 

sudo fdisk -l

to give us a better picture

You'll have to work from the ubuntu or gparted live cd...you'll need to shrink the extended partition down--to do so you may have to move over one or more logical partitions.  Takes a while

---

### Post by dabl on 2008-11-10
> **epqr said:**
> 

 and a common home partion for all my distroes



There's a bad idea.  Your desktop settings and special settings for many packages are recorded in hidden files in /home.  Unless you are planning identical packages and configurations in all your OSs, you'll just come to grief doing it this way.

Make a separate partition for your data. On that partition make folders for "DOCS", "IMAGES", "MUSIC", and whatever.

Install your Ubuntu on a reasonable sized partition, allowing for the occasional downloaded ISO image and so on -- maybe 10GB.  Then symlink the "DOCS" and other data folders into the Ubuntu /home directory, and into the /home directories of your other distributions.  This way, your Ubuntu settings will remain unpolluted with the settings in other distributions, and your data don't get banged around with distro-specific files.

---

### Post by logos34 on 2008-11-10
> **dabl said:**
> There's a bad idea.  Your desktop settings and special settings for many packages are recorded in hidden files in /home.

+1, definitely.

>  Make a separate partition for your data. On that partition make folders for "DOCS", "IMAGES", "MUSIC", and whatever.(that's what I thought the OP really had in mind--a separate 'Data' partition, rather than a 'home' partition strictly speaking, with symlinks folders to each of the distros.)

---

