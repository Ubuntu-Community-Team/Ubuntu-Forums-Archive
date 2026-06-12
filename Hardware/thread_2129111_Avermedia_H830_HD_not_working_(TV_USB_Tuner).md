---
title: "Avermedia H830 HD not working (TV USB Tuner)"
date: 2013-03-25
forum: Hardware
---

### Post by ElaMiNaTo on 2013-03-25
Hi,

I am usuing Ubutunu 12.10 with kernel 3.5.0-26. When I try to install the driver from the Avermedia homepage [http://www.avermedia.com/product/ProductDetail.aspx?Id=501&tab=APDriver](http://www.avermedia.com/product/ProductDetail.aspx?Id=501&tab=APDriver) I geht the following output:

```
/lib/modules/3.5.0-26-generic/build found.
Verifying archive integrity...
Extracting archive...
Running installer...
Start to compile objects...
Failed to compile objects
cp -f prebuild.bak prebuild.o
make -C /lib/modules/3.5.0-26-generic/build  O=/lib/modules/3.5.0-26-generic/build SUBDIRS=`pwd` modules
make[1]: Betrete Verzeichnis '/usr/src/linux-headers-3.5.0-26-generic'
  CC [M]  /tmp/avm-install/installer/KernToDemod.o
  CC [M]  /tmp/avm-install/installer/osdep.o
  CC [M]  /tmp/avm-install/installer/osdep_i2c.o
/tmp/avm-install/installer/osdep_i2c.c:315:1: Warnung: Datendefinition hat keinen Typ oder Speicherklasse [standardmäßig aktiviert]
/tmp/avm-install/installer/osdep_i2c.c:315:1: Warnung: »int« ist Standardtyp in Deklaration von »EXPORT_SYMBOL« [-Wimplicit-int]
/tmp/avm-install/installer/osdep_i2c.c:315:1: Warnung: Parameternamen (ohne Typen) in Funktionsdeklaration [standardmäßig aktiviert]
  CC [M]  /tmp/avm-install/installer/osdep_dvb_2.o
/tmp/avm-install/installer/osdep_dvb_2.c: In Funktion »a336VSBGetModFromFrontendParam«:
/tmp/avm-install/installer/osdep_dvb_2.c:778:21: Fehler: Dereferenzierung eines Zeigers auf unvollständigen Typen
/tmp/avm-install/installer/osdep_dvb_2.c: In Funktion »a336DVBTGetBWFromFrontendParam«:
/tmp/avm-install/installer/osdep_dvb_2.c:792:21: Fehler: Dereferenzierung eines Zeigers auf unvollständigen Typen
/tmp/avm-install/installer/osdep_dvb_2.c:793:7: Fehler: »BANDWIDTH_8_MHZ« nicht deklariert (erste Benutzung in dieser Funktion)
/tmp/avm-install/installer/osdep_dvb_2.c:793:7: Anmerkung: jeder nicht deklarierte Bezeichner wird nur einmal für jede Funktion, in der er vorkommt, gemeldet
/tmp/avm-install/installer/osdep_dvb_2.c:794:7: Fehler: »BANDWIDTH_7_MHZ« nicht deklariert (erste Benutzung in dieser Funktion)
/tmp/avm-install/installer/osdep_dvb_2.c:795:7: Fehler: »BANDWIDTH_6_MHZ« nicht deklariert (erste Benutzung in dieser Funktion)
/tmp/avm-install/installer/osdep_dvb_2.c: In Funktion »a336DVBGetFreqFromFrontendParam«:
/tmp/avm-install/installer/osdep_dvb_2.c:804:21: Fehler: Dereferenzierung eines Zeigers auf unvollständigen Typen
/tmp/avm-install/installer/osdep_dvb_2.c: In Funktion »a336DVBSetTunerParam«:
/tmp/avm-install/installer/osdep_dvb_2.c:815:12: Fehler: zu viele Argumente für Funktion »fe->ops.tuner_ops.set_params«
/tmp/avm-install/installer/osdep_dvb_2.c:819:12: Fehler: zu viele Argumente für Funktion »fe->ops.tuner_ops.set_params«
/tmp/avm-install/installer/osdep_dvb_2.c: In Funktion »a336VSBSetFrontendParam«:
/tmp/avm-install/installer/osdep_dvb_2.c:826:14: Fehler: Dereferenzierung eines Zeigers auf unvollständigen Typen
/tmp/avm-install/installer/osdep_dvb_2.c:827:14: Fehler: Dereferenzierung eines Zeigers auf unvollständigen Typen
/tmp/avm-install/installer/osdep_dvb_2.c: In Funktion »a336DVBTSetFrontendParam«:
/tmp/avm-install/installer/osdep_dvb_2.c:836:33: Fehler: Dereferenzierung eines Zeigers auf unvollständigen Typen
/tmp/avm-install/installer/osdep_dvb_2.c:837:14: Fehler: Dereferenzierung eines Zeigers auf unvollständigen Typen
/tmp/avm-install/installer/osdep_dvb_2.c:838:14: Fehler: Dereferenzierung eines Zeigers auf unvollständigen Typen
/tmp/avm-install/installer/osdep_dvb_2.c:838:45: Fehler: »BANDWIDTH_6_MHZ« nicht deklariert (erste Benutzung in dieser Funktion)
/tmp/avm-install/installer/osdep_dvb_2.c:839:45: Fehler: »BANDWIDTH_7_MHZ« nicht deklariert (erste Benutzung in dieser Funktion)
/tmp/avm-install/installer/osdep_dvb_2.c:840:45: Fehler: »BANDWIDTH_8_MHZ« nicht deklariert (erste Benutzung in dieser Funktion)
/tmp/avm-install/installer/osdep_dvb_2.c:840:63: Fehler: »BANDWIDTH_AUTO« nicht deklariert (erste Benutzung in dieser Funktion)
/tmp/avm-install/installer/osdep_dvb_2.c:841:14: Fehler: Dereferenzierung eines Zeigers auf unvollständigen Typen
/tmp/avm-install/installer/osdep_dvb_2.c: In Funktion »a336DVBGetFreqFromFrontendParam«:
/tmp/avm-install/installer/osdep_dvb_2.c:805:1: Warnung: Kontrollfluss erreicht Ende von Nicht-void-Funktion [-Wreturn-type]
make[3]: *** [/tmp/avm-install/installer/osdep_dvb_2.o] Fehler 1
make[2]: *** [_module_/tmp/avm-install/installer] Fehler 2
make[1]: *** [sub-make] Fehler 2
make[1]: Verlasse Verzeichnis '/usr/src/linux-headers-3.5.0-26-generic'
make: *** [default] Fehler 2

Install log generated on /root/driver_install_log.txt


```

Unfortunately some output is german. But nonetheless maybe you know what could be wrong.
Nicht-deklariert = NOT-DECLARED
Fehler = Error

Thanks for help.

---

### Post by jiemeb on 2014-01-04
Hi,
I try too. But unfortunatly avermedia don't support kernel 3.0 of Linux. 
I try to get source from avermedia but I don't have any answer. :(
Only windaub are supported.


Regards

---

### Post by zarac2 on 2014-01-20
Actually, H830 does kind-of work (DVB-T only, remote does not work, I haven't even tried analogue) with kernel 3.0 and up to 3.2, but not with anything above that.
I currently run it with no problems (TvHeadend and MythTV) on Ubuntu LTS 12.04 with kernel v3.2.0-49.
The linux driver used to be located on AverMedia H830 drivers page, but they removed it a while ago.

Fortunately I kept a copy and you can find it attached to this post.

---

