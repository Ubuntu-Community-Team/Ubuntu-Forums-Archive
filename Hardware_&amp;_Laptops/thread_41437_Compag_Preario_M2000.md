---
title: "Compag Preario M2000"
date: 2005-06-13
forum: Hardware &amp; Laptops
---

### Post by Cubanismo on 2005-06-13
Can't make the modem and the wireless connexion work. Any idea?

Please go slowly and patiently, total linux beginner here.

Config:

Compaq presario M2000
Dual boot (Win XP Home)
Shared FAT32 partition between the 2 OS

---

### Post by jrhodes on 2005-06-13
Compaq's service site is being unbearably slow this afternoon but it seems your system has an Intel 802.11b/g wireless chip of some sort (probably a 2200) and an unspecified modem.

The modem is highly unlikely to have any support, but the wireless NIC is supported by the ipw2200 module, which ships with ubuntu. 

Open up a terminal and type sudo /sbin/modprobe ipw2200
enter the password when it asks you
and then check your network settings. If it shows up, add ipw2200 to /etc/modules with an editor.

---

### Post by Cubanismo on 2005-06-13
Thanks

I'll try that, for the modem I'll find the manufactor and reference under XP and come back

---

### Post by Cubanismo on 2005-06-14
[QUOTE=Cubanismo]Thanks

I'll try that, for the modem I'll find the manufactor and reference under XP and come back[/QUOTE]
 Ok the wireless connection is working with the Acces point configured in open network. I'll check for a more secured config later.

Any good software for scanning acces point?

PS: The modem on the pesario M2000 is a Conextant Soft V90 with smartcp, any idea where I can find help for this one?

---

### Post by Cubanismo on 2005-06-15
Ok, after a search on the net I found a tar package for the modem. My modem is listed in it and all looks fine but...

When I do the make install Iget this :
> cc -I../imported/include -I../modules/osspec/include -DFRAME_WORK=FWK_LINUX_SOFT K56 -DFRAME_WORK_IMPORTED -DOVERRIDE_NEW=1 -DPORTABILITY=0 -DMULTYDP -DHSFLINUXV ERSION="\"5.03.27lnxtbeta03042700\"" -O2 -Wall   -c -o inf2bin.o inf2bin.c
/bin/sh: cc: command not found
make[1]: *** [inf2bin.o] Erreur 127
make[1]: quittant le répertoire « /home/alain/Desktop/hsflinmodem/inf2bin »
make: *** [install] Erreur 2


I guess that cc is a C compiler not included in the Ubuntu distribution. Am I right?

What can I do to solve that problem?

---

### Post by christgod on 2005-06-16
Install the build-essential package.

---

