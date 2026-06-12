---
title: "HP external hard drive slow and buggy"
date: 2012-03-09
forum: Hardware
---

### Post by hylian92 on 2012-03-09
Hello, several months ago I bought a new 2 TB HP external hard drive, and haven't been able to get it working. It was originally formatted with NTFS, but I've since reformatted it as btrfs and ext2-4 in trying to get it to work. I recently started trying again, and have finally been successful in creating folders, but Ubuntu still takes 2-3 minutes to connect it. Every time I try to move a file to it (in nautilus, pcmanfm, and terminal) it initiates it but never actually changes anything on the internal or external drives. Eventually (4-5 minutes) the screen completely glitches up and I can't make sense of it, to the point that I end up having to shut it down.

---

### Post by LinuxFan999 on 2012-03-10
> **hylian92 said:**
> Hello, several months ago I bought a new 2 TB HP external hard drive, and haven't been able to get it working. It was originally formatted with NTFS, but I've since reformatted it as btrfs and ext2-4 in trying to get it to work. I recently started trying again, and have finally been successful in creating folders, but Ubuntu still takes 2-3 minutes to connect it. Every time I try to move a file to it (in nautilus, pcmanfm, and terminal) it initiates it but never actually changes anything on the internal or external drives. Eventually (4-5 minutes) the screen completely glitches up and I can't make sense of it, to the point that I end up having to shut it down.
Maybe you got a defective unit.

---

### Post by hylian92 on 2012-03-10
> **LinuxFan999 said:**
> Maybe you got a defective unit.
I considered that, but I had the same problem with the first one which I returned early on.

---

### Post by ahallubuntu on 2012-03-10
I have plugged numerous external and portable USB drives into various Ubuntu boxes and have never had problems like you describe.  The worst problem I've encountered was a strange problem with 10.04 not recognizing integrated USB ports on the motherboard properly, to the point where it would read very slowly (only about 5Mbps) but oddly could write at about 25Mbps.  Still, I had no issues creating folders or copying files.  It was just slow.  Another USB card fixed it and so did booting 11.04 .  Just a quick with 10.04 and that particular chipset.

You might have something similar: your installation of Ubuntu doesn't like the USB controller or something.  It can a pain to debug these odd problems when you don't have multiple computers or drives (or distros) to plug stuff into.  But, it would help to know you could plug other external drives in successfully (or not), whether you can plug this HP drive into other computers rsuccessfully (using same version of Ubuntu - boot the live CD), etc.

Personally, I do not care for HP products - I have had too many weird problems with them.

---

### Post by hylian92 on 2012-03-10
> **ahallubuntu said:**
> You might have something similar: your installation of Ubuntu doesn't like the USB controller or something.  It can a pain to debug these odd problems when you don't have multiple computers or drives (or distros) to plug stuff into.  But, it would help to know you could plug other external drives in successfully (or not), whether you can plug this HP drive into other computers rsuccessfully (using same version of Ubuntu - boot the live CD), etc.
I have tried it on three different computers, two with Ubuntu 11.10 and one with Lubuntu 11.10. It doesn't work on any of them. My thumb drives work fine on all three. I had this problem with alpha and beta versions of Ubuntu 11.10 as well.

---

### Post by ahallubuntu on 2012-03-10
Then let me suggest that this particular model of hard drive is just not compatible with Linux.  As I said, this is not a general problem for external hard drives in my experience, having used several different models over the years on many computers and versions of Ubuntu.  Since I don't buy HP products I wouldn't know how their hard drives might work with Ubuntu - sorry.

---

