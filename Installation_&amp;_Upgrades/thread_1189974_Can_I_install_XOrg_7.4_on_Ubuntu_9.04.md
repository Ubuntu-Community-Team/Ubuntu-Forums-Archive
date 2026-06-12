---
title: "Can I install XOrg 7.4 on Ubuntu 9.04?"
date: 2009-06-17
forum: Installation &amp; Upgrades
---

### Post by manchro on 2009-06-17
Hi,

I use Ubuntu 9.04 and i have problems with the ATI X550 videocard (if I use 2 screens, with my tvcard, ...). I would like to install the [ATI Catalyst Display Driver 9.3]("http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.20&lang=English")  (this is the latest version of the catalyst driver who support my videocard). But this version does not work with XOrg 7.5.

```

[[SIZE=3]**Release Notes:**[/SIZE]]("https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/catalyst_93_linux.pdf")
[SIZE=2]
[/SIZE] **[SIZE=2]System Requirement[/SIZE]s**:
Before attempting to install the ATI CatalystTM Linux software suite,
the following software must be installed:

[LIST]
[*] XOrg 6.8, 6.9, 7.0, 7.1, 7.2, 7.3 or 7.4
[*] Linux kernel 2.6 or above
[*] glibc version 2.2 or 2.3
[*] POSIX Shared Memory (/dev/shm) support is required for 3D applications
[/LIST]
 
```
I would not like to use other alternative driver.


[COLOR=Red][B]
[SIZE=4]Is it possible to install XOrg 7.4 on Ubuntu 9.04? If, how?[/SIZE]
[/B][/COLOR]

Thanks for read!


I hope someone can help me!



Greetings manchro

---

### Post by izizzle on 2009-06-17
It's probably safest if you hold off on installing a new xserver. Mind telling us the error it gives you when you try to install the driver?

---

### Post by manchro on 2009-06-17
Hi,

thanks for your fast answer. If I try to install the Driver it gives the following error:

```

./ati-driver-installer-9-3-x86.x86_64.run

Created directory fglrx-install.PAjcqf
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.593......................................................
==================================================
ATI Technologies Linux Driver Installer/Packager 
==================================================

Error: ./default_policy.sh does not support version
default:v2:i686:lib::none:2.6.28-11-generic; make sure that the version is being
correctly set by --iscurrentdistro

```



If I use the paramter "--iscurrentdistro" I see the following error message. But I'am not sure, if I use the paramter correctly.

```

./ati-driver-installer-9-3-x86.x86_64.run --iscurrentdistro
Unrecognized flag : --iscurrentdistro
Makeself version 2.1.3 
1) Getting help or info about ./ati-driver-installer-9-3-x86.x86_64.run :
./ati-driver-installer-9-3-x86.x86_64.run -h|--help Print this message
./ati-driver-installer-9-3-x86.x86_64.run -i|--info Print embedded info : title, default target directory, embedded script 
./ati-driver-installer-9-3-x86.x86_64.run -l|--list Print the list of files in the archive
./ati-driver-installer-9-3-x86.x86_64.run -c|--check Checks integrity of the archive
./ati-driver-installer-9-3-x86.x86_64.run --extract NewDirectory Extract this package to NewDirectory only

2) Running ./ati-driver-installer-9-3-x86.x86_64.run :
./ati-driver-installer-9-3-x86.x86_64.run [options] [additional arguments to embedded script] with following options (in that order)
--keep Do not erase target directory after running the embedded script
Following arguments will be passed to the embedded script:
--install Install the driver(default)
--listpkg List all the generatable packages 
--buildpkg package Build "package" if generatable ("package" as returned by --listpkg)
--buildandinstallpkg package Build and Install "package" as returned by --listpkg

```

---

### Post by izizzle on 2009-06-17
My guess is that you are missing some libs that are needed for the install to continue (?) Perhaps someone else on here may be able to help you out.

---

### Post by Mark Phelps on 2009-06-17
Doesn't matter if you ever install all the libraries you need or not -- the Catalyst 9.3 drivers will NOT work with the Xorg version native to Ubuntu 9.04.

However, don't know about "downgrading" to an earlier Xorg by grabbing the source and recompiling the X server.

If you can get that to work, I'd be very interested because, like so many others, I have one of the "older" ATI cards that can not use the restricted drivers in Ubuntu 9.04 due to catalyst-Xorg conflicts.

---

