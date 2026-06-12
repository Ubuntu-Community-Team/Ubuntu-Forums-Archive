---
title: "RAID support (ASUS P4P800 Deluxe)"
date: 2004-11-11
forum: Hardware &amp; Laptops
---

### Post by ubuntu_demon on 2004-11-11
Hi,

I'm running windows XP on my Pentium 4. I would like to run Ubuntu on it but I've got a ASUS p4p800 Deluxe and I'm running 2 harddisks on striping raid. I don't want to lose my movies and I want to be able to run Ubuntu in striping raid. As far as I know Asus doesn't provide linux RAID drivers. 

Does anyone know if running Ubuntu in striping RAID with my motherboard will be possible in the future ?

---

### Post by ubuntu_demon on 2004-11-13
I'll be a bit more speciific :

My motherboard has an ICH5R controller for SATA raid and an VIA controller for IDE ATA133 RAID.

I currently only use IDE ATA133 RAID. I'll try the ubuntu live cd in order to see if it's supported. (I'm running ubunbu hoary on my other pc and I lend the cd to a friend of mine)

I'm pretty sure ICHR5 SATA doesn't work.I don't have SATA drives so I can't test it. In the future I want to buy 2 SATA drives and run an SATA raid array. Does anyone know if there's going be ubuntu support in the future ?

---

### Post by ubuntu_demon on 2004-11-13
I don't see my raid 0 drive and I can't mount it using the live cd :(

---

### Post by jdong on 2004-11-13
The RAID provided by ICH, VIA, etc on consumer mobos are usually software raid's. The mobo does nothing but say "this is a RAID 0", and relies on the OS and software drivers to do the rest.

Linux also has software RAID, md. md supports a vast array of RAID modes, including 0,1, 5,6, 10, 0+1, etc etc etc...

The only reason you'd want to read a BIOS sw raid is to preserve existing data, in which case I don't have any experience with software BIOS RAID's...

---

### Post by ubuntu_demon on 2004-11-14
Thnx,

I didn't know it was software raid. I did know linux supports software raid. And yes I want to preserve my data.

Anyone ?

---

### Post by jhudson on 2004-11-14
I also have one of these same motherboards but mine is the vm model  (micro-atx) and I have lots of trouble with sata drives. Ubutu tells me on startup that there is a problem with the pnpbios and I should upgrade. I have upgrades the bios but still receive this error.
Asus are well known for not being linux friendly.
When I had SuSE installed on this board the sata deive took forever to boot.
suggestion if you still have problems to keep your bios up to date.
Hope this helps

---

### Post by ubuntu_demon on 2004-11-14
Thnx,I'll try.

---

### Post by ubuntu_demon on 2004-11-22
I flashed to Asus 1018 bios. Still doesn't give me acces to my raid partiitions.

lspci gives me the following :

0000:02:04.0 RAID bus controller: VIA Technologies, Inc. VT6410 ATA133 RAID controller (rev 06)

So I've got a VIA VT6410 chip.

---

### Post by ubuntu_demon on 2004-11-22
So I need to know :

- whether current kernels support my VIA chip.
- If I can get acces to my RAID array (because I don't want to lose my data)

---

### Post by ubuntu_demon on 2004-11-22
This Howto describes Installation of Debian Woody (with 2.4.x Kernel) on Asus P4P800 using the VIA6410 Raid Adapter for Parallel ATA Harddisks :

[http://www.is.tu-braunschweig.de/~buethe/p4p800_raid.html](http://www.is.tu-braunschweig.de/~buethe/p4p800_raid.html)

But I don't know the status of the 2.6.x kernel. Maybe there's already kernel support?

Also I want to know if I can preserve my existing ntsf partiitions on the array.

---

### Post by ubuntu_demon on 2004-11-22
I changed my mind and I decided to install ubuntu in a dual boot config with windows XP. I'm now running ubuntu on my P4. But still trying to get acces to my raid partitions.

---

### Post by ubuntu_demon on 2004-11-22
I think I need to recompile my kernel and integrate this driver for 2.4 kernel as described in this howto. But I want to run a 2.6-686 kernel so there's some adaptation necessary. I have no idea how to do it.

[http://www.is.tu-braunschweig.de/~buethe/p4p800_raid.html](http://www.is.tu-braunschweig.de/~buethe/p4p800_raid.html)

Maybe just recompiling the kernel and throwing some raid/via options on works ?

This discussion continues on :

[http://www.ubuntuforums.org/showthread.php?p=22800#post22800](http://www.ubuntuforums.org/showthread.php?p=22800#post22800)

---

### Post by razzmatazz on 2005-01-31
Hey, use dmraid and device-mapper. It needs some tinkering, but is certainly possible to use half-software raid on 2.6.

I've successfully installed and I'm using ICH5-R RAID0 (stripe) as a bootable disk, with windows and ubuntu partitions.

-------
dmraid can be found on [http://people.redhat.com/~heinzm/sw/dmraid/src/](http://people.redhat.com/~heinzm/sw/dmraid/src/). Note to ICH5-R users: the -rc5f version has some issues with raid0 disk ordering, -rc6f should fix that. Write me, I can send a "fixed" version for the time rc6 is not available.

You'll also need to modify /etc/mkinitrd a bit.. if someone is interested I can give more  details/examples.

---

### Post by ubuntu_demon on 2005-01-31
[QUOTE=razzmatazz]Hey, use dmraid and device-mapper. It needs some tinkering, but is certainly possible to use half-software raid on 2.6.

I've successfully installed and I'm using ICH5-R RAID0 (stripe) as a bootable disk, with windows and ubuntu partitions.

-------
dmraid can be found on [http://people.redhat.com/~heinzm/sw/dmraid/src/](http://people.redhat.com/~heinzm/sw/dmraid/src/). Note to ICH5-R users: the -rc5f version has some issues with raid0 disk ordering, -rc6f should fix that. Write me, I can send a "fixed" version for the time rc6 is not available.

You'll also need to modify /etc/mkinitrd a bit.. if someone is interested I can give more  details/examples.[/QUOTE]
 thnx
I won't use it because I've decided to do things differently. (my p4 now only has 1 harddisk)

---

### Post by Z3K3 on 2005-05-03
Custom kernel including VT6410 Support.

This is a custom, testing (aka beta) 2.6.12 kernel that includes support for the VIA VT6410 IDE RAID Controller.

!!!!USE AT YOUR OWN RISK!!!!

[http://www.fazekas.net/ubuntu/kernel/index.html](http://www.fazekas.net/ubuntu/kernel/index.html)

```
wget http://www.fazekas.net/ubuntu/kernel/linux-image-2.6.12-1-386_2.6.11.91-1.2custom_i386.deb

``` 

then

```
dpkg -i linux-image-2.6.12-1-386_2.6.11.91-1.2custom_i386.deb
```

-- Chris Fazekas (Z3K3)

P.S.  I have not tested this with the controllers built in RAID.  I am just using the VT6410 IDE controllers to access my IDE drives.  The drives show up as /dev/hde /dev/hdf.

---

### Post by ubuntu_demon on 2005-05-04
[QUOTE=Z3K3]Custom kernel including VT6410 Support.

This is a custom, testing (aka beta) 2.6.12 kernel that includes support for the VIA VT6410 IDE RAID Controller.

!!!!USE AT YOUR OWN RISK!!!!

[http://www.fazekas.net/ubuntu/kernel/index.html](http://www.fazekas.net/ubuntu/kernel/index.html)

```
wget http://www.fazekas.net/ubuntu/kernel/linux-image-2.6.12-1-386_2.6.11.91-1.2custom_i386.deb

``` 

then

```
dpkg -i linux-image-2.6.12-1-386_2.6.11.91-1.2custom_i386.deb
```

-- Chris Fazekas (Z3K3)

P.S.  I have not tested this with the controllers built in RAID.  I am just using the VT6410 IDE controllers to access my IDE drives.  The drives show up as /dev/hde /dev/hdf.[/QUOTE]
 good work!

---

### Post by Tryforceful on 2006-01-31
```
You are attempting to install an initrd kernel image (version
2.6.12-1-386) but you do not seem to have a mkinitrd command in the
path. This will break the installation, unless initrd-tools are also
being installed right now.

Could not find mkinitrd in path. at /var/lib/dpkg/tmp.ci/preinst line 188.
dpkg: dependency problems prevent configuration of linux-image-2.6.12-1-386:
 linux-image-2.6.12-1-386 depends on initrd-tools (>= 0.1.78ubuntu1); however:
  Package initrd-tools is not installed.
dpkg: error processing linux-image-2.6.12-1-386 (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-2.6.12-1-386
```

I got the above message before (see EDIT below).

I have the exact same hardware that ubuntu_demon has (had?), P4P800 deluxe with VIA VT6410 parallel RAID controller.  Only difference is that I have two RAID-0 arrays out of four HDDs instead of just one. (Also I'm running breezy badger 5.10) I first got a [lead]("https://wiki.ubuntu.com/FakeRaidHowto") as to installing ubuntu permanently on an array by booting the Live CD (I'm on it now) and using dmraid as razzmatazz said, but it seems that dmraid isn't recognizing anything, at least in its current state  ("no block devices found" pops up every time I call it).

I'd like to try what you've suggested (so graciously), Z3K3, but it seems like the Live 'install' doesn't have all the files I need for this... & all my drives are occupied by the RAID arrays, so I can't really install permanently... or can I?

Any guidance would be greatly appreciated! Thanks.


-Tryforceful :-?


EDIT:
So apparently I didn't have & could get initrd-tools from the package manager >_<, but when it tried to install I got the following error message:
```
Unpacking replacement linux-image-2.6.12-1-386 ...
Setting up linux-image-2.6.12-1-386 (2.6.11.91-1.2custom) ...
File descriptor 3 left open
File descriptor 4 left open
File descriptor 5 left open
File descriptor 6 left open
File descriptor 7 left open
    Finding all volume groups
  No volume groups found
/usr/sbin/mkinitrd: /dev/mapper/casper-snapshot: Cannot find LVM device
Failed to create initrd image.
dpkg: error processing linux-image-2.6.12-1-386 (--install):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 linux-image-2.6.12-1-386

```
That "no volume groups found" scares me a little. But I'm not sure what happened;  I hope I don't hafta restart, cuz I can't exactly, can I? (running a Live CD?)

Thanks again.

---

