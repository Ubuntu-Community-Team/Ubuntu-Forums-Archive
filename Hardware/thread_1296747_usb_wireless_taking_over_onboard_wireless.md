---
title: "usb wireless taking over onboard wireless"
date: 2009-10-21
forum: Hardware
---

### Post by tegryan on 2009-10-21
Hi,

When I plug in a USB wireless it dominates over my built in wireless connection, disconnecting me and so on.  I'm testing a virtualbox set up using the USB wireless device so this is very annoying.  Is there a simple way to bind the first (eth1) connection to my wireless router so that even if the second one connects and disconnects I don't lose my primary connection?

Thanks,

Teg

---

### Post by dvlchd3 on 2009-10-21
It sounds like your wireless keyboard is using the same radio frequency as your wifi.  Try changing the channel your wireless operates on to something else. (Like channel 1).

By default, most wireless routers operate on channel 6, which is 2.5 GHz.  A lot of different wireless electronics operate on 2.5 GHz (some wireless phones, for example).  Changing the default channel also helps decrease the interference with any of your neighbors wireless networks.

---

### Post by tegryan on 2009-10-21
Sorry, I didn't explain that very well.  Both are wireless NIC's, one is an onboard NIC and one is a usb one.  I want to make the onboard the first NIC that binds so the second can come and go without disrupting the connection.

Thanks,

Teg

---

### Post by tegryan on 2009-10-22
I fixed the problem by installing [WICD]("http://wicd.sourceforge.net/").  Network manager was forcing the reconnect every time I plugged the USB NIC in, even though I'd do turn the interface off.  Now I can use wlan0 in monitor mode and my built in wireless card to stay connected to my router.  Very cool!  As an aside, I didn't even need to configure wicd, it just worked as soon as I installed it, and it removed network manager automatically.

---

