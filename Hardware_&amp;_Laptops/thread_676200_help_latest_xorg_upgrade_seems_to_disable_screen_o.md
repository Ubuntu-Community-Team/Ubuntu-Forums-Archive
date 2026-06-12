---
title: "help: latest xorg upgrade seems to disable screen outpuyt on thinkpad x40"
date: 2008-01-23
forum: Hardware &amp; Laptops
---

### Post by jaimedavila on 2008-01-23
Hello all,

I am running ubuntu 7.10 on a levono x40 laptop. Just this morning, after returning to the office with it, I notice that the external monitor is not coming on. That is , I get exactly what I would expect on the laptop's screen, but nothing on the external monitor. I have tried both having the monitor connected to the laptop's docking station, and connecting the screen directly to the laptop when the laptop is outside the docking station. The screen is OK, though, since it works on a different computer. I have booted the laptop up both inside and outside the docking station.

When I press fn-f7 to switch the display, I do get a confirmation that the acpi event was detected in /var/log/acpid. But the script configured in /etc/acpi/events to run on that event is /bin/true, as configured in /etc/acpi/events/ibm-videobtn. That file has a time stamp of May 23 2006, well before the xorg upgrade, of course. My xorg.cong has a time stamp of November 1, 2007. But, I do recall that there were some upgrades to the xorg system that I installed after having them announced by ubuntu's update manager a few days ago. 

As further confirmation of xorg being involved, fn-f7 in fact does its job if I press it while the system is booting up, up until the moment right before X starts.

I've done some searching on both the ubuntu forums and the web, but nothing useful has come up.

Any ideas?

Thanks in advance,

Jaime

---

### Post by mohnkern on 2008-01-23
> **jaimedavila said:**
> Hello all,

I am running ubuntu 7.10 on a levono x40 laptop. Just this morning, after returning to the office with it, I notice that the external monitor is not coming on. That is , I get exactly what I would expect on the laptop's screen, but nothing on the external monitor. I have tried both having the monitor connected to the laptop's docking station, and connecting the screen directly to the laptop when the laptop is outside the docking station. The screen is OK, though, since it works on a different computer. I have booted the laptop up both inside and outside the docking station.

When I press fn-f7 to switch the display, I do get a confirmation that the acpi event was detected in /var/log/acpid. But the script configured in /etc/acpi/events to run on that event is /bin/true, as configured in /etc/acpi/events/ibm-videobtn. That file has a time stamp of May 23 2006, well before the xorg upgrade, of course. My xorg.cong has a time stamp of November 1, 2007. But, I do recall that there were some upgrades to the xorg system that I installed after having them announced by ubuntu's update manager a few days ago. 

As further confirmation of xorg being involved, fn-f7 in fact does its job if I press it while the system is booting up, up until the moment right before X starts.

I've done some searching on both the ubuntu forums and the web, but nothing useful has come up.

Any ideas?

Thanks in advance,

Jaime

If you have a nvidia card in your machine -- 

Try reinstalling your restrictd drivers if you're using  them.  Several people have seen problems with the NVIDIA drivers and this most recent update.  Everyone's problem seems to be different, but the reinstallation of the drivers always seems to fix it.

---

### Post by jaimedavila on 2008-01-23
Thanks. But my chipset is from intel. Under system->preferences->hardware information, one of the entries lists "82852/855GM Integrated Graphics Device," which I've always understood to mean that the graphic card is from the 855 family.

Any sense in reinstalling _those_ drivers? How would I go about doing that, anyway?


Thanks,

Jaime

---

