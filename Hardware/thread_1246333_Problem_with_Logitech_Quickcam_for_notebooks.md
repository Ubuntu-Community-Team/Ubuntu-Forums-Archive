---
title: "Problem with Logitech Quickcam for notebooks"
date: 2009-08-21
forum: Hardware
---

### Post by AllRadioisDead on 2009-08-21
Hi, I have a Logitech webcam I've been trying to get going with linux.
First I ran lsusb, here was my output:
```

Bus 004 Device 004: ID 046d:08dd Logitech, Inc. QuickCam for Notebooks

```After a bit of searching, I found how to install the appropriate driver.
Then I installed:
```
sudo apt-get install gspca-source
```I then installed camorama and it crashed before loading, with an unspecified error.
I then tried cheese. My webcam works but it's really blurry, the quality is brutal.
Help is appreciated, thanks.
Edit:
Ran Cheese with terminal:
```

libv4lconvert: Error decompressing JPEG: unknown huffman code: 0000ffff
libv4lconvert: Error decompressing JPEG: unknown huffman code: 0000ffff
libv4lconvert: Error decompressing JPEG: unknown huffman code: 0000ffff
libv4lconvert: Error decompressing JPEG: unknown huffman code: 0000ffff
libv4lconvert: Error decompressing JPEG: unknown huffman code: 0000ffff
libv4lconvert: Error decompressing JPEG: unknown huffman code: 0000ffff
libv4lconvert: Error decompressing JPEG: unknown huffman code: 0000ffff
libv4lconvert: Error decompressing JPEG: unknown huffman code: 0000ffff
libv4lconvert: Error decompressing JPEG: unknown huffman code: 0000ffff
libv4lconvert: Error decompressing JPEG: unknown huffman code: 0000ffff
libv4lconvert: Error decompressing JPEG: unknown huffman code: 0000ffff
libv4lconvert: Error decompressing JPEG: unknown huffman code: 0000fffe
libv4lconvert: Error decompressing JPEG: unknown huffman code: 0000ffff

```
Edit:
Camorama works if launched via:
```

   LD_PRELOAD= /usr/lib/libv4l/v4l1compat.so camorama
```

But still has the same blur and shoots out the same errors.

---

### Post by AllRadioisDead on 2009-08-21
Bump ;(

---

### Post by legitneo on 2009-10-31
Bump

I can't even download the driver. Where did you get the source file from?

---

