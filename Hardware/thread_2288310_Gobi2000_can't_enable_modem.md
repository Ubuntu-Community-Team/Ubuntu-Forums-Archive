---
title: "Gobi2000 can't enable modem"
date: 2015-07-26
forum: Hardware
---

### Post by Bartomiej_Zieli on 2015-07-26
I've a hp 2510p laptop with modded bios, gobi2000 gsm modem. I've managed to install gobi loader, but I can't enable modem, I got this error: GDBus.Error:org.freedesktop.libqmi.Error.Protocol.HardwareRestricted: Couldn't set operating mode: QMI protocol error (83): 'HardwareRestricted'


please help

---

### Post by dino99 on 2015-07-26
This howto might help, even if it is a bit old

[http://securit.se/2012/03/guide-sa-har-far-du-gobi-2000-wireless-modem-att-fungera-ubuntu-12-04/](http://securit.se/2012/03/guide-sa-har-far-du-gobi-2000-wireless-modem-att-fungera-ubuntu-12-04/)

---

### Post by Bartomiej_Zieli on 2015-07-26
I do exactly as it's written, I can see this modem in modem manager, but I can't enable it, just got the message [COLOR=#000000]error: GDBus.Error[/COLOR]:eek:[COLOR=#000000]rg.freedesktop.libqmi.Error.Protocol.HardwareRestr icted: Couldn't set operating mode: QMI protocol error (83): 'HardwareRestricted'[/COLOR]

---

### Post by Stefan.loginubunt on 2015-08-09
I am having the same problem here:
```
Aug  9 22:14:17 X220 ModemManager[1144]: <info>  Simple connect started...
Aug  9 22:14:17 X220 ModemManager[1144]: <info>  Simple connect state (4/8): Wait to get fully enabled
Aug  9 22:14:17 X220 NetworkManager[1261]: <warn> (cdc-wdm0) failed to connect modem: Couldn't wait for 'enabled': new state is 'enabling'
Aug  9 22:14:17 X220 NetworkManager[1261]: <info> (cdc-wdm0): device state change: prepare -> failed (reason 'unknown') [40 120 1]
Aug  9 22:14:17 X220 NetworkManager[1261]: <warn> Activation (cdc-wdm0) failed for connection 'O2 connection'
Aug  9 22:14:17 X220 NetworkManager[1261]: <info> (cdc-wdm0): device state change: failed -> disconnected (reason 'none') [120 30 0]
Aug  9 22:14:17 X220 NetworkManager[1261]: <info> (cdc-wdm0): deactivating device (reason 'none') [0]
Aug  9 22:14:17 X220 ModemManager[1144]: <info>  Modem /org/freedesktop/ModemManager1/Modem/0: state changed (enabling -> disabled)
Aug  9 22:14:17 X220 NetworkManager[1261]: <info> (cdc-wdm0) modem state changed, 'enabling' --> 'disabled' (reason: unknown)
Aug  9 22:14:17 X220 NetworkManager[1261]: <warn> (cdc-wdm0) failed to enable modem: GDBus.Error:org.freedesktop.libqmi.Error.Protocol.HardwareRestricted: Couldn't set operating mode: QMI protocol error (83): 'HardwareRestricted'

```Were you able to fix the problem?

---

