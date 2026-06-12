---
title: "No Operating system Found"
date: 2009-03-16
forum: Installation &amp; Upgrades
---

### Post by Chuck02 on 2009-03-16
I recently installed a new 80gb HDD in a laptop and am in the intentions of installing Ubuntu on it but while using the live cd (several copies made thought i made bad ones) computer goes thru POST then gives me No operating system found, I have set CDROM as primary boot method as well. Any help will be apprieciated.

Chuck

---

### Post by Therion on 2009-03-16
How, exactly, did you burn the disk?  It needs to be burned as an "image" (.iso) not as a typical data CD.

When you open the CD in another computer, do see ONE file on the CD (ending in .iso) or do you see SEVERAL files and a few folders?  If it's the first scenario (one file, .iso extension) you have NOT burned the CD correctly and your computer can not boot to it.  The PC is therefore going to look at the hard drive and of course, it's blank.  Hence the error.

[https://wiki.ubuntu.com/BurningIsoHowto](https://wiki.ubuntu.com/BurningIsoHowto)

---

### Post by Chuck02 on 2009-03-16
burned as image with InfraRecorder this is file list on the cd:
.disk
casper
dists
install
isolinux
pics
pool
preseed
autorun.inf
md5sum.txt
README.diskdefines
ubuntu
umenu.exe
wubi.exe

---

### Post by ugm6hr on 2009-03-16
What hardware are you using?

Did you check md5sum?

Have you ever booted from CD drive before?

Do you know that the CD drive works?

Did you use CD-R (or RW)?

Check [http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso) for advice (Also wiki).

---

