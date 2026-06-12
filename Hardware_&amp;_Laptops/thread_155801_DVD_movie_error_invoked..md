---
title: "DVD movie error invoked."
date: 2006-04-05
forum: Hardware &amp; Laptops
---

### Post by PowerWCRulez on 2006-04-05
Hi all, I put the DVD into CDRW/DVDRom drive, the desktop appeared disc icon with "ROM" in word. auto opened totem player.

The error message says:

Error invoking "dvdnav_get_next_block":
Error reading from DVD

I tried to use other DVD disc, still same message.

How I can solve with my DVD movies?

---

### Post by Phlosten on 2006-04-05
Have you installed libdvdcss2? You will not be able to play encrypted dvd's without this installed.

As far as I know it isnt available in the official repositories. Doing a search in google for 'libdvdcss 1.2.9' should give you somewhere that has the 1.2.9 .deb package. This is the most recent I think.

Then do a 'sudo dpkg -i libdvdcss2_1.2.9-1_i386.deb' or similar depending on the actual filename.

---

### Post by PowerWCRulez on 2006-04-05
[QUOTE=Phlosten]Have you installed libdvdcss2? You will not be able to play encrypted dvd's without this installed.

As far as I know it isnt available in the official repositories. Doing a search in google for 'libdvdcss 1.2.9' should give you somewhere that has the 1.2.9 .deb package. This is the most recent I think.

Then do a 'sudo dpkg -i libdvdcss2_1.2.9-1_i386.deb' or similar depending on the actual filename.[/QUOTE]

dpkg: error processing libdvdcss2_1.2.9-1_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 libdvdcss2_1.2.9-1_i386.deb

??

---

### Post by PowerWCRulez on 2006-04-06
HI there, I got a gxine installed and I edited the hdparm conf to enbled the DMA for a CDRW-DVDRom drive, it's work great :)

---

