---
title: "kingsun 959"
date: 2009-03-31
forum: Hardware
---

### Post by jeepmonster01 on 2009-03-31
I know that there is a thread for this, but it is old and it does not work; because i have the 8.10 version. I am really new to this os (and linux) and was hoping that someone could help me with this in real easy terms since its been 20 years or so since i have done code. i have downloaded the file and i also have downloaded hotwire. i cant figure this out was wondering if someone could help me put it in steps(1,2,3) for me please

---

### Post by jeepmonster01 on 2009-04-17
ive figured it out it just takes practice

---

### Post by scott.nightingale on 2009-10-19
Hi I've got the same IRDA dongle (Ubuntu 9.04).  Can you let me know what you did to get this going with aforementioned driver?

Thanks

---

### Post by pricinosus on 2009-11-13
To install it, you should extract the files inside the tarball, cd into the directory with the files, then run
make
sudo su -c "make install"

---

### Post by hdlucas on 2010-11-15
Hallo,
das make bricht unter 10.10 ab. Meldungen:
make[1]: Betrete Verzeichnis '/usr/src/linux-headers-2.6.35-23-generic'
  CC [M]  /home/horst/Downloads/ks-959-1/ks959-sir.o
/home/horst/Downloads/ks-959-1/ks959-sir.c: In function ‘ks959_probe’:
/home/horst/Downloads/ks-959-1/ks959-sir.c:814: error: ‘struct net_device’ has no member named ‘hard_start_xmit’
/home/horst/Downloads/ks-959-1/ks959-sir.c:815: error: ‘struct net_device’ has no member named ‘open’
/home/horst/Downloads/ks-959-1/ks959-sir.c:816: error: ‘struct net_device’ has no member named ‘stop’
/home/horst/Downloads/ks-959-1/ks959-sir.c:817: error: ‘struct net_device’ has no member named ‘get_stats’
/home/horst/Downloads/ks-959-1/ks959-sir.c:818: error: ‘struct net_device’ has no member named ‘do_ioctl’
/home/horst/Downloads/ks-959-1/ks959-sir.c:824: error: implicit declaration of function ‘info’
make[2]: *** [/home/horst/Downloads/ks-959-1/ks959-sir.o] Fehler 1
make[1]: *** [_module_/home/horst/Downloads/ks-959-1] Fehler 2
make[1]: Verlasse Verzeichnis '/usr/src/linux-headers-2.6.35-23-generic'
make: *** [ks959-sir.ko] Fehler 2
Was tun?

---

### Post by hdlucas on 2010-11-15
Sorry should have been in English. 
Make aborts as quoted above.
Any idea?

---

