---
title: "How do I know if all possible sensors are configured?"
date: 2011-09-25
forum: Hardware
---

### Post by diasf on 2011-09-25
Hi,

HP touchsmart tx2 1050ef, running an RM74 turion processor, kernel 2.6.38-11-generic-phc #50~phc0-Ubuntu x64. Output of lspci:
(only the not  irrelevant bits)

```

00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780/RS880 PCI to PCI bridge (int gfx)
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:14.3 ISA bridge: ATI Technologies Inc SB7x0/SB8x0/SB9x0 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor HyperTransport Configuration (rev 40)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor Link Control

```Output of sensors```

acpitz-virtual-0
Adapter: Virtual device
temp1:       +72.0°C                                    

k10temp-pci-00c3
Adapter: PCI adapter
temp1:       +63.9°C  (high = +70.0°C)   
```Now, my question is: This laptop doesn't have sensors available for fans and stuff or they are not configured? More important, imo, how do I discover the difference (that is, how do I know that I have unconfigured sensors?)


Thanks

---

### Post by tgalati4 on 2011-09-26
On my thinkpad t43p:

tgalati4@tpad-Gloria7 ~ $ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:       +47.0°C  (crit = +99.0°C)                  

thinkpad-isa-0000
Adapter: ISA adapter
fan1:       4745 RPM
temp1:       +47.0°C                                    
temp2:       +47.0°C                                    
temp3:       +37.0°C                                    
temp4:       +55.0°C                                    
temp5:       +33.0°C                                    
ERROR: Can't get value of subfeature temp6_input: Can't read
temp6:        +0.0°C                                    
temp7:       +26.0°C                                    
ERROR: Can't get value of subfeature temp8_input: Can't read
temp8:        +0.0°C                                    
temp9:       +44.0°C                                    
temp10:      +53.0°C                                    
temp11:      +46.0°C                                    
ERROR: Can't get value of subfeature temp12_input: Can't read
temp12:       +0.0°C                                    
ERROR: Can't get value of subfeature temp13_input: Can't read
temp13:       +0.0°C                                    
ERROR: Can't get value of subfeature temp14_input: Can't read
temp14:       +0.0°C                                    
ERROR: Can't get value of subfeature temp15_input: Can't read
temp15:       +0.0°C                                    
ERROR: Can't get value of subfeature temp16_input: Can't read
temp16:       +0.0°C

Thinkpads are well-documented, including locations of all of the sensors.  Perhaps asking on an HP hardware forum how many sensors and where they are located.

Also, check the BIOS, sometimes there are sensors listed there.  You should be able to read all of the sensors that show up in BIOS, provided there are drivers written for the lm-sensors package.

---

### Post by diasf on 2011-09-26
So... no readings on BIOS.... booted up on windows, find a program called speedfan....

I got 3 readings from fans, all 0. My guess is that they did not bother connecting the sensors do the smbus..

---

### Post by .... on 2011-09-26
Yeah, mobo manufacturers tend to take shortcuts like that. SPCR is a good site for finding out what boards support PWM control on the fan headers.

---

