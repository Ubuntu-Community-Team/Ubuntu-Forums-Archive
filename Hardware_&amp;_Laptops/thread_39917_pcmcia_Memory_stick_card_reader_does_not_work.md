---
title: "pcmcia Memory stick card reader does not work"
date: 2005-06-07
forum: Hardware &amp; Laptops
---

### Post by john_walsh54 on 2005-06-07
The pcmcia memory stick card reader does not work on my Thinkpad 600x. Below is the output from dmesg after I inserted the card; the "cardctl status" command and  "cardctl ident" command. I would appreciate any help:

cs: memory probe 0xa0000000-0xa0ffffff: excluding 0xa0000000-0xa0ffffff
cs: memory probe 0x60000000-0x60ffffff: clean.
Probing IDE interface ide2...
hde: MS Adapter, CFA DISK drive
hdf: probing with STATUS(0x00) instead of ALTSTATUS(0x0a)
ide2 at 0x100-0x107,0x10e on irq 3
hde: max request size: 128KiB
hde: 31680 sectors (16 MB) w/1KiB Cache, CHS=495/4/16
hde: cache flushes not supported
 /dev/ide/host2/bus0/target0/lun0:<4>hde: lost interrupt
john@ThinkPad:~$ caedctl status
bash: caedctl: command not found
john@ThinkPad:~$ cardctl status
Socket 0:
  3.3V 16-bit PC Card
  function 0: [ready], [bat dead], [bat low]
Socket 1:
  3.3V CardBus card
  function 0: [ready]
john@ThinkPad:~$ cardctl ident
Socket 0:
  product info: "MS", "Adapter", ""
  manfid: 0x000a, 0x0000
  function: 4 (fixed disk)
Socket 1:
  no product info available

The pcmcia sockets work for my pcmcia firewire card and my pcmcia wireless card (DWL-G650). I use ndiswrapper for the wireless card. I cannot think of any other info, but if you need some give me instructions and I will get the info.

Kind regards

John

---

### Post by Zymous on 2005-06-07
I had what may be unrelated problems with a Cardbus wireless card on my laptop, but can you give us the results of 

lspci -vt 

before and after insertion of the cardreader?

-- 
Zym

---

### Post by john_walsh54 on 2005-06-10
ZYM,
I cannot see any difference, but here are the before and after results of inserting the pcmcia card.

john@ThinkPad:~$ lspci -vt
-+-[06]---00.0  Texas Instruments TSB12LV23 IEEE-1394 Controller
 \-[00]-+-00.0  Intel Corp. 440BX/ZX/DX - 82443BX/ZX/DX Host bridge
        +-01.0-[01]----00.0  Neomagic Corporation NM2360 [MagicMedia 256ZX]
        +-02.0  Texas Instruments PCI1450
        +-02.1  Texas Instruments PCI1450
        +-03.0  Lucent Microelectronics WinModem 56k
        +-06.0  Cirrus Logic CS 4614/22/24 [CrystalClear SoundFusion Audio Accelerator]
        +-07.0  Intel Corp. 82371AB/EB/MB PIIX4 ISA
        +-07.1  Intel Corp. 82371AB/EB/MB PIIX4 IDE
        +-07.2  Intel Corp. 82371AB/EB/MB PIIX4 USB
        \-07.3  Intel Corp. 82371AB/EB/MB PIIX4 ACPI
john@ThinkPad:~$ lspci -vt
-+-[06]---00.0  Texas Instruments TSB12LV23 IEEE-1394 Controller
 \-[00]-+-00.0  Intel Corp. 440BX/ZX/DX - 82443BX/ZX/DX Host bridge
        +-01.0-[01]----00.0  Neomagic Corporation NM2360 [MagicMedia 256ZX]
        +-02.0  Texas Instruments PCI1450
        +-02.1  Texas Instruments PCI1450
        +-03.0  Lucent Microelectronics WinModem 56k
        +-06.0  Cirrus Logic CS 4614/22/24 [CrystalClear SoundFusion Audio Accelerator]
        +-07.0  Intel Corp. 82371AB/EB/MB PIIX4 ISA
        +-07.1  Intel Corp. 82371AB/EB/MB PIIX4 IDE
        +-07.2  Intel Corp. 82371AB/EB/MB PIIX4 USB
        \-07.3  Intel Corp. 82371AB/EB/MB PIIX4 ACPI

Kind Regards

John

---

### Post by Zymous on 2005-06-17
I had a similar problem with a Toshiba Equium A60 and a Linksys WPC11 ver 4 card.

After days of searching I found my answer on [http://www.linuxforum.com/forums/index.php?showtopic=122887](http://www.linuxforum.com/forums/index.php?showtopic=122887). Nova's post of "Mar 24 2005, 01:16 PM" in follow up to his original post "Pcmcia Problem, Unable to detect Belkin F5D7010" sorted out my problem and can be summarised in one line

setpci -s 0:14.4 SUBORDINATE_BUS=03

but your numbers may vary - nova's post explains why.

-- 
Zym

---

### Post by john_walsh54 on 2005-06-23
ZYM
Thanks for your help. Since the last time I posted, I found this solution worked for me [http://ubuntuforums.org/showpost.php?p=119707&postcount=2](http://ubuntuforums.org/showpost.php?p=119707&postcount=2)
Thanks for your help anyway.

---

