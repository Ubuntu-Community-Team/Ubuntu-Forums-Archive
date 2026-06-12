---
title: "Does anyone know if this modem (CX06834-11) will work in Ubuntu?"
date: 2009-03-29
forum: Installation &amp; Upgrades
---

### Post by crjackson on 2009-03-29
```
05:08.0 Communication controller: Conexant Systems, Inc. CX06834-11 HCF V.92 56k Data/Fax/Voice/Spkp Modem (rev 89)

```

I just installed Ubuntu for a friend of mine who is stuck on dial-up. lspci reports the above hardware.

His ASUS A8N-SLI Deluxe doesn't have an RS232 com connector so I'm wondering if it's possible to get this thing working.

Broadband is not an option in the rural area where he lives.

Thanks for any information.

---

### Post by crjackson on 2009-03-31
Bump

---

### Post by sgosnell on 2009-03-31
It should.  He'll need a USB/serial converter, though.  It converts a USB port to a virtual serial port.  The problem is that it requires drivers, and most manufacturers only provide Windows drivers.  Google may provide more information on that.

Broadband is an option, if he's willing to go with satellite.  HughesNet runs ads all the time aimed at exactly these type customers.

---

### Post by crjackson on 2009-04-01
> **sgosnell said:**
> It should.  He'll need a USB/serial converter, though.  It converts a USB port to a virtual serial port.  The problem is that it requires drivers, and most manufacturers only provide Windows drivers.  Google may provide more information on that.

Broadband is an option, if he's willing to go with satellite.  HughesNet runs ads all the time aimed at exactly these type customers.

I'm not sure why a PCI card would need a USB/Serial converter.

It's been googled plenty.

As stated above, broadband is NOT an option.  HughesNet is not able to provide a connection for him. He lives in a heavily wooded area and there is not clear view of the southern sky.

---

### Post by _duncan_ on 2009-04-02
Here are possible avenues for further search:

1. [COLOR="Blue"][http://www.linmodems.org]("http://www.linmodems.org")[/COLOR]. They have a scanModem tool that detects the specific chipset used by the modem. If supported by open-source drivers, the tool will also suggest ways to get the modem working in linux. I am not too optimistic about this option. From what I heard, the erstwhile open-source conexant driver is no longer maintained past couple of years.

2. [COLOR="Blue"][http://www.linuxant.com]("http://www.linuxant.com")[/COLOR]. They offer free but crippled conexant modem drivers. It's a crippled version coz connect speed is limited to 16 kbps (max is 56 kbps theoretical). From what I heard you have to pay US$ 20 to get the full uncrippled version.

3. Dell website. I've seen posts here reporting success using Dell's conexant drivers since the company started selling computers with Ubuntu pre-installed.

BTW, I don't have first-hand experience with conexant modems. Just passing on info based on posts here about dial-up past 2-3 years. So please view my post with the proverbial grain of salt.

---

### Post by Irihapeti on 2009-04-02
I've used a Conexant hsfmodem driver for the past 18 months. _duncan_ is basically right; the free version has a maximum speed of 14.4 kpbs, and to get full functionality you need to either pay $20 US or try the Dell version.

There are also HCF drivers on the Linuxant website. More details are here: [https://www.linuxant.com/drivers/hcf/index.php](https://www.linuxant.com/drivers/hcf/index.php) You could download and install the free version and check that it will work with the modem. If it works, it's then over to you whether to pay for the full version or try the Dell website.

Incidentally, if you use the cnxtinstall.run installer/diagnostic program, I suggest you backup your browser profile first. It managed to corrupt mine when I used it and I had to restore from backup.

Hope that's of some help.

---

### Post by crjackson on 2009-04-02
> **_duncan_ said:**
> Here are possible avenues for further search:

1. [COLOR="Blue"][http://www.linmodems.org]("http://www.linmodems.org")[/COLOR]. They have a scanModem tool that detects the specific chipset used by the modem. If supported by open-source drivers, the tool will also suggest ways to get the modem working in linux. I am not too optimistic about this option. From what I heard, the erstwhile open-source conexant driver is no longer maintained past couple of years.

2. [COLOR="Blue"][http://www.linuxant.com]("http://www.linuxant.com")[/COLOR]. They offer free but crippled conexant modem drivers. It's a crippled version coz connect speed is limited to 16 kbps (max is 56 kbps theoretical). From what I heard you have to pay US$ 20 to get the full uncrippled version.

3. Dell website. I've seen posts here reporting success using Dell's conexant drivers since the company started selling computers with Ubuntu pre-installed.

BTW, I don't have first-hand experience with conexant modems. Just passing on info based on posts here about dial-up past 2-3 years. So please view my post with the proverbial grain of salt.

Thanks for the info. I tried the Dell driver and it did nothing as far as I could tell. GnomePPP couldn't detect the moved. It does show using lspci in a terminal though (with or without the driver).

I'll try the crippled driver out of curiosity, but I won't buy it. I have an external USR Sportster I'll give him before paying that.

---

### Post by crjackson on 2009-04-02
> **Irihapeti said:**
> I've used a Conexant hsfmodem driver for the past 18 months. _duncan_ is basically right; the free version has a maximum speed of 14.4 kpbs, and to get full functionality you need to either pay $20 US or try the Dell version.

There are also HCF drivers on the Linuxant website. More details are here: [https://www.linuxant.com/drivers/hcf/index.php](https://www.linuxant.com/drivers/hcf/index.php) You could download and install the free version and check that it will work with the modem. If it works, it's then over to you whether to pay for the full version or try the Dell website.

Incidentally, if you use the cnxtinstall.run installer/diagnostic program, I suggest you backup your browser profile first. It managed to corrupt mine when I used it and I had to restore from backup.

Hope that's of some help.

Thanks for the heads-up

---

### Post by _duncan_ on 2009-04-02
> I'll try the crippled driver out of curiosity, but I won't buy it. I have an external USR Sportster I'll give him before paying that.

Good call. Serial external USR modems are the easiest to work with. It will probably show up as /dev/ttyS0 in gnome-ppp. No drivers required.

---

