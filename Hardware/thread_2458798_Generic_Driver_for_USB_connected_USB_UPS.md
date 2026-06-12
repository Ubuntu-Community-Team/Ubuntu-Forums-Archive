---
title: "Generic Driver for USB connected USB UPS"
date: 2021-03-04
forum: Hardware
---

### Post by chribonn on 2021-03-04
Hello,

I would like to enquire whether there is a generic driver that I can query to get UPS status.  I would like to be able to read if it is on A/C or not and parameters like estimated run time and % capacity.

The idea is to write a PowerScript script that will periodically poll the device.

Thanks

---

### Post by him610 on 2021-03-04
You might want to take a look at apcupsd. 
This is its description from synaptic, "apcupsd provides UPS power management for APC products, including most BackUPS series models (including USB), SmartUPS V/S, SmartUPS (NET/RM), and Matrix series."

---

### Post by chribonn on 2021-03-05
Thank you. Will have a look at it.

I developed a PowerScript 7 Windows 7 generic UPS driver (source: [http://www.github.com/chribonn/UPSMonitor](http://www.github.com/chribonn/UPSMonitor)).

PowerScript 7 is multiplatform and my idea was to see whether I could port the script to this OS.  In Windows I used the Win32_UPS driver.

---

