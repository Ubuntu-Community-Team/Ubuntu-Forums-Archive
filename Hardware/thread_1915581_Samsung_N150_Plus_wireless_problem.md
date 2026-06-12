---
title: "Samsung N150 Plus wireless problem"
date: 2012-01-26
forum: Hardware
---

### Post by ruby444 on 2012-01-26
Hello,

I have a problem with wireless connection on my N150 Plus. WiFi seems to randomly cut off, while the icon suggests that I'm connected. I'm using Ubuntu 11.10 32-bit, with the STA driver installed from Additional Drivers app (though the driver in use is brcmsmac, as stated in the Connection Information window).

Most networks I experience the problem with are hidden (SSID broadcast off) and protected with WPA2/PSK. The problem occurs irregularly, both on G and N networks. It usually goes away for some time after reconnecting, but sometimes returns almost at once.

Also, I think it's worth noting that I'm using Voria's "Linux on my Samsung" PPA for kernel updates (so that backlight control works properly).

Please help.

---

### Post by madvinegar on 2012-01-26
Could you please post the outcome of

```
lspci
```

---

### Post by ruby444 on 2012-01-29
```
$ lspci
00:00.0 Host bridge: Intel Corporation N10 Family DMI Bridge
00:02.0 VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller
00:02.1 Display controller: Intel Corporation N10 Family Integrated Graphics Controller
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation N10/ICH7 Family SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
05:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)
09:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller
```

Here you go.

---

### Post by coffeecat on 2012-01-29
@ruby444, I have the same BCM4313 wireless chipset in my HP netbook. I was interested in this comment:

> **ruby444 said:**
> I'm using Ubuntu 11.10 32-bit, with the STA driver installed from Additional Drivers app (though the driver in use is brcmsmac, as stated in the Connection Information window).

Although you've installed the STA driver, the brcmsmac one is still the one in use. That's intriguing. When 11.10 was still in development I tried running it from a live USB with persistence, and tried to install the STA driver, but this failed. After some fruitless investigation I gave up because the brcmsmac drive worked just fine for me. When 11.10 was released I upgraded my permanent Natty/11.04 installation and continued to use the brmcmsmac driver. I haven't tried the STA driver since.

My experience is that I get a consistently stable connection with the brcmsmac driver - with the proviso I describe below - and I'm sorry to hear that this is not the case for you.

Two things. If I get time later, I'll try installing the STA driver to see what happens. It may be that there is still a bug and that it is not installing properly.

The second thing is that the brcmsmac driver *should* work for you but doesn't. One thing to investigate is whether your problem is down to interference from other wireless networks. I had to change the channel on my wireless router so that it was a different one from my near-neighbours. So - do you get a stable connection with another machine or with another operating-system? Also - try installing the app wifi-radar. This will tell you which channel other networks are using so that you can see if they are the same as yours.

---

### Post by coffeecat on 2012-01-29
@ruby444, I've done a bit of investigating and I've found that the  problem with the bcmwl-kernel-source package (which installs the STA driver = wl module) is that it is not blacklisting the correct modules. It blacklists the "brcm80211" driver (which is what the brcmsmac driver was called in Natty/11.04) in /etc/modprobe.d/. You need to blacklist brcmsmac as well as bcma for the STA driver to work.

But before you try that, I suggest you investigate whether there may be a problem with interference from other networks as I mention before. Although, since you've experienced this with more than one network, this may not be the issue.

If you want to try getting the STA driver to function and need help with the blacklisting, post back.

---

### Post by ruby444 on 2012-01-30
Here's a strange thing: I removed the STA driver before to try out something, and when installing it, Jockey said the package didn't have a trusted origin. So I installed with apt-get, and it compiled perfectly. It was the bcmwl-kernel-source package.

Then, I blacklisted the brcmsmac driver... but it seems it disabled wireless completely, ie. there's no option to turn it on in the networking menu.

No, there's no interference - our network is on channel 11, whereas most other networks are on channels 8 and lower.

In yet another twist, after adding bcma to blacklist, wireless returned! Now I'm going to check if everything works well.

---

### Post by coffeecat on 2012-01-30
> **ruby444 said:**
> 
Then, I blacklisted the brcmsmac driver... but it seems it disabled wireless completely, ie. there's no option to turn it on in the networking menu.

No, there's no interference - our network is on channel 11, whereas most other networks are on channels 8 and lower.

In yet another twist, after adding bcma to blacklist, wireless returned! Now I'm going to check if everything works well.

Yes, that's it! :) It seems that both brcmsmac and bcma need to be blacklisted for the STA driver to work. I'd count that as a bug in the Oneiric bcmwl-kernel-source package, because it's doing what needed to be done (and which works) in Natty. I haven't had time to see if this has been reported to Launchpad yet. My guess is that it only affects the users of the small number (4, I think) of Broadcom devices that are supported by the brcmsmac driver.

Let us know if you get better performance with the STA driver (bcmwl-kernel-source).

---

### Post by ruby444 on 2012-01-30
Thank you, it works fine now:KS

---

