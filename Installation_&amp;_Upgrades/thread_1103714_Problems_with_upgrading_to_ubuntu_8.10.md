---
title: "Problems with upgrading to ubuntu 8.10"
date: 2009-03-23
forum: Installation &amp; Upgrades
---

### Post by Zuwer on 2009-03-23
Hello, while trying to upgrade to 8.10 from 8.04 I ran into a problem while it was updating. All help will be appreciated for resolving this issue.
> 
Failed to fetch [http://nz.archive.ubuntu.com/ubuntu/pool/universe/x/xserver-xorg-video-nsc/xserver-xorg-video-nsc_2.8.3-4ubuntu1_i386.deb](http://nz.archive.ubuntu.com/ubuntu/pool/universe/x/xserver-xorg-video-nsc/xserver-xorg-video-nsc_2.8.3-4ubuntu1_i386.deb) 404 Not Found
Failed to fetch [http://nz.archive.ubuntu.com/ubuntu/pool/universe/x/xserver-xorg-video-tga/xserver-xorg-video-tga_1.1.0-9ubuntu4_i386.deb](http://nz.archive.ubuntu.com/ubuntu/pool/universe/x/xserver-xorg-video-tga/xserver-xorg-video-tga_1.1.0-9ubuntu4_i386.deb) 404 Not Found
Failed to fetch [http://nz.archive.ubuntu.com/ubuntu/pool/universe/c/cups-pdf/cups-pdf_2.4.8-1ubuntu1_i386.deb](http://nz.archive.ubuntu.com/ubuntu/pool/universe/c/cups-pdf/cups-pdf_2.4.8-1ubuntu1_i386.deb) 404 Not Found
Failed to fetch [http://nz.archive.ubuntu.com/ubuntu/pool/universe/f/fdutils/fdutils_5.5-20060227-2_i386.deb](http://nz.archive.ubuntu.com/ubuntu/pool/universe/f/fdutils/fdutils_5.5-20060227-2_i386.deb) 403 Forbidden
Failed to fetch [http://nz.archive.ubuntu.com/ubuntu/pool/universe/o/openal-soft/libopenal1_1.3.253-4ubuntu1_i386.deb](http://nz.archive.ubuntu.com/ubuntu/pool/universe/o/openal-soft/libopenal1_1.3.253-4ubuntu1_i386.deb) 404 Not Found
Failed to fetch [http://nz.archive.ubuntu.com/ubuntu/pool/universe/c/console-tools/libconsole_0.2.3dbs-65.1ubuntu1_i386.deb](http://nz.archive.ubuntu.com/ubuntu/pool/universe/c/console-tools/libconsole_0.2.3dbs-65.1ubuntu1_i386.deb) 404 Not Found
Failed to fetch [http://nz.archive.ubuntu.com/ubuntu/pool/universe/libe/libelf/libelfg0_0.8.10-2_i386.deb](http://nz.archive.ubuntu.com/ubuntu/pool/universe/libe/libelf/libelfg0_0.8.10-2_i386.deb) 403 Forbidden
Failed to fetch [http://nz.archive.ubuntu.com/ubuntu/pool/universe/libc/libcdio/libiso9660-5_0.78.2+dfsg1-3_i386.deb](http://nz.archive.ubuntu.com/ubuntu/pool/universe/libc/libcdio/libiso9660-5_0.78.2+dfsg1-3_i386.deb) 404 Not Found


I do not understand what I am meant to do to fix this.

---

### Post by SteveDee on 2009-03-23
> **Zuwer said:**
> Hello, while trying to upgrade to 8.10 from 8.04 I ran into a problem while it was updating. All help will be appreciated for resolving this issue.


I do not understand what I am meant to do to fix this.

Other than saying that there were a bunch of packages that Ubuntu tried to retrieve, but couldn't due to internet HTTP 403 & 404 errors, I'm not sure what to suggest.

Is your system basically working?

If your system is working, you could open Synaptic Package Manager and search for each of the packages in turn. If they are not already installed, mark them for installation.

If it helps (& it probably doesn't), on my system these packages from your list are installed:-

xserver-xorg-video-nsc   X.Org X server -- NSC Geode GX1 display driver

xserver-xorg-video-tga   X.Org X server -- TGA display driver

fdutils   Linux floppy utilities

libopenal1   Software implementation of the OpenAL API (libraries)

libconsole   Shared libraries for Linux console and font manipulation

libelfg0   an ELF object file access library

libiso9660-5   library to work with ISO9660 filesystems


...this one is not installed:-
cups-pdf   PDF printer for CUPS

---

### Post by trevbus on 2009-03-23
> **Zuwer said:**
> Hello, while trying to upgrade to 8.10 from 8.04 I ran into a problem while it was updating. All help will be appreciated for resolving this issue.


I do not understand what I am meant to do to fix this.

I have seen similar probs with the Australian archive last night and just now this morning. I'm now using the same URLs without "au" and the upgrade seems OK:

Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/g/glib2.0/libglib2.0-0_2.18.2-0ubuntu2_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/g/glib2.0/libglib2.0-0_2.18.2-0ubuntu2_i386.deb) 404 Not Found [IP: 91.189.88.40 80]
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/g/glib2.0/libglib2.0-data_2.18.2-0ubuntu2_all.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/g/glib2.0/libglib2.0-data_2.18.2-0ubuntu2_all.deb) 404 Not Found [IP: 91.189.88.40 80]

My last attempted upgrade a couple of weeks ago failed, perhaps for the same reason?

---

