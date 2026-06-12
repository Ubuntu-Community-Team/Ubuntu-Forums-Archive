---
title: "HP pavilion dv6 speakers crackling and Broadcom BCM 4312"
date: 2010-06-19
forum: Hardware
---

### Post by fireflyltd on 2010-06-19
Hi, 

I just installed Ubuntu 10.04 LTS onto my HP Pavilion dv6 (2.0 GHz Core 2 duo, 3 gb ddr2).

The sound works fine through the speakers, but everytime I hit restart, and when the screen goes blank before robooting, the speakers give out a crackling noise. Is this repairable?

Secondly, I was going through wifi card support forums and found that the Broadcomm BCM 4312 have propritry linux drivers ([http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)).

It was a tar.gz file. I followed the instructions to install them

```
tar -zxvf nameof.tar.gz
./configure
make
make install


```

However, at the configure command i get an message saying

```
No such file or directory
```

Im a complete beginner to linux, and im a bit stumped :(

---

### Post by ShadowMage on 2010-07-23
Hi fireflyltd,

I also have an HP Pavilion DV6, but my WiFi card is not a Broadcom.

However, regarding the audio issue, I also experience a crackling noise when I reboot. I found a bug report related to this [COLOR=Blue][here]("https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/578566")[/COLOR]. In the meantime, I've been looking for a workaround, but unfortunately I haven't been able to find one as of yet.

---

### Post by lidex on 2010-07-25
For wireless:
[http://linux.aldeby.org/howto-ubuntu-linux-on-hp-pavilion-dv2000-dv6000-dv9000-series-laptops.html/4#wireless](http://linux.aldeby.org/howto-ubuntu-linux-on-hp-pavilion-dv2000-dv6000-dv9000-series-laptops.html/4#wireless)

---

