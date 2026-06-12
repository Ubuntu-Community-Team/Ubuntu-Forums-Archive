---
title: "System Settings | System Services crashes"
date: 2005-11-17
forum: General Help
---

### Post by kalahari875 on 2005-11-17
About half the time I click the System Services icon under System Settings, it crashes and sends me to the KDE crash handler. Any ideas?

---

### Post by mlomker on 2005-11-17
Launch it from a command line the next few times.  If it crashes you might get some error information in the terminal.  **sudo systemsettings**

---

### Post by kalahari875 on 2005-11-18
Of course, I can't get it to crash now. Oh well; if it reoccurs I will reply again.

---

### Post by abandoned_hussam on 2005-11-18
you should probably launch it using kdesu and not sudo.
I got this crash the first time I ran it but it's a but more stable now.

---

### Post by TheTeZ on 2007-12-11
i had the problem with it crashing.... and searched and found this thread... this is what i get when i run the command... any help anyone?

tom@toms-lappy:~$ kdesu systemsettings
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kbuildsycoca running...
kio (KSycoca): WARNING: Found version 93, expecting version 94 or higher.
kio (KSycoca): WARNING: Found version 93, expecting version 94 or higher.
KCrash: Application 'systemsettings' crashing...
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
tom@toms-lappy:~$

---

