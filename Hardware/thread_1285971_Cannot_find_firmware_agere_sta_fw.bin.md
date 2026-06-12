---
title: "Cannot find firmware agere_sta_fw.bin"
date: 2009-10-08
forum: Hardware
---

### Post by iposner on 2009-10-08
Just installed xubuntu karmic beta on [http://support.vaio.sony.eu/computing/vaio/specifications/index.aspx?l=en_GB&m=PCG-SRX51P_B]("http://support.vaio.sony.eu/computing/vaio/specifications/index.aspx?l=en_GB&m=PCG-SRX51P_B")

On startup, I get the following message:

eth1: Cannot find firmware agere_sta_fw.bin

Following login (I think) the ALT-F1 terminal shows the above message plus the following:

eth1: orinoco_reset: Error -2 re-initializing firmware
eth1: Device has been disabled!

Lo and behold, the wireless doesn't work.

I tried installing the windows drivers using NDIS, but the original drivers that ship with the laptop produce an "Invalid Driver!" message when installed using the ndisgtk tool.

I would be grateful if someone could provide some guidance.

---

### Post by trundlenut on 2009-10-08
DO you actually have the firmware on the machine?  On my machine (running Jaunty) it is in /lib/firmware.  If you don't have it I can upload it onto her for you, though you could find it if you search.

---

### Post by Yellow Pasque on 2009-10-08
[http://git.kernel.org/?p=linux/kernel/git/dwmw2/linux-firmware.git;a=blob;f=agere_sta_fw.bin;h=bae000f5a7162f5a5b052a2f5b78016e95f825c5;hb=HEAD](http://git.kernel.org/?p=linux/kernel/git/dwmw2/linux-firmware.git;a=blob;f=agere_sta_fw.bin;h=bae000f5a7162f5a5b052a2f5b78016e95f825c5;hb=HEAD)

---

