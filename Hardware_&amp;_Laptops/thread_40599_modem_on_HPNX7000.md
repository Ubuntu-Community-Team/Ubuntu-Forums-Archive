---
title: "modem on HPNX7000"
date: 2005-06-09
forum: Hardware &amp; Laptops
---

### Post by ntanghe on 2005-06-09
Hello,

I have a HPNX 7000 laptop and my modem 56k don't work. I have downloaded scanModem for identifying the modem's chip but it is not very lucid explainations for me :(

Class 0703: 8086:24c6   Modem: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01) (prog-if 00 [Generic])
  SubSystem 0e11:0860   Compaq Computer Corporation: Unknown device 0860
0000:00:1f.6 0703: 8086:24c6 (rev 01)
        Flags: bus master, medium devsel, latency 0, IRQ 10
        I/O ports at 4400 [size=256]
        I/O ports at 4800 [size=128]

                  -----PCI_IDs-------                    --CompilerVer-
    Feature List:  Primary  Subsystem Distr  KernelVer   kernel default  CPU
 ./scanModem test 8086:24c6 0e11:0860 debian 2.6.10-5-386 3.3.5 3.3.5    i686


 The soft modem Subsystem operates under a controller
   8086:24c6 82801DB ICH4



Somebody have a HPNX700 and help me ?
Thanks a lot

---

### Post by uidzer0org on 2005-06-22
is this s winmodem? they are not supported in linux

---

### Post by somez on 2005-06-23
[QUOTE=ntanghe]Hello,

I have a HPNX 7000 laptop and my modem 56k don't work. I have downloaded scanModem for identifying the modem's chip but it is not very lucid explainations for me :(

Class 0703: 8086:24c6   Modem: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01) (prog-if 00 [Generic])
  SubSystem 0e11:0860   Compaq Computer Corporation: Unknown device 0860
0000:00:1f.6 0703: 8086:24c6 (rev 01)
        Flags: bus master, medium devsel, latency 0, IRQ 10
        I/O ports at 4400 [size=256]
        I/O ports at 4800 [size=128]

                  -----PCI_IDs-------                    --CompilerVer-
    Feature List:  Primary  Subsystem Distr  KernelVer   kernel default  CPU
 ./scanModem test 8086:24c6 0e11:0860 debian 2.6.10-5-386 3.3.5 3.3.5    i686


 The soft modem Subsystem operates under a controller
   8086:24c6 82801DB ICH4



Somebody have a HPNX700 and help me ?
Thanks a lot[/QUOTE]

Can you tell wether the other parts of your computer are working or not? I also want to buy a HP NX7000, but I haven't choose one yet.

---

### Post by ntanghe on 2005-06-27
yes all other parts works fine...

Nicolas

---

### Post by somez on 2005-06-27
[QUOTE=ntanghe]yes all other parts works fine...

Nicolas[/QUOTE]

That's great! Thanks for your answer. Try searching for "winmodem" in this forum, because I've read that someone could make it working under ubuntu.

---

