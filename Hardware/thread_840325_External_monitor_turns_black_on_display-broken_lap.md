---
title: "External monitor turns black on display-broken laptop"
date: 2008-06-25
forum: Hardware
---

### Post by RadenMu'az on 2008-06-25
I have an old Compaq Presario 900 with battered keyboard and broken display (read: rendered useless and have no chance to repair). 
Before Hardy I use Samsung LCD external monitor and other peripherals to use the laptop, like kind of mini desktop computer.

The problem is, after installed Xubuntu Hardy (alternate cd), the external monitor turns blank (no signal) after GDM loads. This is probably something to do with Xorg. I have no such issues before when running Feisty. Loading screen and ttys however shown correctly on the external screen. :(

> lspci:
00:00.0 Host bridge: ATI Technologies Inc AGP Bridge [IGP 320M] (rev 13)
00:01.0 PCI bridge: ATI Technologies Inc PCI Bridge [IGP 320M] (rev 01)
00:02.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:07.0 ISA bridge: ALi Corporation M1533/M1535 PCI to ISA Bridge [Aladdin IV/V/V+]
00:08.0 Multimedia audio controller: ALi Corporation M5451 PCI AC-Link Controller Audio Device (rev 02)
00:0a.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 02)
00:0b.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 20)
00:0c.0 Communication controller: Conexant HSF 56k HSFi Modem (rev 01)
00:0f.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:10.0 IDE interface: ALi Corporation M5229 IDE (rev c4)
00:11.0 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility U1
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)


Some other people have the problem just like me when using Hardy and said it's just fine when in Gutsy. :mad:
[http://ubuntuforums.org/showthread.php?t=767298&highlight=laptop+broken+display]("http://ubuntuforums.org/showthread.php?t=767298&highlight=laptop+broken+display")
[http://ubuntuforums.org/showthread.php?t=834175&highlight=laptop+external+screen+blank]("http://ubuntuforums.org/showthread.php?t=834175&highlight=laptop+external+screen+blank")
[http://ubuntuforums.org/showthread.php?t=822125&highlight=laptop+broken+display]("http://ubuntuforums.org/showthread.php?t=822125&highlight=laptop+broken+display")

Now Xubuntu is only usable as a CLI system. No usable X.

Thanks for helping.

---

### Post by ukripper on 2008-06-25
Boot into live cd and post your xorg here and do lspci from there.

```
gedit /etc/X11/xorg.conf
```

---

### Post by RadenMu'az on 2008-06-26
> **ukripper said:**
> Boot into live cd and post your xorg here and do lspci from there.

```
gedit /etc/X11/xorg.conf
```

Okay.
I can't see X at all I have to post lspci manually with recovery mode. :(
The external monitor is the only hope to see what Xubuntu is using.

---

### Post by RadenMu'az on 2008-06-27
Anyone?

---

### Post by ukripper on 2008-06-27
> **RadenMu'az said:**
> Anyone?

try this on command line:

> sudo dpkg-reconfigure xserver-xorg

---

### Post by RadenMu'az on 2008-06-27
Still the same,
Does anyone know how to use xrandr to fix this?

---

### Post by ukripper on 2008-06-29
> **RadenMu'az said:**
> Still the same,
Does anyone know how to use xrandr to fix this?
Use method 2 from here- [http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

---

