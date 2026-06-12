---
title: "APC UPS with USB - is it possible to install on Ubuntu?"
date: 2016-05-15
forum: Hardware
---

### Post by ericoporto2008 on 2016-05-15
I can't find updated information on the web. Is it possible to install and get both an appindicator for the UPS and an action to shutdown the pc correctly to avoid HDD corruption?

My UPS is:

APC Smart-UPS 1000VA USB & Serial Brazil 120V
partnumber:    SUA1000-BR

---

### Post by weatherman2 on 2016-05-15
I believe I have tried this before.  Ubuntu should simply detect the UPS as a battery, like a laptop would.  So it will shut down in the same way a laptop would shut down when it detects the battery is about to die.  No special application would be needed - it should act just like a laptop with a battery.

---

### Post by him610 on 2016-05-15
I have two UPS units, one for a computer, and in another room, there is a smaller capacity unit for the network devices; cable modem, router, and switch.

When the USB or serial cable is connected between your UPS and you CPU, it monitors the status of the battery inside of the UPS. There is a utility you may need to install; in synaptic search for *apcupsd*,  or....```
sudo apt show apcupsd

```

---

### Post by SeijiSensei on 2016-05-16
You just need to install apcupsd and edit its configuration file to tell it you're using a USB cable.  It will shutdown the system gracefully if the power is off for longer than a criterion value, and it can tell other machines to shut themselves down as well.  Read the manual page for more details: [http://linux.die.net/man/8/apcupsd](http://linux.die.net/man/8/apcupsd)

---

