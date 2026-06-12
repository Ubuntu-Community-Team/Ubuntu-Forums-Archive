---
title: "[SOLVED] Kubuntu Sound not working"
date: 2008-09-02
forum: Hardware
---

### Post by ice2921 on 2008-09-02
Kubuntu Sound not working
After a fresh install of Kubuntu I noticed that I did not have any sound. I have checked the parameters of the alsamixer as well as the kmix settings all settings are raised, and none muted. I have tried both settings with the external amplifier both on and off but to no avail. I have also restarted alsa as well each time. I am assuming that my drivers are properly installed because I have outputs from aplay as well as lspci that appear to show drivers installed.However I may be looking at the wrong output. I am using Ubuntu 8.04.1, and my sound card is as follows :

Code:

00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (IC
H6 Family) AC'97 Audio Controller (rev 04)
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, medium devsel, latency 0, IRQ 10
        I/O ports at e100 [size=256]
        I/O ports at e200 [size=64]
        Memory at d0180000 (32-bit, non-prefetchable) [size=512]
        Memory at d0180200 (32-bit, non-prefetchable) [size=256]

Any help as always is appreciated thanks.

---

### Post by ajgreeny on 2008-09-02
Do you have an onboard card as well as a pci card?  If so, you may need to disable the onboard one in your BIOS.

---

### Post by ice2921 on 2008-09-02
I do not have an pci card. I am sure that I have just one card. I have been searching everywhere for help with this. I am beginning to lose hope:(

---

### Post by ice2921 on 2008-09-09
I have booted with the irpoll option and sound is working.

---

