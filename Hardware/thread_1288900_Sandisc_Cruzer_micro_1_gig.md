---
title: "Sandisc Cruzer micro 1 gig"
date: 2009-10-11
forum: Hardware
---

### Post by pvalley on 2009-10-11
Hi I just switched over to ubuntu from Vista and the only thing wrong is that I cannot see my sandisc micro cruzer it shows up in lsusb as the following

Bus 004 Device 014: ID 0781:5151 SanDisk Corp. Cruzer Micro 256/512MB Flash Drive

but does not show on my desktop
using 8.04

---

### Post by sgosnell on 2009-10-11
Is it set for MTP or MSC?

---

### Post by pvalley on 2009-10-12
not sure what that is or even how to set it

---

### Post by sgosnell on 2009-10-12
There are two different USB modes, and if the wrong one is set the files won't be seen.  It is probably set to MTP, and you may need to install some files as shown in the Ubuntu help system:

1.4.2.&#8195;MTP Media Players

A number of MP3 players, such as those produced by Samsung use 
			Media Transfer Protocol(MTP). These devices, when used with the correct
			driver, often appear in Windows as a media device but can be accessed as a USB
			device.

Ubuntu supports these devices but requires two steps:

   1. Install the mtpfs 
      				and mtp-tools packages.
   2. Open Applications &#9656; Sound & Video &#9656; Rhythmbox Music Player.
   3. Click Edit &#9656; Plugins
   4. Tick the Portable Players - MTP plugin.
   5. Click Close.

Your device will now be displayed in the left hand pane under Devices 
			when connected.

The mode in use when the files were added determines which mode has to be used to access them.  The files on my Sansa Clip won't show in Windows at all.

---

