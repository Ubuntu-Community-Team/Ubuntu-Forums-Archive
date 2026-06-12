---
title: "UNR Post-install update: webcam vanishes"
date: 2009-11-14
forum: Hardware
---

### Post by myonta on 2009-11-14
Alright, just used WUBI to install UNR 9.10 on my LG X110 (MSI Wind clone). So far, not too bad. I like the remix. Could get used to it. However...

Well, the built in webcam (1.3MP) was working just fine initially. I added the mediabuntu repo and installed Skype as well as updated the system (*sudo apt-get update*).

Anyway, somewhere between all that and restarting the system the webcam has vanished as far as Ubuntu is concerned. 

Now, I'm pretty darn sure it's on the USB bus so here's my *lsusb* output:
```
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 5986:0203 Acer, Inc 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

Pretty sure it's the Acer device, but I'm not too savvy with hardware in Linux. Not to mention, I still have no idea what's wrong...

So, be sure to let me know if this is handled elsewhere. Also, I'll post the synaptic update log if you like or the *lsusb -v* output or whatever if requested/needed. Let me know. Lack of webcam is kind of a biggie for a netbook (even if the one in my non-smart-phone is better quality).

~Jon

---

