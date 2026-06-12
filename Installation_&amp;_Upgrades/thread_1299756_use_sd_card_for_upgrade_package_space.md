---
title: "use sd card for upgrade package space"
date: 2009-10-24
forum: Installation &amp; Upgrades
---

### Post by milton1 on 2009-10-24
Hi all,

I am running a mini 9 with the 4GB drive and UNR 9.04. I am getting ready for 9.10, but I fear that, after the addition of a few extras, I will not have enough disk space to download and extract all the packages for the upgrade. My thought is to somehow use an SD card for extra space. Is it possible to mount the SD card to the correct folder, and have apt use that space for the upgrade? If so, what would be the correct folder? something in /tmp? or /var?

---

### Post by milton1 on 2009-10-24
Better yet, instead of remounting part of the existing directory structure, can I create a new mount point for the SD card and modify the settings for apt to use the new mount point for saving and extracting packages?

---

### Post by phillw on 2009-10-24
Hi,

I don't have experience of this netbook, but you do seem to be in good company - there's a forum set up specifically for you and your bretheren.

[http://www.ubuntumini.com/](http://www.ubuntumini.com/)

I've had a kwik look at it and they are discussing 9.10, amongst other things.

Hope that helps,

Phill.

---

### Post by milton1 on 2009-10-24
Thanks, Phill; I'm aware of the ubuntumini forum. I have not found my answer there so far. My question is not specific to the mini. It is really a question about apt. Can I redirect it to save and extract packages on a different physical drive?

---

### Post by milton1 on 2009-10-29
OK, I think I found my answer here:

[http://ubuntuforums.org/showthread.php?t=671990](http://ubuntuforums.org/showthread.php?t=671990)

but I am still wondering if this will work. When new packages are downloaded, they must be extracted before install, correct? Does this extraction occur within the same folder as download, or is there a second, temporary folder that would also need space for a large update/upgrade?

---

### Post by victor.cighir on 2009-11-07
> **milton1 said:**
> OK, I think I found my answer here:

[http://ubuntuforums.org/showthread.php?t=671990](http://ubuntuforums.org/showthread.php?t=671990)

but I am still wondering if this will work. When new packages are downloaded, they must be extracted before install, correct? Does this extraction occur within the same folder as download, or is there a second, temporary folder that would also need space for a large update/upgrade?

Thanks for the link. I used it with some small modification, because my problem was slightly different. 

I was running out of space on my root partition, so I needed to use a folder on my bigger partition as a download target for packages. :D


1. ```
sudo rm -Rf /var/cache/apt/archives
```
this removes the folder.

2. ```
cd /path-to-folder-on-big-partition
```

3. ```
sudo mkdir archives
```
and ```
sudo mkdir ./archives/partial
``` . This last one is necessary because I had an error with that missing folder.

4. and finally simlink to this folder from /var/cache/apt
```
sudo ln -s /path-to-folder-on-big-partition/archives /var/cache/apt/
```

Good luck!

---

