---
title: "Amilo M7440G - wireless button problem"
date: 2007-01-18
forum: Hardware &amp; Laptops
---

### Post by Qtea on 2007-01-18
After long hard night of searching the Internet and the Forum, I still have not found any solutions for getting up the wireless network on my FuijitsuSiemens laptop Amilo M7440g. There is a wireless button that is supposed to activate the network card and works perfectly in W XP.

I suppose I have the ipw2200 module loaded:
```
qtea@graal:~$ dmesg | grep ipw
[17179597.624000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.1.1[17179597.624000] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[17179597.624000] Warning: PCI driver ipw2200 has a struct device_driver shutdown method, please update!
[17179597.624000] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection[17179598.032000] ipw2200: Radio Frequency Kill Switch is On:
[17179598.032000] ipw2200: Detected geography ZZR (14 802.11bg channels, 0 802.11a channels)
```

I guess I also have the network card detected:
```
qtea@graal:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      radio off  ESSID:off/any
          Mode:Managed  Channel:0  Access Point: Not-Associated
          Bit Rate=0 kb/s   Tx-Power=off   Sensitivity=8/0
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.
```

However, I don't get any scanning results although an another Ubuntu laptop (a Macbook, not FS) detects several networks right on the side.
```
qtea@graal:~$ iwlist eth1 scan
eth1      No scan results

```

I'd just be so happy to get this wireless up and runnig.

---

### Post by automatthias on 2007-02-11
Try this:

sudo modprobe acerhk
sudo su -c "echo 1 > /proc/driver/acerhk/wirelessled"

It it works, you can make it permanent by creating a file /etc/modprobe.d/ipw2200 with the two following lines:

options ipw2200 led=1
install ipw2200 /sbin/modprobe acerhk; sleep 1; echo 1 > /proc/driver/acerhk/wirelessled; /sbin/modprobe --ignore-install ipw2200

---

### Post by flixer on 2007-03-24
Try this:

1.[Download this file]("http://downloads.sourceforge.net/fsam7440/fsam7440-0.4.tar.bz2?modtime=1177886562&big_mirror=0") unpack it to your home directory /home/username


2. ```

cd fsam7440-0.4 && make && sudo make install

```

3.Read README

Important: You have to do this everytime your kernel changes.

---

