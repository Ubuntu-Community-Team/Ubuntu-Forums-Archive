---
title: "HP dv3, Jaunty, wireless takes a long time to connect"
date: 2009-08-16
forum: Hardware
---

### Post by inverseroom on 2009-08-16
I've been running jaunty for a couple of months on a new HP dv3 laptop, and it works great.  One problem though--when i was running Hardy on my old HP dv1000, wireless internet would connect almost immediately upon startup.  With the new machine and new OS, connection speed and signal strength are fine, but I wait quite a long time to connect--more than a minute.  Here's my iwconfig:

```
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11abgn  ESSID:"Love Connection"  Nickname:""
          Mode:Managed  Frequency:5.62 GHz  Access Point: 00:1A:70:40:C5:B8   
          Bit Rate=5.5 Mb/s   Tx-Power:32 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Managementmode:All packets received
          Link Quality=2/5  Signal level=-77 dBm  Noise level=-92 dBm
          Rx invalid nwid:0  Rx invalid crypt:1  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

I'm using a Linksys WRT300N that is running DD-WRT, with a somewhat boosted output level.  Overall, wireless connectivity is not quite as good with this new computer and Jaunty, compared to my 4-year-old dv1000 and hardy!  In every other way, Jaunty seems superior.  Any ideas?

---

### Post by sergiom99 on 2009-08-16
I would start by trying Wicd instead of Network Manager. Works way much better.
```
sudo apt-get install wicd
```

good luck!

---

### Post by inverseroom on 2009-08-17
Great, trying that now!

EDIT: Wow, wicd immediately wiped network managed off the face of the earth.  WTF?  I'm now connected again using it, but it seemed to take just as long as before, and the connection indicator has vanished from my tray.  Is there a tray icon to display wireless connectivity using wicd?

---

### Post by inverseroom on 2009-08-17
OK, tray icon appeared on restart.  Connection might have been slightly faster, but nothing like it was under Hardy on my old machine.

I vastly prefer the Network Manager tray icon, but wicd seems to be working well.

I've got the Broadcom BCM4322 controller in this computer, and am using the STA driver.

---

### Post by inverseroom on 2009-08-22
Just giving this a bump...does anyone have any ideas/insights here?  Is this common to all laptops with Jaunty, or just mine?

---

