---
title: "Trouble with Canon Selphy CP1300 Printer Support"
date: 2020-06-03
forum: Hardware
---

### Post by domenico-somma on 2020-06-03
Hi! I am trying to install canon CP1300 as well, but on Ubuntu 20.04.
If I use the Gnome printer GUI, [COLOR=#000000]the printer goes busy and sometimes respond "Cannot read data! Cannot print incompatible images or memory card not readable".[/COLOR]

I tried the code posted in this thread
```

domenico@domenico-HP-ENVY-Notebook:~$ driverless
ipp://Canon%20SELPHY%20CP1300._ipp._tcp.local/
domenico@domenico-HP-ENVY-Notebook:~$ avahi-browse -rt _ipp._tcp
+ wlp1s0 IPv4 Canon SELPHY CP1300                           Internet Printer     local
= wlp1s0 IPv4 Canon SELPHY CP1300                           Internet Printer     local
   hostname = [CP1300b7ae37.local]
   address = [192.168.1.9]
   port = [631]
   txt = ["note=" "mopria-certified=1.3" "print_wfds=T" "kind=photo" "URF=W8,SRGB24,V1.4,RS300,IS7,MT11,PQ4,OB9,IFU0,OFU0,CP99" "TLS=1.2" "Staple=F" "Sort=F" "Scan=F" "Punch=0" "PaperMax=<legal-A4" "PaperCustom=T" "Fax=F" "Duplex=F" "Copies=T" "Color=T" "Collate=F" "Bind=F" "TBCP=F" "Binary=F" "Transparent=F" "UUID=c4f86db0-9270-4c32-a1ec-9c32ceb7ae37" "usb_CMD=URF" "usb_MDL=SELPHY CP1300" "usb_MFG=Canon" "adminurl=http://CP1300b7ae37.local:8008/index.html" "pdl=image/urf,image/jpeg,image/pwg-raster,application/octet-stream" "product=(Canon SELPHY CP1300 HTTP)" "ty=Canon SELPHY CP1300 HTTP" "priority=50" "qtotal=1" "rp=ipp/print" "txtvers=1"]
domenico@domenico-HP-ENVY-Notebook:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 20.04 LTS
Release:    20.04
Codename:    focal


domenico@domenico-HP-ENVY-Notebook:~$ lpadmin -p cp1300 -v ipp://CP1300b7ae37.local:631/ipp/print -E -m everywhere
lpadmin: Unable to query printer: Success
domenico@domenico-HP-ENVY-Notebook:~$ lp -d cp1300 /etc/nsswitch
lp: Error - unable to access "/etc/nsswitch" - No such file or directory
domenico@domenico-HP-ENVY-Notebook:~$ 

```
but nothing.

I installed gutenprint from synaptic (v5.3), installed via CUPS GUI [http://localhost:631/](http://localhost:631/)
there are 2 "printer" CP1300, I choose the driverless one, then I selected the driverless driver (the driveless version Canon SELPHY CP1300 HTTP, driverless, cups-filters 1.27.4 (color)).
It printed, but the image is 1/4 of the the original one, with a 2 cm white corner on top and right sides. I don't know why.
Any suggestion?
Thanks

---

### Post by QIII on 2020-06-03
Moved to its own post from [here]("https://ubuntuforums.org/showthread.php?t=2423567").

Hello!

Rather than hijacking another user's thread, please start your own.  You may feel free to make reference to the other thread if you think it might help others understand.

There are two problems with hijacking:

1.  The OP of the thread does not get individual attention and attempts to answer two people make a thread confusing.

2.  Although symptoms may appear similar, the root causes are often different.  Your problem may be entirely different than the other person's.

Thanks.

---

