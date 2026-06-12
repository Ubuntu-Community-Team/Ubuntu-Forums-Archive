---
title: "package `sudo' is missing final newline"
date: 2006-01-13
forum: Installation &amp; Upgrades
---

### Post by m0o0gg on 2006-01-13
When ever I run Update Manager it always fails with this message:

[FONT="Courier New"]E: /var/cache/apt/archives/cpio_2.5-1.2ubuntu1.1_i386.deb: files list file for package `sudo' is missing final newline[/FONT]

I tried doing:
[LIST]
[*]apt-get autoclean
[*]apt-get update
[/LIST]

But I still get this error when I try to update.  I haven't touched my software sources... all are "Officially supported".

I even tried this:

root@fred:~# apt-get install sudo

Reading package lists... Done
Building dependency tree... Done
The following packages will be upgraded:
  sudo
1 upgraded, 0 newly installed, 0 to remove and 11 not upgraded.
Need to get 0B/159kB of archives.
After unpacking 0B of additional disk space will be used.

Preconfiguring packages ...
(Reading database ... dpkg: error processing /var/cache/apt/archives/sudo_1.6.8p9-2ubuntu2.3_i386.deb (--unpack):
 files list file for package `sudo' is missing final newline
Errors were encountered while processing:
 /var/cache/apt/archives/sudo_1.6.8p9-2ubuntu2.3_i386.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by memarko on 2006-02-18
Probaby the package database of installed packages is damaged. Try to find it and repair it. Probably is text file.
I have a same problem. Now i am looknig for the location. If you find it before me, please tell me the location.

---

### Post by memarko on 2006-02-18
Now it is working. This is acting so strange. So try again to install after reset.

---

