---
title: "Install and Enable wireless Aheros 802.11"
date: 2009-03-24
forum: Hardware
---

### Post by wolfysix on 2009-03-24
Hello Im a totally new to Ubuntu, and i have a little problem with my wireless conection.

I have a laptop Toshiba Satellite A300, AMD Turion X2 64

I dont know how to enable or install the wireless card: Atheros 802.11

I read some website but still nothing I download the ubuntu driver but cant install the driver I get an error:

wolfysix@wolfysix-laptop:~$ cd ~/madwifi
wolfysix@wolfysix-laptop:~/madwifi$ make
Checking requirements... ok.
Checking kernel configuration... ok.
make -C /lib/modules/2.6.27-11-generic/build SUBDIRS=/home/wolfysix/madwifi modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-11-generic'
  CC [M]  /home/wolfysix/madwifi/net80211/ieee80211_power.o
/home/wolfysix/madwifi/net80211/ieee80211_power.c: In function 'ieee80211_pwrsave':
/home/wolfysix/madwifi/net80211/ieee80211_power.c:240: error: implicit declaration of function '__skb_append'
make[3]: *** [/home/wolfysix/madwifi/net80211/ieee80211_power.o] Error 1
make[2]: *** [/home/wolfysix/madwifi/net80211] Error 2
make[1]: *** [_module_/home/wolfysix/madwifi] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-11-generic'
make: *** [modules] Error 2

please help me I dont know anything about the terminal or how to enable the wireless conection.

  *-network DISABLED

PLEASE HELP ME!!!!:(

---

### Post by Open-SuSe-A-Me on 2009-03-24
Are you using 8.04 Hardy, or 8.10 Intrepid?

Install build-essential:

sudo apt-get install build-essential

then try to compile the driver again, using this guide is your using Hardy: [http://ubuntuforums.org/showthread.php?t=792158](http://ubuntuforums.org/showthread.php?t=792158)

---

