---
title: "Trying to get an Atheros 5006 EG wireless card to work / no &quot;ath0&quot;"
date: 2008-01-26
forum: Hardware &amp; Laptops
---

### Post by EckoAK on 2008-01-26
I'm pretty good with computers, but my experience is limited to Windows OS. I have this ASUS laptop that has an Atheros 5006 EG wireless card in it that isn't supported "out of the box" by Ubuntu. I've tried to get Ndiswrapper (v. 1.51) and Madwifi (v. 0.9.3.3) to run, but I'm not sure if they are installing properly. I'm not even sure how to run programs if they aren't in one of the menus at the top of the screen.

Ok hold up, I managed to get Ndiswrapper to run in terminal, and installed the driver. However, my card still doesn't show up. iwconfig shows
```
lo         no wireless extensions.
eth0    no wireless extensions.
```

Everywhere I've read online people are messing with the "ath0" configuration. I guess thats where all the Atheros 5006 EG card stuff is supposed to show up.

Anyone have any ideas for a Linux newbie? I'd really like to get into this OS and develop programs (I'm taking programming classes in my free time, C++ at the moment), but it's kinda hard to do without internet

---

### Post by EckoAK on 2008-01-26
ok I found some other people who who have the same problem here
[http://ubuntuforums.org/showthread.php?t=667525&highlight=ath0]("http://ubuntuforums.org/showthread.php?t=667525&highlight=ath0")
however the issue didn't get resolved for a user named Gusanto, who is experiencing the exact same difficulties as I am.

Neither of our cards are being powered, apparently. I'm confident that I have the driver issue solved, however it does me no good if the card itself is for some reason not being turned on.

this is the result of running in root: lshw -C network

```
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth0
       version: 01
       serial: 00:1d:60:9e:ae:03
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=half latency=0 link=no module=r8169 multicast=yes port=twisted pair
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR5006EG 802.11 b/g Wireless PCI Express Adapter
       vendor: Atheros Communications, Inc.
       physical id: 0
       bus info: pci@0000:07:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list
       configuration: latency=0


```

---

### Post by AndyC_772 on 2008-01-27
What's your PC?

My wife's laptop is an Acer with an Atheros card, actually an AR5007EG even though it reports itself in Ubuntu as a 5006. This means the current version of madwifi won't support it, you'll need to use ndiswrapper instead.

In her case I also had to install acer_acpi to ensure the card is physically switched on.

---

### Post by kegobeer on 2008-01-27
I've never had any luck with ndiswrapper.  Instead, I installed the experimental madwifi drivers and got my 5008 chipset working.  It might work for you, give it a try.

[http://www.thinkwiki.org/wiki/How_to_checkout_and_install_madwifi_experimental_driver_for_ar5008](http://www.thinkwiki.org/wiki/How_to_checkout_and_install_madwifi_experimental_driver_for_ar5008)

---

### Post by i_TheDevil_i on 2008-01-27
ndiswrapper will work perfectly if u read carefully this [HOWTO]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper")

---

### Post by EckoAK on 2008-01-27
if you read carefully ndiswrapper wasn't the problem

hehe sorry. well i couldn't afford to waste any more time on this, so i gave up and reinstalled vista :( thanks for the attempts fellas

---

### Post by aprilian bandit on 2008-01-31
This link is worth a try - I used it on Fedora, but I don't see why it wouldn't be the same on ubuntu...

[http://home.nyc.rr.com/computertaijutsu/rhwireless.html](http://home.nyc.rr.com/computertaijutsu/rhwireless.html)

Section is near the bottom, on the AR5007EG (which it seems is really the one that is out there, not the AR5006EG)

---

### Post by AndyC_772 on 2008-01-31
Thanks for the link, I may give it a go.

Do you know if the patched madwifi driver can automatically connect to a network with a hidden SSID at start-up? That's the only problem we have with using ndiswrapper - my SSID is hidden and neither my wife's Acer / Atheros PC, nor my new Asus / Intel 9645AGN will connect (using Wicd) at start-up without entering the SSID first. My old Dell (Broadcom-based card) worked fine.

---

