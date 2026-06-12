---
title: "[SOLVED] laptop fan wont turn off since I upgraded to 8.10"
date: 2008-11-10
forum: Hardware
---

### Post by stephanecharette on 2008-11-10
I have a DELL Latitude D630 laptop.  Previously had Ubuntu 8.04 loaded fine.

Now that I've upgraded to 8.10, I notice the fan is **always** running at max, even when the laptop is sitting idle for several days.  It is actually quite loud.  This is new behaviour since I upgraded to 8.10.

Running "acpi -V" tells me:
```
Battery 0: Full, 100%
AC Adapter 0: on-line
Thermal 0: ok, 35.5 degrees C
Cooling 0: Processor 0 of 10
Cooling 1: Processor 0 of 10
```

That's it, no other temperature sensors.  Following a hint I found in another thread, I also ran the following:
```
sudo apt-get install lm-sensors
sudo sensors-detect
sensors
```
This gave me:  ```
temp1:    +34.5°C (crit = +99.0°C)
```

Any hints as to how to get Ubuntu 8.10 to "step down" on idle would be greatly appreciated.

Stéphane Charette

---

### Post by stephanecharette on 2008-11-10
Problem solved by doing a firmware update.  And it can even be done from within linux!

Information was found here:
[http://linux.dell.com/wiki/index.php/Tech/libsmbios_dellBiosUpdate](http://linux.dell.com/wiki/index.php/Tech/libsmbios_dellBiosUpdate)

In summary:
1) [COLOR="Blue"]sudo apt-get install firmware-addon-dell[/COLOR]
2) [COLOR="Blue"]sudo getSystemId[/COLOR]   # note the "System ID" line
3) download most recent firmware from [http://linux.dell.com/repo/firmware/bios-hdrs/](http://linux.dell.com/repo/firmware/bios-hdrs/)
4) [COLOR="Blue"]sudo modprobe dell_rbu[/COLOR]
5) [COLOR="Blue"]sudo dellBiosUpdate -u -f ~/Desktop/bios.hdr[/COLOR]
6) [COLOR="Blue"]sudo reboot[/COLOR]

Stéphane Charette

EDIT #1:  Step #3 can be confusing if you don't also read the Dell wiki page with the details on naming conventions.  To summarize from the [Dell wiki page]("http://linux.dell.com/wiki/index.php/Tech/libsmbios_dellBiosUpdate"), the directories are named as [COLOR="Green"]system_bios_ven_0x1028_dev_[/COLOR][COLOR="Red"]SYSTEM_ID[/COLOR][COLOR="Green"]_version_[/COLOR][COLOR="Red"]BIOS_VERSION[/COLOR].  Note the [COLOR="Red"]SYSTEM_ID[/COLOR] which was discovered during step #2.  In my case, for the Dell Latitude D630, the most recent bios as of mid-November 2008 which fixed the fan issue I experienced was [COLOR="Green"]system_bios_ven_0x1028_dev_0x01f9_version_a13[/COLOR].

EDIT #2:  As victorb mentions in a posting below, ensure your laptop is running on AC and not on battery when you upgrade the firmware!

EDIT #3:  I've used this method to successfully update the bios on several of my Dell computers, including a few different models of desktops and laptops, not just the Latitude.

---

### Post by ciscosurfer on 2008-11-11
You might be interested in reading [this thread]("http://swiss.ubuntuforums.org/showthread.php?t=948556") as well (I know you've fixed your issue).  The thread makes mention of downgrading video drivers as another possible solution.  Probably moot at this point, but thought I'd pass it along anyways. :-)
[]("http://ubuntuforums.org/showthread.php?t=318789")

---

### Post by victorb on 2008-11-12
Thanks Stephane for the step by step solution... Problem solved in 5 minutes!

Note to others: the laptop has to be plugged in when you reboot for the bios update to be performed. If not it just stops with an error message... don't ask me how I found out..

---

### Post by HydroModeler on 2008-11-18
Thank you for the post, your suggestion fixed my problem about 90%.

Prior to upgrading the BIOS on my Inspiron 1420 (originally had Vista not Ubuntu)the fan would be on at what appeared to be full speed.  After upgrading the BIOS the fan speed has gotten better, but still not perfect.  

Now it seems to almost never loud enough to hear it when plugged in, but when running on battery it runs constantly after being on battery for a few mins.  It is not as loud/fast as it was before upgrading the BIOS, but still pretty high.  The real problem I have with this is that it is killing my battery life to about 2 hrs from 4 hrs.

Any thoughts?  I was thinking about trying the other driver (*173?), but it seems like it is more of a configuration problem since it is fine when plugged in.  Not sure where to begin to trouble shoot this.

---

### Post by zigx on 2008-11-21
stephanecharette worked perfectly. thank you so much for this fix!

---

### Post by fifth_rune on 2008-11-21
Unfortunately this did not work for me.  When I tried to install the bios it told me that I already had the newest version or that it was the existing version.  My System ID was 0x01d8 and I used bios version a10

I did a check with lshw-gtk and it turns out the Dell Technicians gave me a version that's not even on the web which is A11.  WTF am I supposed to do now?

---

### Post by joshobrien77 on 2008-11-28
Worked like a charm.  Thanks for the quick fix!

---

### Post by morganm on 2009-11-18
Thanks for the research and the detailed instructions.  The fan was driving me nuts and this fixed it for me!

---

### Post by kwalsh on 2010-07-07
Thank you for the post. I needed to update BIOS and it resolved my laptop temp issues

---

