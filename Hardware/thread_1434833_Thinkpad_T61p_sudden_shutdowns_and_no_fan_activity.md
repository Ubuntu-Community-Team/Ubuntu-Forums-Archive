---
title: "Thinkpad T61p sudden shutdowns and no fan activity"
date: 2010-03-20
forum: Hardware
---

### Post by yamagami on 2010-03-20
Hi there
I have a pretty severe problem that started after (just recently) upgrading to 9.10. 
My laptop started shutting down occasionally, very suddenly and without warning. 
ACPI messages in syslog suggests the laptop is overheating:

```
ar 20 09:45:40 yamagami kernel: [150897.601042] thinkpad_acpi: THERMAL EMERGENCY: a sensor reports something is extremely hot!
Mar 20 09:45:44 yamagami wpa_supplicant[1358]: CTRL-EVENT-SCAN-RESULTS
Mar 20 09:45:50 yamagami kernel: [150907.450892] thinkpad_acpi: THERMAL EMERGENCY: a sensor reports something is extremely hot!
```

However, I also don't remember the last time I heard my fan spinning since I upgraded. 

I can see I'm not the only experiencing the sudden shutdowns and loss of fan activity (and there's me thinking I'm popular just to see my only fan go away :D )

Anyone has a solution to this? How can I kick my fan back into action?

Thanks
Harel

---

### Post by yamagami on 2010-03-20
Seems like a bios update and using kernel 2.6.28-18 seems to kick the fan up a notch, though I have yet to hear it spin in anger. At least it spins though...

---

### Post by tgalati4 on 2010-03-20
sudo apt-get install tpfan-admin

---

### Post by yamagami on 2010-03-21
This doesn't seem to work... My apt can't find that package....

sudo apt-get install tpfan-admin 

Is there a special repo i need to add to sources.list?

---

