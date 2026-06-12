---
title: "Wierd IPW2200 dmesg error"
date: 2005-11-14
forum: Hardware &amp; Laptops
---

### Post by Delvien on 2005-11-14
[4299885.795000] ipw2200: Firmware error detected.  Restarting.
[4300026.110000] ipw2200: Firmware error detected.  Restarting.
[4300362.645000] ipw2200: Firmware error detected.  Restarting.
[4300375.248000] ipw2200: Firmware error detected.  Restarting.
[4300379.352000] ipw2200: Firmware error detected.  Restarting.
[4300397.251000] ipw2200: Firmware error detected.  Restarting.
[4300528.445000] ipw2200: Firmware error detected.  Restarting.
[4300543.526000] ipw2200: Firmware error detected.  Restarting.
[4300686.274000] ipw2200: Firmware error detected.  Restarting.
[4300761.140000] ipw2200: Firmware error detected.  Restarting.
[4300836.838000] ipw2200: Firmware error detected.  Restarting.
[4301003.557000] ipw2200: Firmware error detected.  Restarting.


Anyone know how to fix this or get rid of ipw2200 since my wifi works, but ipw2200 doesnt.

---

### Post by Delvien on 2005-11-15
bump

---

### Post by maher on 2005-11-16
Try adding: 
options ipw2200 hwcrypto=0

in /etc/modprobe.conf/ipw2200

(create it if necessary)

---

### Post by Delvien on 2005-11-16
[QUOTE=maher]Try adding: 
options ipw2200 hwcrypto=0

in /etc/modprobe.conf/ipw2200

(create it if necessary)[/QUOTE]


Says i cannot write the file... and ran it as sudo etc..  doesnt bother me, just annoying when checking dmesg

---

### Post by ispiked on 2005-11-16
[QUOTE=Delvien]Says i cannot write the file... and ran it as sudo etc..  doesnt bother me, just annoying when checking dmesg[/QUOTE]
```

sudo gedit /etc/modprobe.d/ipw2200

```
Add that line to it and save it. It should work...

---

### Post by Delvien on 2005-11-16
didnt work , still getting error. sudo kedit /et/modprobe.d/ipw2200 made a new file...

So i put the code in , saved it, and tried sudo dmesg -c. did it again, still came up with the error. Tried sudo modprobe ipw2200 too and still have the error

---

### Post by Delvien on 2005-11-16
Update Got it fixed. thanks all , had to do a different modprobe -r and some other stuff.

---

