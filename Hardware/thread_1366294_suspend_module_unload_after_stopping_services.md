---
title: "suspend module unload after stopping services"
date: 2009-12-28
forum: Hardware
---

### Post by schitthoch2 on 2009-12-28
Hi.

I am running mythbuntu 9.10 and i have a Terratec Cinergy T2 DVB-T card, which prevents my box to go to suspend needed for acpi-wakeup to work (S3 is the only thing my MB supports)

I have put all suspend blocking modules to unload in /etc/default/acpi-support before running /etc/acpi/sleep.sh by an external script. And i have put the mythtv-backend services in the stop services there too.

The problem seems to be that the **modules are beeing unloaded before stopping the service**. Therefore the backend still captures the dvb device and the **modules are NOT unloaded** correctly which leeds to a failure to suspend (blinking console cursor in VT1).

If i stop the mythtv-backend manually, then remove the modules manually and run /etc/acpi/sleep.sh manually, it suspends correctly.

I have tried to stop the service in my custom suspend script before running /etc/acpi/sleep.sh, but as the script itself is run by mythtv-backend (mythwelcome) it somehow does not run commands after /etc/init.d/mythtv-backend stop as mythwelcome looses contact to mythtv-backend.

Therefore i need a way to unload the modules after the service is stopped by the official suspend integration (pm-suspend). 

But how would i do that?

TIA

---

### Post by juergi on 2009-12-30
I ran into the same problem.
Did you find a solution meanwhile?

---

### Post by schitthoch2 on 2010-01-02
hi juergi

no, unfortunately not yet

someone else?

---

### Post by schitthoch2 on 2010-01-03
I have solved this issue with a workaround by **forcing** the modules to unload (rmmod --f, see man rmmod) but i need to reboot my pc after the resume to guarantee that my dvb-t cards' module is loaded correctly

**dvb_usb_cinergyT2 dvb_usb dvb_core** are my conflicting modules

My personal myth shutdown script i let run by mythwelcome. The service mythtv-backend is still set to stop/restart in /etc/default/acpi-support

```

#!/bin/bash
sudo **rmmod --f** dvb_usb_cinergyT2 dvb_usb dvb_core &
sudo **rmmod --w** dvb_usb_cinergyT2 dvb_usb dvb_core &
sudo /etc/acpi/sleep.sh
#sudo /etc/acpi/hibernate.sh # does not resume with this board
sudo reboot

```

You need /etc/acpi/sleep.sh, /usr/**X**bin/rmmod, and probably the pm-suspend script in your /etc/sudoers file

---

### Post by peterpall on 2010-05-27
Even if I had a different problem (I want to unload ath-hal on suspend) I came to the same solution. In my case solving the problem was possible by addding the module name to the MODULES= line of /etc/default/acpi-support instead. This solution involves less typing work in case it works - but of course is less flexible if more complex actions might be required to unload the modules.

---

### Post by peterpall on 2010-05-27
Did find a way to make it work with more power management backends:

Create a file in /etc/pm/config.d/ (The name of this file doesn't seem to matter) and put the following line into it:
```

SUSPEND_MODULES="ath5k memstick jmb38x_ms ath_pci ath_hal ath_rate_sample"
#SLEEP_MODULE="uswsusp"

```
(naturally replacing the module names listed here with the modules you want to be removed during suspend).

---

