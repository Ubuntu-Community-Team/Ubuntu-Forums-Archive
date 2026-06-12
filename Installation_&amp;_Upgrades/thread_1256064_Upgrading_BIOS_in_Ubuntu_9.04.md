---
title: "Upgrading BIOS in Ubuntu 9.04"
date: 2009-09-02
forum: Installation &amp; Upgrades
---

### Post by leofea on 2009-09-02
I have a Dell, and I am wanting to upgrade the BIOS, using the Dell drivers website.

I have downloaded the BIOS program, which is downloadable as a .BIN file.

I want to install this, but when trying, I get the following:

leo@BCServer:~$ cd Desktop
leo@BCServer:~/Desktop$ chmod +x PE1600SC_BIOS_LX_A12.BIN
leo@BCServer:~/Desktop$ ./PE1600SC_BIOS_LX_A12.BIN
./PE1600SC_BIOS_LX_A12.BIN: 33: typeset: not found
./PE1600SC_BIOS_LX_A12.BIN: 34: typeset: not found
./PE1600SC_BIOS_LX_A12.BIN: 37: typeset: not found
./PE1600SC_BIOS_LX_A12.BIN: 38: typeset: not found
./PE1600SC_BIOS_LX_A12.BIN: 71: typeset: not found
./PE1600SC_BIOS_LX_A12.BIN: 72: typeset: not found
./PE1600SC_BIOS_LX_A12.BIN: 73: typeset: not found
./PE1600SC_BIOS_LX_A12.BIN: 76: typeset: not found
./PE1600SC_BIOS_LX_A12.BIN: 81: typeset: not found
./PE1600SC_BIOS_LX_A12.BIN: 84: typeset: not found
./PE1600SC_BIOS_LX_A12.BIN: 85: typeset: not found
./PE1600SC_BIOS_LX_A12.BIN: 86: typeset: not found
./PE1600SC_BIOS_LX_A12.BIN: 87: typeset: not found
./PE1600SC_BIOS_LX_A12.BIN: 88: typeset: not found
./PE1600SC_BIOS_LX_A12.BIN: 89: typeset: not found
./PE1600SC_BIOS_LX_A12.BIN: 92: typeset: not found
./PE1600SC_BIOS_LX_A12.BIN: 93: typeset: not found
./PE1600SC_BIOS_LX_A12.BIN: 94: typeset: not found
./PE1600SC_BIOS_LX_A12.BIN: 95: typeset: not found
./PE1600SC_BIOS_LX_A12.BIN: 96: typeset: not found
./PE1600SC_BIOS_LX_A12.BIN: 97: typeset: not found
./PE1600SC_BIOS_LX_A12.BIN: 98: typeset: not found
./PE1600SC_BIOS_LX_A12.BIN: 99: typeset: not found
./PE1600SC_BIOS_LX_A12.BIN: 100: typeset: not found
./PE1600SC_BIOS_LX_A12.BIN: 101: typeset: not found
./PE1600SC_BIOS_LX_A12.BIN: 102: typeset: not found
./PE1600SC_BIOS_LX_A12.BIN: 103: typeset: not found
./PE1600SC_BIOS_LX_A12.BIN: 104: typeset: not found
./PE1600SC_BIOS_LX_A12.BIN: 106: typeset: not found
./PE1600SC_BIOS_LX_A12.BIN: 107: typeset: not found
./PE1600SC_BIOS_LX_A12.BIN: 108: typeset: not found
./PE1600SC_BIOS_LX_A12.BIN: 111: typeset: not found
./PE1600SC_BIOS_LX_A12.BIN: 112: typeset: not found
./PE1600SC_BIOS_LX_A12.BIN: 113: typeset: not found
./PE1600SC_BIOS_LX_A12.BIN: 114: typeset: not found
./PE1600SC_BIOS_LX_A12.BIN: 115: typeset: not found
./PE1600SC_BIOS_LX_A12.BIN: 116: typeset: not found
./PE1600SC_BIOS_LX_A12.BIN: 117: typeset: not found
./PE1600SC_BIOS_LX_A12.BIN: 120: typeset: not found
./PE1600SC_BIOS_LX_A12.BIN: 123: typeset: not found
./PE1600SC_BIOS_LX_A12.BIN: 126: typeset: not found
./PE1600SC_BIOS_LX_A12.BIN: 129: typeset: not found
./PE1600SC_BIOS_LX_A12.BIN: 130: typeset: not found
./PE1600SC_BIOS_LX_A12.BIN: 131: typeset: not found
./PE1600SC_BIOS_LX_A12.BIN: 132: typeset: not found
./PE1600SC_BIOS_LX_A12.BIN: 133: typeset: not found
./PE1600SC_BIOS_LX_A12.BIN: 134: typeset: not found
./PE1600SC_BIOS_LX_A12.BIN: 137: typeset: not found
./PE1600SC_BIOS_LX_A12.BIN: 138: typeset: not found
./PE1600SC_BIOS_LX_A12.BIN: 139: typeset: not found
./PE1600SC_BIOS_LX_A12.BIN: 140: typeset: not found
./PE1600SC_BIOS_LX_A12.BIN: 141: typeset: not found
./PE1600SC_BIOS_LX_A12.BIN: 142: typeset: not found
./PE1600SC_BIOS_LX_A12.BIN: 143: typeset: not found
./PE1600SC_BIOS_LX_A12.BIN: 144: typeset: not found
./PE1600SC_BIOS_LX_A12.BIN: 145: typeset: not found
./PE1600SC_BIOS_LX_A12.BIN: 175: typeset: not found
./PE1600SC_BIOS_LX_A12.BIN: 825: typeset: not found
./PE1600SC_BIOS_LX_A12.BIN: 825: Bad substitution
./PE1600SC_BIOS_LX_A12.BIN: 1: typeset: not found
sleep: missing operand
Try `sleep --help' for more information.
leo@BCServer:~/Desktop$ 


What am i doing wrong?

Thanks

---

### Post by Partyboi2 on 2009-09-02
Hi, try following [[COLOR=Blue]this[/COLOR]]("http://ubuntuforums.org/showthread.php?t=648824") thread through to update your bios.

---

### Post by x33a on 2009-09-02
you could also give this a try

[http://www.coreboot.org/Flashrom](http://www.coreboot.org/Flashrom)

note: never mess with the firmware/bios unnecessarily. and don't do anything you don't understand, otherwise you'll brick your hardware.

---

