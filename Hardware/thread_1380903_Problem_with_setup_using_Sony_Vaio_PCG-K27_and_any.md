---
title: "Problem with setup using Sony Vaio PCG-K27 and any dist later than 7.x"
date: 2010-01-14
forum: Hardware
---

### Post by dsimmie on 2010-01-14
Hey,

I'm new to linux and am having trouble running any distribution later than gutsy with my vaio notebook.

I have tried 8.04, 8.10 and 9.10 all do pretty much the same thing.

They install and boot fine but randomly lock after login. This could be immediately or after a few minutes of operation but has always happened.

Starting a failsafe gnome session and turning off the wlan card seems to fix the issue but that is not really an acceptable fix. I'd say this is a driver problem but I don't really know what to look for or do..

Any suggestions would be appreciated.

I've had to reinstall gutsy to be able to post here but would like to use a later supported distribution as my package manager cannot find any packages.

Here is my setup

Ubuntu: 7.10
Hardware:

WLAN: Atheros AR5212/AR5213 Multiprotocol MAC/baseband processor
GPU: ATI Radeon IGP 340m
HD: Hitachi DK23fa-80
Proc: Mobile INTEL pentium 3.06ghz

Bios: Phoenix R0110X1, released 05/19/2004

Also gutsy lists this driver as restricted (which is not in later versions):
Atheros hardware access layer

Sorry if I left anything out can't get sysinfo or hardinfo via package manager, not sure how else to get report..


Thanks

---

### Post by joefer70 on 2010-06-21
Hey dsimmie,

I am having the exact same problem you described with a Sony VAIO PCG-K27 laptop. After installing ubuntu 10.04 and 9.10 the laptop runs but the freezes completely after a few minutes.

A colleague of mine suggested that this may indicate a problem with the display driver for the GPU (ATI Radeon IGP 340m) and suggested swapping out the driver: [https://help.ubuntu.com/community/RadeonDriver]("https://help.ubuntu.com/community/RadeonDriver")

I'm a bit of a newbie, so it may take me a while to try out this solution. In the meantime, I'm going to fall back to v7.x and see if can get it to run reliably with that version.

\\Joe

---

