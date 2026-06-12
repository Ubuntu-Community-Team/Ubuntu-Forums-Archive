---
title: "ipw2200 startup error messages"
date: 2005-09-21
forum: Hardware &amp; Laptops
---

### Post by fdimmling on 2005-09-21
Hi,

I'm running Hoary on my Acer Travelmate 291LCi Centrino Notebook. Since the last kernel update (2.6.10-5-686) I get the following messages at boot time:

ipw2200: Firmware Error detected. Restarting
ipw2200: Firmware Error detected. Restarting
ipw2200: Failed to send SSID command

Obviously ipw2200 is recovering because wireless is working afterwards including WPA.

I found 2 versions of the ipw2200 firmware on my notebook, one ipw-2.3-... copied by me to /usr/lib/hotplug/firmware when I first compiled the ipw2200 driver to allow WPA and now another set of 7 files ipw-2.2-...fw-2.6.10-5-686 which I guess was copied by the kernel update to /lib/hotplug/firmware

Well it's not really serious since wireless i working, just a bit irritating.

Friedrich

---

### Post by mlomker on 2005-09-22
> Well it's not really serious since wireless i working, just a bit irritating.


I'm surprised that it wasn't occuring before your kernel update.  That is a common problem with that driver.  I get it, too.

---

### Post by fdimmling on 2005-09-23
[QUOTE=mlomker]I'm surprised that it wasn't occuring before your kernel update.  That is a common problem with that driver.  I get it, too.[/QUOTE]
 This means: Just ignore it. 

BTW I have another problem with the wireless connection. After about one hour the connection is broken. When I switch off  the access point and on again the connection is reestablished and works for another hour or so. Maybe this problem is connected with WPA. It maybe a problem of the access point (3COM Office Connect Wireless 54MBps 11g Travel Router) too. Is this also a common problem?

Best regards

Friedrich

---

### Post by mlomker on 2005-09-23
> ed and works for another hour or so. Maybe this problem is connected with WPA. It maybe a problem of the access point (3COM Office Connect Wireless 54MBps 11g Travel Router) too. Is this also a common problem?


I've read numerous threads with similar issues related to encryption.  Most of the posters say that they have to reboot their machines and then they can reconnect.  Theirs only occurs a few times per day, not every hour.  Have you used Windows with your access point?  I have a bad access point at work that has to be rebooted every hour...there's something wrong with it.

I do not use encryption at home and I've never had a problem with wireless.

The firmware errors never seem to hurt anything--downloads don't disconnect or anything like that so they can be ignored.  I also get a ton of ACPI errors in my dmesg that are related to the Intel drivers:

```

APIC error on CPU0: 40(40)

```

---

### Post by fdimmling on 2005-09-23
[QUOTE=mlomker]Have you used Windows with your access point?[/QUOTE]

I'm living in a pure Linux environment - no Windows anywhere. 

I agree that it might well be a problem of the access point. Anyway I can live with it. 
I have another AP a Siemens Gigaset WLAN Repeater which works well while using the internet but communication gets stuck immediately when connecting via NFS to another computer. Thus I did not use it much and cannot say if it also stops working after an hour or so.

Friedrich

---

