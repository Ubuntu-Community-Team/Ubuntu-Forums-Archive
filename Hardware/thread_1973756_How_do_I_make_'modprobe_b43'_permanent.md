---
title: "How do I make 'modprobe b43' permanent?"
date: 2012-05-05
forum: Hardware
---

### Post by transistor on 2012-05-05
Ubuntu 12.04 on old Compaq Evo N610C. Buffalo G54 wifi card.

Every time I reboot I have to run 'sudo modprobe b43' to get the wireless going again. How do I get this to work automatically?

Many thanks.

---

### Post by prshah on 2012-05-05
> **transistor said:**
> Every time I reboot I have to run 'sudo modprobe b43' to get the wireless going again. How do I get this to work automatically?

You can add "b43" (no quotes) to your /etc/modules file.

To edit the file, open the run box/bar (Alt+F2) and give the command```
gksudo gedit /etc/modules
```

the comments in the /etc/modules file should be self-explanatory.

Leave a blank line at the end of the file.

---

### Post by transistor on 2012-05-05
That seems to work. 
Thank you very much.

---

