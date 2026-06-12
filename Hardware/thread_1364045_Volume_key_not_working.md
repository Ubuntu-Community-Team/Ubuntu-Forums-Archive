---
title: "Volume key not working"
date: 2009-12-25
forum: Hardware
---

### Post by Leion on 2009-12-25
Hi, 

I have just upgraded my ubuntu from 8.10 to 9.10 in one go.
The new OS is great. the only thing is that the volume keys are not working. 
I am using IBM T43 notebook. The volume keys(volume up, volume down and mute) had always been working fine before I do the upgrade. 
I tried changing the keyboard layout but I am not able to get the volume keys to work. 

Anyone can help me on this?

---

### Post by labinnsw on 2009-12-26
"Keytouch" and "keytouch editor" is one way to fix this.
You can install them from "Synaptic"

To open them after installation go to System >> Preferences >> KeyTouch/KeyTouch Editor.

---

### Post by pabc on 2009-12-26
paste this into your terminal;

```
echo enable,0x00ffffff | sudo tee /proc/acpi/ibm/hotkey
```

it enabled the volume and mute keys on my T42. they worked out of the box on 9.10 but a subsequent update took them out. that line taken from a different thread on here worked

---

