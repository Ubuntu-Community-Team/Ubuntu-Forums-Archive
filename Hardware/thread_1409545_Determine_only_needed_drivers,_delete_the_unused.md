---
title: "Determine only needed drivers, delete the unused"
date: 2010-02-17
forum: Hardware
---

### Post by volkswagner on 2010-02-17
Hi all,

I hope this is the best category.  Although this question is not directly for Ubuntu, it should apply none the less.

I am running Debian Lenny, LXDE on a WebDT366.  It only has a 524MB SSD for the OS.  I would like to trim the fat by removing driver files that don't apply.

How can I determine what drivers are being utilised, and which are not?

I have been using the du command to find fat folders.  I found and deleted the following without issue.

```
$ ls -alt /usr/lib/dri
total 32657
drwxr-xr-x 57 root root   10824 2009-11-28 17:03 ..
drwxr-xr-x  2 root root     528 2009-11-27 04:56 .
-rw-r--r--  1 root root 2103776 2008-12-14 01:02 trident_dri.so
-rw-r--r--  1 root root 2178756 2008-12-14 01:02 unichrome_dri.so
-rw-r--r--  1 root root 2188828 2008-12-14 01:02 i810_dri.so
-rw-r--r--  1 root root 2293692 2008-12-14 01:02 i915_dri.so
-rw-r--r--  1 root root 2316060 2008-12-14 01:02 i965_dri.so
-rw-r--r--  1 root root 2253408 2008-12-14 01:02 mach64_dri.so
-rw-r--r--  1 root root 2301884 2008-12-14 01:02 mga_dri.so
-rw-r--r--  1 root root 2184252 2008-12-14 01:02 r128_dri.so
-rw-r--r--  1 root root 2261276 2008-12-14 01:02 r200_dri.so
-rw-r--r--  1 root root 2191068 2008-12-14 01:02 r300_dri.so
-rw-r--r--  1 root root 2224000 2008-12-14 01:02 radeon_dri.so
-rw-r--r--  1 root root 2158620 2008-12-14 01:02 s3v_dri.so
-rw-r--r--  1 root root 2227296 2008-12-14 01:02 savage_dri.so
-rw-r--r--  1 root root 2248188 2008-12-14 01:02 sis_dri.so
-rw-r--r--  1 root root 2241852 2008-12-14 01:02 tdfx_dri.so

``` 

I just guessed all the above were not needed video drivers, which gained me 32MB or nearly 7% disk space for / partition. 

I would like a more realistic approach.  I thought I could determine loaded drivers with dmesg, but that does not appear correct.

Any other suggestions for removing fat are appreciated.

---

