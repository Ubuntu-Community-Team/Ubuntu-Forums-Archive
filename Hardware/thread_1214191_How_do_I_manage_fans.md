---
title: "How do I manage fans"
date: 2009-07-15
forum: Hardware
---

### Post by oh my on 2009-07-15
Hi,

I would like my fans to run faster than they do right now. How can I change the settings for them?

---

### Post by ThisEndlessFall on 2009-07-15
> **oh my said:**
> Hi,

I would like my fans to run faster than they do right now. How can I change the settings for them?

Including your graphics card fan, if you have one?

---

### Post by oh my on 2009-07-15
Yes. :)

It's a laptop, don't know if this is going to have any effect?

EDIT: I wouldn't mind the graphic card fan running faster, but I don't know if I have one

---

### Post by ThisEndlessFall on 2009-07-15
> **oh my said:**
> Yes. :)

It's a laptop, don't know if this is going to have any effect?

EDIT: I wouldn't mind the graphic card fan running faster, but I don't know if I have one

Hmmmm. What laptop do you have & what graphics chipset does it contain?

---

### Post by oh my on 2009-07-15
I have an acer travelmate 6492, it is an integrated intel graphic chip. I think it is called [Intel Graphics Media Accelerator (GMA) X3100]("http://www.notebookcheck.net/Intel-Graphics-Media-Accelerator-X3100.2176.0.html")

---

### Post by oh my on 2009-07-18
ThisEnlessFall are you still with me? Did I do something wrong?

---

### Post by oh my on 2009-08-08
help! What do you have to do to get any help?

---

### Post by oh my on 2009-08-21
up

---

### Post by trundlenut on 2009-08-21
could this and your temperature sensor problem by ACPI related?  Did you have any problems with ACPI when you installed ubuntu?

---

### Post by Grenage on 2009-08-21
I'll take over, let me see what I can find out.

---

### Post by urosg3 on 2009-08-21
Look this link
[http://ubuntuforums.org/showthread.php?t=42737]("http://ubuntuforums.org/showthread.php?t=42737")

---

### Post by oh my on 2009-08-21
Hi,

thanks for the link urosg3, I do get the error message "/usr/sbin/pwmconfig: There are no pwm-capable sensor modules installed", but I have Jaunty and the fix no longer corresponds to what is written in the config file. 
Somebody asked about the same thing in the guide 2 weeks ago, but noone replied: [link]("http://ubuntuforums.org/showpost.php?p=7725356&postcount=90"). Is there a more up to date guide I could use? Or a known workaround for that problem?

trundlenut, well right now the fancontrol is not a problem in itself, I'm merely trying to find out how to manage my fans, if possible. But yes, I checked the temperatures and they went over 70°C with the fans barely active, so I wondered if I could get the fans to be more active.

Grenage thanks, :) I'll stay tuned. :)

regards

---

### Post by Yellow Pasque on 2009-08-21
Laptops usually use ACPI to control the fans.

If this module loads successfully, then you should have entries in /proc/acpi/fan
```
sudo modprobe acer-wmi
```

[http://www.columbia.edu/~ariel/acpi/acpi_howto.0.2a.html#proc_fan](http://www.columbia.edu/~ariel/acpi/acpi_howto.0.2a.html#proc_fan)

EDIT: You might want to check your vendor's page for BIOS updates, and see if any BIOS updates fix ACPI or thermal issues.

---

### Post by oh my on 2009-08-21
Hi,

acer_wmi is working fine from what I can tell. 
There also is a Fan0 listed in /proc/acpi/fan, currently the state says it's off, even though I can hear it working.. I'm going to monitor the fan for a while and see if the status changes. :)

Thanks for the link, it is awesome!

regards

---

