---
title: "WG511T not picked up, or lighting up"
date: 2005-10-17
forum: Hardware &amp; Laptops
---

### Post by dickohead on 2005-10-17
Hey folks,

I have tried many times now to configure my wireless card with Ndiswrapper, madwifi and prism54 drivers, but one thing remains true for all of them - my wireless card never lights up - ever (with the exception of windows).

How do i make the system recognise that i have  a wireless card in my pcmcia slot, or how do i see if my pcmcia slot has even been recognized.

I am using an Arima laptop, which also happens to be 64bit, so my hardware is not exactly middle-of-the-road but it runs very well! Especially since the upgrade from Hoary,

If anyone can help me solve the mystery of my WG511t not lighting up, it would be much appreciated.

---

### Post by knappen on 2005-10-17
What does ndiswrapper -l tell you?

---

### Post by dickohead on 2005-10-17
at the moment, nothing, but when i load the driver is says it's fine. I have spoken to other people with wireless cards using Linux, and whther the card works or not, it will always light up during the boot process, mine never does, even when i add the ndiswrapper driver as a module it still won't work.

---

### Post by spd106 on 2005-10-22
What does **cardctl status** show?

Does anything show up with **dmesg**?

---

### Post by AndrewB on 2005-10-22
perhaps a Bios setting?

---

### Post by MrMojoRising on 2006-06-02
add this to your /boot/grub/menu.lst :


pci=assign-busses


put that after the other boot options for the linux kernel....here's mine
```
title		Ubuntu Dapper Drake
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda3 ro quiet splash pci=assign-busses
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot
```


Then look go here
[http://ubuntuforums.org/showthread.php?t=105437&highlight=wg511t](http://ubuntuforums.org/showthread.php?t=105437&highlight=wg511t)

---

