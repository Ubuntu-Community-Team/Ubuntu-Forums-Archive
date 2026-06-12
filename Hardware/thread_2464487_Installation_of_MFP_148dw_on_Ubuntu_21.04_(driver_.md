---
title: "Installation of MFP 148dw on Ubuntu 21.04 (driver issues)"
date: 2021-07-03
forum: Hardware
---

### Post by alain.roger on 2021-07-03
Hi,

My mom purchased a Multifunction MFP148dw HP device and It already worked under Ubuntu 20.04. However due to installation of new SSD, I decided to do a clean install of latest ubuntu version 21.04.

I downloaded HP driver ([https://developers.hp.com/hp-linux-imaging-and-printing/gethplip](https://developers.hp.com/hp-linux-imaging-and-printing/gethplip)) HPLIP 3.21.4 to be able to use printer and scanner.

During installation of HP drivers, drivers raised that some librairies are missing and need to be installed:
```
[FONT=monospace][COLOR=#000000]pyqt5-dbus           gui_qt5              OPTIONAL             [/COLOR]
pil                  scan                 OPTIONAL             
pyqt4-dbus           gui_qt4              REQUIRED             
libavahi-dev         scan                 REQUIRED             
python-dbus          fax                  REQUIRED             
reportlab            fax                  OPTIONAL             
pyqt5                gui_qt5              REQUIRED             
pyqt4                gui_qt4              REQUIRED             
python-notify        gui_qt5              OPTIONAL  
[/FONT]
```

It seems ubuntu 21.04 does not include "[FONT=monospace][COLOR=#000000]python-qt4-dbus" and this lib was included in ubuntu 18.04 for the last time.
How can I install it on Ubuntu 21.04 ?
Is there someone who succeed in it ?

thx
[/COLOR]
[/FONT]

---

### Post by brian_p on 2021-07-03
> **alain.roger said:**
> Hi,

My mom purchased a Multifunction MFP148dw HP device and It already worked under Ubuntu 20.04. However due to installation of new SSD, I decided to do a clean install of latest ubuntu version 21.04.

I downloaded HP driver ([https://developers.hp.com/hp-linux-imaging-and-printing/gethplip](https://developers.hp.com/hp-linux-imaging-and-printing/gethplip)) HPLIP 3.21.4 to be able to use printer and scanner.


USB or wireless?

The HPLIP provided by 21.04 supports the MFP148dw.

---

### Post by alain.roger on 2021-07-07
USB connected.
I was successful with drivers supplied by ubuntu packages... Official drivers from HP website did not install

---

