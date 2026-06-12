---
title: "HPT DC7280 driver compile issues"
date: 2012-08-24
forum: Hardware
---

### Post by DarkMorford on 2012-08-24
I'm building a file server using Ubuntu Server 12.04 x64, with a Highpoint DC7280 RAID controller handling the data drives. (The OS drive is on the motherboard's SATA controller.)

The only Linux driver Highpoint offers on their site for the controller is source code, so after installing [FONT=Courier New]build-essential[/FONT] I unpacked the driver and ran [FONT=Courier New]make[/FONT]. The compile process didn't even get started, though, before issuing an error message.
```
../../../inc/linux/Makefile.def:85: *** Only kernel 2.4/2.6 is supported but you use 2.2.  Stop.
```The machine is currently running kernel [FONT=Courier New]3.2.0-29-generic[/FONT]. I'm guessing the makefile is only looking at the minor version number and assuming that it has 2.2, rather than 3.2.

I consider myself an intermediate C/C++ programmer, but I've never dealt with writing drivers or anything at the kernel level. So I ask you, forums: What do I have to change to compile a 2.6 driver under kernel 3.2?

EDIT: The driver package in question is available at [http://www.highpoint-tech.com/USA_new/DC7280_download.htm](http://www.highpoint-tech.com/USA_new/DC7280_download.htm).

---

### Post by DarkMorford on 2012-08-25
After looking at the makefile more closely, I found I was able to fake it out by explicitly using [FONT=Courier New]make KERNEL_VER=2.6[/FONT]. It seems to compile fine, except for one warning.
```
  MODPOST 1 modules
WARNING: could not find /home/user/highpoint/dc7280-linux-src-v1.0/product/dc7280/linuxla/.build/.him_dc7280.o.cmd for /home/user/highpoint/dc7280-linux-src-v1.0/product/dc7280/linuxla/.build/him_dc7280.o
  LD [M]  /home/user/highpoint/dc7280-linux-src-v1.0/product/dc7280/linuxla/.build/dc7280.ko
```
Running [FONT=Courier New]sudo make install KERNEL_VER=2.6[/FONT] after this doesn't result in anything unusual, and [FONT=Courier New]sudo modprobe dc7280[/FONT] likewise issues no errors, so I'm guessing the warning at the compile stage isn't serious. I'd like a second opinion on that, though.

---

