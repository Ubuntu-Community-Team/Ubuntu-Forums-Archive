---
title: "Problem with USB Keyboard and waking up system"
date: 2010-10-18
forum: Hardware
---

### Post by MaTrIcKs133 on 2010-10-18
Hi all! 
I am new to this forum and general new to Linux.
I was able to get my USB Keyboard waking up my old laptop with ```
echo "USBx">/proc/acpi/wakeup
```Worked fine without any problems.

Now I have a new Laptop, an Acer Aspire 1830T with a new i5 processor. And now I cant get it to work.

cat /proc/acpi/wakeup shows following things:
```

Device    S-state      Status   Sysfs node
P0P2      S4     disabled  
PEGP      S4     disabled  
P0P1      S0     disabled  pci:0000:00:1e.0
EHC1      S4     disabled  pci:0000:00:1d.0
USB1      S4     enabled   
USB2      S4     enabled   
USB3      S4     enabled   
USB4      S4     enabled   
EHC2      S4     disabled  pci:0000:00:1a.0
USB5      S4     enabled   
USB6      S4     enabled   
USB7      S4     enabled   
HDEF      S0     disabled  pci:0000:00:1b.0
RP01      S5     disabled  pci:0000:00:1c.0
PXSX      S5     disabled  pci:0000:01:00.0
RP02      S0     disabled  pci:0000:00:1c.1
PXSX      S5     disabled  pci:0000:02:00.0
RP03      S0     disabled  
PXSX      S5     disabled  
RP04      S0     disabled  
PXSX      S5     disabled  
RP05      S0     disabled  
PXSX      S5     disabled  
RP07      S0     disabled  
PXSX      S5     disabled  
RP08      S0     disabled  
PXSX      S5     disabled  
GLAN      S0     disabled  
PEG3      S4     disabled  
PEG5      S4     disabled  
PEG6      S4     disabled  
SLPB      S3    *enabled   
LID0      S3    *enabled  

```First thing I notice is that the USB ports are "S4" states , and not "S3" as with my old Laptop.

lspci shows that the "EHC1" and "EHC2" are the Controllers:
```

-+-[0000:ff]-+-00.0  Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers
 |           +-00.1  Intel Corporation Core Processor QuickPath Architecture System Address Decoder
 |           +-02.0  Intel Corporation Core Processor QPI Link 0
 |           +-02.1  Intel Corporation Core Processor QPI Physical 0
 |           +-02.2  Intel Corporation Core Processor Reserved
 |           \-02.3  Intel Corporation Core Processor Reserved
 \-[0000:00]-+-00.0  Intel Corporation Core Processor DRAM Controller
             +-02.0  Intel Corporation Core Processor Integrated Graphics Controller
             +-16.0  Intel Corporation 5 Series/3400 Series Chipset HECI Controller
             +-1a.0  Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller
             +-1b.0  Intel Corporation 5 Series/3400 Series Chipset High Definition Audio
             +-1c.0-[0000:01]----00.0  Atheros Communications AR8151 v1.0 Gigabit Ethernet
             +-1c.1-[0000:02]----00.0  Broadcom Corporation Device 4357
             +-1d.0  Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller
             +-1e.0-[0000:03]--
             +-1f.0  Intel Corporation Mobile 5 Series Chipset LPC Interface Controller
             +-1f.2  Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller
             +-1f.3  Intel Corporation 5 Series/3400 Series Chipset SMBus Controller
             \-1f.6  Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem

```So for example if I go into suspend mode, my mouse laser turns on when I press a mouse button, so it has power in S3 mode, but the Laptop wont wake up.
When I now enable all USBx ports it doesnt work either.
When I now enable the "EHCx" usb controller the laptop just comes out of suspend/hibernate instantly.

My question is now if the "S4" states includes the "S3" states and if not, how can I switch them to "S3"?
And if its not the case, how can I get the USB Keyboard to work? The Keyboard from the Laptop works just fine to wake the Laptop out of suspend mode :/

Greetings,
Arne

---

### Post by MaTrIcKs133 on 2010-10-22
No one knows an answer?
I am also confused why all the USB ports dont have a hardware ID.  
But it must be possible to wake the notebook in S3 mode, because the mouse has energy in S3. 
[http://forums.opensuse.org/english/get-help-here/hardware/446432-11-3-no-s3-proc-acpi-wakeup.html](http://forums.opensuse.org/english/get-help-here/hardware/446432-11-3-no-s3-proc-acpi-wakeup.html)

I found this link, but it couldnt help me either :/

Maybe someone has an idea how to solve this problem.

---

