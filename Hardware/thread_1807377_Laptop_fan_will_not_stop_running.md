---
title: "Laptop fan will not stop running"
date: 2011-07-19
forum: Hardware
---

### Post by MrSlaggers on 2011-07-19
I purchased a new HP Pavilion dv6 laptop today, and I installed Ubuntu on it. For whatever reason, the fan runs non-stop even when it doesn't need to. Can someone please help me fix this issue?

---

### Post by whatthefunk on 2011-07-19
Theres a lot of info about this out there.

[http://ubuntuforums.org/showthread.php?t=42737](http://ubuntuforums.org/showthread.php?t=42737)

---

### Post by MrSlaggers on 2011-07-19
> **whatthefunk said:**
> Theres a lot of info about this out there.

[http://ubuntuforums.org/showthread.php?t=42737](http://ubuntuforums.org/showthread.php?t=42737)


That thread is from 2005. Would it still work?

---

### Post by daison3 on 2011-07-19
try this, this might work...

make your cursor on top, and right click the PANEL, and click "add to panel"

after that, an application will prompt to you, and add the "CPU frequency monitor" after that, close the prompted application, and click the ICON, maybe if you have a 2.5GHz then it will show to you like 2500Mhz is used to your system, you can adjust it to lower value..

also check if your place is too hot for your computer, laptop computer needs atleast lower than 30Degrees Celsius.

Update also your OS using the Update Manager or using the terminal "sudo apt-get update && sudo apt-get upgrade".

you can also use a debugging mode, try to install a Win7 to your system, and check if that OS will support it.

also check the "System Monitor", check it if there's an application that eating a lot of RAM to your Computer.




List the specification of your Computer.

---

### Post by MrSlaggers on 2011-07-19
> **daison3 said:**
> try this, this might work...

make your cursor on top, and right click the PANEL, and click "add to panel"

after that, an application will prompt to you, and add the "CPU frequency monitor" after that, close the prompted application, and click the ICON, maybe if you have a 2.5GHz then it will show to you like 2500Mhz is used to your system, you can adjust it to lower value..

also check if your place is too hot for your computer, laptop computer needs atleast lower than 30Degrees Celsius.

Update also your OS using the Update Manager or using the terminal "sudo apt-get update && sudo apt-get upgrade".

you can also use a debugging mode, try to install a Win7 to your system, and check if that OS will support it.

also check the "System Monitor", check it if there's an application that eating a lot of RAM to your Computer.




List the specification of your Computer.

Unfortunately the fan seems to stay on regardless of how much the CPU is being used. The laptop is not hot, and there's pretty much no reason for the fan to be running. The laptop came with Windows 7 on it, and while I ran that I did not have this issue. Here are the specs:

AMD Phenom II Quad Core 1.8 GHz processor
8 GB RAM
640 GB HDD

---

### Post by mikewhatever on 2011-07-20
Not sure this is going to help, but can you post the outputs of the following from your Ubuntu installation:
```
uname -a

dmesg | grep ACPI
```

---

### Post by MrSlaggers on 2011-07-20
> **mikewhatever said:**
> Not sure this is going to help, but can you post the outputs of the following from your Ubuntu installation:
```
uname -a

dmesg | grep ACPI
```


```

Linux mike-laptop 2.6.38-10-generic #46-Ubuntu SMP Tue Jun 28 15:07:17 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
``````

[    0.000000]  BIOS-e820: 00000000de4b7000 - 00000000de6b7000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000dfdbf000 - 00000000dfebf000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000dfebf000 - 00000000dfef6000 (ACPI data)
[    0.000000] ACPI: RSDP 00000000000fe020 00024 (v02 HPQOEM)
[    0.000000] ACPI: XSDT 00000000dfef5120 0005C (v01 HPQOEM SLIC-MPC 00000001      01000013)
[    0.000000] ACPI: FACP 00000000dfef4000 000F4 (v04 HPQOEM SLIC-MPC 00000003 MSFT 01000013)
[    0.000000] ACPI: DSDT 00000000dfee3000 0DE26 (v01 HP     INSYDE   F0000000 MSFT 01000013)
[    0.000000] ACPI: FACS 00000000dfe97000 00040
[    0.000000] ACPI: HPET 00000000dfef3000 00038 (v01 HP     INSYDE   00000001 MSFT 01000013)
[    0.000000] ACPI: APIC 00000000dfef2000 00084 (v02 HP     INSYDE   00000001 MSFT 01000013)
[    0.000000] ACPI: MCFG 00000000dfef1000 0003C (v01 HP     INSYDE   00000001 MSFT 01000013)
[    0.000000] ACPI: BOOT 00000000dfee2000 00028 (v01 HP     INSYDE   00000001 MSFT 01000013)
[    0.000000] ACPI: SLIC 00000000dfee1000 00176 (v01 HPQOEM SLIC-MPC 00000001 MSFT 01000013)
[    0.000000] ACPI: SSDT 00000000dfee0000 0088C (v01 HP     INSYDE   00000001 AMD  00000001)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x1002a201 base: 0xfed00000
[    0.018106] ACPI: Core revision 20110112
[    0.651504] ACPI: bus type pci registered
[    0.654744] ACPI: EC: Look up EC in DSDT
[    0.661057] ACPI: Executed 1 blocks of module-level executable AML code
[    0.665956] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.670119] ACPI: Interpreter enabled
[    0.670126] ACPI: (supports S0 S3 S4 S5)
[    0.670168] ACPI: Using IOAPIC for interrupt routing
[    0.780748] ACPI: EC: GPE = 0x3, I/O: command/status = 0x66, data = 0x62
[    0.780980] ACPI: No dock devices found.
[    0.780987] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.840690] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.940240] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.940487] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[    0.940539] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB4_._PRT]
[    0.940591] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB5_._PRT]
[    0.940639] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB6_._PRT]
[    0.940736] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[    0.940944]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.941244]  pci0000:00: ACPI _OSC control (0x19) granted
[    0.947755] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 10 11 12 14 15) *0
[    0.947822] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 10 11 12 14 15) *0
[    0.947891] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 10 11 12 14 15) *0
[    0.947959] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 10 11 12 14 15) *0
[    0.948013] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 10 11 12 14 15) *0
[    0.948055] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 10 11 12 14 15) *0
[    0.948098] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 10 11 12 14 15) *0
[    0.948140] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 10 11 12 14 15) *0
[    0.950297] PCI: Using ACPI for IRQ routing
[    0.968350] pnp: PnP ACPI init
[    0.968371] ACPI: bus type pnp registered
[    0.969023] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[    0.969339] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.969339] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.969339] pnp 00:03: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.969339] pnp 00:04: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.969339] pnp 00:05: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.969339] pnp 00:06: Plug and Play ACPI device, IDs SYN1e46 PNP0f13 (active)
[    0.969339] system 00:07: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.969339] system 00:08: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.970286] pnp 00:09: Plug and Play ACPI device, IDs HPQ0004 (active)
[    0.970298] pnp: PnP ACPI: found 10 devices
[    0.970300] ACPI: ACPI bus type pnp unregistered
[    1.138840] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    1.140205] ACPI: AC Adapter [AC] (on-line)
[    1.140375] ACPI: Power Button [PWRB]
[    1.143436] ACPI: Lid Switch [LID]
[    1.143535] ACPI: Power Button [PWRF]
[    1.143733] ACPI: acpi_idle registered with cpuidle
[    1.143828] ACPI: processor limited to max C-state 1
[    1.157163] ACPI Warning: For \_TZ_.THRM._AL0: Return Package has no elements (empty) (20110112/nspredef-456)
[    1.157173] ACPI: [Package] has zero elements (ffff8801fd98aa00)
[    1.157176] ACPI: Invalid active0 threshold
[    1.167763] ACPI: Thermal Zone [THRM] (40 C)
[    1.202167] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    1.202177] ACPI: Battery Slot [BAT0] (battery present)
[   13.948479] ACPI: resource piix4_smbus [io  0x0b00-0x0b07] conflicts with ACPI region SMB0 [io 0xb00-0xb0f]
[   13.948484] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   14.122917] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[ 2026.630213] ACPI handle has no context!
[ 2027.590147] pcieport 0000:00:04.0: wake-up capability enabled by ACPI
[ 2027.670307] ACPI: Preparing to enter system sleep state S3
[ 2028.992416] ACPI: Waking up from system sleep state S3
[ 2029.161870] pcieport 0000:00:04.0: wake-up capability disabled by ACPI
[ 2770.612570] ACPI handle has no context!
[ 2771.680141] pcieport 0000:00:04.0: wake-up capability enabled by ACPI
[ 2771.760330] ACPI: Preparing to enter system sleep state S3
[ 2772.952445] ACPI: Waking up from system sleep state S3
[ 2773.100637] pcieport 0000:00:04.0: wake-up capability disabled by ACPI

```

---

### Post by mikewhatever on 2011-07-21
How about trying the **acpi_osi=Linux** boot option?

You have the following message in dmesg:
```
[    0.665956] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
```
According to Google, it's harmless, but it's at least something to try.

---

### Post by MrSlaggers on 2011-07-21
> **mikewhatever said:**
> How about trying the **acpi_osi=Linux** boot option?

You have the following message in dmesg:
```
[    0.665956] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
```According to Google, it's harmless, but it's at least something to try.

The fan hasn't been running all the time anymore, but it seems to turn on and off randomly. I actually just saw this suggestion in another thread and am trying it out now. I'll let you know how it goes.

---

### Post by mikewhatever on 2011-07-21
So, it fixed itself?

---

### Post by linux_tech on 2011-07-21
The fan turns on whenthe cpu reaches a certain temp. 
To ensure its turning on at the right time you may want to monitor the cpu temp.  There are a variety of desktop cpu utils that you can also choose when it turns on or off.  Keeping the cpu cool enough is the main objective of course. For example the i8kmon daemon, [http://manpages.ubuntu.com/manpages/hardy/man1/i8kmon.1.html](http://manpages.ubuntu.com/manpages/hardy/man1/i8kmon.1.html).  You can also install the sensors applet for a display
```
sudo apt-get install sensors-applet
sudo sensors-detect

```

---

### Post by MrSlaggers on 2011-07-21
> **mikewhatever said:**
> So, it fixed itself?

In a way. It is no longer on all the time like it used to be, however it still turns on randomly without stopping until I do something like put the computer to sleep for a while. I tried adding the  **acpi_osi=Linux **but I'm still getting that behavior. [This post]("http://ubuntuforums.org/showpost.php?p=8318825&postcount=41") from a while back says to add slashes, so that is what I am trying now. I'll let you know if the fan comes on when it shouldn't.

_**Edit: **_Unfortunately the slashes don't seem to have worked either. The fan came on randomly again and will not shut off on its own.

> **linux_tech said:**
> The fan turns on whenthe cpu reaches a certain temp. 
To ensure its turning on at the right time you may want to monitor the  cpu temp.  There are a variety of desktop cpu utils that you can also  choose when it turns on or off.  Keeping the cpu cool enough is the main  objective of course. For example the i8kmon daemon, [http://manpages.ubuntu.com/manpages/hardy/man1/i8kmon.1.html](http://manpages.ubuntu.com/manpages/hardy/man1/i8kmon.1.html).  You can also install the sensors applet for a display
```
sudo apt-get install sensors-applet
sudo sensors-detect

```

Yeah I already have sensors setup. The fan seems to come on regardless of the temperature it shows, and even when it cools down, the fan continues to run.

---

### Post by MrSlaggers on 2011-07-22
It actually seems to be working now, however, I would like to adjust the temperature points at which it turns on and off. Can anyone help me getting fancontrol working properly?

---

### Post by mikewhatever on 2011-07-23
Try the **sudo pwmconfig** command.

---

### Post by MrSlaggers on 2011-07-23
> **mikewhatever said:**
> Try the **sudo pwmconfig** command.

I get this error:

```
# pwmconfig revision 5857 (2010-08-22)
This program will search your sensors for pulse width modulation (pwm)
controls, and test each one to see if it controls a fan on
your motherboard. Note that many motherboards do not have pwm
circuitry installed, even if your sensor chip supports pwm.

We will attempt to briefly stop each fan using the pwm controls.
The program will attempt to restore each fan to full speed
after testing. However, it is ** very important ** that you
physically verify that the fans have been to full speed
after the program has completed.

/usr/sbin/pwmconfig: There are no pwm-capable sensor modules installed

```

I ran **sudo sensors-detect **beforehand, but it still doesn't work.

---

### Post by mikewhatever on 2011-07-23
Well, as I told you before, no fan sensors are detected.

---

### Post by MrSlaggers on 2011-07-24
> **mikewhatever said:**
> Well, as I told you before, no fan sensors are detected.

So is there any way to detect them?

---

### Post by 3602 on 2011-07-25
I'm running an HP dv7-4101ca. Unless your BIOS isn't Insyde, the following *should *apply.

[LIST]
[*]In the BIOS, there is an option, Fan Always On. If you don't want the constant fan, change it to Disabled.
[*]The HP dv7 has serious design issues. The shell cannot dissipate heat effectively. Even with Fan Always On at Enabled, I get constant 43°C reported. My dv7 has Turion II P540 and HD4250M. If you ever touched a running Envy 17 with i7-940M and HD6970M, the shell is burning hot. What does that mean? Having Fan Always On is actually *beneficial*. However I cannot speak for the dv6 as it is somewhat smaller.
[*]The whole ACPI thing doesn't work well in Linux. A key problem is having the fan come on at a certain point. It plainly doesn't. With Fan Always On at Disabled, the temperatures reported are at 55°C *right after a boot* and at higher temps, the fan *doesn't come on*. Even if the Fan Always On is Enabled, the fan turns at a constant, low speed regardless of the temperature.
[/LIST]
All this to say, setting the fan to Off might lead you to constant overheating.

---

### Post by MrSlaggers on 2011-07-26
> **3602 said:**
> I'm running an HP dv7-4101ca. Unless your BIOS isn't Insyde, the following *should *apply.

[LIST]
[*]In the BIOS, there is an option, Fan Always On. If you don't want the constant fan, change it to Disabled.
[*]The HP dv7 has serious design issues. The shell cannot dissipate heat effectively. Even with Fan Always On at Enabled, I get constant 43°C reported. My dv7 has Turion II P540 and HD4250M. If you ever touched a running Envy 17 with i7-940M and HD6970M, the shell is burning hot. What does that mean? Having Fan Always On is actually *beneficial*. However I cannot speak for the dv6 as it is somewhat smaller.
[*]The whole ACPI thing doesn't work well in Linux. A key problem is having the fan come on at a certain point. It plainly doesn't. With Fan Always On at Disabled, the temperatures reported are at 55°C *right after a boot* and at higher temps, the fan *doesn't come on*. Even if the Fan Always On is Enabled, the fan turns at a constant, low speed regardless of the temperature.
[/LIST]
All this to say, setting the fan to Off might lead you to constant overheating.

Yeah, I found that setting early on and disabled it, and at first it didn't seem to work, but now it looks like it might have. The fan is no longer constantly running, however, it's still on a lot of the time, and that's something I want to adjust.

I've noticed that the fan seems to come on around 50-53C, and that it doesn't turn back off until it gets to around 43C. Unfortunately, the system gets to 50-53C quite easily, and the fan is seldom able to cool it down to 43C. What I am hoping to do now is just make it so the fan will turn on and off at higher temperatures, like on at 55C and off at 47C.

---

### Post by rickytikki on 2011-07-26
> **MrSlaggers said:**
> Yeah, I found that setting early on and disabled it, and at first it didn't seem to work, but now it looks like it might have. The fan is no longer constantly running, however, it's still on a lot of the time, and that's something I want to adjust.

I've noticed that the fan seems to come on around 50-53C, and that it doesn't turn back off until it gets to around 43C. Unfortunately, the system gets to 50-53C quite easily, and the fan is seldom able to cool it down to 43C. What I am hoping to do now is just make it so the fan will turn on and off at higher temperatures, like on at 55C and off at 47C.

the fans run in the bios partition as a program the only way to get it to switch on and off or to switch at what temp it comes on at is to hack the Bios. trust me you dont want to hack you system bios if you dont know what u are doing or know how to read code.

---

### Post by 3602 on 2011-07-26
If you hack the BIOS, you might b0rk the BIOS. You b0rk the BIOS, your computer don't boot. In laptops, unless you can source a new BIOS chip and are very good at precision manual soldering, heh...

---

### Post by MrSlaggers on 2011-07-26
> **rickytikki said:**
> the fans run in the bios partition as a program the only way to get it to switch on and off or to switch at what temp it comes on at is to hack the Bios. trust me you dont want to hack you system bios if you dont know what u are doing or know how to read code.

I've seen threads that discuss and show how to manipulate fan speeds based off of temperatures with programs like powersaved and fancontrol.

---

### Post by 3602 on 2011-07-26
No. Unless the dv6 has a different structure, the dv7 has no speed-controlling modules. Neither fancontrol in Linux nor Speedfan in Windows can detect anything.

---

### Post by MrSlaggers on 2011-07-26
> **3602 said:**
> No. Unless the dv6 has a different structure, the dv7 has no speed-controlling modules. Neither fancontrol in Linux nor Speedfan in Windows can detect anything.

Ah, I see. That's unfortunate. Well thank you for your help.

---

### Post by MrSlaggers on 2011-08-11
I came across this website ([http://notebookequus.blogspot.com/2008/09/patching-dsdt-table.html](http://notebookequus.blogspot.com/2008/09/patching-dsdt-table.html)) which describes how to fix the issue in Windows Vista, but I am not sure how I would go about doing this in Ubuntu. It worked for a user with dv5 in this thread: [http://h30434.www3.hp.com/t5/Notebook-Hardware/Pavilion-1150-em-Fan-Noise/m-p/25553/message-uid/25553/highlight/true#U25553](http://h30434.www3.hp.com/t5/Notebook-Hardware/Pavilion-1150-em-Fan-Noise/m-p/25553/message-uid/25553/highlight/true#U25553)

It looks like I need to modify certain parts of a dsdt.aml file, however I cannot find this file on my system.

---

### Post by 3602 on 2011-08-11
Hacking the DSDT table is highly not recommended unless you really know whatcha doing.

---

### Post by MrSlaggers on 2012-01-30
I dual boot with Windows 7 now and the fan only runs when needed and turns off when it's not needed. Because the fan is able to work correctly in Windows, I'm sure there must be some way to get it to turn off in Ubuntu. If someone could help me resolve this issue I would be very grateful.

---

### Post by MrSlaggers on 2012-02-02
Bump

---

### Post by MrSlaggers on 2012-02-03
Bump. If I try editing the DSDT table in Windows ([http://notebookequus.blogspot.com/2008/09/patching-dsdt-table.html](http://notebookequus.blogspot.com/2008/09/patching-dsdt-table.html)), would the changes I make there affect the fan in Ubuntu?

---

### Post by MrSlaggers on 2012-02-04
bump

---

### Post by xyzzyman on 2012-02-04
To use an updated dsdt file in Linux you will have to compile it into the kernel. I do it with my Acer Aspire 6930G. If you mess up you can always just boot into your previous kernel.

---

### Post by MrSlaggers on 2012-02-05
> **xyzzyman said:**
> To use an updated dsdt file in Linux you will have to compile it into the kernel. I do it with my Acer Aspire 6930G. If you mess up you can always just boot into your previous kernel.

Do you think modifying it like this will work for what I'm trying to do? Also, do you have a tutorial on how I can go about doing it?

---

### Post by xyzzyman on 2012-02-05
I don't know. dv6's and dv7's are very wide model series with hundreds of different laptops. within each series they came with amd and intel CPU's, ati and nvidia and intel graphics. So unless knowing if it's actually a DSDT issue on that specific model there's no way for me to know. To find tutorials on how to modify DSDT you're going to want to look into hackintosh, as that's where most data on modifying DSDT's is geared towards.

---

### Post by sambuev on 2012-02-07
I have an opposite question: I have Backtrack 5 on Toshiba and I need to run my fans for 100% all the time with no stop. 
Do you know how to set them to be on all the time?
Thank you! :P

---

