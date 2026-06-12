---
title: "fglrx on a ATI Radeon Mobility 7000 IGP 4437"
date: 2006-02-11
forum: Hardware &amp; Laptops
---

### Post by spiregrain on 2006-02-11
I have an ATI Radeon Mobility 7000 IGP 4437 in a Toshiba laptop.  At least, I think that's what it is:  
```
ken@franklin Downloads $ lspci | grep VGA
0000:01:05.0 VGA compatible controller: ATI Technologies Inc: Unknown device 4437
```

But device 4437 seems to be the Mobility 7000.

Should I expect to be able to use fglrx driver in xorg?  I get this:
```
ken@franklin Downloads $ sudo modprobe fglrx
FATAL: Error inserting fglrx (/lib/modules/2.6.12-10-686-smp/misc/fglrx.ko): No such device
ken@franklin Downloads $ dmesg | tail -n 2
[4297452.835000] [fglrx] Maximum main memory to use for locked dma buffers: 373 MBytes.
[4297452.835000] [fglrx:firegl_init] *ERROR* Device not found!
```

I've seen scraps about using ChipID lines, or even hex-editing the driver(!) to force the issue.  But should I try that, or something else?

---

### Post by tripleee on 2006-02-20
I believe the supported models are numbered like 8500 and up. I actually tried it (ATI Radeon VE 7000) and it simply told me -- buried in the X log, of course -- which models are supported; if you don't want to take my word for it, try it yourself.  [http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide) (also available here, but I don't have the link handy)

---

