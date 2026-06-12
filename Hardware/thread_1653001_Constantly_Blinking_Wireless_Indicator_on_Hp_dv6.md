---
title: "Constantly Blinking Wireless Indicator on Hp dv6"
date: 2010-12-26
forum: Hardware
---

### Post by Stratosmacker on 2010-12-26
I have a new hp dv6 multimedia laptop that i put ubuntu on today. Aside from multitouch touchpad problems everything worked fairly well, but the wireless when connected would blink continuously. When not connected it would stay white and when disabled orange. Any thoughts?

---

### Post by gobbledigook on 2010-12-26
it is blinking to show you are connected and that it is working?  different colours to represent different hardware states... what is your question? if you find it annoying and want to change, then it should be clear ;) i have a similar issue with my compaq 110 mini, mine doesn't flash but that and the power light are like torches!!! if i find out how to adjust i'll post you a link :)

---

### Post by gobbledigook on 2010-12-26
there is a thread [here]("http://ubuntuforums.org/showthread.php?t=966511") on the blinking LED issue... it has been going a couple of years so start near the end :)

found easily using the forums search function ;)

---

### Post by Stratosmacker on 2010-12-26
> **gobbledigook said:**
> there is a thread [here]("http://ubuntuforums.org/showthread.php?t=966511") on the blinking LED issue... it has been going a couple of years so start near the end :)

found easily using the forums search function ;)

Thanks, but I was looking at that thread earlier to no avail. The output of ls /sys/class/leds only gives me HP::hddprotect which is not the led for the wireless. IF it makes any difference the LED is in the keyboard.

---

### Post by Stratosmacker on 2010-12-26
After lots of googleing I found this [http://ubuntuguide.net/stop-the-blinking-wireless-led-light-on-ubuntu-10-10-laptops](http://ubuntuguide.net/stop-the-blinking-wireless-led-light-on-ubuntu-10-10-laptops)

Problem solved!

---

### Post by tanpopo_chan on 2011-01-11
Since this is the thread that always comes up when searching about the dv6, I'll post what worked for me here. By the way, I have an HP Pavillion dv6-2145es and I'm running Maverick (Ubuntu 10.10).

First, I looked up all of the possible solutions for the drivers available... Most are posted at [http://ubuntuforums.org/showthread.php?t=966511](http://ubuntuforums.org/showthread.php?t=966511) (thanks gobbledigook for the link and thank you to OMFGitsme and mobusby for the code!)

Then, I checked which driver I had by doing the following:

Open a terminal and put in:
```
sudo lshw -C Network
```

And this was my output:
```
*-network               
       description: **_Wireless interface_**
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: wlan0
       version: 01
       serial: c4:17:fe:74:70:5c
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes **_driver=ath9k_** driverversion=2.6.35-24-generic firmware=N/A ip=192.168.0.14 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:f1200000-f120ffff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 03
       serial: c8:0a:a9:0e:22:af
       size: 10MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:45 ioport:2000(size=256) memory:f1004000-f1004fff memory:f1000000-f1003fff memory:f1010000-f101ffff
```
Notice how in the section "configuration" of my "Wireless interface" it says *driver=ath9k*? Welp! That's the solution to the problem! All you have to do is check which driver you've got and search the forum!

If you have the iwlagn driver, all you have to do is follow the solution given by Stratosmacker, and if you have the ath5k driver, follow the instructions posted at [http://ubuntuforums.org/showpost.php?p=9835897&postcount=7](http://ubuntuforums.org/showpost.php?p=9835897&postcount=7).
If you have the ath9k driver like me, here's what you do.

First, let's create a file where the code will execute. You can name it however you like, but just make sure you create it in the directory "/etc/network/if-up.d/". I named mine ath9k-no-blink.
So, let's go back to the terminal and type:
```
sudo gedit /etc/network/if-up.d/ath9k-no-blink
```


When gedit opens, paste the following, then save and close. This is us telling the led how to act. In other words, we're saying, "when the wifi's off, turn red, and when it's on, turn blue."
```
#!/bin/sh

if [ "$IFACE" = "wlan0" ]; then
    for direc in /sys/class/leds/ath9k-phy0::rx
    do
        echo none > $direc/trigger
        # never trigger blinking for RX
    done
    
    for direc in /sys/class/leds/ath9k-phy0::radio
    do
        echo none > $direc/trigger
        # never trigger blinking for radio
    done

    for direc in /sys/class/leds/ath9k-phy0::assoc
    do
        echo phy0assoc > $direc/trigger
        # do trigger blinking during association
    done
    
    for direc in /sys/class/leds/ath9k-phy0::tx
    do
        echo phy0assoc > $direc/trigger
        # never trigger blinking for TX
    done
fi
```


Now, after closing gedit, put in the following two lines in the terminal. Here we're making sure that only root can manipulate this file and giving it permission to execute.:
```
sudo chown root /etc/network/if-up.d/ath9k-no-blink
sudo chmod a+x /etc/network/if-up.d/ath9k-no-blink
```

Now, restart the computer and voilá! Problem fixed!


So just to wrap it up, if you have the ath9k driver, follow the instructions above.

For the ath5k driver, check this post: [http://ubuntuforums.org/showpost.php?p=9835897&postcount=7](http://ubuntuforums.org/showpost.php?p=9835897&postcount=7) 

If you have the iwlagn driver, follow the solution from [http://ubuntuguide.net/stop-the-blinking-wireless-led-light-on-ubuntu-10-10-laptops](http://ubuntuguide.net/stop-the-blinking-wireless-led-light-on-ubuntu-10-10-laptops).

---

### Post by gosmoon on 2011-01-20
The simple solution that worked for me: [http://ubuntuguide.net/stop-the-blinking-wireless-led-light-on-ubuntu-10-10-laptops]("http://ubuntuguide.net/stop-the-blinking-wireless-led-light-on-ubuntu-10-10-laptops")

HP Pavillion dv5184ea with driver=iwl3945.

---

### Post by billdougan on 2011-02-26
This worked for me, thanks!

> **Stratosmacker said:**
> After lots of googleing I found this [http://ubuntuguide.net/stop-the-blinking-wireless-led-light-on-ubuntu-10-10-laptops](http://ubuntuguide.net/stop-the-blinking-wireless-led-light-on-ubuntu-10-10-laptops)

Problem solved!

---

