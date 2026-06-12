---
title: "Sitecom wireless 300N problem"
date: 2009-09-30
forum: Hardware
---

### Post by the-furrie on 2009-09-30
I tried to instal the drivers for Sitecom wireless 300N X2 using ndiswrapper. After that I have run sudo dmesg and it say:
```
ndiswrapper (import:242): unknown symbol: ntoskrnl.exe: 'MmGetSystemRoutineAddress'
ndiswrapper (load_sys_files:210): couldn't prepare driver 'rt2870'
ndiswrapper (load_wrapper_driver:112): couldn't load driver rt2870; check system log for messages from 'loadndisdriver'

```I have checked the log add /var/log/messages but that file is empty.
I also followed the following guid :[https://help.ubuntu](https://help.ubuntu) .com/community/WifiDocs/Driver/Ndiswrapper. That didn't work either.
The device ID is 0DF6:0040. If someone needs more information to solve the problem please ask.

Just tried [http://onlyubuntu.blogspot.com/2008/06/howto-setup-dlink-wua-2340-usb-wireless.html](http://onlyubuntu.blogspot.com/2008/06/howto-setup-dlink-wua-2340-usb-wireless.html), but with that one it goes wrong where you go to Open System->Administration->Network. The thing that goes wrong is that there is no wireless network in the list

*note*
I'm using gos ([http://www.thinkgos.com/](http://www.thinkgos.com/))

---

### Post by nickmcg on 2009-10-01
You shouldn't need to use ndiswrapper as the rt2870 driver is included in Jaunty and Karmic, although in Karmic you need to blacklist rt2800usb.

Your post said you're using gos (private beta?) - you may need to build the driver - sources on the ralink website.

Nick

---

