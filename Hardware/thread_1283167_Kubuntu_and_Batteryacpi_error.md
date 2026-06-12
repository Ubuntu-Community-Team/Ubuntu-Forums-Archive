---
title: "Kubuntu and Battery/acpi error"
date: 2009-10-05
forum: Hardware
---

### Post by saulo2 on 2009-10-05
Hello Guys

I have one question concerned to Kubuntu 9.04 and 9.10 beta (I have not tested olders); My laptop is an Intelbras i39(same model and hardware as Dell Vostro 1200), dual core, 1gb RAM, webcam, fingerprint a laptop with very common hardware; when Kubuntu was installed, it recognized everything (less the fingerprint); but my question is about acpi! when the system is loaded, "Battery monitor" shows my battery normally, if it is plugged in AC, it shows; if it is using battery, it shows its state; the problem is when I use the "Sleep - Suspend to RAM" function. The notebook sleeps very fast, but when it "wakes", acpi doesnt recognize it's battery anymore and "Battery monitor" says: No battery

In console before sleep:
cat /proc/acpi/battery/BAT0/state
capacity state: yes
charging state: ok
present rate: charged
remaining capacity: 4752 mWh
present voltage: 10800mV

In console AFTER sleep:
cat /proc/acpi/battery/BAT0/state
no battery present

It seems like an acpi error, not kde or battery application; in the other operating system sleeps works fine; does someone knows how to fix that?

---

### Post by saulo2 on 2009-10-07
Anyone??

---

### Post by Saljack on 2009-10-17
I have the same problem.

---

