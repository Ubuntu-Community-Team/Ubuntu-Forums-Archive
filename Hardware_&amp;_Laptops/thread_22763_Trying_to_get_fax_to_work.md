---
title: "Trying to get fax to work"
date: 2005-03-29
forum: Hardware &amp; Laptops
---

### Post by sunscape on 2005-03-29
I have been checking the forum looking for a way to get my fujitsu p7010 to use the modem and send/recieve faxes. So I ran accross a thread talking about scanModem. I ran it and this is the output. What now?

Thanks


UPDATE=2005_March_27
ONLY use scanModem downloaded as: [http://linmodems.technion.ac.il/packages/scanModem.gz](http://linmodems.technion.ac.il/packages/scanModem.gz)

 scanModem should ONLY be run within a Linux/UNIX partition.
   If within a MicroSoft/DOS partition, abort with Ctrl-C now !!!
   Copy scanModem.gz to your Linux partition and restart.

PCIBUS=0000:00:1f.6

Providing detail for device at PCI_bus 0000:00:1f.6
  with vendor-ID:device-ID
            ----:----
Class 0703: 8086:24c6   Modem: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03) (prog-if 00 [Generic])
  SubSystem 10cf:10d1   Fujitsu Limited.: Unknown device 10d1
0000:00:1f.6 0703: 8086:24c6 (rev 03)
        Flags: bus master, medium devsel, latency 0, IRQ 11
        I/O ports at 2400 [size=256]
        I/O ports at 2000 [size=128]

                  -----PCI_IDs-------                    --CompilerVer-
    Feature List:  Primary  Subsystem Distr  KernelVer   kernel default  CPU
 ./scanModem test 8086:24c6 10cf:10d1 debian 2.6.10-5-686 3.3.5 3.3.5    i686


 The soft modem Subsystem operates under a controller
   8086:24c6 82801DB ICH4
 capable of supporting under Linux AT LEAST modem Subsystem chips from manufacturers:
        Broadcom
        AgereSystems
        Conexant
        Intel
        Smartlink



   A subfolder Modem/  has been written,  containing these files with more detailed Information:
 ------------------------------------------------------------------------------------------
 1stRead.txt ATI.txt DriverCompiling.txt General.txt ModemData.txt Rational.txt Slmodem.txt SoftModem.txt Testing.txt UNSUBSCRIBE.txt
-------------------------------------------------------------------------------------------
       Please read 1stRead.txt first for Guidance.

---

