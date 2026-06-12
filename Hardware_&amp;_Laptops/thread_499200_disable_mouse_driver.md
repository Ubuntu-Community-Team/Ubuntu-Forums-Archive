---
title: "disable mouse driver"
date: 2007-07-12
forum: Hardware &amp; Laptops
---

### Post by alanandhispc on 2007-07-12
hi,

Until my touch pad is correctly recognised as a synaptics touchpad: 
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/123775]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/123775")

how can i disable the touchpad, as it's driving me nuts? 

I: Bus=0011 Vendor=0002 Product=0005 Version=0063
N: Name="ImPS/2 Logitech Wheel Mouse"
P: Phys=isa0060/serio2/input0
S: Sysfs=/class/input/input4
H: Handlers=mouse2 event4 ts2
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=103

this is the bit dmesg outputs for this device based on the hardware manager details for this "mouse":
serio: i8042 AUX1 port at 0x60,0x64 irq 12

what can i do to get this recognised as a touchpad? as "sudo tpconfig -i" does know it's there, i believe its the kernel not picking it up properly.


Thank you,

Alan


Thanks,

---

### Post by EXCiD3 on 2007-07-12
Is there no button on your laptop to turn it off? 

Here is the section for my touchpad in /etc/X11/xorg.conf:
```
Section "InputDevice"
    Identifier     "Synaptics Touchpad"
    Driver         "synaptics"
    Option         "SendCoreEvents" "true"
    Option         "Device" "/dev/psaux"
    Option         "Protocol" "auto-dev"
    Option         "HorizScrollDelta" "0"
EndSection

```

I also don't know if you downloaded the Synaptic Touchpad configuration tool from the repositiories would help or not.

---

### Post by alanandhispc on 2007-07-13
as i said in my first post, the touchpad is not correctly recognised as a touchpad, so i can not do anything like this.

The touchpad is detected as "ImPS/2 Logitech Wheel Mouse" , so until it is correctly recognised in the kernel, i want to disable it...there is no bios option for it.


Please read my post fully, i do appreciate your help though.

any takers?

Thanks

Alan

---

### Post by EXCiD3 on 2007-07-14
Sorry, i was kinda busy when i was reading that. Um, i really don't have a clue other than, is there a button on the touchpad to turn it off? mine has a button right above it to shut it off.

---

### Post by alanandhispc on 2007-07-19
when the touchpad is detected as a touchpad, which it isn't yet, i will be able to program the shortcut key to use the synaptics application to disable it.

but as said, it's not detected as a touchpad, so until it is, is there anyway i can just stop it from working in ubuntu. there is no option in the bios for this?


Thanks

Alan

---

