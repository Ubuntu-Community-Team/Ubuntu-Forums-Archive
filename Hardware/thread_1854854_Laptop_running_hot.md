---
title: "Laptop running hot :/"
date: 2011-10-05
forum: Hardware
---

### Post by meatytaco on 2011-10-05
First I wanna say that I am relatively new to the whole linux deal as well as Ubuntu forums, I know enough to get around it but that's about it. I've recently installed Xubuntu on my older Sony Vaio laptop. I'm running the LXDE desktop environment. While idling it will get hot enough to burn my legs, causing me to have to find a pillow or something to set it on. I can't hear my fan working, but so far, my comp hasn't gotten hot enough to shut off. I've googled around looking to see if this would be normal. I apologize if this post is in the wrong section.  

So questions are:

1. Is my comp temp normal?
2. Is there a way short of hearing it that i can tell if my fan is working?
3. If not, how do I go about fixing it?

Kernel version: 2.6.38-11-generic

less /proc/cpuinfo
```
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 15
model name      : Intel(R) Core(TM)2 CPU         T5500  @ 1.66GHz
stepping        : 6
cpu MHz         : 1000.000
cache size      : 2048 KB
physical id     : 0
siblings        : 2
core id         : 0
cpu cores       : 2
apicid          : 0
initial apicid  : 0
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
/proc/cpuinfo 

```
sudo top
```
top - 04:43:23 up 28 min,  4 users,  load average: 0.01, 0.04, 0.06
Tasks: 127 total,   1 running, 126 sleeping,   0 stopped,   0 zombie
Cpu(s):  1.3%us,  1.3%sy,  0.5%ni, 95.2%id,  1.7%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   2050904k total,   618588k used,  1432316k free,    55144k buffers
Swap:  2085884k total,        0k used,  2085884k free,   323960k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 1130 root      20   0 65484  15m 9420 S    3  0.8   0:23.41 Xorg               
 1799 lobos     20   0 94988  13m  10m S    3  0.7   0:01.73 xfce4-terminal     
 1610 lobos     20   0  321m  59m  31m S    1  3.0   0:48.03 chromium-browse    
 2183 lobos     20   0  146m  34m  21m S    1  1.7   0:23.08 chromium-browse    
 2068 lobos     20   0  142m  29m  18m S    1  1.5   0:20.33 chromium-browse    
 2204 lobos     25   5  153m  41m  19m S    1  2.1   0:04.80 chromium-browse    
 2291 root      20   0  2632 1136  860 R    1  0.1   0:00.14 top                
 1634 lobos     25   5  142m  27m  16m S    0  1.4   0:06.05 chromium-browse    
 1637 lobos     25   5  181m  67m  18m S    0  3.4   0:24.54 chromium-browse    
    1 root      20   0  3048 1816 1252 S    0  0.1   0:00.59 init               
    2 root      20   0     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      20   0     0    0    0 S    0  0.0   0:00.05 ksoftirqd/0        
    5 root      20   0     0    0    0 S    0  0.0   0:00.44 kworker/u:0        
    6 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/0        
    7 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/1   
```

sudo sensors (while idle)
```
acpitz-virtual-0
Adapter: Virtual device
temp1:       +70.0°C  (crit = +105.0°C)                  
temp2:       +70.0°C  (crit = +105.0°C)                  

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +71.0°C  (high = +100.0°C, crit = +100.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +69.0°C  (high = +100.0°C, crit = +100.0°C)  


```

sudo sensors (while using around 70% of the CPU)
```
acpitz-virtual-0
Adapter: Virtual device
temp1:       +91.0°C  (crit = +105.0°C)                  
temp2:       +91.0°C  (crit = +105.0°C)                  

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +91.0°C  (high = +100.0°C, crit = +100.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +92.0°C  (high = +100.0°C, crit = +100.0°C)  


```

My apologies if the post is a little long, just wanted to include all the info that may be needed. Thank you everyone in advance for any help. :)

---

### Post by meatytaco on 2011-10-05
Note: the second sensors command was after about 1 min of CPU usage. Still couldn't hear the fan.

---

### Post by diasf on 2011-10-05
No, it's not normal. You need the fan.

And don't use a pillow under it. You are closing the vents under the laptop. Try a hard surface.

---

### Post by meatytaco on 2011-10-05
Sitting it on the table helped a bit. Down to 55 Celsius. I could get one of the cooling pads you set your laptop on, but that would seem to be in vain if my fan isn't spinning. Appreciate the suggestion though. :)

---

