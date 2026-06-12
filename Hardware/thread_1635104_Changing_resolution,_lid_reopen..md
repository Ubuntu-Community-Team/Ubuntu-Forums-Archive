---
title: "Changing resolution, lid reopen."
date: 2010-12-01
forum: Hardware
---

### Post by 1Michael1 on 2010-12-01
Hello, so I've had this problem for quite a while now.
Whenever I shut off my laptop, it's on the regular settings 1366x768, all good. But whenever I boot up the laptop, the resolution is changed, it's either blurry or just wrong resolution. So to fix it, I've to close lid and then open again a couple of times and changing back the resolution in monitor settings a few times till it finally works.

This is alright if it happens once or twice, but having to work with this 1-2 minutes whenever I reboot the laptop is frustrating, so if someone has a fix for this or whatever, it'd be highly appreciated.

I run 10.04 LTS 64bit.

Thanks a lot,
Michael.

---

### Post by meijer.o on 2010-12-01
Dear linux user,

I have the same problem and found a solution (not very easy). Please post the output of lspci

Best regards,

otto

---

### Post by 1Michael1 on 2010-12-02
Alright here is the output of lspci

```
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation ICH9M/M-E 2 port SATA IDE Controller (rev 03)
00:1f.5 IDE interface: Intel Corporation ICH9M/M-E 2 port SATA IDE Controller (rev 03)
02:00.0 Network controller: Intel Corporation PRO/Wireless 5100 AGN [Shiloh] Network Connection
85:00.0 Ethernet controller: Marvell Technology Group Ltd. Device 436c (rev 10)
```

---

### Post by meijer.o on 2010-12-02
Dear linux user,

This bug is very likely the same one that bothers me and can be fixed

fix 1 
(try this first) Install a kernel 2.6.31 (ubuntu 9.10). This will very likely fix your bug. just download it here: [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.31.13-karmic](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.31.13-karmic)


fix 2 (patch and recompile kernel)
Patch kernel 2.6.35 or 2.6.36 with the patch form here: [https://bugzilla.kernel.org/show_bug.cgi?id=16236](https://bugzilla.kernel.org/show_bug.cgi?id=16236) (last attachment from list)

Don't worry if you do not know how to do this, reply or send me a personal note.

Please let me know your results.

Best regards,

Otto Meijer

---

### Post by antony_css on 2011-01-12
It happens on my HP Probook 4410s.

I don't think the patch works on Lucid anymore.

Do you have any workarounds for this problem?

BTW, I found some so called "X Quirks" to workaround intel chipset hardware bugs, are they related to resolution problem?

[https://wiki.ubuntu.com/X/Quirks#Ignore%20TV%20Output%20Quirk](https://wiki.ubuntu.com/X/Quirks#Ignore%20TV%20Output%20Quirk)

---

### Post by antony_css on 2011-01-12
It happens on my HP Probook 4410s.

I don't think the patch works on Lucid anymore.

Do you have any workarounds for this problem?

BTW, I found some so called "X Quirks" to workaround intel chipset hardware bugs, are they related to resolution problem?

[https://wiki.ubuntu.com/X/Quirks#Ignore%20TV%20Output%20Quirk](https://wiki.ubuntu.com/X/Quirks#Ignore%20TV%20Output%20Quirk)

---

### Post by meijer.o on 2011-01-12
Dear antony_css,

I have a HP 4510s with probably almost the same hardware. The solution I mentioned in post no. 4 should work for you. I think it is related to [https://wiki.ubuntu.com/X/Quirks#Ign...Output%20Quirk](https://wiki.ubuntu.com/X/Quirks#Ign...Output%20Quirk) but this solution does not work anymore.

Please file a bug so it can be fixed. If you know how to compile a kernel, try the kernel patch of post no 4. against e.g. kernel 2.6.36.2.

Best regards,

Otto Meijer

---

