---
title: "Camera not recognized"
date: 2024-09-24
forum: Hardware
---

### Post by leocig on 2024-09-24
I have a Lenovo Thinkpad T460s and the camera is recognized in lsusb:
```
Bus 001 Device 004: ID 5986:0706 Bison Electronics Inc. ThinkPad P50 Integrated Camera

```
but when I open Cheese the camera doesn't get recognized.

Note that I've used this pc with linux mint also and the camera got recognized without any problem there

```
# Rapporto sui dettagli del sistema
---

## Dettagli del rapporto
- **Generato in data:**                            2024-09-24 21:31:24

## Informazioni sull'hardware:
- **Modello hardware:**                            Lenovo ThinkPad T460s
- **Memoria:**                                     8,0 GiB
- **Processore:**                                  Intel® Core™ i5-6300U × 4
- **Scheda grafica:**                              Intel® HD Graphics 520 (SKL GT2)
- **Capacità del disco:**                          512,1 GB

## Informazioni sul software:
- **Versione del firmware:**                       N1CET90W (1.58 )
- **Nome del sistema operativo**                   Ubuntu 24.04.1 LTS
- **Build del sistema operativo:**                 (null)
- **Tipo di sistema operativo:**                   64-bit
- **Versione di GNOME:**                           46
- **Gestore grafico:**                             Wayland
- **Versione del kernel:**                         Linux 6.8.0-45-generic


```

---

### Post by yancek on 2024-09-24
Do you open it from the GUI menu?  Have you tried running cheese from a terminal?  If not, try that and if it fails take note of any warning/error messages when you close cheese.  When was it recognized with Mint and which release of Mint were you using?  The site at the link below shows various Thinkpad computer and how they work/or don't work with a number of Linux distros.

[http://linux-hardware.org/?id=usb:5986-02d2](http://linux-hardware.org/?id=usb:5986-02d2)

---

### Post by leocig on 2024-09-24
It worked with mint 22 wilma. I had tried cheese with ubuntu lts 22.04.05, and I updated it today to 22.04.01. I tried to open the camera (it wasn't called cheese) and it said device not found. After reading your post i installed cheese and tried it, and the camera works. Sorry for not having tried that earlier and thanks for your help. I'll mark the thread as solved

---

