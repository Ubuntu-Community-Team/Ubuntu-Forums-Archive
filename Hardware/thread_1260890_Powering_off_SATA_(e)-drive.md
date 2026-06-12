---
title: "Powering off SATA (e)-drive"
date: 2009-09-08
forum: Hardware
---

### Post by PrinsValium on 2009-09-08
When I was using Windows XP I had a third-party program able to scan for new hardware on demand as well as shutting them down for safe removal. I used this to hot-swap SATA disks to/from my system. When I unmount a drive in Ubuntu it does not power down. Is there a way to do this? I have tried "sudo hdparm -Y /dev/sdb" for example as well as with -y. The drive then sort of stops but immediately powers up again.

---

### Post by megamania on 2009-09-08
> **PrinsValium said:**
> When I was using Windows XP I had a third-party program able to scan for new hardware on demand as well as shutting them down for safe removal. I used this to hot-swap SATA disks to/from my system. When I unmount a drive in Ubuntu it does not power down. Is there a way to do this? I have tried "sudo hdparm -Y /dev/sdb" for example as well as with -y. The drive then sort of stops but immediately powers up again.
As far as I know, there's a bug in the version of hdparm currently shipped with Ubuntu. I have exactly the same problem when I try to shutdown one of my two hard disks in my laptop.

You can download the latest version from the net, or wait for Karmic.

---

### Post by PrinsValium on 2009-09-08
> **megamania said:**
> As far as I know, there's a bug in the version of hdparm currently shipped with Ubuntu. I have exactly the same problem when I try to shutdown one of my two hard disks in my laptop.

You can download the latest version from the net, or wait for Karmic.

Thanks, that actually worked perfectly. Well I am a linux newbie, I downloaded this version [http://sourceforge.net/projects/hdparm/](http://sourceforge.net/projects/hdparm/) unpacked it and ran "make" in the source folder. Then "sudo ./hdparm -Y /dev/sdb" shut the disk down properly. Now, how do I replace/install it to be the first choice hdparm of the system?

---

### Post by megamania on 2009-09-08
> **PrinsValium said:**
> Then "sudo ./hdparm -Y /dev/sdb" shut the disk down properly. Now, how do I replace/install it to be the first choice hdparm of the system?
Since I decided to wait for Karmic, I have no ready-made solution.

You can try to:
- locate where the old hdparm is installed
- uninstall it from synaptic
- create a symbolic link of the new hdparm to the old directory

But I'm sure there are much easier solutions.

Or just live with the current situation for 1,5 months...  :-)

---

### Post by megamania on 2009-09-09
> **megamania said:**
> You can try to:
- locate where the old hdparm is installed
- uninstall it from synaptic
- create a symbolic link of the new hdparm to the old directory

That's bad advice. I did what I suggested and I broke my system.

So, either live with the current situation or look for a better solution...  :-(

---

### Post by PrinsValium on 2009-09-09
I will wait for this Karmic thing and use my new ./hdparm for now i think =) Thanks again.

---

