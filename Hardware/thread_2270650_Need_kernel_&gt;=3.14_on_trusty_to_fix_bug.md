---
title: "Need kernel &gt;=3.14 on trusty to fix bug"
date: 2015-03-24
forum: Hardware
---

### Post by jcllings on 2015-03-24
Neither my wifi nor my bluetooth works due to a bug that is fixed as of 3.14.  

I could "roll my own" or I could wait. Been waiting for a while now. Are there any other options I've not covered?

---

### Post by ajgreeny on 2015-03-24
You can install the 3.16 series of kernels from the repositories.  Install **linux-generic-lts-utopic** in software centre or synaptic and it will pull in the 3.16 kernel plus the hrader packages and keep them updated automatically.

---

### Post by jeremy31 on 2015-03-24
> **jcllings said:**
> Neither my wifi nor my bluetooth works due to a bug that is fixed as of 3.14.  

I could "roll my own" or I could wait. Been waiting for a while now. Are there any other options I've not covered?

Do you have a link to a bug report or a patch?

---

### Post by mastablasta on 2015-03-25
if you go with the new kernel you should also look at this article: [https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

it explains the policies and procedures.

---

### Post by jcllings on 2015-04-10
Got 3.13.0-49-generic today. 

Well now my WiFi works but it looks like my bluetooth doesn't. Specific problem is that it won't connect.  When I first installed it, I did see one of my headsets get added but then it quickly disappeared. 

Print out from dmesg:

```
10.017164] init: bluetooth-touch main process (577) terminated with status 127
[   10.036241] init: avahi-cups-reload main process (614) terminated with status 1
[   10.040039] Bluetooth: Core ver 2.17
[   10.040051] NET: Registered protocol family 31
[   10.040052] Bluetooth: HCI device and connection manager initialized
[   10.040057] Bluetooth: HCI socket layer initialized
[   10.040058] Bluetooth: L2CAP socket layer initialized
[   10.040061] Bluetooth: SCO socket layer initialized
[   10.044610] Bluetooth: RFCOMM TTY layer initialized
[   10.044617] Bluetooth: RFCOMM socket layer initialized
[   10.044621] Bluetooth: RFCOMM ver 1.11
[   10.045815] wmi: Mapper loaded
[   10.047178] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   10.049788] mei_me 0000:00:16.0: irq 54 for MSI/MSI-X
[   10.049914] type=1400 audit(1428683552.920:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=592 comm="apparmor_parser"
[   10.049918] type=1400 audit(1428683552.920:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/cupsd" pid=592 comm="apparmor_parser"
[   10.050135] type=1400 audit(1428683552.920:4): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=592 comm="apparmor_parser"
[   10.057146] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   10.057148] Bluetooth: BNEP filters: protocol multicast
[   10.057154] Bluetooth: BNEP socket layer initialized
```

---

### Post by jeremy31 on 2015-04-10
Can you post the results of ```
lsusb; hciconfig -a; dmesg | grep firmware; dmesg | grep -i bluetooth
```

---

