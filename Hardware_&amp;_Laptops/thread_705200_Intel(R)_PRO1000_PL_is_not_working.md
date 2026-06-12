---
title: "Intel(R) PRO/1000 PL is not working"
date: 2008-02-23
forum: Hardware &amp; Laptops
---

### Post by Chillbilly on 2008-02-23
hey all
Ich habe Ubuntu 7.10 auf einem Samsung X60
Meine Lan-Karte Intel(R) PRO/1000 PL wird dabei aber nicht erkannt.
Habe den Treiber e1000-7.6.15.4 runtergeladen und mit "make install" versucht zu installieren
Dabei erscheint folgende Meldung:

[I]root@Josef:/home/mat/Desktop/e1000-7.6.15.4/src# make install
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
e1000.[/I]


nach einem modprobe e1000 und reboot erscheint aber keine Lan karte

Hätte mir jemand eine Tipp oder kann mir jemand sagen was ich falsch mache?
Vielen Dank im Voraus

---

### Post by Chillbilly on 2008-02-24
Hey all
wäre um Hilfeleistung sehr dankbar ):P

---

