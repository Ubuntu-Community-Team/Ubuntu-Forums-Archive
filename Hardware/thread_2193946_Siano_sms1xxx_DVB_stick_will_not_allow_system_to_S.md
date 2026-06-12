---
title: "Siano sms1xxx DVB stick will not allow system to Standby/Suspend/Hibernate"
date: 2013-12-15
forum: Hardware
---

### Post by os2 on 2013-12-15
The stick itself works on my system. But I wish to put my system into Standby from time to time and so that means unloading the associated kernel modules and then reloading them later.

I am trying to get the kernel modules for this USB DVB-T stick to unload prior to Suspend.

The kernel modules for the device are smsmdtv which is dependent on smsdvb and smsusb.

When I try and unload smsusb these are the device messages (dmesg) I get:

> 
[10131.948838] usbcore: deregistering interface driver smsusb
[10131.949086] smsusb_onresponse: line: 91: error, urb status -108 (-ESHUTDOWN), 0 bytes
[10131.949097] smsusb_onresponse: line: 91: error, urb status -108 (-ESHUTDOWN), 0 bytes
[10131.949102] smsusb_onresponse: line: 91: error, urb status -108 (-ESHUTDOWN), 0 bytes
[10131.949107] smsusb_onresponse: line: 91: error, urb status -108 (-ESHUTDOWN), 0 bytes
[10131.949111] smsusb_onresponse: line: 91: error, urb status -108 (-ESHUTDOWN), 0 bytes
[10131.949116] smsusb_onresponse: line: 91: error, urb status -108 (-ESHUTDOWN), 0 bytes
[10131.949120] smsusb_onresponse: line: 91: error, urb status -108 (-ESHUTDOWN), 0 bytes
[10131.949125] smsusb_onresponse: line: 91: error, urb status -108 (-ESHUTDOWN), 0 bytes
[10131.949130] smsusb_onresponse: line: 91: error, urb status -108 (-ESHUTDOWN), 0 bytes
[10131.949135] smsusb_onresponse: line: 91: error, urb status -108 (-ESHUTDOWN), 0 bytes


If I try to reload smsusb these are device messages I get:

> 
[10214.784106] smscore_detect_mode: line: 1272: MSG_SMS_GET_VERSION_EX_REQ failed first try
[10219.784116] smscore_set_device_mode: line: 1352: mode detect failed -62
[10219.784128] smsusb_init_device: line: 431: smscore_start_device(...) failed
[10219.784638] smsusb_onresponse: line: 143: error, urb status -2, 0 bytes
[10219.785057] smsusb_onresponse: line: 143: error, urb status -2, 0 bytes
[10219.785511] smsusb_onresponse: line: 143: error, urb status -2, 0 bytes
[10219.785935] smsusb_onresponse: line: 143: error, urb status -2, 0 bytes
[10219.786353] smsusb_onresponse: line: 143: error, urb status -2, 0 bytes
[10219.786810] smsusb_onresponse: line: 143: error, urb status -2, 0 bytes
[10219.787040] smsusb_onresponse: line: 143: error, urb status -2, 0 bytes
[10219.787310] smsusb_onresponse: line: 143: error, urb status -2, 0 bytes
[10219.787565] smsusb_onresponse: line: 143: error, urb status -2, 0 bytes
[10219.787788] smsusb_onresponse: line: 143: error, urb status -2, 0 bytes


---

### Post by os2 on 2013-12-15
OK I need to be removing just the one module smsusb prior to Suspend/Hibernate and then modprobing it on Resume.

> modprobe -r smsusb

Leave smsmdtv and smsdvb alone.
Linux Kernel 3.11-8.

---

### Post by os2 on 2013-12-15
This is what my /etc/pm/sleep.d/script-name looks like:

```

#! /bin/bash

# Script to stop mythbackend before suspend and do something after wake.

case "${1}" in
    suspend|hibernate)
        if [ "$(pidof mythbackend)" ] ; then
            service mythtv-backend stop
            sleep 5
        fi
        modprobe -r smsusb
    ;;

    resume|thaw)
        modprobe smsusb
        service mythtv-backend start
    ;;
esac

```

I alternatively could have also put the following in say /etc/pm/config.d/config

```

# cat /etc/pm/config.d/config
SUSPEND_MODULES=smsmdtv

```

This also works but tends to cause a glitch more often than not with the mythTV backend server, through misaligned ordering of the execution shown above.

---

