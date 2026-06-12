---
title: "Intel(R) PRO/1000 PL is not working"
date: 2008-02-26
forum: Hardware &amp; Laptops
---

### Post by Chillbilly on 2008-02-26
hey all
I am working with Ubuntu 7.10 on my Samsung X60 laptop
My Lan-Network card Intel(R) PRO/1000 PL is not working nor detected.
So I downloaded the Intel driver  e1000-7.6.15.4 which should work with my Network card.
After a "make install" I got the following:

root@Josef:/home/mat/Desktop/e1000-7.6.15.4/src# make install
make -C /lib/modules/2.6.22-14-generic/build SUBDIRS=/home/mat/Desktop/e1000-7.6.15.4/src modules
make[1]: Betrete Verzeichnis '/usr/src/linux-headers-2.6.22-14-generic'
Building modules, stage 2.
MODPOST 1 modules
make[1]: Verlasse Verzeichnis '/usr/src/linux-headers-2.6.22-14-generic'
# remove all old versions of the driver
find /lib/modules/2.6.22-14-generic -name e1000.ko -exec rm -f {} \; || true
find /lib/modules/2.6.22-14-generic -name e1000.ko.gz -exec rm -f {} \; || true
install -D -m 644 e1000.ko /lib/modules/2.6.22-14-generic/kernel/drivers/net/e1000/e1000.ko
/sbin/depmod -a || true
install -D -m 644 e1000.7.gz /usr/share/man/man7/e1000.7.gz
man -c -P'cat > /dev/null' e1000 || true
man:
Kann im catman Modus nicht nach /var/cache/man/cat7/e1000.7.gz schreiben
e1000.

I am not sure what went wrong, because it said: "I can't write to /var/cache/man/cat7/e1000.7.gz in catman Mode"

After a modprobe e1000 and a reboot my Lan Network-Card is still not working. Just eta0, witch is the wlan card.

If someone could help me out here I would appreciate it very much
Thanks

---

