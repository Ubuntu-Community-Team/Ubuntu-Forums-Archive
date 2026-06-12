---
title: "has somebody the drivers for qemu: for NE2000 driver PCI for windows95?"
date: 2009-10-22
forum: Hardware
---

### Post by frenchn00b on 2009-10-22
Hello 

I run windows95, under qemu. Is there some drivers for the net: NE2000 driver PCI for windows95

Has still somebody that at home, some floppy disks, or the exe?


> qemu\qemu -localtime -soundhw sb16  -cdrom drivers_qemu3.iso    -hda windows.img     -no-kqemu -L qemu\   -net nic,model=ne2k_pci

---

### Post by frenchn00b on 2009-10-22
ok you need those files


 infinst_enu.exe 
 w95_8029.zip  

md5
169a0f2d9980c6d03f0300ff9c5c4fcd  infinst_enu.exe
fd9e1ccde5b7417005dd6a808cdb7f8b  w95_8029.zip
 
u get pci bridge qemu insatlled and the ne2000 type card.
those drivers work             [http://www.claunia.com/qemu/drivers/index.html](http://www.claunia.com/qemu/drivers/index.html)


[B][COLOR="Red"]OK but command
and ifconfig 
says command not found . why?? 

I have windows 95B[/COLOR][/B]

---

