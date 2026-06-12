---
title: "#0 0xb7873b71 in memcpy () from /lib/tls/i686/cmov/libc.so.6"
date: 2009-01-25
forum: Installation &amp; Upgrades
---

### Post by efone on 2009-01-25
Hi guys,

When I compile and link my code on my gentoo box everything works fine and the program runs fine.
At work I have a ubuntu box and I need to run the same code, when I compile and link it everything seems fine; however, when I start it I get a segmentation fault. I use gfortran and upon checking with gdb I get:

(gdb) bt
#0 0xb7d94b6a in memcpy () from /lib/tls/i686/cmov/libc.so.6
#1 0xb7f4a653 in *_gfortrani_write_a (dtp=0xbf98d558, f=0x9f6f59c,
source=0xbf98d688 'Hello \000', len=8) at /usr/include/bits/string3.h:52
#2 0xb7f42cb8 in formatted_transfer_scalar (dtp=0xbf98d558,
type=<error reading variable>, p=0xbf98d688, len=8, size=8)
at ../../../src/libgfortran/io/transfer.c:1041
#3 0xb7f4305e in formatted_transfer (dtp=0xbf98d558,
type=<error reading variable>, p=0xbf98d688, kind=8, size=8, nelems=1)
at ../../../src/libgfortran/io/transfer.c:1378
#4 0xb7f3f396 in *_gfortran_transfer_character (dtp=0x2, p=0x20f6d515, len=5)
at ../../../src/libgfortran/io/transfer.c:1434
#5 0x0804894b in simple () at simple.f:12
#6 0x080489d9 in main ()
#7 0xb7d32685 in __libc_start_main () from /lib/tls/i686/cmov/libc.so.6
#8 0x08048701 in _start ()

Any idea on how I can fix this? Maybe something wrong with libc? By the way, I couldnt figure out how to include libc symbols for debuging in ubuntu.

Any help is highly appreciated.

Thanks in advance.

Efo

---

### Post by efone on 2009-01-26
Here is what I found after further debugging.

I simplified the problem and I found:
1) The problem occurs only when out.txt is new (i.e. not there)
2) The problem disappears when I uncomment the second "rewind(7)"
3) The problem disappears if I remove "1x," from the format at 20

What basic mistake am I making?


Here is the code:

program simple
character*8 strngw,strngr
strngw='Hello'

open(unit=7,file='out.txt',status='unknown')
rewind(7)
read(7,20,end=10) strngr
10 continue
c rewind(7)
write(7,20) strngw
close(7)
20 format(1x,a5)
c
return
c
end program simple

---

