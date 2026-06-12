---
title: "Hard Drive Size Showing Differently Between Ubuntu and BIOS"
date: 2007-08-18
forum: Hardware &amp; Laptops
---

### Post by i.wanna.corndog on 2007-08-18
Quick question. I just bought a 500GB hard drive and threw it in an older Compaq iPaq Desktop Computer. The iPaq's BIOS shows the drive as being 137GB, but Ubuntu's setup shows the full 500GB in the disk partitioner.

Do I need to be worried at all? I know that the 500GB works in Windows XP (using the Intel Application Accelerator), so I'd guess that I'd be fine (BUT I never wrote over 137GB worth of files to test for BIOS overwriting).

Any thoughts? I'm mainly worried about the BIOS not being able to address sectors beyond 137.4GB and overwriting other files. I guess the only true way to test this would be to write over 137GB in data onto the hard drive, then test the data to make sure it's not corrupt :).

---

### Post by logos34 on 2007-08-18
check to see if there's a Bios update to fix this

---

### Post by i.wanna.corndog on 2007-08-18
I've got the latest BIOS. Ubuntu is installing fine, so I guess I'll just copy over 137 Gigs of media stuff and large filler files to see what happens...

---

### Post by logos34 on 2007-08-18
XP SP1 should see all of it so I think you'll be ok. unless you try to put some other linux distros on it with the /boot past the 137 limit (in which case the Bios won't be able to address it--grub uses bios 'calls' to find stage2).  

Is the Bios drive detect set for 'auto', 'user', "LBA', or what?

---

### Post by i.wanna.corndog on 2007-08-18
Drat. Just got GRUB error 18. Right now I'm trying to format a 10GB partition mounted to /boot and the rest mounted to /. Is this correct? I usually just let it set things up for me manually, so I'm not sure about the mount point stuff.

BIOS is set to AUTO.

BTW thanks a ton for the help logos...people like you are the reason why I love the Ubuntu community...

---

### Post by i.wanna.corndog on 2007-08-18
Update: GRUB is now working fine and the system boots without error. I'm going to go ahead and try copying a bunch of media stuff over just to make absolute sure this will work, since I don't want this giving me problems down the road. I'll post results ASAP.

---

### Post by logos34 on 2007-08-18
> **i.wanna.corndog said:**
> Drat. Just got GRUB error 18. Right now I'm trying to format a 10GB partition mounted to /boot and the rest mounted to /. Is this correct? I usually just let it set things up for me manually, so I'm not sure about the mount point stuff.

BIOS is set to AUTO.

BTW thanks a ton for the help logos...people like you are the reason why I love the Ubuntu community...

I was just going to suggest that--make a separate /boot partition at the front of the disk...But it doesn't need to be 10 GB!!!   ~100 MB should be more than enough (just for comparison the average linux /boot folder with 2 or 3 kernel versions is under 20 MB).  

Make a /boot, /swap, and rest to /, OR make / ~ 10 GB and rest to a separate /home partition.  But
that will exhaust the 4 primary partition limit.  Alternatively put some of the partitions inside an extended:

/boot (primary)
/ root  (primary)

(extended)
/swap  
/home

---

### Post by i.wanna.corndog on 2007-08-19
Well, I copied a bunch of media stuff over to the drive (about 150GB, a bunch of duplicates) and was able to play everything just fine, so I'm gonna guess it worked. :)

Thanks again for the help.

---

