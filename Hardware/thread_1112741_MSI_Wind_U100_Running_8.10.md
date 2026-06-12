---
title: "MSI Wind U100 Running 8.10"
date: 2009-04-01
forum: Hardware
---

### Post by pittmantechno on 2009-04-01
Hello Beautiful Ubuntu Community,

   I just bought a MSI Wind U100 - The fist thing I did was Clean install Ubutnu 8.10 
and I Have no Network connectivity  - WIFI or LAN -LAN shows up but no connection and WIFI is totally blank - can anyone help ? I have a no Windows Policy in my house - I bought this bad boy just for Ubuntu =)

---

### Post by Teamgeist on 2009-04-01
Ubuntu 8.10 does not contain the RTL8187SE driver.
Ubuntu 9.04 will though.
You can load a Beta-Version of 9.04 here:
[http://releases.ubuntu.com/releases/9.04/](http://releases.ubuntu.com/releases/9.04/)
And the Netbook-Remix-Version here:
[http://cdimage.ubuntu.com/releases/9.04/beta/](http://cdimage.ubuntu.com/releases/9.04/beta/)

---

### Post by texasred218 on 2009-04-02
ubuntu  beta 9.04 has all the wifi  drivers that work on my msi u90    the kernal has the new drivers

---

### Post by OlympicSoftworks on 2009-04-04
I bought a U100 and everything with the single exception of wireless work perfectly.  The wired lan worked after a fresh install, but then after the 284 package initial update was done and the unit rebooted it failed.  I powered down completely so any firmware could be reloaded and after the first boot up it is back in action.

There seem to be 3 different WiFi cards used.  An Atheros, one from RealTech, and one from RALink.  Mine uses the RALink one, Model# 2700E.  I have not found a kernel module for this yet, but just started looking for it like an hour ago.  I will post here once I find a reliable solution.

---

