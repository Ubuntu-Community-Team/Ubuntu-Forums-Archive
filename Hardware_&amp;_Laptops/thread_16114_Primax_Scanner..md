---
title: "Primax Scanner."
date: 2005-02-19
forum: Hardware &amp; Laptops
---

### Post by Slay3r on 2005-02-19
I am trying to get a scanner working on Ubuntu "Primax Colorado 9600" using sanes pxscan 41 but when i try to make the file i get the error below.

root@system:/home/scotland/pxscan # make
gcc -O -c -g -Wall -I/usr/local/tiff-v3.4/libtiff/ pxscan.c
make: gcc: Command not found
make: *** [pxscan.o] Error 127

---

### Post by Slay3r on 2005-02-19
fixed that with gcc but now i get the below.

gcc -O -c -g -Wall -I/usr/local/tiff-v3.4/libtiff/ pxscan.c
pxscan.c:102:20: tiffio.h: No such file or directory
In file included from pxscan.c:108:
pxscan.h:178: error: parse error before '*' token
pxscan.h:180: error: parse error before '*' token
pxscan.c:266: error: parse error before '*' token
pxscan.c: In function `tiff_open':
pxscan.c:268: error: `tiffile' undeclared (first use in this function)
pxscan.c:268: error: (Each undeclared identifier is reported only once
pxscan.c:268: error: for each function it appears in.)
pxscan.c:268: warning: implicit declaration of function `TIFFOpen'
pxscan.c:268: error: `image' undeclared (first use in this function)
pxscan.c:274: warning: implicit declaration of function `TIFFSetField'
pxscan.c:274: error: `TIFFTAG_IMAGEWIDTH' undeclared (first use in this function)
pxscan.c:275: error: `TIFFTAG_IMAGELENGTH' undeclared (first use in this function)
pxscan.c:276: error: `TIFFTAG_ORIENTATION' undeclared (first use in this function)
pxscan.c:276: error: `ORIENTATION_TOPLEFT' undeclared (first use in this function)
pxscan.c:277: error: `TIFFTAG_PLANARCONFIG' undeclared (first use in this function)
pxscan.c:277: error: `PLANARCONFIG_CONTIG' undeclared (first use in this function)
pxscan.c:278: error: `TIFFTAG_ROWSPERSTRIP' undeclared (first use in this function)
pxscan.c:279: warning: implicit declaration of function `TIFFDefaultStripSize'
pxscan.c:285: error: `TIFFTAG_PHOTOMETRIC' undeclared (first use in this function)
pxscan.c:285: error: `PHOTOMETRIC_RGB' undeclared (first use in this function)
pxscan.c:286: error: `TIFFTAG_SAMPLESPERPIXEL' undeclared (first use in this function)
pxscan.c:287: error: `TIFFTAG_BITSPERSAMPLE' undeclared (first use in this function)
pxscan.c:288: error: `TIFFTAG_COMPRESSION' undeclared (first use in this function)
pxscan.c:288: error: `COMPRESSION_NONE' undeclared (first use in this function)
pxscan.c: At top level:
pxscan.c:322: error: parse error before '*' token
pxscan.c: In function `tiff_close':
pxscan.c:324: warning: implicit declaration of function `TIFFClose'
pxscan.c:324: error: `tiffile' undeclared (first use in this function)
pxscan.c: In function `readscandata':
pxscan.c:723: error: `TIFF' undeclared (first use in this function)
pxscan.c:723: error: `tiffile' undeclared (first use in this function)
pxscan.c:837: warning: implicit declaration of function `TIFFWriteScanline'
pxscan.c: In function `scan':
pxscan.c:1130: warning: comparison is always false due to limited range of data type
make: *** [pxscan.o] Error 1

---

### Post by Slay3r on 2005-02-20
Used synaptiic to install primaxscan

Checked all my libtiff stuff and ran make and i get the info posted below.

gcc -O -c -g -Wall -I/usr/local/tiff-v3.4/libtiff/ pxscan.c
pxscan.c: In function `scan':
pxscan.c:1130: warning: comparison is always false due to limited range of data type
gcc -O -c -g -Wall -I/usr/local/tiff-v3.4/libtiff/ probe_lp.c
gcc -O -c -g -Wall -I/usr/local/tiff-v3.4/libtiff/ portio.c
portio.c: In function `epp_off':
portio.c:42: warning: implicit declaration of function `ioperm'
portio.c:43: warning: implicit declaration of function `iopl'
cc -ltiff -lm -O -g pxscan.o probe_lp.o portio.o -o pxscan

and if i do cp pxscan.1 /usr/locan/man/man1 as the readme info says i still cant get xsane to show the scanner it keeps giving "No devices available".

---

