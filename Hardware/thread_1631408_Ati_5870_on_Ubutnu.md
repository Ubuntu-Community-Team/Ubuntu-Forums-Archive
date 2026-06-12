---
title: "Ati 5870 on Ubutnu"
date: 2010-11-26
forum: Hardware
---

### Post by dr.m0x on 2010-11-26
Got 10.10 x64 installed with out too much fuss but it just booted to a  blank screen (monitor was not receiving any signal). Rebooted into  recovery mode with command prompt did:

apt-get update
apt-get install fglrx
aticonfig --initial
reboot

This time around I was able to boot to desktop successfully but I can't enable 3d desktop effects. 

I did:

dmesg | grep fglrx 

[    7.524596] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[    7.549629] [fglrx] Maximum main memory to use for locked dma buffers: 5775 MBytes.
[    7.549692] [fglrx]   vendor: 1002 device: 6898 count: 1
[    7.550067] [fglrx] ioport: bar 4, base 0xde00, size: 0x100
[    7.550402] [fglrx] Kernel PAT support is enabled
[    7.550411] [fglrx] module loaded - fglrx 8.78.30 [Sep 20 2010] with 1 minors
[   191.932236] fglrxinfo[2809]: segfault at 4 ip 00007fd1de06e38e sp  00007fff38cf2130 error 4 in libGL.so.1.2[7fd1de013000+ae000]
[   223.363897] fglrxinfo[2813]: segfault at 4 ip 00007f275de5b38e sp  00007fff4aa7ca90 error 4 in libGL.so.1.2[7f275de00000+ae000]

Where I am stuck is on how to fix it.
Any help would be greatly appreciated

---

### Post by dr.m0x on 2010-11-26
Ok managed to get things working. Was as easy as adding the xorg updates and xorg edgers ppa's to my sources and updating.

---

