---
title: "another suspend/battery problem"
date: 2006-01-11
forum: Hardware &amp; Laptops
---

### Post by nwcowboysfan on 2006-01-11
I know there are several posts on these topics already, but I thought I would ask anyway since there don't appear to be any resolutions.

I have a Tosiba Satellite L25-S1194. Suspend works great until I try to wake it back up. The hard drive comes back fine but the screen remains black and the keyboard does not respond (can't use ctrl+alt+F1 for terminal screen). I have read that this may be due to the ATI proprietary graphics drivers. Is there any way to resolve this? Does suspend2 solve this problem?

Secondly, when running on batteries the monitor shows 0%.

          $ cat /proc/acpi/battery/BAT1/state
          present:                 yes
          ERROR: Unable to read battery status

          $ cat /proc/acpi/battery/BAT1/info
          present:                 yes
          design capacity:         2250 mAh
          last full capacity:      2144 mAh
          battery technology:      rechargeable
          design voltage:          14400 mV
          design capacity warning: 300 mAh
          design capacity low:     132 mAh
          capacity granularity 1:  32 mAh
          capacity granularity 2:  32 mAh
          model number:            PA3450U-1BRS
          serial number:           26314
          battery type:            LION
          OEM info:                TOSHIBA

I know these issues have come up with several users, but if anyone can give me some insight or direction it would be greatly appreciated!

Thanks in advance!

---

