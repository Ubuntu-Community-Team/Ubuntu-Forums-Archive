---
title: "EPSON Imagescan drivers on 18.04 LTS Bionic"
date: 2019-07-11
forum: Hardware
---

### Post by nought2 on 2019-07-11
Today I made multiple futile attempts to install EPSON proprietary drivers for its Image Scan software on my x64 Ubuntu installation. I searched the interwebs for solutions but none seemed to work.

My scanner is an EPSON Perfection 1660. 
Download link: [http://download.ebz.epson.net/dsc/search/01/search/searchModule](http://download.ebz.epson.net/dsc/search/01/search/searchModule)

The driver bundle downloaded from the EPSON website was this one:
iscan-bundle-1.0.4.x64.deb.tar.gz

This installation package was extracted from *.tar.gz file:
iscan-bundle-1.0.4.x64.deb

Following a recipe found in these forums, I saved the package to the Ubuntu desktop and then ran the following commands in terminal:
```

cd Desktop
cd iscan-bundle-1.0.4.x64.deb
sudo ./install.sh

```

After executing the command to run the script to deploy the package as sudo, the installation routine flashed though the terminal. I thought I was home and hosed. 

When installation had completed, using the Super key I accessed app search which duly presented the icon for Image Scan! for Linux. I double clicked it to launch the software. The program did not launch but after a few seconds' delay a notification box appeared on screen. It read:

> Could not send command to scanner.
Check the scanner's status.

The scanner's connection to the PC via USB cable is good and its power connection is too. The scanner works with Simple Scan. It recognises the scanner as an Epson GT-8300.

After this I tried other methods to install the software. The most straightforward of these was to extract the following three components from the package and sequentially double click them to install each one:
iscan_2.30.3-1_amd64.deb
iscan-data_1.39.0-1_all.deb
iscan-network-nt_1.1.1-1_amd64.deb

This didn't work either. When I attempted to launch Image Scan I got the same error message as before.

I'm brand new to Ubuntu and Linux but trying my best to be self sufficient. However, I cannot find way to get around this obstacle. Knowledgable help to get Image Scan working would be much appreciated.

---

### Post by brian_p on 2019-07-11
The iscan package puts its scanner drivers in /usr/lib/sane. This should be ok, but there is a bug in Ubuntu's libsane that causes it not to look there. See

[https://wiki.debian.org/Scanner#issue](https://wiki.debian.org/Scanner#issue)

for a solution.

---

### Post by nought2 on 2019-07-11
Following the info at the link you provided...

Epson iscan backend files get put in [SIZE=3][FONT=courier new]/usr/lib/sane[/FONT][/SIZE]

That directory contains these files:
[SIZE=3][FONT=courier new]libsane-epkowa.la  libsane-epkowa.so.1  libsane-epkowa.so.1.0.15[/FONT][/SIZE]

But Ubuntu's libsane looks for them in [FONT=courier new][SIZE=3]/usr/lib/x86_64-lunux-gnu/sane[/SIZE][/FONT]
That directory contains numerous [SIZE=3][FONT=courier new]libsane-*[/FONT][/SIZE] files; many peripheral hardware brands are represented.

[FONT=courier new][SIZE=3]/usr/lib/x86_64-linux-gnu/sane[/SIZE][/FONT] must be patched to make frontends (?) also check [FONT=courier new][SIZE=3]/usr/lib/sane[/SIZE][/FONT] for Epson drivers/backends.

With this patch: [https://jff.email/cgit/sane-backends.git/tree/debian/patches/0125-multiarch_dll_search_path.patch](https://jff.email/cgit/sane-backends.git/tree/debian/patches/0125-multiarch_dll_search_path.patch)

How do I apply the patch?

---

### Post by brian_p on 2019-07-11
> **nought2 said:**
> Following the info at the link you provided...

Epson iscan backend files get put in [SIZE=3][FONT=courier new]/usr/lib/sane[/FONT][/SIZE]

That directory contains these files:
[SIZE=3][FONT=courier new]libsane-epkowa.la  libsane-epkowa.so.1  libsane-epkowa.so.1.0.15[/FONT][/SIZE]

But Ubuntu's libsane looks for them in [FONT=courier new][SIZE=3]/usr/lib/x86_64-lunux-gnu/sane[/SIZE][/FONT]

That's on Bionic (Ubuntu 18,04).

> 
That directory contains numerous [SIZE=3][FONT=courier new]libsane-*[/FONT][/SIZE] files; many peripheral hardware brands are represented.

As advised in the link given, put the iscan drivers there too.

> 
[FONT=courier new][SIZE=3]/usr/lib/x86_64-linux-gnu/sane[/SIZE][/FONT] must be patched to make frontends (?) also check [FONT=courier new][SIZE=3]/usr/lib/sane[/SIZE][/FONT] for Epson drivers/backends.

With this patch: [https://jff.email/cgit/sane-backends.git/tree/debian/patches/0125-multiarch_dll_search_path.patch](https://jff.email/cgit/sane-backends.git/tree/debian/patches/0125-multiarch_dll_search_path.patch)

How do I apply the patch?

libsane in disco has the patch applied.

---

### Post by nought2 on 2019-07-11
```
sudo cp -r /usr/lib/sane/. /usr/lib/x86_64-linux-gnu/sane
cd /usr/lib/x86_64-linux-gnu/sane
/usr/lib/x86_64-linux-gnu/sane$ ls
```

Bingo!

Thank you, Brian.

---

