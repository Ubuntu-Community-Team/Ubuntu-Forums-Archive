---
title: "Problems with Memory Stick on Vaio"
date: 2008-07-03
forum: Hardware
---

### Post by gfrangia on 2008-07-03
My internal Memory Stick reader on Vaio VGN-SZ4M has problems to mount memory stick card:(. I use Ubuntu 8.04. The card is visible to the system but a problem occurs. Can anyone help me?

Following the dmesg log:

[  540.769608] sd 4:0:0:0: [sdb] 16220160 512-byte hardware sectors (8305 MB)
[  540.773378] sd 4:0:0:0: [sdb] Write Protect is off
[  540.773384] sd 4:0:0:0: [sdb] Mode Sense: 03 00 00 00
[  540.773387] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[  540.775452] sd 4:0:0:0: [sdb] 16220160 512-byte hardware sectors (8305 MB)
[  540.776952] sd 4:0:0:0: [sdb] Write Protect is off
[  540.776957] sd 4:0:0:0: [sdb] Mode Sense: 03 00 00 00
[  540.776959] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[  540.776966]  sdb: sdb1
[  542.235596] VMBlock warning: DentryOpRevalidate: invalid args from kernel
[  542.235618] VMBlock warning: DentryOpRevalidate: invalid args from kernel
[  542.284648] VMBlock warning: DentryOpRevalidate: invalid args from kernel
[  542.284914] VMBlock warning: DentryOpRevalidate: invalid args from kernel
[  676.904975] VMBlock warning: DentryOpRevalidate: invalid args from kernel
[  676.905002] VMBlock warning: DentryOpRevalidate: invalid args from kernel
[  676.940315] VMBlock warning: DentryOpRevalidate: invalid args from kernel
[  676.940342] VMBlock warning: DentryOpRevalidate: invalid args from kernel
[  723.433160] VMBlock warning: DentryOpRevalidate: invalid args from kernel
[  723.433188] VMBlock warning: DentryOpRevalidate: invalid args from kernel
[  739.053334] VMBlock warning: DentryOpRevalidate: invalid args from kernel
[  739.053362] VMBlock warning: DentryOpRevalidate: invalid args from kernel
[  740.317262] VMBlock warning: DentryOpRevalidate: invalid args from kernel
[  740.317299] VMBlock warning: DentryOpRevalidate: invalid args from kernel
[  740.320519] VMBlock warning: DentryOpRevalidate: invalid args from kernel
[  740.320750] VMBlock warning: DentryOpRevalidate: invalid args from kernel
[  759.295721] tifm_core: MemoryStick card detected in socket 0:0
[ 1387.812321] ACPI: PCI interrupt for device 0000:09:04.2 disabled
[ 1404.344399] ACPI: PCI Interrupt 0000:09:04.2[C] -> GSI 22 (level, low) -> IRQ 23
[ 1624.870316] tifm_core: MemoryStick card detected in socket 0:0
[ 2090.469704] /dev/vmmon[6463]: host clock rate change request 83 -> 1043
[ 2100.460388] /dev/vmmon[6463]: host clock rate change request 1043 -> 83
[ 2106.380495] /dev/vmmon[6463]: host clock rate change request 83 -> 1043
[ 2116.381826] /dev/vmmon[6463]: host clock rate change request 1043 -> 83
[ 2602.285067] tifm0 : demand removing card from socket 0:0
[ 2606.420005] tifm_core: MemoryStick card detected in socket 0:0

---

### Post by kmilosol1 on 2008-07-08
You can try it:

svn co -r155 [http://svn.berlios.de/svnroot/repos/tifmxx/trunk/driver/](http://svn.berlios.de/svnroot/repos/tifmxx/trunk/driver/)
cd driver/
wget [http://www.sw83.de/misc/tifm_ms.patch](http://www.sw83.de/misc/tifm_ms.patch)
patch -p0 < tifm_ms.patch
make
sudo make install

Make sure if you have install subversion if not:

apt-get intall subversion,:lolflag:

Resource: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/222557]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/222557")

Note: It's work for vaio VGN-NR120E

---

### Post by core on 2008-08-06
I digged around and didn't find that launchpad bug, that was exactly my issue for weeks now.

It works perfectly now, thanks a lot!

---

### Post by mattboschetti on 2008-09-12
hey kmilosol1,
thank you, i ve tried these steps and they worked perfectly...
note that i have a vaio fz21s...

thanks

---

### Post by _Jo_ on 2008-09-14
I also had the same problem. Thank kmilosol1 for helping!
(Sony Vaio PCG-9W4M)

---

### Post by waitcursor on 2008-09-16
Whenever I try the make install command I always receive errors that it cannot stat: file ...................... I used sudo make but same could it be that the drivers location under the kernel needs a specific user account for accessing/creating the drivers?
Hope somebody can help me with this one.
regards,
waitcursor

---

### Post by danmiddle2 on 2008-09-30
> **kmilosol1 said:**
> You can try it:

svn co -r155 [http://svn.berlios.de/svnroot/repos/tifmxx/trunk/driver/](http://svn.berlios.de/svnroot/repos/tifmxx/trunk/driver/)
cd driver/
wget [http://www.sw83.de/misc/tifm_ms.patch](http://www.sw83.de/misc/tifm_ms.patch)
patch -p0 < tifm_ms.patch
make
sudo make install

Make sure if you have install subversion if not:

apt-get intall subversion,:lolflag:

Resource: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/222557]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/222557")

Note: It's work for vaio VGN-NR120E

Thanks kmilosol1 - the fixed the problem on my UX1XN.

---

### Post by IagainstI on 2008-10-16
> **kmilosol1 said:**
> You can try it:

svn co -r155 [http://svn.berlios.de/svnroot/repos/tifmxx/trunk/driver/](http://svn.berlios.de/svnroot/repos/tifmxx/trunk/driver/)
cd driver/
wget [http://www.sw83.de/misc/tifm_ms.patch](http://www.sw83.de/misc/tifm_ms.patch)
patch -p0 < tifm_ms.patch
make
sudo make install

Make sure if you have install subversion if not:

apt-get intall subversion,:lolflag:

Resource: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/222557]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/222557")

Note: It's work for vaio VGN-NR120E

Sweet!!  This worked for my Toshiba Satellite M55-S325.  Many thanks!

---

### Post by tobimat on 2008-11-14
Is this still supposed to work on 8.10?

I tried the steps above, but during "make" I get a ton of error messages, starting with

"/memstick.h:279: error: field &#8216;cdev&#8217; has incomplete type"

and eventually ending on

"make: *** [all] Error 2"

I am on a Vaio FE-21M.

---

### Post by sugardeath on 2008-11-23
Yeah, I get the same error when I try to make it.  Any ideas?  I would REALLY love to be able to use my memory stick reader.

---

### Post by MissingLink on 2008-12-09
Same thing here, worked on my vgn fs315s back on 8.04. 

I have to find a new solution everytime I upgrade my ubuntu and it's becoming rather annoying :mad:

Edit: just found this launchpad bug report. Apparently, the module won't compile with 2.6.27...

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/222557](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/222557)

---

