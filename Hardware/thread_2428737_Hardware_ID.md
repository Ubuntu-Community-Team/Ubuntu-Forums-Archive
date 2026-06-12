---
title: "Hardware ID"
date: 2019-10-08
forum: Hardware
---

### Post by draboluk on 2019-10-08
Hi,

How can I change hardware ID (serial numbers) all components (mainboard, ram, gpu, cpu, hard drive etc.)?
Permanent change is possible?

---

### Post by QIII on 2019-10-08
It might be helpful if you would tell us what your goal is.

Do you want to change what the hardware reports about itself?  Do you want the OS to use different identification information?  What OS are you using?

---

### Post by TheFu on 2019-10-08
> **draboluk said:**
> Hi,

How can I change hardware ID (serial numbers) all components (mainboard, ram, gpu, cpu, hard drive etc.)?
Permanent change is possible?

I've never heard about this being done.  S/N is burned into the chips, but each specific device should have documentation about modifying the firmware.  Some software licenses are tied to those burned in numbers.  You might be able to have a small side-chip replaced on the motherboard, but there will be risks.

With some NICs, you can change the MAC, but only if the NIC supports it and the driver supports that change.  *macchanger* is a tool to change a MAC on a NIC. GNU MAC Changer.  This doesn't have anything to do with the S/N.

---

### Post by draboluk on 2019-10-09
I received an order from clients. We have various computer components, complete pc. I would like to change the serial numbers displayed on each operating system (all Linux distributions, Windows, Apple OS). How can I do it without physical interference?

Example for RAM: sudo dmidecode --type 17
```
Serial Number: 0021C245
Part Number HMT251U6CFR9C-PB
```

---

### Post by wildmanne39 on 2019-10-09
For what purpose? Are you trying to get around a licensing issue with Windows and Apple?

---

### Post by Yellow Pasque on 2019-10-09
You'd have to flash the SMBIOS (which is risky, even with the right utility). I know HP has a tool called dmifit.

---

### Post by draboluk on 2019-10-09
> **wildmanne39 said:**
> For what purpose? Are you trying to get around a licensing issue with Windows and Apple?

No. I don't care about guarantees or licenses.

That what I know dmidecode reports information about system's hardware as described in system BIOS and does not scan hardware, it only reports what the BIOS told it to. My goal is recognize hardware by any os and display hardware with other serial numbers. I'm not sure but os reading hardware information from the BIOS or scan hardware and display. I wonder how can I change serial numbers directly... for example... in ram because when I insert them to another pc the serial number might be default > That's why I care about permanent change.

---

### Post by wildmanne39 on 2019-10-09
Closed for Staff review.

---

### Post by wildmanne39 on 2019-10-10
After discussion with other Staff members this thread will remain closed, from the CoC, which is the forum rules:
> Material that suggests illegal activity or contains illegal content is also forbidden. We do not support circumventing TOS, EULA, etc here. 
Edit:
CoC located here:

[https://ubuntuforums.org/misc.php?do=showrules](https://ubuntuforums.org/misc.php?do=showrules)

---

