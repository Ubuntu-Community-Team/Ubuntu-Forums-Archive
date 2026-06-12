---
title: "ohci1394 causing flood of &quot;APIC error on CPU0: 40(40)&quot;"
date: 2006-10-30
forum: Hardware &amp; Laptops
---

### Post by Cosmic_Crusader on 2006-10-30
I have an Acer Ferrari 4005 laptop and since installing it has been flooding dmesg with:
  "APIC error on CPU0: 40(40)"
messages.

I have just narrowed it down to the ohci1394 module (which appears to be firewire related).  The messages immediately stop when I remove this module (ie: "modprobe -r ohci1394").

I've tried blacklisting this module but can't find a way to prevent it from loading (and therefore prevent these errors on startup).

I have added comments to a bug raised ([https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/66900](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/66900)) but since I don't currently use firewire I'd prefer to know how to turn it off on bootup (without resorting to rc.local).

Does anyone know of this issue, and perhaps a way of preventing this module form loading?

(now if I could just get my BCM4318 wireless working!)  :-|

---

### Post by seanUSXIII on 2006-11-16
try :

```
sudo echo "blacklist ohci1394" >> /etc/modprobe.d/blacklist
```

This will add the line blacklist ohci1394 to the file "blacklist" and will prevent this module from being loaded. I had this same problem for a while too. I just applied this change. I'll repost as to whether it helped.

---

### Post by syounkim on 2007-07-06
I added ohci1394 to blacklist. I can see it in the blacklist. But it is still loaded. Can you tell me what I have done possibly wrong?

---

