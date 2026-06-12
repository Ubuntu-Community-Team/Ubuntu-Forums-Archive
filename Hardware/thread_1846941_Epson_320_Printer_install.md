---
title: "Epson 320 Printer install"
date: 2011-09-19
forum: Hardware
---

### Post by spec36 on 2011-09-19
I have just bought a Epson workforce 320 (C364A) printer and I am trying to get it working in ubuntu, but have no idea what I need to do. Do I need to install a driver, Where do I get this driver, etc...?

Any help would be greatly appreciated.

Thanks

---

### Post by bikewrecker on 2011-09-21
What ubuntu are you using? Im using 11.10 beta and i have a epson cx7400 printer. I just plugged it in for the first time, went to some c code i was working on in gedit and clicked print and it started working... I've never had a printer install done that quick in any OS... ever! 
Hopefully this helps!

---

### Post by wolfen69 on 2011-09-21
A printer will either work out of the box in linux, or it won't. I checked epson's website for drivers, and there are none for linux. That's why I only use HP printers, as they are plug and play in linux.

---

### Post by spec36 on 2011-09-26
yeah I have never had a problem installing a printer either. Usually just plug and play, but turns out this one is even not able to be selected from the add printer menu. Does anyone know how I can go about finding and installing the driver from Epson Workforce 320 printer?

ANy help would be great.

Thanks

---

### Post by spec36 on 2011-09-26
I solved this by downloading the amd64 driver for Epson workforce 320 from here

```
[/http://avasys.jp/eng/linux_driver
```

I then ran dpkg -I [driverpackagename]

Then connected to cups web link

Selected find new printer and then followed through the on screen steps until completion.

Printer now works.

Thanks for everyone who responded.

---

