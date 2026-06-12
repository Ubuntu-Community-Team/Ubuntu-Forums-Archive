---
title: "aticonfig segfault (radeon mobility x2300)"
date: 2007-10-05
forum: Hardware &amp; Laptops
---

### Post by fictivetoast on 2007-10-05
Hey - 

I have a new hp 6910p laptop with an Ati Radeon Mobility x2300 video card.  I've installed the latest beta of gutsy, which defaulted to a vesa driver and won't let me properly pick a resolution for my widescreen lcd.  The default xorg.conf entry I've been given is:

```
Section "Device"
	Identifier	"Generic Video Card"
	Driver		"vesa"
	BusID		"PCI:1:0:0"
EndSection
```

Running the ATI drivers from the restricted package works... but I'd rather use fglrx to allow compositing and compiz.  So to install fglrx as indicated [here]("http://ubuntuforums.org/showthread.php?t=478238&highlight=x2300"), I've tried:

```
sudo apt-get install linux-restricted-modules-$(uname -r)
sudo apt-get install xorg-driver-fglrx
sudo depmod -a
sudo aticonfig --initial
```


Upon running aticonfig for the first time though, I get the following output:

```
Uninitialised file found, configuring.
Using /etc/X11/xorg.conf
Saved back-up to /etc/X11/xorg.conf.original-1
Segmentation fault (core dumped)
```

anyone know what I can do here?  why is aticonfig segfaulting on the initial run?  is there a way around this?

Thanks in advance for any help!

---

### Post by cronfy on 2007-11-04
Hi,

I have Asus F5V laptop with ATI Radeon X3200, and aticonfig segfaults too, It provides some backtrace information:

```

# aticonfig --initial
Warning: Could not find configuration file
Please copy configuration file template to /etc/X11
root@presentation:/home/cronfy# cp /etc/X11/xorg.conf.original-0 /etc/X11/xorg.conf
root@presentation:/home/cronfy# aticonfig --initialUninitialised file found, configuring.
Using /etc/X11/xorg.conf
Saved back-up to /etc/X11/xorg.conf.original-3
*** glibc detected *** aticonfig: munmap_chunk(): invalid pointer: 0xbfee99ea ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(cfree+0x1bb)[0xb7d1792b]
aticonfig[0x805c5c7]
aticonfig[0x805c875]
aticonfig[0x8054528]
aticonfig[0x804985e]
aticonfig[0x80496cb]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0)[0xb7cc0050]
aticonfig[0x8049601]
======= Memory map: ========
08048000-08067000 r-xp 00000000 08:06 1522       /usr/bin/aticonfig
08067000-0806a000 rw-p 0001e000 08:06 1522       /usr/bin/aticonfig
0806a000-0808b000 rw-p 0806a000 00:00 0          [heap]
b7c87000-b7c91000 r-xp 00000000 08:01 515139     /lib/libgcc_s.so.1
b7c91000-b7c92000 rw-p 0000a000 08:01 515139     /lib/libgcc_s.so.1
b7c9c000-b7c9d000 rw-p b7c9c000 00:00 0 
b7c9d000-b7c9f000 r-xp 00000000 08:01 548278     /lib/tls/i686/cmov/libdl-2.6.1.so
b7c9f000-b7ca1000 rw-p 00001000 08:01 548278     /lib/tls/i686/cmov/libdl-2.6.1.so
b7ca1000-b7ca2000 rw-p b7ca1000 00:00 0 
b7ca2000-b7ca6000 r-xp 00000000 08:06 1622       /usr/lib/libXdmcp.so.6.0.0
b7ca6000-b7ca7000 rw-p 00003000 08:06 1622       /usr/lib/libXdmcp.so.6.0.0
b7ca7000-b7ca9000 r-xp 00000000 08:06 1611       /usr/lib/libXau.so.6.0.0
b7ca9000-b7caa000 rw-p 00001000 08:06 1611       /usr/lib/libXau.so.6.0.0
b7caa000-b7dee000 r-xp 00000000 08:01 548272     /lib/tls/i686/cmov/libc-2.6.1.so
b7dee000-b7def000 r--p 00143000 08:01 548272     /lib/tls/i686/cmov/libc-2.6.1.so
b7def000-b7df1000 rw-p 00144000 08:01 548272     /lib/tls/i686/cmov/libc-2.6.1.so
b7df1000-b7df4000 rw-p b7df1000 00:00 0 
b7df4000-b7e17000 r-xp 00000000 08:01 548280     /lib/tls/i686/cmov/libm-2.6.1.so
b7e17000-b7e19000 rw-p 00023000 08:01 548280     /lib/tls/i686/cmov/libm-2.6.1.so
b7e19000-b7f06000 r-xp 00000000 08:06 1605       /usr/lib/libX11.so.6.2.0
b7f06000-b7f0a000 rw-p 000ed000 08:06 1605       /usr/lib/libX11.so.6.2.0
b7f0a000-b7f17000 r-xp 00000000 08:06 1626       /usr/lib/libXext.so.6.4.0
b7f17000-b7f18000 rw-p 0000d000 08:06 1626       /usr/lib/libXext.so.6.4.0
b7f18000-b7f19000 rw-p b7f18000 00:00 0 
b7f19000-b7f20000 r-xp 00000000 08:06 1648       /usr/lib/libXrender.so.1.3.0
b7f20000-b7f21000 rw-p 00006000 08:06 1648       /usr/lib/libXrender.so.1.3.0
b7f21000-b7f26000 r-xp 00000000 08:06 1646       /usr/lib/libXrandr.so.2.1.0
b7f26000-b7f27000 rw-p 00005000 08:06 1646       /usr/lib/libXrandr.so.2.1.0
b7f30000-b7f33000 rw-p b7f30000 00:00 0 
b7f33000-b7f4d000 r-xp 00000000 08:01 515092     /lib/ld-2.6.1.so
b7f4d000-b7f4f000 rw-p 00019000 08:01 515092     /lib/ld-2.6.1.so
bfed5000-bfeeb000 rw-p bfed5000 00:00 0          [stack]
ffffe000-fffff000 r-xp 00000000 00:00 0          [vdso]
Aborted (core dumped)

```

Any ideas how to fix this?

Thanks in advance.

---

### Post by cronfy on 2007-11-05
I have found that aticonfig segfaults only when fglrx deiver is not loaded at the moment, i.e. when X runs with 'vesa' driver. Restarting X with manually configured fglrx driver (no setup, just driver change) solved the problem - after this aticonfig works fine.

---

