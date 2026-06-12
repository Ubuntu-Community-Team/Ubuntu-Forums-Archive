---
title: "Suspend / Resume problem with TV card"
date: 2009-06-09
forum: Hardware
---

### Post by dookka on 2009-06-09
My new MythTV front/backend locks up when trying to suspend and needs to be powered down from the wall.
The culprit's the Hauppauge Nova-TD 500 PCI tv card, and I can fix it by:
```

# service mythtv-backend stop       (uses dvb_usb_dib0700)
# rmmod dvb_usb_dib0700
# pm-suspend
```
Now it suspends and resumes and I can get mythtv-backend going again:
```

# modprobe dvb_usb_dib0700
# service mythtv-backend start
```
But how do I do this automatically?  I tried adding the editing /etc/default/acpi-suspend
```

MODULES="dvb_usb_dib0700"
...
STOP_SERVICES="mythtv-backend networking"
```
But it hangs when I press the sleep button.

Also, my D-Link DWA-110 Wireless G PCI card can't reconnect after resume, hence 'networking' in STOP_SERVICES, but it still can't reconnect.  I can fix it after a resume by:
```

# rmmod rt61pci
# modprobe rt61pci
```
Now I can reconnect using the networking icon.  How can I add this into the mix?

Thanks!
dookka.

---

