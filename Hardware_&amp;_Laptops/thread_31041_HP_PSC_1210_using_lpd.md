---
title: "HP PSC 1210 using lpd"
date: 2005-05-01
forum: Hardware &amp; Laptops
---

### Post by chungsijay on 2005-05-01
hello, I want to try my HP PSC 1210 printer using lpd
although it  succesfully  work using cupsys,
now I want to try it using lpd.

I install lpr magicfilter gs
and then use `magicfilterconfig` to configure /etc/printcap
and looks like this:
```
lp|hp|HP-PSC_1210:\
:lp=/dev/lp0:sd=/var/spool/lpd/hp:\
:sh:pw#80:pl#72:px#1440:mx#0:\
:if=/etc/magicfilter/hpijs-filter:\
:af=/var/log/lp-acct:lf=/var/log/lp-errs:
```
I try to print a ps file but failed:
lpr -Plp test.ps 

but if I use command line like this, it did printed test.ps
```
gs -sDEVICE=ijs -sIjsServer=hpijs -dIjsUseOutputFD -sDeviceManufacturer="HEWLETT-PACKARD" -sDeviceModel="psc 1200 series" -r300 -dNOPAUSE -dSAFER -sOutputFile="/dev/lp0" test.ps -c quit
```

I dont know whats wrong with my lpd configuration,
I tried many ways like modify /etc/magicfilter/hpijs-filter 
to use the parameters I used in the command line above,
but still failed.

Does someone use lpd to set up HP PSC * printers and works?

---

