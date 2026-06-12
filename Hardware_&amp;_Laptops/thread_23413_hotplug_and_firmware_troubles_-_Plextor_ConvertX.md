---
title: "hotplug and firmware troubles - Plextor ConvertX"
date: 2005-04-01
forum: Hardware &amp; Laptops
---

### Post by tube013 on 2005-04-01
I have a Plextor ConvertX usb2 tv tuner/hardware mpeg 1/2/4 encoder.  It has linux drivers, but something with the Unbuntu and Debian hotplug scripts are making my life misreable trying to get this to work.  The connection works by having the computer upload one firmware upon connection, then disconnecting and reconnecting under a different id, and requiring a 2nd firmware.  this second firmware is where it is failing with Ubuntu.

I had it working way back on Feb. 17, but keeping up with hoary updates did something that is preventing this from working.

If anyone has any idea about changes to the ubuntu hotplug package that could effect the loading of firmware, please speak up.

---

### Post by tube013 on 2005-04-02
[QUOTE=tube013]I have a Plextor ConvertX usb2 tv tuner/hardware mpeg 1/2/4 encoder.  It has linux drivers, but something with the Unbuntu and Debian hotplug scripts are making my life misreable trying to get this to work.  The connection works by having the computer upload one firmware upon connection, then disconnecting and reconnecting under a different id, and requiring a 2nd firmware.  this second firmware is where it is failing with Ubuntu.

I had it working way back on Feb. 17, but keeping up with hoary updates did something that is preventing this from working.

If anyone has any idea about changes to the ubuntu hotplug package that could effect the loading of firmware, please speak up.[/QUOTE]
 FYI, I got this working.  there is something wrong with hotplug that loads the driver before loading the firmware.  the firmware loads after the driver, so removing the module, and then modprobing it solved the problem

---

