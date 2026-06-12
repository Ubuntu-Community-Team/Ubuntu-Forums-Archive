---
title: "Trouble Installing SCSI Driver"
date: 2008-12-28
forum: Installation &amp; Upgrades
---

### Post by chimpunk on 2008-12-28
Linux newbie trying to install the driver for an ATTO U320 PCIe card, to run an LTO-3 tape deck with TAR. I'm used to OSX, and way in the past, IRIX, DOS 3 and CP/M before that, but I'm an artist, not an engineer, so go easy on idiot me. Working now on a Mac Pro, rEFIt, Ubuntu 64 Heron on it's own drive. The ATTO driver instructions say I have to compile/install as Root from the tarball, and I've made a root PWD, but when I try "login root" in the BASH (while logged in as Administrator user), it tells me:

No UMTP entry. You must exec "login" from the lowest level "SH"

Whatever that means. I see no help reference to different levels of shell. Internet postings on this subject suggest it's caused by everything from a corrupted UTMP file to the file system being too full (600+ GB free in this case). Answers seem psychotic to me, but neither TAR nor ATTO's admin utility properly see the deck, so I've got to get the %$#@#& driver installed.

Instructions also say that only Red Hat and SUSE are supported, but I presume that doesn't mean it won't compile for Ubuntu, just not supported? Also, how does one enable HFS+ in GParted?

TIA,

---

### Post by pastalavista on 2008-12-28
There is no actual root in Ubuntu except for the system itself. Just use sudo.

---

