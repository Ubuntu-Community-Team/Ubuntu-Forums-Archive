---
title: "Satelco EasyWatch DVB-T"
date: 2005-11-29
forum: Hardware &amp; Laptops
---

### Post by skyboy on 2005-11-29
Does anybody know how to setup this DVB-T card to work under Breezy ??
 I guess it should use a dvb firmware named pluto2 but there isn't such in Breezy. How to get it work please ??
 
 Card is : Satelco EasyWatch DVB-T (Tuner Philips TDA10046, LG Innotek TDTE-E001P)

---

### Post by skyboy on 2005-11-29
ok, I've managed to find the pluto2 driver for the card.
Then I had to modify a file and I finally got it to compile and to load the module. here is the log :
[4294927.892000] PCI: Enabling device 0000:03:00.0 (0000 -> 0002)
[4294927.892000] ACPI: PCI Interrupt 0000:03:00.0[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[4294927.892000] PCI: Setting latency timer of device 0000:03:00.0 to 64
[4294927.892000] Pluto 2 MacAddress : 00:d0:16:02:22:7d
[4294927.892000] Pluto Card Revision (Maj,Min) : (2,15)
[4294927.893000] DVB: registering new adapter (SCM Microsystems Pluto2 driver).
[4294927.940000] Detected Philips Tda10046H frontend
[4294927.940000] Detected LG Innotek TdtpE001P Tuner
[4294927.940000] Please wait while uploading firmware...
[4294935.451000] Firmware uploaded successfully !
[4294935.451000] DVB: registering frontend 0:0 (Philips TDA10046H)...


Now, I still can't use it ! why  ??? do I need to create something ! actually the led is still not green on the card ;(

any help would be really appreciated

---

### Post by skyboy on 2005-11-29
when I try to scan, I get that :

scanning /usr/share/doc/dvb-utils/examples/scan/dvb-t/fi-Tampere
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
main:1882: FATAL: failed to open '/dev/dvb/adapter0/frontend0': 2 No such file or directory

?? what have I done wrong

the worse it that I have the files !

$ ls -l /dev/dvb/adapter0/demux0
crwxrwxrwx  1 root video 212, 4 2005-11-29 19:27 /dev/dvb/adapter0/demux0

$ ls -l /dev/dvb/adapter0/frontend0
crwxrwxrwx  1 root video 212, 3 2005-11-29 19:27 /dev/dvb/adapter0/frontend0

---

### Post by skyboy on 2005-11-29
Well, I got it to work.
How : I've downloaded the CVS version of the last dvb-kernel (now join with v4l), did a make and make install.
Removed the old modules, and reload everything.
If someone needs further details, message me but for the moment I'm talking to myself here :)
thanks me for my help ! :D

---

