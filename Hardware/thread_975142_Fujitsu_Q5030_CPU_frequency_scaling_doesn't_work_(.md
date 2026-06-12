---
title: "Fujitsu Q5030: CPU frequency scaling doesn't work (ICH9M platform)"
date: 2008-11-08
forum: Hardware
---

### Post by TheCan on 2008-11-08
Hello,

unfortunately it seems the CPU frequency scaling is not working with Ubuntu 8.10 (x86_64 version) on my Fujitsu Esprimo Q5030 machine (If I looked this up correctly, it should be i45GMt-HD AOpen Mainboard with Intel GM45/GM47, Intel ICH9-M chipset). I am getting this at startup:

```
Setting up powernowd (1.00-1ubuntu2) ...                                        
 * Starting powernowd...                                                         * CPU frequency scaling not supported...                                [ OK ] 
```

Which is propably caused due to this output from /proc/acpi/processor/CPU0/info:
```
processor id:            0
acpi id:                 0
bus mastering control:   yes
power management:        no
throttling control:      no
limit interface:         no
```

Here are some details about the platform (CPU is an Intel Core2Duo P8400):

```
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)                                                                   
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:19.0 Ethernet controller: Intel Corporation 82567LF Gigabit Network Connection (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
02:00.0 Network controller: Atheros Communications Inc. AR928X Wireless NetworkAdapter (PCI-Express) (rev 01)
```

Any useful suggestions how to get this working are highly appreciated.

---

### Post by unit3 on 2008-11-10
Yep, this is a known issue on amd64 ([https://bugs.launchpad.net/ubuntu/+source/linux/+bug/246434](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/246434)). There hasn't really been much response from the Ubuntu devs as to why this is an issue.

If you want to see some traction on this, it'd be good to subscribe to the bug, mark yourself as being affected, and add a "me too" comment. Hopefully that'll help bring it to the devs' attention.

---

### Post by TheCan on 2008-11-10
thanks for the reply - but this is not the real issue, on i386 speedstepping is broken as well due to a faulty BIOS :(

---

### Post by TheCan on 2008-11-19
Update: I tried to do investigate the issue a bit more. As it seems, the EIST feature (needed for frequency scaling to work) is deactivated in the BIOS of the machine. Unfortunately, there is no way to activate this feature.

Although the machine comes from Fujitsu, it seems that it uses the MP-45D or MP-45DR platform from AOpen (Specs: [http://www.aopen.de/products_spec.asp](http://www.aopen.de/products_spec.asp)). Except the branding and some minor details, the case of this MP-45DR model looks exactly the same as the one in the Fujitsu model.

AOpen seems to provide various new BIOS versions for this board, including an updated Fan controller profile and I really expect the option to activate EIST to be there as well. Unfortunately, Fujitsu seems to hold back the fixed BIOS versions away from their customers :( I really hope, they will provide this soon.

The interesting mystery here is, how come that Frequency Scaling is (at least partly) working in Windows? There the CPU scales down from 2,26 GHz to 1,80 GHz - although I believe with properly enabled EIST it should be possible to scale down the CPU much much more - according to this post ([http://article.gmane.org/gmane.linux.debian.devel.bugs.general/494475](http://article.gmane.org/gmane.linux.debian.devel.bugs.general/494475)) down to 800MHz.

I found an interesting posting in one of those crazy overclocker-forums which points out, that it is possible to deactivate EIST writing directly into MSR registers. So it should work the other way round as well. It seems, those registers are CPU-specific, so maybe it is possible to find the right values in Intel's Specs for this processor. Here's the link to the related thread:

[http://www.xtremesystems.org/forums/showthread.php?t=104811](http://www.xtremesystems.org/forums/showthread.php?t=104811)

Does anybody know if these MSRs are initially read on bootup time from the ACPI DSDT/SSDT tables?

---

### Post by xrat on 2009-02-07
Hi TheCan,

Any news since your last update?
The FSC Esprimo Q5030 is giving Linux users a hard time :(
There was a BIOS update in December, version R1.06TFS, but apparently, it did not help with CPU frequency scaling :/
-- xrat

---

### Post by xrat on 2009-04-26
In the meantime I have upgraded to Ubuntu 9.04 Jaunty (without any problems), but I stil get the warning message "CPU Frequency Scaling Unsupported" :(

```
Linux Ubuntu 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686 GNU/Linux
```
```

root@Ubuntu:~# cpufreq-info
cpufrequtils 004: cpufreq-info (C) Dominik Brodowski 2004-2006
Report errors and bugs to cpufreq@lists.linux.org.uk, please.
analyzing CPU 0:
  no or unknown cpufreq driver is active on this CPU
analyzing CPU 1:
  no or unknown cpufreq driver is active on this CPU
```

---

### Post by TheCan on 2009-04-26
Hi,

no unfortunately no good news I would be aware of. I haven't upgraded yet to 9.04, but it seems it won't help with this issue anyways. Actually the problem is that Fujitsu (not -Siemens meanwhile) does not incorporate the latest BIOS version from the Vendor (AOpen) which possibly could fix this issue.

So please feel free to contact Fujitsu and open up a support issue. I didn't have time for this yet. The interesting thing here is, that the Scaling does not work in Windows either - there you can choose between 1600 und 2260MHz, but the full downclocking to 800MHz is also broken, so no need to accept a "unsupported configuration" answer from Fujitsu.

---

### Post by xrat on 2009-04-27
Thanks TheCan,
I simply forgot that it's probably a BIOS issue (BTW, thanks for all your investigations in this regard). I own only 1 Q5030 which I am running with Ubuntu only. I guess it's better if someone with a working Windows installation is reporting to Fujitsu/FSC.
-- xrat

---

