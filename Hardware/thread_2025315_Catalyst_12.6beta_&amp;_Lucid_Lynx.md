---
title: "Catalyst 12.6beta &amp; Lucid Lynx"
date: 2012-07-14
forum: Hardware
---

### Post by arkanabar on 2012-07-14
Is there an issue with the current Catalyst Beta drivers (12.6) from the manufacturer's site?

I understand that this might not be the most suitable place to put this, but I'm not sure where it ought to go.  I'm trying to follow the manual instructions for installing Catalyst 12.6beta (examples [here]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI#Manually_installing_Catalyst_12.6"); I'm following [these here]("http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide#Installing_the_drivers_manually")) in Lucid Lynx, since I want to see how World of Warcraft plays in Lucid, and the WoW appDB page over at WineHQ says the version of Catalyst that Jockey installs is too old.

I get to this step:```
sudo sh amd-driver-installer-12-6-x86.x86_64.run --buildpkg Ubuntu/lucid
```and I get this result:  ```
sh: Can't open amd-driver-installer-12-6-x86.x86_64.run
```So my questions are:  
First, what the hey?  I've done everything exactly as instructed (except that I had to grab & unzip a .zip version of the file in question).  And yes, the file is executable.
Second, is anyone else having this issue?
Third, is there a hash of this file somewhere that I can use to check its integrity?

---

### Post by Perfect Storm on 2012-07-14
Thread moved.

---

### Post by Icarus315 on 2012-07-14
Have you tried:

```
chmod +x amd-driver-installer-12-6-x86.x86_64.run
```

Before executing it with "sudo sh..."?

I don't know if the 12.6 Catalyst driver will support Lucid but making it executable may help.

---

### Post by Icarus315 on 2012-07-14
Sorry, missed the part where you said the file was executable.

Are you getting your installer from [This Page](http://support.amd.com/us/gpudownload/Pages/index.aspx).  Because 12.6 isn't beta anymore.  It is an official release.

I have an AMD Radeon 6870 and I followed the instructions on the [Same Page](https://help.ubuntu.com/community/BinaryDriverHowto/ATI) you are working off of.  Except for some packages that needed to be installed that that page glosses over it worked fine for myself.  Using them right now, Catalyst 12.6.

---

### Post by arkanabar on 2012-07-16
Filling in all the drop down boxes on that page led me to [this page]("http://support.amd.com/us/kbarticles/Pages/catalyst126legacyproducts.aspx"), and the link is once again to [http://www2.ati.com/drivers/legacy/amd-driver-installer-12.6-legacy-x86.x86_64.zip](http://www2.ati.com/drivers/legacy/amd-driver-installer-12.6-legacy-x86.x86_64.zip) -- the exact same filename I already have.  I'll try downloading it again.  

I'd really appreciate it if you could list all the packages I should install that they glossed over.

---

### Post by typhoon_tip on 2012-07-16
Try:

```
sudo sh **./**amd-driver-installer-12-6-x86.x86_64.run --buildpkg Ubuntu/lucid
```

---

