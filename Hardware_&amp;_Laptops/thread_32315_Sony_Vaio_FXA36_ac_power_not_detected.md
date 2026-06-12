---
title: "Sony Vaio FXA36 ac power not detected"
date: 2005-05-07
forum: Hardware &amp; Laptops
---

### Post by whistl on 2005-05-07
I have a Sony VAIO PCG-FXA36 laptop with ubuntu 5.04 installed.  Right away, I noticed that the hard drive kept spinning down every couple of minutes, and the gnome battery monitor was incorrectly saying I was always running on battery (with -1% charge left), even when it was plugged into AC power.  /proc/acpi/battery/*/state says I have no batteries and /proc/acpi/ac_adapter/ACAD/state says I am not running on ac.  Call the white house, I've solved the energy crisis!

I ended up just closing down the gnome power monitor app, since it didn't display correct info.  To workaround the hardware strain and delays caused by the hard drive spinning down, I just renamed /etc/rc2.d/S99acpi-support to _S99acpi-support, so it wouldn't run at boot time.  That's the script that runs hdparm commands to set the hard drive spin down timer.  I suppose I could run the script or the hdparm commands manually, if I ever do run on battery somewhere.

What's odd, is that the Kismet program is able to detect and display the AC power/battery status and level correctly.  Hmm.  Must not use ACPI.

---

