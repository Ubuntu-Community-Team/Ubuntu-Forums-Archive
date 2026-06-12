---
title: "Linux BIOS ?"
date: 2010-04-25
forum: Hardware
---

### Post by lucasart on 2010-04-25
hello everyone,

my boot time is pretty good, that is from grub to the desktop. but before it reaches that stage, it has to go trough all the BIOS bullshit, and that takes for ever. I've found on google that you can flash it and  install a generic linux bios so called "coreboot". but never found any  simple explanation on how to do it, what to download, how to install,  compatibility etc.
has anyone ever done it on their machine ? where can i find a simple  explanation for it ?

Thank you

---

### Post by P4man on 2010-04-25
Ive never tried it, but have a look here:
[http://www.coreboot.org/Supported_Motherboards](http://www.coreboot.org/Supported_Motherboards)

If your motherboard isnt listed there, then forget it (for now). If it is listed and marked as fully supported, then we may look further, but be advised this is not without risk

---

### Post by lucasart on 2010-04-25
> **P4man said:**
> Ive never tried it, but have a look here:
[http://www.coreboot.org/Supported_Motherboards](http://www.coreboot.org/Supported_Motherboards)

If your motherboard isnt listed there, then forget it (for now). If it is listed and marked as fully supported, then we may look further, but be advised this is not without risk

ok thanks for that. now do you know how to list in the most precise and detailed way possible your hardware on ubuntu ? is there a command line that produces a report listing all the hardware you have or a GUI application ?

thanks

---

### Post by VeeDubb on 2010-04-25
Also, I highly recommend that you either bookmark [http://www.biosman.com/](http://www.biosman.com/) on another computer first, or just order a spare bios chip from them.

Most bios chips are hot-swappable, so you can boot into your bios flashing utility, pull you bios chip, but in the blank, and flash away.

If it doesn't work, and you system won't post (very possible) then you just swap your old bios chip back in, clear the CMOS, and it's just like you never messed with it.

---

### Post by P4man on 2010-04-25
open a terminal and type


```
lspci
```

for a brief list of PCI devices. For more extensive information:

```
lshw
```

The output will be too long to fit the console, so you can redirect the output to a file

```
lshw > myhardware.txt
```

If you want a gui, install "device manager" from ubuntu software center.

But is this for a laptop? If so, forget it already. Lobby your oem, but you wont get far trying to get this work.

---

### Post by lucasart on 2010-04-25
> **P4man said:**
> open a terminal and type


```
lspci
```for a brief list of PCI devices. For more extensive information:

```
lshw
```The output will be too long to fit the console, so you can redirect the output to a file

```
lshw > myhardware.txt
```If you want a gui, install "device manager" from ubuntu software center.

But is this for a laptop? If so, forget it already. Lobby your oem, but you wont get far trying to get this work.

no it's for a desktop computer. thanks for these commands, they can be very useful. i dont need a gui, a command line is just as good.

---

### Post by cb951303 on 2010-04-25
keep in mind that you won't find your mobo model in those outputs.

---

