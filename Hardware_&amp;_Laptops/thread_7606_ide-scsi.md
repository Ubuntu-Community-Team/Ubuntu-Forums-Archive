---
title: "ide-scsi"
date: 2004-12-09
forum: Hardware &amp; Laptops
---

### Post by miss tina on 2004-12-09
hi I've been using ubuntu for 2weeks now 
it works great except that it seem to  be that there is no ide-scsi module to emulate scsi for my optical drives i've included the hdc=ide-scsi hdd=ide-scsi param in the /boot/grub/menu.lst it give s a boot time the error no ide_mod module found....
[COLOR=YellowGreen]
title           Ubuntu, kernel 2.6.8.1-3-686
root            (hd2,0)
kernel          /boot/vmlinuz-2.6.8.1-3-686 root=/dev/sdb1 ro quiet splash hdd=ide-scsi hdc=ide-scsi 
initrd          /boot/initrd.img-2.6.8.1-3-686
savedefault
boot
[/COLOR]

do i have to recompile my kernel with the module? and how to do that???, is it more or less the same as in gentoo manual kernel installation: dwnl the kernel-source make menuconfig .... pleaze give me a clue
is there an other way to get my opt-drives work fasters, eg enable dma without the ide-scsi trick??
 hdparm -d1 /dev/hdc doesn't work

the usb mass storage works great ans d it emulates scsi my archos usbv2.0drive works fast and is found as media/sdc1

my firewire lacie  dvd burner works and is found as dev/sr0 but grip doesnt work with it, it rips empty tracks!! and the other opt-devices rip at max speed2x
i realy want grip to work need my cd's back on my pc had a crash (cause windows?)lost mycollectioin and i want to rebuild it... but not in a windows enviroment... i just need to get my opt-drives work faster  

tnx tina

---

### Post by miss tina on 2004-12-09
in a thread i found:
[COLOR=YellowGreen]You will need to get rid of the hdc=ide-scsi, too as that is for oler linux kernels.[/COLOR]

so how to speed up optical-devices??? :confused:

---

### Post by miss tina on 2004-12-16
the prob is solved don't ask how or what was wrong they just work fine now :oops:

---

### Post by miss tina on 2004-12-17
i've found this witch explains why rippinhg is slow
Linux with ATAPI

If you are using an ATAPI CD drive with Linux for anything other than mounting CDROMs or playing audio CDs, I strongly recommend configuring your kernel to use the SCSI host adapter emulation. ATAPI drives use much the same command set as SCSI/MMC drives, so the emulation contributes very little overhead whilst allowing software total control of the device. This is esential for CD burning and very useful for audio ripping, especially for damaged CDs. CDparanoia is a lot faster with the SCSI interface. Newer linux kernels (>=2.4?) do have a direct ATAPI packet ioctl() interface, but as far as I'm aware CDparanoia doesn't support it.

---

### Post by miss tina on 2005-01-05
cdda2wav will speed up ripping no more cdparanoia... simply use cripple to rip your cd collection
[COLOR=YellowGreen] cripple -d /dev/sr0 -R cdda2wav[/COLOR] is a simple command  for ripping a cd on device sr0 (a firewire dvddrive) i could even rip 3 cd's at once, now i've finaly my collection back.. :!:

---

