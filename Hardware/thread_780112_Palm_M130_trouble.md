---
title: "Palm M130 trouble"
date: 2008-05-03
forum: Hardware
---

### Post by jimmyd850 on 2008-05-03
Hello,

I'm happy I've made the jump to ubuntu from XP but there is one last thing that's bugging me. I can't get my palm to sync up. I've trawled through many forums and I'm still stuck.

I have visor running but when I press hotsync I get the following message in the var/log/syslog:

May  3 14:24:48 jimmyd-desktop kernel: [ 2324.693908] usb 2-1: new full speed USB device using ohci_hcd and address 7
May  3 14:24:49 jimmyd-desktop kernel: [ 2324.909878] usb 2-1: configuration #1 chosen from 1 choice
May  3 14:24:49 jimmyd-desktop kernel: [ 2324.926811] visor: probe of 2-1:1.0 failed with error -5
May  3 14:24:49 jimmyd-desktop NetworkManager: <debug> [1209821089.114505] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_830_50_PalmSN12345678'). 
May  3 14:24:49 jimmyd-desktop NetworkManager: <debug> [1209821089.191463] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_830_50_PalmSN12345678_if0'). 
May  3 14:26:01 jimmyd-desktop kernel: [ 2397.283612] usb 2-1: usbfs: USBDEVFS_CONTROL failed cmd gpilotd rqt 194 rq 4 len 20 ret -62
May  3 14:26:01 jimmyd-desktop kernel: [ 2397.284847] usb 2-1: USB disconnect, address 7
May  3 14:26:01 jimmyd-desktop NetworkManager: <debug> [1209821161.497226] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_830_50_PalmSN12345678_if0'). 
May  3 14:26:01 jimmyd-desktop NetworkManager: <debug> [1209821161.504860] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_830_50_PalmSN12345678'). 

Am I right in thinking that at some point the palm should be assigned to tty0 or tty1 or something like that? I'm still a little new to linux but I am willing to learn so I just need a prompt in the right direction!

Thanks,
James

---

