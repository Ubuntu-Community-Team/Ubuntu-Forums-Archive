---
title: "WiFi Issuses. I would like to completely reset network settings."
date: 2006-03-27
forum: Hardware &amp; Laptops
---

### Post by I922sParkCir on 2006-03-27
WiFi Issues. I would like to completely reset network settings.

I am running Dapper, on an Dell 700m, with the Intel 2200 card, and the ipw2200 drivers.

My wifi is no longer working. It used to automatically connect to the strongest non-encrypted signal, now it continuously tries to connect to a signal that isn't present, leaving my wifi useless. I have rebooted my machine, reset the card, and manually tried to connect to the network.

I would just like to completely reset my network settings, and have things the way they were when I first installed ubuntu.

If you need any information just ask, thank you.

-Jai

---

### Post by FryerFox on 2006-03-27
What do you get when you type (on the command line):

```
iwconfig
```

---

### Post by FryerFox on 2006-03-27
Incidentally, while you may already know this, you can bring up the network administration panel by typing:

```
network-admin
```

Click on your wireless connection and click on properties to select the network.

You may have already tried this, but just trying to start at the beginning :)

---

### Post by I922sParkCir on 2006-03-27
I got it working but I must deactivate the connectiton using the network-admin, than dissable the card using my laptop hotkeys, enable it using the same hotkeys, activate the conection, and then select the connection manually to my network.  I must do this every time I come out of suspend. The laptop wants connect to a network that is present.

This is a 3 min process.

It used to work pefectly, how can I just reset all the settings.

Here is my iwconfig:

eth0      IEEE 802.11g  ESSID:"Jai's Free WiFi"
          Mode:Managed  Frequency:2.442 GHz  Access Point: 00:13:10:D0:60:E2
          Bit Rate=36 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=86/100  Signal level=-40 dBm  Noise level=-89 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:20   Missed beacon:1

Thanks FryerFox, any more help would be greatly appreciated.

-Jai

---

### Post by FryerFox on 2006-03-28
Acutally, when I initially responded, I hadn't realized that you were running Dapper. Do you think it might be an issue that has been brought up on the dapper boards?

For example: [http://ubuntuforums.org/showthread.php?p=870903#post870903](http://ubuntuforums.org/showthread.php?p=870903#post870903) or [http://ubuntuforums.org/showthread.php?t=151889](http://ubuntuforums.org/showthread.php?t=151889)

I'm not yet running it myself, so I'm not familiar with the ins and outs yet.

---

