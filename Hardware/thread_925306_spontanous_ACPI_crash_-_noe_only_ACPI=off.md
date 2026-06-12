---
title: "spontanous ACPI crash - noe only ACPI=off"
date: 2008-09-20
forum: Hardware
---

### Post by bloblu on 2008-09-20
Hi,
I have got a big problem with my laptop. It was running without problems from 6.10 to now. Then, after not using it a month, installig a lot of updates, it hangs during boot. The last message is about:
ACPI ... ... dsdt.aml not found
Then nothing happens, I have the press power button. So i checked around and found out, that I can still boot with ACPI=off boot-option. But using that is not really fun, there's a lot of stuff not working so that's no solution. Note that Live-CDs, even old ones, which were working doesn'T boot.
Then I tried to build my own DSDT.aml using ASL compiler from Intel and acpidump to read out the DSDT table. I could fix the single error by deleting a "*" (error 4001), copied the DSDT.aml into /etc/initramfs-tools/DSDT.aml. And now the boot hangs after two more messages. 
Damn I cannot remember, I will check later, but it seems like Ubuntu doesn't want to use my DSDT.aml. 

So it's really curious. ACPI was always working. Maybe a hardware porblem?I dont know. The laptop is an ACER Aspire 9300, which should actuelly work well after some WIKIs. 

I need help,
thx

---

### Post by bloblu on 2008-09-21
noone any idea?

---

### Post by bloblu on 2008-09-22
really noone?, damn, I cannot work...

---

### Post by theirishfozz on 2008-10-03
Hi

Try and follow the instructions on posting acpi problems here:

[https://wiki.ubuntu.com/DebuggingACPI](https://wiki.ubuntu.com/DebuggingACPI)

You could start by creating new boot entries for each of those acpi options listed and try each one out, see if any work.

Good luck!

---

