---
title: "[SOLVED] fbi: fbgs will not open PDF files"
date: 2008-11-06
forum: General Help
---

### Post by Poyntz on 2008-11-06
Binary package : fbi
Ubuntu Release: Ubuntu 8.10 (*Intrepid Ibex*)
Package Version: 2.07-1

I expected to see a the unformatted text of the PDF file but instead, after trying to load a PDF file through the **fbgs** package of **fbi**
(ie, in bash: fbgs 355Lecture10_Governing_Internet.pdf )

I got the following output:

------------START OF SHELL OUTPUT---------------
### rendering pages, please wait ... ##

GPL Ghostscript 8.63 (2008-08-01)
Copyright (C) 2008 Artifex Software, Inc. All rights reserved.
This software comes with NO WARRANTY: see the file PUBLIC for details.
   **** Warning: File has an invalid xref entry: 34. Rebuilding xref table.
Processing pages 1 through 7.
Page 1
Page 2
Page 3
Page 4
Page 5
Page 6
Page 7

   **** This file had errors that were repaired or ignored.
   **** The file was produced by:
   **** >>>> Mac OS X 10.5.5 Quartz PDFContext <<<<
   **** Please notify the author of the software that produced this
   **** file that it does not conform to Adobe's published PDF
   **** specification.

using "DejaVu Sans Mono-16", pixelsize=16.67 file=/usr/share/fonts/truetype/ttf-dejavu/DejaVuSansMono.ttf
ioctl VT_GETSTATE: Invalid argument (not a linu console?)
------------END OF SHELL OUTPUT---------------

How can I fix this?

---

### Post by Poyntz on 2008-11-14
Ok. I've discovered the way to fix this is to do the following.

Open menu.lst in a text editor:
```
sudo vim /boot/grub/menu.lst
``` 

Search for **defoptions=** and add the **vga=791** after **# defoptions=quiet splash** 

Then search for **/boot/vmlinuz** and add **vga=791** to the end of the line

- this makes the dimensions of shell adequate to support fbi

---

### Post by Makmiller on 2009-10-17
Hi, 

I didn't manage to get fbgs working on my computer...  I get the same error message mentioned in the first message of this thread (i.e. ioctl VT_GETSTATE: Invalid argument (not a linu console?)). I added vga=791 as indicated above, but I continue getting the same error message 
(actually, when I change my menu.lst file, the page that appears when loading ubuntu shows "ubuntu" aligned to the right side).

I don't know if that makes any difference, but I'm dual-booting ubuntu with windows. I'm using fbi version 2.07-1.

So, do you have any suggestion of how I can solve this problem?

Thanks already!

mak

---

