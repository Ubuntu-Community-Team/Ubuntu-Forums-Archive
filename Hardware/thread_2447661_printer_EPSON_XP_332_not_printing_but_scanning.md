---
title: "printer EPSON XP 332 not printing but scanning"
date: 2020-07-23
forum: Hardware
---

### Post by alain.roger on 2020-07-23
Hi,

my mom has a printer / multifunction EPSON XP 332 USB connected to ubuntu 20.04 .
While this printer scans without any issue, i'm not able to make it print.

I tried several methods under KDE plasma 5.

1. standard method: settings > printers

[[IMG]https://i.ibb.co/qM8pDcc/2020-07-lsb-driver.png[/IMG]]("https://imgbb.com/")


2. using http:localhost:631 interface

[[IMG]https://i.ibb.co/nCSzqxc/2020-07-localhost-port-631.png[/IMG]]("https://ibb.co/74F2xsW")

the only thing i get while printing a testing page is "Rendering completed". However no page is printed.


[[IMG]https://i.ibb.co/3WgWyLX/2020-07-rendering-completed-not-printing.png[/IMG]]("https://imgbb.com/")


Any idea what could be the problem ?
printer is connected using USB or USB Hub and result is always the same.
thx

---

### Post by brian_p on 2020-07-23
Please give what you get for ```
scanimage -L
``` ```
systemctl list-units "ippusbxd*" | grep service
``` ```
lpstat -l -e
```

---

### Post by brian_p on 2020-07-26
I imagine mom has solved her problem but does not want anyone to know how she did it. Very wise. Disseminating knowledge could help others.

---

### Post by alain.roger on 2020-07-28
> **brian_p said:**
> Please give what you get for ```
scanimage -L
``` ```
systemctl list-units "ippusbxd*" | grep service
``` ```
lpstat -l -e
```

Sorry i was out for few days...

Anyway, here it is:

lsusb returns:
 ```
[FONT=monospace][COLOR=#000000]Bus 003 Device 005: ID 04b8:1103 Seiko Epson Corp.[/COLOR][/FONT] 
```[FONT=monospace]
[/FONT]
scanimage -L returns

```
[FONT=monospace][COLOR=#000000]
device `escl:http://127.0.0.1:60000' is a ESCL XP-332 335 Series [573237503230303918] flatbed scanner[/COLOR]
[/FONT]
```


systemctl list-units "ippusbxd*" | grep service returns:

```
[FONT=monospace][COLOR=#000000]ippusbxd@003:005.[/COLOR][COLOR=#FF5454]**service**[/COLOR][COLOR=#000000] loaded active running Daemon to make IPP-over-USB printers available as network printers (003:005)[/COLOR][/FONT]
```


lpstat -l -e returns:
```
[FONT=monospace][COLOR=#000000]EPSON_XP-332_335_Series permanent ipp://localhost/printers/EPSON_XP-332_335_Series ipp://XP-332%20335%20Series%20%5B573237503230303918%5D._ipp._tcp.local/[/COLOR]
XP_332_335_Series_573237503230303918_ network none ipp://XP-332%20335%20Series%20%5B573237503230303918%5D._ipp._tcp.local/[/FONT]
```

---

### Post by brian_p on 2020-07-28
> **alain.roger said:**
> Sorry i was out for few days...

I was feeling grumpy at the time :(.

> 
Anyway, here it is:

lsusb returns:
 ```
[FONT=monospace][COLOR=#000000]Bus 003 Device 005: ID 04b8:1103 Seiko Epson Corp.[/COLOR][/FONT] 
```[FONT=monospace]
[/FONT]
scanimage -L returns

```
[FONT=monospace][COLOR=#000000]
device `escl:http://127.0.0.1:60000' is a ESCL XP-332 335 Series [573237503230303918] flatbed scanner[/COLOR]
[/FONT]
```


systemctl list-units "ippusbxd*" | grep service returns:

```
[FONT=monospace][COLOR=#000000]ippusbxd@003:005.[/COLOR][COLOR=#FF5454]**service**[/COLOR][COLOR=#000000] loaded active running Daemon to make IPP-over-USB printers available as network printers (003:005)[/COLOR][/FONT]
```

All ok.

> 
lpstat -l -e returns:
```
[FONT=monospace][COLOR=#000000]EPSON_XP-332_335_Series permanent ipp://localhost/printers/EPSON_XP-332_335_Series ipp://XP-332%20335%20Series%20%5B573237503230303918%5D._ipp._tcp.local/[/COLOR]
XP_332_335_Series_573237503230303918_ network none ipp://XP-332%20335%20Series%20%5B573237503230303918%5D._ipp._tcp.local/[/FONT]
```

I reckon the first print queue entry could be  using an Epson driver. Your sceenshots indicate such a driver is on your system. This driver will not work with ippusbxd installed. See

[https://wiki.debian.org/CUPSDriverlessPrinting#ippoverusb](https://wiki.debian.org/CUPSDriverlessPrinting#ippoverusb)

and the sections following it. (ipp-usb and ippusbxd do the same job).

The second queue should work. Execute ```
lpadmin -p xp332 -v "ipp://XP-332%20335%20Series%20%5B573237503230303918%5D._ipp._tcp.local/" -E -m everywhere
```

Try printing with ```
lp -d xp332 /etc/nsswitch.conf
```

How's that?

---

### Post by alain.roger on 2020-08-03
> **brian_p said:**
> 

Execute ```
lpadmin -p xp332 -v "ipp://XP-332%20335%20Series%20%5B573237503230303918%5D._ipp._tcp.local/" -E -m everywhere
```


returns me: [FONT=monospace][COLOR=#000000]lpadmin: Unable to query printer: Requête incorrecte.[/COLOR]

[/FONT]
> **brian_p said:**
> 
Try printing with ```
lp -d xp332 /etc/nsswitch.conf
```


returns: [FONT=monospace][COLOR=#000000]lp : Aucun fichier ou dossier de ce type
i.e: lp: no such file or folder
[/COLOR]
i guess you wanted to tell lpr. If i write lpr command, the printer xp332 is not known. Anyway i tried each printer name returned by the lpstat with no success.
I wonder why you are using xp332 as printer name as this name is not return by any command line. I understood that in your command line xp332 is the NAME of the printer and it should not have any impact on the job sent to the printer via pool.

In order to be sure, i decided to reinstall printer and here it is what lpstat -l -e returns:

```
[/FONT][FONT=monospace][COLOR=#000000]Epson_Inkjet_Printer_1 permanent ipp://localhost/printers/Epson_Inkjet_Printer_1 ecblp:/var/run/ecblp0[/COLOR]
EPSON_XP-332_reseaux permanent ipp://localhost/printers/EPSON_XP-332_reseaux ipp://XP-332%20335%20Series%20%5B573237503230303918%5D._ipp._tcp.local/
XP_332_335_Series_573237503230303918_ network none ipp://XP-332%20335%20Series%20%5B573237503230303918%5D._ipp._tcp.local/
[/FONT][FONT=monospace]
```

so:
[/FONT][COLOR=#000000][FONT=monospace]Epson_Inkjet_Printer_1: is the local printer installed using the USB port
[/FONT][/COLOR][FONT=monospace]EPSON_XP-332_reseaux: is the local printer (usb is used for ipp protocol) installed the dedicated driver / driverless from ubuntu
[/FONT][FONT=monospace]XP_332_335_Series_573237503230303918_: is the local printer detected by ubuntu but i see no queue and no installation for this one. So i guess this is the one ubuntu installed by its own.[/FONT]

---

