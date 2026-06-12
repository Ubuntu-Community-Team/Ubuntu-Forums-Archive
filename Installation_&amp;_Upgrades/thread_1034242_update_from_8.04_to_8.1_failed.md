---
title: "update from 8.04 to 8.1 failed"
date: 2009-01-08
forum: Installation &amp; Upgrades
---

### Post by jonbjarna on 2009-01-08
An error occured during the update, when I booted up again I got this:
[B]Starting up..
Aperture pointing to e820 RAM. Ignoring
Your BIOS doesn't leave a aperture memory hole
Please enable the IOMMU option in the Bios setup
This costs you 64 MB of RAM
Kernel panic - not syncing: VFS: unable to mount root fs on unknown-block(0,0)[/B]

I'm trying to go back up 8.04 and using this: [https://help.ubuntu.com/community/DowngradeHowto](https://help.ubuntu.com/community/DowngradeHowto)

I booted from CD and moutned my disks, but when I do apt-get update.
I get this:
[SIZE="1"]
on-is
Ign [http://ubuntu.lhi.is](http://ubuntu.lhi.is) intrepid/restricted Translation-is
Ign [http://ubuntu.lhi.is](http://ubuntu.lhi.is) intrepid/universe Translation-is
Ign [http://ubuntu.lhi.is](http://ubuntu.lhi.is) intrepid/multiverse Translation-is
Hit [http://ubuntu.lhi.is](http://ubuntu.lhi.is) intrepid-updates Release.gpg
Hit [http://ubuntu.lhi.is](http://ubuntu.lhi.is) intrepid-updates/main Translation-is
Ign [http://ubuntu.lhi.is](http://ubuntu.lhi.is) intrepid-updates/restricted Translation-is
Ign [http://ubuntu.lhi.is](http://ubuntu.lhi.is) intrepid-updates/universe Translation-is
Ign [http://ubuntu.lhi.is](http://ubuntu.lhi.is) intrepid-updates/multiverse Translation-is
Hit [http://ubuntu.lhi.is](http://ubuntu.lhi.is) intrepid-security Release.gpg
Ign [http://ubuntu.lhi.is](http://ubuntu.lhi.is) intrepid-security/main Translation-is
Ign [http://ubuntu.lhi.is](http://ubuntu.lhi.is) intrepid-security/restricted Translation-is
Ign [http://ubuntu.lhi.is](http://ubuntu.lhi.is) intrepid-security/universe Translation-is
Ign [http://ubuntu.lhi.is](http://ubuntu.lhi.is) intrepid-security/multiverse Translation-is
Hit [http://ubuntu.lhi.is](http://ubuntu.lhi.is) intrepid Release
Hit [http://ubuntu.lhi.is](http://ubuntu.lhi.is) intrepid-updates Release
Hit [http://ubuntu.lhi.is](http://ubuntu.lhi.is) intrepid-security Release
Hit [http://ubuntu.lhi.is](http://ubuntu.lhi.is) intrepid/main Packages
Hit [http://ubuntu.lhi.is](http://ubuntu.lhi.is) intrepid/restricted Packages
Hit [http://ubuntu.lhi.is](http://ubuntu.lhi.is) intrepid/main Sources
Hit [http://ubuntu.lhi.is](http://ubuntu.lhi.is) intrepid/restricted Sources
Hit [http://ubuntu.lhi.is](http://ubuntu.lhi.is) intrepid/universe Packages
Hit [http://ubuntu.lhi.is](http://ubuntu.lhi.is) intrepid/universe Sources
Hit [http://ubuntu.lhi.is](http://ubuntu.lhi.is) intrepid/multiverse Packages
Hit [http://ubuntu.lhi.is](http://ubuntu.lhi.is) intrepid/multiverse Sources
Hit [http://ubuntu.lhi.is](http://ubuntu.lhi.is) intrepid-updates/main Packages
Hit [http://ubuntu.lhi.is](http://ubuntu.lhi.is) intrepid-updates/restricted Packages
Hit [http://ubuntu.lhi.is](http://ubuntu.lhi.is) intrepid-updates/main Sources
Hit [http://ubuntu.lhi.is](http://ubuntu.lhi.is) intrepid-updates/restricted Sources
Hit [http://ubuntu.lhi.is](http://ubuntu.lhi.is) intrepid-updates/universe Packages
Hit [http://ubuntu.lhi.is](http://ubuntu.lhi.is) intrepid-updates/universe Sources
Hit [http://ubuntu.lhi.is](http://ubuntu.lhi.is) intrepid-updates/multiverse Packages
Hit [http://ubuntu.lhi.is](http://ubuntu.lhi.is) intrepid-updates/multiverse Sources
Hit [http://ubuntu.lhi.is](http://ubuntu.lhi.is) intrepid-security/main Packages
Hit [http://ubuntu.lhi.is](http://ubuntu.lhi.is) intrepid-security/restricted Packages
Hit [http://ubuntu.lhi.is](http://ubuntu.lhi.is) intrepid-security/main Sources
Hit [http://ubuntu.lhi.is](http://ubuntu.lhi.is) intrepid-security/restricted Sources
Hit [http://ubuntu.lhi.is](http://ubuntu.lhi.is) intrepid-security/universe Packages
Hit [http://ubuntu.lhi.is](http://ubuntu.lhi.is) intrepid-security/universe Sources
Hit [http://ubuntu.lhi.is](http://ubuntu.lhi.is) intrepid-security/multiverse Packages
Hit [http://ubuntu.lhi.is](http://ubuntu.lhi.is) intrepid-security/multiverse Sources
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. [/SIZE]
and when I do dpkg --configure -a I get the log attached ending with:
[B]/usr/bin/perl: symbol lookup error: /usr/lib/perl5/auto/Locale/gettext/gettext.so: undefined symbol: Perl_Tstack_sp_ptr
dpkg: error processing mime-support (--configure):
 subprocess post-installation script returned error exit status 127
dpkg: too many errors, stopping
dpkg: ../../src/packages.c:252: process_queue: Assertion `!queuelen' failed.[/B]

Can anyone help ?

---

### Post by cdtech on 2009-01-08
Try running a force install:
```
sudo dpkg --configure -a && sudo apt-get -f install
```

---

### Post by jonbjarna on 2009-01-08
I get the same errors.

> **cdtech said:**
> Try running a force install:
```
sudo dpkg --configure -a && sudo apt-get -f install
```

---

### Post by jonbjarna on 2009-01-08
I found this in an year old thread:
```
sudo apt-get autoremove
sudo dpkg --configure -a
```
I dont know what autoremove will do, is it safe to use ?

---

### Post by jonbjarna on 2009-01-08
Oh, I get the same.. error: dpkg --configure -a 
Does anyone know what I can do to fix this ?

> **jonbjarna said:**
> I found this in an year old thread:
```
sudo apt-get autoremove
sudo dpkg --configure -a
```
I dont know what autoremove will do, is it safe to use ?

---