### Post by meatytaco on 2011-10-06
Still no fan, still runs hot. Gonna keep searching the net. I have found supposed ways to control the fan speed, but none of them seem to work. (or I'm doing something wrong, yeah probably that) as always, any suggestions are welcome. This has been an official bump. :)

---

### Post by Redblade20XX on 2011-10-06
Hey take a look at this:

[https://wiki.ubuntu.com/DebuggingACPI](https://wiki.ubuntu.com/DebuggingACPI)

Specifically, the debug section  about fan issues and report back with what you've seen. :D

- Red

---

### Post by meatytaco on 2011-10-06
Sweet, a lead. I will definitely check this out and report back. Just looking at it, my /proc/acpi has 
```
lobos@Taquito:~$ cd /proc/acpi/
ac_adapter/ battery/    button/     
lobos@Taquito:~$ cd /proc/acpi/

```

So I believe this may be the issue.

---

### Post by meatytaco on 2011-10-06
BIOS is up to date.

---

### Post by meatytaco on 2011-10-06
this was part of the output when i entered dmesg | grep ACPI
Don't honestly know if this has something to do with it, but i have a feeling it does. 

```
[    0.571846] ACPI: Invalid active0 threshold
[    0.572555] ACPI: Thermal Zone [TZ00] (77 C)
[    0.573497] ACPI: Invalid active0 threshold
[    0.574364] ACPI: Thermal Zone [TZ01] (77 C)

```

---

### Post by Redblade20XX on 2011-10-06
Hey can you run this command and post the output?

```
dmesg | grep -i acpi
```

Also can you burn or usb bootable a newer version of the buntu you have and run it in live mode to see if the fan turns on? I think it's a kernel problem and newer buntu's have newer kernels. Also see if you can use the previous acpi command in the live mode. :)
 
-Red

---

### Post by meatytaco on 2011-10-07
```
lobos@Taquito:~$ dmesg | grep -i acpi
[    0.000000]  BIOS-e820: 000000007f690000 - 000000007f69a000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007f69a000 - 000000007f700000 (ACPI NVS)
[    0.000000] ACPI: RSDP 000f7250 00014 (v00 PTLTD )
[    0.000000] ACPI: RSDT 7f6922f8 00054 (v01   Sony     VAIO 20070205 PTL  00000000)
[    0.000000] ACPI: FACP 7f699c9a 00084 (v02   Sony     VAIO 20070205 PTL  0000005A)
[    0.000000] ACPI: DSDT 7f69416d 05B2D (v01   Sony     VAIO 20070205 PTL  20050228)
[    0.000000] ACPI: FACS 7f69afc0 00040
[    0.000000] ACPI: APIC 7f699d1e 00068 (v01   Sony     VAIO 20070205 PTL  0000005A)
[    0.000000] ACPI: HPET 7f699d86 00038 (v01   Sony     VAIO 20070205 PTL  0000005A)
[    0.000000] ACPI: MCFG 7f699dbe 0003C (v01   Sony     VAIO 20070205 PTL  0000005A)
[    0.000000] ACPI: SLIC 7f699dfa 00176 (v01   Sony     VAIO 20070205 PTL  01000000)
[    0.000000] ACPI: APIC 7f699f70 00068 (v01   Sony     VAIO 20070205 PTL  00000000)
[    0.000000] ACPI: BOOT 7f699fd8 00028 (v01   Sony     VAIO 20070205 PTL  00000001)
[    0.000000] ACPI: SSDT 7f6939e1 0078C (v01   Sony     VAIO 20070205 PTL  20050228)
[    0.000000] ACPI: SSDT 7f693345 0069C (v01   Sony     VAIO 20070205 PTL  20050228)
[    0.000000] ACPI: SSDT 7f6928e2 0025F (v01   Sony     VAIO 20070205 PTL  20050228)
[    0.000000] ACPI: SSDT 7f69283c 000A6 (v01   Sony     VAIO 20070205 PTL  20050228)
[    0.000000] ACPI: SSDT 7f69234c 004F0 (v01   Sony     VAIO 20070205 PTL  20050228)
[    0.000000] ACPI: BIOS bug: multiple APIC/MADT found, using 0
[    0.000000] ACPI: If "acpi_apic_instance=2" works better, notify linux-acpi@vger.kernel.org
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-11-generic root=UUID=3bcaf3a3-64fa-4286-984b-698bcaa07153 ro quiet splash acpi_osi=Linux acpi=copy_dsdt vt.handoff=7
[    0.010769] ACPI: Core revision 20110112
[    0.010859] ACPI: Forced DSDT copy: length 0x05B2D copied locally, original unmapped
[    0.157784] ACPI: bus type pci registered
[    0.161023] ACPI: Added _OSI(Linux)
[    0.162884] ACPI: EC: Look up EC in DSDT
[    0.167313] ACPI: SSDT 7f693082 001FB (v01   Sony     VAIO 20070205 PTL  20050228)
[    0.167783] ACPI: Dynamic OEM Table Load:
[    0.167788] ACPI: SSDT   (null) 001FB (v01   Sony     VAIO 20070205 PTL  20050228)
[    0.168198] ACPI: SSDT 7f692b41 004BC (v01   Sony     VAIO 20070205 PTL  20050228)
[    0.168641] ACPI: Dynamic OEM Table Load:
[    0.168645] ACPI: SSDT   (null) 004BC (v01   Sony     VAIO 20070205 PTL  20050228)
[    0.168990] ACPI: SSDT 7f69327d 000C8 (v01   Sony     VAIO 20070205 PTL  20050228)
[    0.169447] ACPI: Dynamic OEM Table Load:
[    0.169451] ACPI: SSDT   (null) 000C8 (v01   Sony     VAIO 20070205 PTL  20050228)
[    0.169611] ACPI: SSDT 7f692ffd 00085 (v01   Sony     VAIO 20070205 PTL  20050228)
[    0.170055] ACPI: Dynamic OEM Table Load:
[    0.170059] ACPI: SSDT   (null) 00085 (v01   Sony     VAIO 20070205 PTL  20050228)
[    0.372134] ACPI: Interpreter enabled
[    0.372150] ACPI: (supports S0 S3 S4 S5)
[    0.372186] ACPI: Using IOAPIC for interrupt routing
[    0.388509] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
[    0.397509] ACPI: EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62
[    0.424442] ACPI: ACPI Dock Station Driver: 1 docks/bays found
[    0.424442] PCI: Ignoring host bridge windows from ACPI; if necessary, use "pci=use_crs" and report a bug
[    0.424788] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.429328] pci 0000:00:1f.0: quirk: [io  0x1000-0x107f] claimed by ICH6 ACPI/GPIO/TCO
[    0.431627] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.431893] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    0.431975] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    0.432067] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
[    0.432151] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT]
[    0.432266] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[    0.432574]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.440612] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 *7 10 12 14 15)
[    0.440688] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 *3 4 5 6 7 11 12 14 15)
[    0.440760] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    0.440846] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.440919] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    0.440991] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 *7 11 12 14 15)
[    0.441063] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 *4 5 6 7 10 12 14 15)
[    0.441134] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *5 6 7 11 12 14 15)
[    0.441984] PCI: Using ACPI for IRQ routing
[    0.459114] pnp: PnP ACPI init
[    0.459142] ACPI: bus type pnp registered
[    0.466125] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[    0.466281] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.466658] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.466737] pnp 00:03: Plug and Play ACPI device, IDs INT0800 (active)
[    0.466903] pnp 00:04: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.467001] pnp 00:05: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.467223] system 00:06: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.467312] pnp 00:07: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.467415] pnp 00:08: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.467505] pnp 00:09: Plug and Play ACPI device, IDs SNY9001 PNP0f13 (active)
[    0.467545] pnp: PnP ACPI: found 10 devices
[    0.467547] ACPI: ACPI bus type pnp unregistered
[    0.467553] PnPBIOS: Disabled by ACPI PNP
[    0.525380] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.526217] ACPI: AC Adapter [ADP1] (on-line)
[    0.526965] ACPI: Lid Switch [LID0]
[    0.552028] ACPI: Power Button [PWRB]
[    0.552413] ACPI: acpi_idle registered with cpuidle
[    0.567841] ACPI: Invalid active0 threshold
[    0.568784] ACPI: Thermal Zone [TZ00] (61 C)
[    0.569694] ACPI: Invalid active0 threshold
[    0.570649] ACPI: Thermal Zone [TZ01] (61 C)
[    0.580813] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.580823] ACPI: Battery Slot [BAT0] (battery absent)
[   23.996378] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
[   24.047162] acpi device:06: registered as cooling_device2
[   24.075196] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   24.688403] sony-laptop: brightness ignored, must be controlled by ACPI video driver
[ 7982.294210] e100 0000:0a:08.0: wake-up capability enabled by ACPI
[ 7982.517597] ACPI: Preparing to enter system sleep state S4
[ 7982.721366] ACPI: Waking up from system sleep state S4
[ 7983.267848] e100 0000:0a:08.0: wake-up capability disabled by ACPI
[ 7983.435518] ata3.00: ACPI cmd ef/03:0c:00:00:00:a0 (SET FEATURES) filtered out
[ 7983.435522] ata3.00: ACPI cmd ef/03:45:00:00:00:a0 (SET FEATURES) filtered out
[ 7983.435526] ata3.00: ACPI cmd ef/10:03:c0:00:00:a0 (SET FEATURES) filtered out
[ 7983.435531] ata3.00: ACPI cmd f5/00:00:c0:00:00:a0 (SECURITY FREEZE LOCK) filtered out
[ 7983.440444] ata1.00: ACPI cmd ef/03:0c:00:00:00:a0 (SET FEATURES) filtered out
[ 7983.440449] ata1.00: ACPI cmd ef/03:42:00:00:00:a0 (SET FEATURES) filtered out
[11286.881642] e100 0000:0a:08.0: wake-up capability enabled by ACPI
[11287.086203] ACPI: Preparing to enter system sleep state S4
[11287.293352] ACPI: Waking up from system sleep state S4
[11287.816271] e100 0000:0a:08.0: wake-up capability disabled by ACPI
[11287.983541] ata1.00: ACPI cmd ef/03:0c:00:00:00:a0 (SET FEATURES) filtered out
[11287.983545] ata1.00: ACPI cmd ef/03:42:00:00:00:a0 (SET FEATURES) filtered out
[11287.983736] ata3.00: ACPI cmd ef/03:0c:00:00:00:a0 (SET FEATURES) filtered out
[11287.983741] ata3.00: ACPI cmd ef/03:45:00:00:00:a0 (SET FEATURES) filtered out
[11287.983745] ata3.00: ACPI cmd ef/10:03:c0:00:00:a0 (SET FEATURES) filtered out
[11287.983750] ata3.00: ACPI cmd f5/00:00:c0:00:00:a0 (SECURITY FREEZE LOCK) filtered out
[26810.965914] e100 0000:0a:08.0: wake-up capability enabled by ACPI
[26811.086209] ACPI: Preparing to enter system sleep state S4
[26811.205356] ACPI: Waking up from system sleep state S4
[26811.739208] e100 0000:0a:08.0: wake-up capability disabled by ACPI
[26811.908457] ata1.00: ACPI cmd ef/03:0c:00:00:00:a0 (SET FEATURES) filtered out
[26811.908461] ata1.00: ACPI cmd ef/03:42:00:00:00:a0 (SET FEATURES) filtered out
[26811.908827] ata3.00: ACPI cmd ef/03:0c:00:00:00:a0 (SET FEATURES) filtered out
[26811.908832] ata3.00: ACPI cmd ef/03:45:00:00:00:a0 (SET FEATURES) filtered out
[26811.908836] ata3.00: ACPI cmd ef/10:03:c0:00:00:a0 (SET FEATURES) filtered out
[26811.908840] ata3.00: ACPI cmd f5/00:00:c0:00:00:a0 (SECURITY FREEZE LOCK) filtered out

```
I'll try to get a live version going tomorrow... any suggestions as to which?

---

### Post by 3177 on 2011-10-07
55C isnt running hot, Ive been running my laptop since 9 o clock and im reading 57C on my couch, and the bottom of my computer seems normal.

As for the fan issue, listen carefully when your computer boots, do you hear any noise?
If so your fans working fine. If not, afer reading all other posts, you have a defective fan.

---

### Post by meatytaco on 2011-10-07
yeah. 55C is idle though. i havent heard my fan yet.  i have gotten it up to 100C playing minecraft >.> pretty sure thats not supposed to happen lol

---

### Post by 3177 on 2011-10-07
did you try listening to your computer when it starts up?
If you hear ANYTHING, its your fan.

---

### Post by Redblade20XX on 2011-10-07
Give the 11.10 beta a try. Also if the live cd does nothing, see if windows can enable the fans. If windows can, take a look at this (might be a little intense, lol):

[http://cannibalcandy.wordpress.com/2011/02/18/dsdt-editing-put-an-end-to-your-acpi-woes/](http://cannibalcandy.wordpress.com/2011/02/18/dsdt-editing-put-an-end-to-your-acpi-woes/) :)

- Red

---

### Post by meatytaco on 2011-10-10
I appreciate all the help, and I'm gonna bookmark that site Red, but what i ended up doing is just re-installing. I don't know if I messed something up in the last install, but the fan is working now. O.o Again, thank you everyone for all the help :)

---

