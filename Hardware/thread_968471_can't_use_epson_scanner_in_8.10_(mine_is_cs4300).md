---
title: "can't use epson scanner in 8.10 (mine is cs4300)"
date: 2008-11-02
forum: Hardware
---

### Post by sam1948 on 2008-11-02
for a first installation the printer will work !
but i need help 
accidentally i installed the epson linux driver([from avasys]("http://www.avasys.jp/lx-bin2/linux_e/spc/DL1.do"))
now the printer has stoped working and i don't know how to remove that driver ?!?!?

_**printer:**_
install printer via 
System ==> Administration ==> printing ==> new printer
(8.10 tries to find a driver by it self press _cancel_ when it dose)
select epson and _cx5500_ when you will be asked
apply and the printer should now work

_**scanner:**_
i had it solved ' but i probably did some thing more i'll keep looking

driver can be downloaded from _[here(file one)]("http://lx1.avasys.jp/iscan/2.10.0/iscan-2.10.0-1.c2.i386.rpm")_
[second file from here]("http://lx1.avasys.jp/iscan/2.10.0/iscan-plugin-cx4400-2.0.0-0.c2.i386.rpm")
open terminl
enter the directory with the downloaded files
```
sudo alien --scripts first_downloaded_rpm_file
```
```
sudo alien --scripts second_downloaded_rpm_file
```
```
sudo dpkj -i first_deb_file_created
```
```
sudo dpkj -i second_deb_file_created
```
the scanner should now work

Please let me know if it works because I messed up with my computer a lot before finding this solution so it might be incomplete



i had a **problem** with the scanner some thing about printer and scanner using the connection at the same time 
i think it was because the printer ink was empty and it tried to tell me that
any way with new inks it should just work
**_if any one solves this one please post it here _**

the printers which are listed below should have the same drivers so in case you end up with other non working printer or scanner you can look for solution to any of them
this info is from _[this page]("http://linux.avasys.jp/customerservice/pips3x_ubuntu804_e.html#caution")_


(Search extras: a bit messy but has the important key words: PX-V780  PM-G860, PX-G5100  PX-G930  PX-V630  PX-5500  PX-5800    Pro 3800 Photo R2400 Stylus Photo R280/R285/R290 Epson Stylus C110/C120/D120 (v3.0)
     Stylus C90/C91/C92/D92 (v3.0)
    Stylus D78/C79 (v3.0)
     Stylus C58/C59/ME2 (v3.0)
     Stylus CX6900F/DX7000F (v3.0)
    * Epson Stylus CX5700F/CX5800F (v3.0)
    * Epson Stylus CX4300/CX4400/CX4450/CX5500/CX5600/DX4400/DX4450 (v3.0)
    * Epson Stylus S20/T10/T11/T20/T20E/T23/T26 (v3.1)

---

