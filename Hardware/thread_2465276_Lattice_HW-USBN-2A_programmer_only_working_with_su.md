---
title: "Lattice HW-USBN-2A programmer only working with sudo"
date: 2021-07-28
forum: Hardware
---

### Post by detzi88 on 2021-07-28
Hi there,
i use Lattice Diamond ([https://www.latticesemi.com/latticediamond](https://www.latticesemi.com/latticediamond)) to program some FPGAs and managed to install the software in my Kubuntu 21.04 system. Now when i launch Diamond and want to program a target (programmer is attached via USB), it detects the programmer ([https://www.latticesemi.com/en/Products/DevelopmentBoardsAndKits/ProgrammingCablesforPCs](https://www.latticesemi.com/en/Products/DevelopmentBoardsAndKits/ProgrammingCablesforPCs)) fine but fails the programming process and tells me that i should install the drivers or wait a sec and try again. When i launch it via terminal and "sudo", the programming finishes flawlessly.
Now because of that i suspect/assume that this is some kind of permission issue which needs some adjustment at the right place so normal users are allowed to fully access the programmer. But sadly i do not know how kubuntu manages usbdevice access. Can someone hook me up on how to proceed?

Thanks in advance
Detzi

---

### Post by detzi88 on 2021-07-28
Found it myself: get the Bus and Device number with lsusb and then "chmod [FONT=monospace][COLOR=#000000][FONT=monospace][COLOR=#000000]777[/COLOR] [/FONT]/dev/bus/usb/001/022" where 001 was my bus and 022 my Device. After that the programmer works perfectly well. Do i have to pay attention when chmod'ing this or can i just call a script on plugin that automates this?[/COLOR]

EDIT:
I found the actual Problem :) the .rules supplied by Lattice had syntax errors in them. I figured this out using udevadm. Guess the syntax is different on red hat systems. I changes the rules files name to 51-lattice.rules and its content to:
> 
#Lattice
SUBSYSTEM=="usb", ATTRS{idVendor}=="1134", ATTRS{idProduct}=="8001", MODE="0666", OWNER="1000", GROUP="1000"

#FTDI
SUBSYSTEM=="usb",ACTION=="add", ATTRS{idVendor}=="0403", ATTRS{idProduct}=="6010", MODE="0666", OWNER="1000", GROUP="1000",SYMLINK+="ftdi-%n"
SUBSYSTEM=="usb",ATTRS{idVendor}=="0403", ATTRS{idProduct}=="6010",RUN+="/bin/sh -c 'basename %p > /sys/bus/usb/drivers/ftdi_sio/unbind'"

that's all that was missing. :) hope this helps someone avoid the diggin.
[/FONT]

---

