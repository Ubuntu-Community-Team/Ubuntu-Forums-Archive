---
title: "Unstable wlan in Jaunty"
date: 2009-05-15
forum: Hardware
---

### Post by Dalle85 on 2009-05-15
After updating to Jaunty, I have been experiencing massive problems with my wireless connection! Whenever I reboot, it connects to my wireless network (though it takes WAY to long, about 25-30 seconds) and everything seems fine for a while, but then with no apparant cause, my connection becomes extremely unstable. In the syslog, there is an entry each time it happens:

morten-laptop kernel: [ 8961.000196] iwlagn: Error sending REPLY_SCAN_ABORT_CMD: time out after 500ms.

And then there are about 50 entries related to the wlan authentication. The only solution is to deactivate the wireless connection, but then when I reactivate it, it doesn't pick up any networks what-so-ever (usually, I can pick up at least 10 different networks). Each time, it produces the following messages:

May 15 23:38:57 morten-laptop kernel: [ 8520.071738] ADDRCONF(NETDEV_UP): wlan0: link is not ready
May 15 23:40:22 morten-laptop kernel: [ 8604.836522] iwlagn 0000:06:00.0: PCI INT A disabled

Sometimes, it resolves itself and connects to my wireless automatically (eventually), sometimes, I have to restart the computer 4-5 times and when it is really bad I have to (ohh the horror) boot up in Windows Vista (where the wlan works flawlessly) and then reboot to Ubuntu in order to get my wlan back!

The comp is an Acer Aspire 5920g with an Intel Wireless WiFi Link 4965AGN.

Does anyone have any idea to what might be the cause and more importantly, how I fix it?! I've tried "rmmod iwlagn"+"modprobe iwlagn", I've tried restarting the networking, I've tried different network managers, I've tried everything, but until I can find the cause and I can find a way to reliably replicate, I don't think it would be appropriate to open a bug report - it might just be my computer but it just seems strange that it appeared after updating to Jaunty

---

### Post by koffu on 2010-02-13
I have the same problem with HP Compaq 610
```
Network controller: Intel Corporation Wireless WiFi Link 5100
iwlagn 0000:10:00.0: Error sending REPLY_SCAN_ABORT_CMD: time out after 500ms
```

To fix I need to reboot PC, but sometimes switch it off to get wifi come back!

---

