---
title: "Doesn't recognise scanner from HP printer"
date: 2021-02-01
forum: Hardware
---

### Post by loudi on 2021-02-01
Hi,
I changed my printer to a HP Office jet 3830 and as I was testing it it printed the colors in grey, even after checking all settings and verifying that the color cartridge was full. So I followed this tutorial [https://support.hp.com/gb-en/document/bud09113/](https://support.hp.com/gb-en/document/bud09113/) in which the last step is to install the most current printer driver hplip. Now I am able to print colors but I can't use the scanner.

With the Document Scanner software it finds the scanner but when clicking to scan a document it returns "Impossible to connect to the scanner" (translated from french).
With Xsane it returns Erreur de retour du périphérique 'hpaio:/usb/officejet... Erreur d'entrée/sortie sur le périphérique." Which means Error on the return from the peripheral, Error from the entrance/way out on the peripheral. (sounds weird but périphérique is the scanner.)

I don't know if this may help but here it goes:
```
ludi@ludi-ThinkPad-T430:~$ cat /etc/lsb-release && uname -ir && groups && lsusb
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=20.04
DISTRIB_CODENAME=focal
DISTRIB_DESCRIPTION="Ubuntu 20.04.1 LTS"
5.4.0-65-generic x86_64
ludi adm cdrom sudo dip plugdev lpadmin sambashare
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 04f2:b2db Chicony Electronics Co., Ltd Thinkpad T430 camera
Bus 001 Device 003: ID 0a5c:21e6 Broadcom Corp. BCM20702 Bluetooth 4.0 [ThinkPad]
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 009: ID 03f0:e511 HP, Inc OfficeJet 3830 series
Bus 003 Device 002: ID 090c:2000 Silicon Motion, Inc. - Taiwan (formerly Feiya Technology Corp.) USB DISK
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
ludi@ludi-ThinkPad-T430:~$ 


```

```
ludi@ludi-ThinkPad-T430:~$ dpkg -l | grep sane
ii  libsane:amd64                                 1.0.29-0ubuntu5.2                    amd64        API library for scanners
ii  libsane-common                                1.0.29-0ubuntu5.2                    all          API library for scanners -- documentation and support files
ii  libsane-dev:amd64                             1.0.29-0ubuntu5.2                    amd64        API development library for scanners [development files]
ii  libsane-hpaio:amd64                           3.20.3+dfsg0-2                       amd64        HP SANE backend for multi-function peripherals
ii  sane-utils                                    1.0.29-0ubuntu5.2                    amd64        API library for scanners -- utilities
ii  xsane                                         0.999-8ubuntu2                       amd64        featureful graphical frontend for SANE (Scanner Access Now Easy)
ii  xsane-common                                  0.999-8ubuntu2                       all          xsane architecture independent files
ludi@ludi-ThinkPad-T430:~$ 


```

```
[sudo] Mot de passe de ludi : 
found USB scanner (vendor=0x0a5c [Broadcom Corp], product=0x21e6 [BCM20702A0]) at libusb:001:003
found USB scanner (vendor=0x03f0 [HP], product=0xe511 [OfficeJet 3830 series]) at libusb:003:009
ludi@ludi-ThinkPad-T430:~$
```

I was trying a new printer because the old Canon printed with slightly visible parallel lines which made it impossible to print good quality images, and after a long search on printers that work well with Linux I found out that HP made their own drivers for Linux, and that it might solve the issues. Could it be that it is a HP model that has issues on Linux? Can you help me find what is bugging with the scanner?

Thanks
Rod

---

### Post by slickymaster on 2021-02-01
Thread moved to **Hardware** for a better fit

---

### Post by Autodave on 2021-02-01
What version of 'buntu are you running?  How is the printer connected: USB, wifi, ethernet?

---

### Post by loudi on 2021-02-01
Ubuntu 20.04 focal

I am trying with USB.

---

### Post by loudi on 2021-02-01
I tried this tutorial: [https://askubuntu.com/questions/1056077/how-to-install-latest-hplip-on-my-ubuntu-to-support-my-hp-printer-and-or-scanner](https://askubuntu.com/questions/1056077/how-to-install-latest-hplip-on-my-ubuntu-to-support-my-hp-printer-and-or-scanner)  and this one h[ttps://doc.ubuntu-fr.org/hplip]("http://ttps://doc.ubuntu-fr.org/hplip")
and the [HP official one]("https://developers.hp.com/hp-linux-imaging-and-printing/install/install/index")
It always got stuck on the hp-setup graphical interface (even when choosing installing via command line there will be a time when the installation process launches the graphical interface. It finds the printer, the button changes from "Next" to "Add printer" and it doesn't add it. I found the error in the terminal
```
error: Unable to communicate with device (code=12): hp:/usb/OfficeJet_3830_series?serial=CN65H2J1Z30664


```

and when searching for it I found that there was some success when connecting the computer with the printer via the network and the printer's IP address, [here]("https://bugs.launchpad.net/hplip/+bug/1811088/comments/7") and [here]("https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=687395") and [here]("https://www.linuxquestions.org/questions/blog/vik-404221/hplip-error-unable-to-communicate-with-device-code%3D12-35211/")

So I used the printer's digital panel to connect to my home's network and in the process it gave me the IP address, which I added in the hp-setup graphical interface selecting the option to connect the printer through a network and checking the case for manual input. I inserted the IP address there and the hp-setup concluded successfully.

The printing works well.

The Document Scanner doesn't seem to resume, even that it starts the scanning process. But Xsane works well.

issue solved, I would say
Where do we mark it as solved?

---

### Post by ajgreeny on 2021-02-01
I am not totally sure what you mean by
> The printing works well.
The Document Scanner doesn't seem to resume, even that it starts the scanning process. But Xsane works well.
issue solved, I would say 
but if you are really happy that the problem is solved please mark the thread as SOLVED from the Thread Tools menu at the top.

---

