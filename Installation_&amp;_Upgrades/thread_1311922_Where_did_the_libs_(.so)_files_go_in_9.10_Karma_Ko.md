---
title: "Where did the libs (.so) files go in 9.10 Karma Koala"
date: 2009-11-02
forum: Installation &amp; Upgrades
---

### Post by andylh on 2009-11-02
I installed 9.10 last week, no sound, then found out about the grub problem on a multi boot system. Fixed that eventually and now have the correct kernel loaded.

Now however programs do not find the libs that are in the /usr/lib directory.

Here is a sample ldd

Ubuntu:~$ ldd /bin/fldigi 
	linux-gate.so.1 =>  (0xf77d7000)
	libportaudio.so.2 => not found
	libpthread.so.0 => /lib32/libpthread.so.0 (0xf77a9000)
	libpng12.so.0 => not found
	libz.so.1 => not found
	libjpeg.so.62 => not found
	libXft.so.2 => not found
	libdl.so.2 => /lib32/libdl.so.2 (0xf77a4000)
	libm.so.6 => /lib32/libm.so.6 (0xf777d000)
	libXext.so.6 => not found
	libX11.so.6 => not found
	libsndfile.so.1 => not found
	libsamplerate.so.0 => not found

All the not found files are in /usr/lib, why are they not found?

Thanks

A.

---

