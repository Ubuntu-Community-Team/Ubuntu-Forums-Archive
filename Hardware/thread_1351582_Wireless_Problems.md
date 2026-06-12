---
title: "Wireless Problems"
date: 2009-12-10
forum: Hardware
---

### Post by KommaH on 2009-12-10
Hi, all, I'm a new Ubuntu user, and, I know this has been asked quite a few times, but I appear to have a particularly special case...

A week ago, I had the sudden urge to try out Ubuntu again, so, I re-installed it. It's worked great so far except for one thing -- the wireless doesn't work anymore! :(

I have a BCM4315 wireless card in an Acer Extensa 4420. I've searched and searched and searched, tried solution after solution after solution, and cannot fix it. I dunno whether it's just not (easily) fixable, or if I'm simply trying to fix it the wrong way.

I've already looked [here]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx") and have tried bcm43xx as well as ndiswrapper with both a bcmwl6 and bcmwl5. Neither worked (gui diswrapper said that the hardware wasn't found).

I've also tried the [broadcom linux drivers]("http://www.broadcom.com/support/802.11/linux_sta.php"). This got my computer to detect the wireless (ifconfig) for one session, but it couldn't connect. I then restarted, reactivated it, and it ceased to work.

Any suggestions?

---

### Post by HappyFeet on 2009-12-10
Did you try the drivers from system>administration>hardware drivers?

---

### Post by KommaH on 2009-12-10
I can't, because I don't have internet on the laptop. Thank you for the response, though.

Ok, update:
I tried ndiswrapper again. Turns out I was using the wrong .inf file. ndiswrapper now says the hardware is present, however, I still cannot connect to the internet.

Whenever I ifconfig, I cannot see the wireless device.

Also, whenever I enter [FONT=courier new]ndiswrapper -l[/FONT] in the terminal, I get this:
```

bcmwl6 : driver installed
    device (14E4:4315) present (alternate driver: ssb)

```

---

### Post by Greenwidth on 2009-12-10
> **KommaH said:**
> I can't, because I don't have internet on the laptop.

Did you try adding the CD as a software source?

---

### Post by KommaH on 2009-12-10
I installed from a USB. Is there a way I can add that as a software source?

EDIT: I tried putting it in [font="courier new"]/etc/apt/sources.list[/font], but that didn't seem to help.

---

### Post by Greenwidth on 2009-12-10
I don't know how to add USB as source, but it should work if you can.

---

### Post by KommaH on 2009-12-11
I burned a CD and re-installed ubuntu. I went to the hardware drivers area and enabled the broadcom linux drivers and Ubuntu has started detecting my wireless device as [FONT=courier new]eth2[/FONT]. However, I still cannot connect.

[FONT=courier new]iwconfig[/FONT]
```

lo        no wireless extensions

eth0    no wireless extensions

irda0   no wireless extensions

eth2    IEEE 802.11  Nickname:""
          Access Point: Not-Associated

```

---

### Post by Greenwidth on 2009-12-12
Can you 'see' any wireless networks?
Is your SSID set to hidden on your router?

---

### Post by KommaH on 2009-12-12
I cannot see any networks (there should be some in range, although barely). My router's SSID is set to not broadcast. I've already made a profile for it (with WEP key) in the network connections area.

---

### Post by KommaH on 2009-12-12
I dunno why, but it all of the sudden decided to work. Thanks for your help!

---

### Post by Greenwidth on 2009-12-12
Good!
WEP is pretty rubbish though, have you got any other options?

---

### Post by hdoeallil on 2009-12-12
[CENTER][FONT=Tahoma][SIZE=2]Thank you very much[/SIZE][/FONT][/CENTER]

---

### Post by stephen_b on 2010-04-18
I have same issue, but it does not work after estart. eth2 is the logical name and driver is supposedly active. pls help with SSID. I have wireless router from Bell and Vista connects to it without a problem

---

