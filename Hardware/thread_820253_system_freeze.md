---
title: "system freeze"
date: 2008-06-06
forum: Hardware
---

### Post by ezekiel77 on 2008-06-06
Hi, I have a AMD atlon 64 3500 with 1 Gb of Kingmax. I have 2 hard disk, one western digital 80 Gb ( where run my ubuntu 8.04) and a segate 250Gb both with ext3 file system.
My mother board is a ABIT KN8 with socket 939.
And I have a Nvidia 7600 Gt XFX 512Mb.
I have installed more distribution (slackware, frugalware, mandriva, fedora and ubuntu) but all distros caused me problems, the system freeze.
sometimes happens many times a day, sometimes not happening for days, I have not yet understood what may be the causes of freeze.
can someone tell me know if problems with this hardware configuration and possible solutions.
one last thing, sometimes led the keyboard light up and go out as when there is a kernel panic but it seems strange that happens with every distros


ezekiel77

---

### Post by johnny47ns on 2009-09-16
The same happens to me, too. Windows works fine but any linux distro I tried (Mandriva, Fedora, SuSE, Debian... now it's Ubuntu 8.04) started freezing clinically after computer warms up a bit. Windows XP works fine, though!

Today I decided to isolate a problem on, since it has to be harware related. I pulled out one 128Mb memory module and changed ATA cable from Primary to Secondary on my old Maxtor 60gb HDD. Just when Gnome started, it stopped responding.

So fine, I restart computer and then get an error message after booting a while
```
init: Unable to execute "/bin/sh" for rcS: Not a directory
init: rcS process (2456) terminated with status 255

```

When I started Ubuntu from the CD, I saw that /bin directory is still on the partition, but corrupted. I cannot **cd**, **rm**, **chmod** OR **mkdir** /bin directory because it got corrupted; it's permission attributes were literally "d?????????".

Has anyone seen anything like this (it's kinda hard to search for)?? Is there any way to fix my distro without formatting the partition?

---

