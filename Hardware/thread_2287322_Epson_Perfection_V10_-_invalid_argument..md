---
title: "Epson Perfection V10 - invalid argument."
date: 2015-07-18
forum: Hardware
---

### Post by Kraftfoder on 2015-07-18
Hello! I would be very glad if someone could help med with this!

I'm trying to get my scanner to work on my new computer with Ubuntu. It worked fine on my old machine (with Linux Mint).

The system found the scanner (i had to do a lot of work with drivers for that). When I start xsane it found the scanner, but when I start scanning i get a window saying:nster som säger:

"Failed to start scanner: Invalid argument"

When I ran:
$ strace -o strace.out -f scanimage -T
I got the attached strate.out file.


Configuration:

/etc/sane.d/dll.conf  has only one line not commented away: "epson".

/etc/sane.d/epson.conf has the line  "usb 0x04b8 0x012d" (to make it find the scanner)

/etc/sane.d/dll.d/iscan has the line "epkowa" (I don't know what that is).

---

