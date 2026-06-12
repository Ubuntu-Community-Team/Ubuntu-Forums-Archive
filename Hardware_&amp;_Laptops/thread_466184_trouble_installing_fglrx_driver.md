---
title: "trouble installing fglrx driver"
date: 2007-06-06
forum: Hardware &amp; Laptops
---

### Post by robhilken on 2007-06-06
I am trying to get 3d acceleration working on my ATI Radeon XPRESS 200M 5955 (PCIE) by following the instructions at [http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide)

I am trying method 2

once the driver is downloaded it has a .bin extension that I wasn't expecting.

I then altered the code below to include the .bin (I have no idea if that is the right thing to do)

```
sudo bash ati-driver-installer-8.37.6-x86.x86_64.run.bin --buildpkg Ubuntu/feisty
```

i get:

```
Created directory fglrx-install.f13528
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.37.6.....................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................Extraction failed.
Signal caught, cleaning up
```

I have tried redownloading the file a few times but I still get the same error.

Can anyone help?

---

### Post by mitch.c on 2007-06-07
It's been a while, and I don't know if this is an issue still with Feisty, but do:
```
$ ls -l $(which sh)
```
If the output reads (at the end):
```
 /bin/sh -> dash
```
then try:
```
$ sudo ln -sf /bin/bash /bin/sh
$ sudo bash ati-driver-installer-8.37.6-x86.x86_64.run.bin --buildpkg Ubuntu/feisty
$ sudo ln -sf /bin/dash /bin/sh

```
[URL="http://ubuntuforums.org/showthread.php?t=377083"][COLOR="Red"]
UAResolved[/COLOR][/URL]

---

### Post by intMain on 2007-07-01
> **robhilken said:**
> I am trying to get 3d acceleration working on my ATI Radeon XPRESS 200M 5955 (PCIE) by following the instructions at [http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide)

I am trying method 2

once the driver is downloaded it has a .bin extension that I wasn't expecting.

I then altered the code below to include the .bin (I have no idea if that is the right thing to do)

```
sudo bash ati-driver-installer-8.37.6-x86.x86_64.run.bin --buildpkg Ubuntu/feisty
```

i get:

```
Created directory fglrx-install.f13528
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.37.6.....................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................Extraction failed.
Signal caught, cleaning up
```

I have tried redownloading the file a few times but I still get the same error.

Can anyone help?

i put the file in a folder on my desktop and chmod 777 ati-blah.run

---

