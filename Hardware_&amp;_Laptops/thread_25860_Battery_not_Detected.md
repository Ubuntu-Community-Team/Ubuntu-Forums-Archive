---
title: "Battery not Detected"
date: 2005-04-11
forum: Hardware &amp; Laptops
---

### Post by Yolteotl on 2005-04-11
Hi, I decided to try out Ubuntu since the new version (Hoary) just came out and I was getting bored of Fedora Core 3. I must say I must say I'm quite pleased, specially since it detected my wifi card during install, and set it up without a problem.

Anyway, my laptop is a Sony Vaio PCG-K23 and my problem is that Ubuntu doesn't detect my battery. Gnome's Battery-Monitor Applet is displaying the message "No battery present".  Which I find strange since in FC3 my battery got detected just fine.

I've also checked /proc/acpi and found that there is a /proc/acpi/battery/BAT1 folder, so my battery must get detected on some level, but when i do "cat /proc/acpi/battery/BAT1/state", it returns "present: no"

Is there a way to make Ubuntu detect my battery?

Thanks in advanced.

---

### Post by erkki70 on 2005-04-11
Hi,
Just ideas but try to pass this argument acpi=force on boot to the kernel to see if it solves the prob.
Also try to see if sonypi is loaded.

Hope this helps.
Cheers,
Erkki

---

### Post by luca_linux on 2005-04-11
There was a problem like yours on my laptop (Asus M6N) untill the latest bios that fixes it. Before I needed to patch the kernel or to use a custom DSDT.
Look at dmesg and let me know if you get some errors concerning "AML"...

---

### Post by Yolteotl on 2005-04-11
I had already tried acpi=on and acpi=force neither worked.

I checked to see if sonypi was loaded, and it wasn't. I tried to do "sudo modplug sonypi" and my PC just hanged completly. I then tried booting in Recovery Mode and I tried "modplug sonypi" and I got a Kernel Panic error :-? 

I also checked dmesg and there is nothing conerning "AML".

Any more suggestions?

---

### Post by erkki70 on 2005-04-11
Hi,
Have you tried to pass apm parameter on boot along with acpi?
```
acpi=on apm=on
```

Also found this [http://ubuntuforums.org/showthread.php?t=13264](http://ubuntuforums.org/showthread.php?t=13264) and might be of interest...

BTW, what kernel are you using?

Hope this helps...
Cheers,
Erkki

---

### Post by Yolteotl on 2005-04-11
I've just tried it, didn't work. 

I'm using the deafult kernel from the Hoary install CD, 2.6.10-5-386 .

I read the thread you linked too, I didn't find anything usefull since that guy's problem was that he didn't have an ACPI folder on "/proc" while I do have it.

Peace.

---

### Post by luca_linux on 2005-04-11
Are there any error in your dmesg? If yes, could you post them?
Try to pass the kernel parameter "nolapic" at boot.

---

### Post by Yolteotl on 2005-04-11
I tried passing "nolapic" on boot but it also didn't work.
But when I searched through dmesg and found this.
```
    ACPI-1138: *** Error: Method execution failed [\_SB_.BAT1.UPBS] (Node dbb2c2e0), AE_AML_OPERAND_TYPE
    ACPI-1138: *** Error: Method execution failed [\_SB_.BAT1.CHBP] (Node dbb2c260), AE_AML_OPERAND_TYPE
    ACPI-1138: *** Error: Method execution failed [\_SB_.PCI0.PIB_.EC0_._Q20] (Node dbb2f340), 
``` 
We may be on to something. [-o< 

I'm attatching the rest of my dmesg output, in case it's of any use.


EDIT:
I just noticed that I get different messages in dmesg, depending on if I boot up with the AC plug connected or not. The error I posted earlier, was when I booted without the AC plug. When I boot witht the AC plug, i get this on dmesg :

```
ACPI: Battery Slot [BAT1] (battery absent)
```

---

### Post by luca_linux on 2005-04-12
Try this patch: [http://m6n.ath.cx/aml_method_exec_hack.patch](http://m6n.ath.cx/aml_method_exec_hack.patch)

---

### Post by kuleali on 2005-04-12
thanks that workwed, luca_linix!

---

### Post by bnutting on 2005-04-12
This may sound stupid, but how do you use the above patch?
'patch -p0 <ThePatchFile' ?

I have an issue with my laptop lid and X not coming back.

Thanks

---

### Post by luca_linux on 2005-04-12
First of all that patch was written by Herman Sheremetyev, a friend of mine, in order to get battery status to work on Asus M6N(e) laptops; so no result is sure on other notebooks.
In order to patch the kernel sources, you have to type: "patch -p1 < file.patch".
Anyway it can just be applied by hand, since there are just three lines to edit in psparse.c.

bnutting, what laptop have you got? Are you just using X.org or some other drivers, such as fglrx, too?

---

### Post by NuSYS on 2005-04-28
hi, how can I recompile my kernel to apply this patch?My ubuntu came with no kernel source. I downloaded with synaptic linux-source-2-6-10 but when i recompile the kernel it gives me no hardware 3d acceleration (but with default kernel it works).
Any idea?

---

