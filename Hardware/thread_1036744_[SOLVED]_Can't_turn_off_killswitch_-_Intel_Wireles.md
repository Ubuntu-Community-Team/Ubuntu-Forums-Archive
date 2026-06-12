---
title: "[SOLVED] Can't turn off killswitch - Intel Wireless 3945ABG"
date: 2009-01-11
forum: Hardware
---

### Post by smihaylov on 2009-01-11
Hi,

I have an issue on my Fujitsu Siemens Amilo Pro Laptop.

I can't turn off HW Kill Switch. The card is Intel Wireless 3945ABG. 
It's currently on:
```
iwl3945 0000:04:00.0: Radio disabled by HW RF Kill switch

```

When i press Fn+F10 (the way to turn on the Wireless) it says:
```
Jan 11 13:01:09 leti-laptop kernel: [  529.247614] atkbd.c: Unknown key pressed (translated set 2, code 0xd6 on isa0060/serio0).
Jan 11 13:01:09 leti-laptop kernel: [  529.247629] atkbd.c: Use 'setkeycodes e056 <keycode>' to make it known.

```

I tried to do:
```
#cat /sys/class/rfkill/rfkill0/state 
2
#echo 0 > /sys/class/rfkill/rfkill0/state
#cat /sys/class/rfkill/rfkill0/state 
2

```

Any ideas how to turn that kill switch off?

Thanks a lot!

---

### Post by smihaylov on 2009-01-11
I forgot to mention that I'm using Ubuntu 8.10 with 2.6.27 kernel.

```
# uname -a
Linux leti-laptop 2.6.27-11-generic #1 SMP Thu Jan 8 08:38:33 UTC 2009 i686 GNU/Linux

```

---

### Post by HunterThomson on 2009-01-11
It is a problem with your ESDT or DSDT. They are files in your BIOS that are loaded into RAM at boot and the ACPI kernel module talks to it to know how to handle the hardware.

The ACPI standers were made by a group of corps. Intel and MS were among them. In the end Intel made a compiler and MS made one. Internal documents that were presented to the Supreme Court of the USA, in which Bill gates was saying how they should pervert the code so ACPI only work under Windows. They supreme court found MS guilty of this unfair business practices as well of many others.

MS's compiler is not standers compliant and it is not open source so only MS knows how it is messed up. Most computer makers use the MS compiler. So, in then end a whole bunch of widows only computers flood the market. My laptop had a problem in the DSDT that cosed the back-light to be dim on boot and messed up in general. We fixed it on our thread and now it works.

[http://ubuntuforums.org/showthread.php?t=870681](http://ubuntuforums.org/showthread.php?t=870681)

You can start fixing the problem by recompiling the DSDT and stuff with the intel open source standers compliant compiler. It will through errors at you and you have to fix them. Then if the problem persists you have to fix the code. It is a hard task.

Just to make it clear This is a deliberate act of MS to mess up your computer. 

Kill Bill

---

### Post by smihaylov on 2009-01-11
Problem solved with **fsam7400** module:

```
# modprobe fsam7400
# rmmod -r iwl3945
# modprobe iwl3945
```

Thanks for Your attention!

---

### Post by HunterThomson on 2009-01-11
Hay cool my bad.... 

but still

Kill Bill

---

### Post by super100 on 2009-02-03
it also works for me on GATEWAY notebook M505/Intel pro2200 by doing the following:

**sudo modprobe fsam7400 radio=1**


my question is how to make it permanent after root? I tried this but got the error of [COLOR="Red"]Permission denied[/COLOR]...

[B]sudo echo fsam7400 >> /etc/modules

sudo echo options fsam7400 radio=1 >> /etc/modprob.d/options[/B]

---

### Post by thiruvan on 2010-01-06
> **super100 said:**
> it also works for me on GATEWAY notebook M505/Intel pro2200 by doing the following:

**sudo modprobe fsam7400 radio=1**


my question is how to make it permanent after root? I tried this but got the error of [COLOR="Red"]Permission denied[/COLOR]...

[B]sudo echo fsam7400 >> /etc/modules

sudo echo options fsam7400 radio=1 >> /etc/modprob.d/options[/B]



hi could u plz tell me how to turn on permanently

---

