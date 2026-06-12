---
title: "DVD Burn ends prematurely"
date: 2010-06-13
forum: Hardware
---

### Post by epet7_wp on 2010-06-13
I've tried to burn several files to a blank DVD -R, but the process ends in a prematurely way. 

I'm using a Ubuntu Lucid Lynx 10.04 x86 installation over a Biostar motherboard with a Via SATA chipset (8738 to be precise), and a LG GH22NS50 DVD drive. I was aware of the issue with DMA signal (or something like that) with the sata_via module which causes a DVD been burn with data corruption. This issue was solved and merged into kernel 2.6.34, so I had installed a ppa kernel 2.6.34 in my Ubuntu system; because before that I was unable to burn any kind of disc.

I happily burn some disc a few days ago. But now, after some updates (I really can't remember which packages has been updated since then) I get a Brasero error after 2 or 3 seconds of burning has passed. I have to add that I tried the Brasero 2.30.0 (downgrading the 2.30.1) but with the same result.

I don't think the problem is the sata_via kernel module any more, because dmesg doesn't show a emask exception (like 2.6.32 kernel, with the DMA problem).

I attached the brasero output and the content of message log file during the burning process. Thanks.

PD: Sorry my bad English, I speak spanish.

---

### Post by garvinrick4 on 2010-06-13
Brasero Disk Burner works well for me. So I would just get a fresh copy

rick@rick-laptop:~$ aptitude show brasero
Package: brasero
State: installed
Automatically installed: no
Version: 2.30.1-0ubuntu2
Priority: optional
Section: gnome
Maintainer: Ubuntu Desktop Team <ubuntu-desktop@lists.ubuntu.com>
Uncompressed Size: 1,163k
Depends: libatk1.0-0 (>= 1.29.3), libbeagle1 (>= 0.3.9), libbrasero-media0 (>=
         2.27.92), libc6 (>= 2.7), libcairo2 (>= 1.2.4), libdbus-1-3 (>= 1.0.2),
         libdbus-glib-1-2 (>= 0.78), libfontconfig1 (>= 2.8.0), libfreetype6 (>=
         2.2.1), libgconf2-4 (>= 2.27.0), libglib2.0-0 (>= 2.23.5),
         libgstreamer-plugins-base0.10-0 (>= 0.10.12), libgstreamer0.10-0 (>=
         0.10.15), libgtk2.0-0 (>= 2.20.0), libice6 (>= 1:1.0.0),
         liblaunchpad-integration1 (>= 0.1.17), libnautilus-extension1 (>=
         1:2.29.1), libpango1.0-0 (>= 1.14.0), libsm6, libtotem-plparser17 (>=
         2.29.1), libunique-1.0-0 (>= 1.0.0), libxml2 (>= 2.7.4),
         gstreamer0.10-plugins-base (>= 0.10.0), gnome-icon-theme, gvfs, wodim,
         genisoimage, dvd+rw-tools, brasero-common (>= 2.30), brasero-common (<
         2.31)
Recommends: gstreamer0.10-plugins-good
Suggests: gstreamer0.10-plugins-bad, gstreamer0.10-plugins-ugly,
          gstreamer0.10-fluendo-mp3, cdrdao, dvdauthor, vcdimager, libdvdcss2
Conflicts: nautilus-cd-burner
Replaces: libbrasero-media0 (< 2.29.2-0ubuntu2)
Description: CD/DVD burning application for GNOME
 Brasero is a simple application to burn, copy and erase CD and DVD media:
 audio, video or data. It features among other things: 
 * On-the-fly burning 
 * Multisession support 
 * On-the-fly conversion of music playlists in all formats supported by
   GStreamer 
 * CD-Text writing 
   
 This package contains the main binary, the burning plugins and the nautilus
 extension. 
 
 The following packages, if installed, will provide Brasero with added
 functionality: 
 * GStreamer backends to support more audio or video formats 
 * dvdauthor to create video DVDs 
 * vcdimager to create VCDs or SVCDs 
 * libdvdcss2 to copy encrypted DVDs
Homepage: [http://www.gnome.org/projects/brasero/](http://www.gnome.org/projects/brasero/)

rick@rick-laptop:~$ 
```
sudo apt-get remove brasero
```
```
sudo apt-get clean
```
```
sudo apt-get install brasero
```

---

### Post by epet7_wp on 2010-06-13
Thanks about a quick reply :)

But, I forgot to mention that I've already did that.
Even more, I do a purge option for brasero, expecting a wrong config file (also, I deleted the brasero config folder under my home directory).

Still, the problem persist.

---

