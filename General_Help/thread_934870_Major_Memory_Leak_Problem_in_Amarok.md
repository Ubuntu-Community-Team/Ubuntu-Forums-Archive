---
title: "Major Memory Leak Problem in Amarok"
date: 2008-10-01
forum: General Help
---

### Post by tutwabee on 2008-10-01
Amarok is currently leaking memory at an alarming rate.  It eats up to 30 megabytes of memory per second sometimes and is currently at over 3GB of virtual memory used.

As I play songs in amarok output like the output below repeats without stopping.  What is the problem and how can I fix this?  Should I downgrade my version of amarok?  My current amarok version is 1.4.9.
> 
Corrupt JPEG data: 296 extraneous bytes before marker 0x03
Unsupported marker type 0x03
QImage::smoothScale: Image is a null image
QImage::smoothScale: Image is a null image
QImage::smoothScale: Image is a null image
QImage::smoothScale: Image is a null image
QImage::smoothScale: Image is a null image
QImage::smoothScale: Image is a null image
QImage::smoothScale: Image is a null image
In file kernel/qimage.cpp, line 1300: Out of memory
QImage::smoothScale: Image is a null image
In file kernel/qimage.cpp, line 1300: Out of memory
QImage::smoothScale: Image is a null image
In file kernel/qimage.cpp, line 1300: Out of memory
QImage::smoothScale: Image is a null image
In file kernel/qimage.cpp, line 1300: Out of memory
QImage::smoothScale: Image is a null image
Corrupt JPEG data: 296 extraneous bytes before marker 0x03
Unsupported marker type 0x03
QImage::smoothScale: Image is a null image
Corrupt JPEG data: 296 extraneous bytes before marker 0x03
Unsupported marker type 0x03
QImage::smoothScale: Image is a null image
QImage::smoothScale: Image is a null image
QImage::smoothScale: Image is a null image
QImage::smoothScale: Image is a null image
QImage::smoothScale: Image is a null image
QImage::smoothScale: Image is a null image
QImage::smoothScale: Image is a null image
In file kernel/qimage.cpp, line 1300: Out of memory
QImage::smoothScale: Image is a null image
In file kernel/qimage.cpp, line 1300: Out of memory
QImage::smoothScale: Image is a null image
In file kernel/qimage.cpp, line 1300: Out of memory
QImage::smoothScale: Image is a null image
In file kernel/qimage.cpp, line 1300: Out of memory
QImage::smoothScale: Image is a null image
Corrupt JPEG data: 296 extraneous bytes before marker 0x03
Unsupported marker type 0x03
QImage::smoothScale: Image is a null image
Corrupt JPEG data: 296 extraneous bytes before marker 0x03
Unsupported marker type 0x03
QImage::smoothScale: Image is a null image
QImage::smoothScale: Image is a null image
QImage::smoothScale: Image is a null image
QImage::smoothScale: Image is a null image
QImage::smoothScale: Image is a null image
QImage::smoothScale: Image is a null image
QImage::smoothScale: Image is a null image
In file kernel/qimage.cpp, line 1300: Out of memory
QImage::smoothScale: Image is a null image
In file kernel/qimage.cpp, line 1300: Out of memory
QImage::smoothScale: Image is a null image



---

### Post by aurelieng on 2008-10-01
1.4.9.1 here, Kubuntu Hardy. No problem.

---

### Post by tutwabee on 2008-10-05
The problem only seems to happen when I play music.  If my cursor is on top of Amarok while it is playing music, the cursor will change to a "working" cursor for about half a second every few seconds.

I may try wiping my Amarok settings and reinstalling to see if that fixes the problem.

---

