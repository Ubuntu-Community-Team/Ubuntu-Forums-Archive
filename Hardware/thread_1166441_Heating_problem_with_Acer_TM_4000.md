---
title: "Heating problem with Acer TM 4000"
date: 2009-05-21
forum: Hardware
---

### Post by hewart on 2009-05-21
Hi everyone

I've just installed Ubuntu 9.04 and I find it smart and very fast. The performance has really improved since 7.10, the other version I tried on this laptop. It's a 1.6GHz Centrino Dothan cpu (monocore), with 512Mb ram amd ati 9800 with 64Mb. 
The only problem I encountered is the excessive heat. The temperature easily goes high and the fan turns on many times. My cpu is scaled and runs by default at 600Mhz, like the Xubuntu 7.10 I had before, which didn't have this problem.
I tried disabling special effects, but the problem persists. What can I do?
Thanks in advance!

---

### Post by 67GTA on 2009-05-21
You might look at your DSDT file. I wrote a how to here: [http://ubuntuforums.org/showthread.php?t=1036051](http://ubuntuforums.org/showthread.php?t=1036051) This seems to affect a lot of newer laptops. If this is too scary, just follow the first two commands, and send me the dsdt.dat file. I will be happy to take a look.

---

### Post by hewart on 2009-05-22
Hi again

I'm reading about it, and trying to find out how to solve it. Anyway, as I tend to screw things up by modifying these archives, I'd aprecciate your help very much.
There are only 3 warnings according to iasl.

Thank you :D

---

### Post by 67GTA on 2009-05-22
ignore

---

### Post by 67GTA on 2009-05-22
I got the warnings fixed. The iasl compiler also made 776 optimizations to the original. I saw a couple of optimizations were done to the thermal area of the ACPI tables. Hopefully it will help with your heat problem. The zip package has your fixed dsdt.dsl, and your dsdt.aml. The dsdt.aml is the one you need. Follow my how to to implement it. You can just copy and paste the commands, so not much to screw up. Be sure to add ```
acpi_osi="Linux"
``` to /boot/grub/menu.lst per the how to. Once you are done, and reboot, send me a copy of ```
sudo dmesg
``` from a terminal. You will need to tell the Gnome terminal to use more memory to catch all of the dmesg output. Open a terminal, click "Edit" and "Profile Preferences". Click on the "Scrolling" tab. Then change 512 to something like 3000. Then run dmesg.

[ATTACH]114661[/ATTACH]

---

### Post by hewart on 2009-05-22
Thank you!

I've done it. I can't try it now, just had time to type the command.
Anyway tomorrow I'll chech if the problem has gone.

---

### Post by 67GTA on 2009-05-22
Have you checked your BIOS settings? It might control some of this. Some things that stand out in your dmesg output:

Local APIC disabled by BIOS -- you can enable it with "lapic"

HPET not enabled in BIOS. You might try hpet=force boot option

fan PNP0C0B:00: registered as cooling_device0
ACPI: Fan [FAN0] (off)
 fan PNP0C0B:01: registered as cooling_device1
 ACPI: Fan [FAN1] (off)
 processor ACPI_CPU:00: registered as cooling_device2
 thermal LNXTHERM:01: registered as thermal_zone0
 ACPI: Thermal Zone [THRM] (58 C)

Your BIOS may actually be controlling your fans and not letting Ubuntu control them. If the problem persists, you might want to see if you can change your BIOS settings to let go of the fan control.

---

### Post by hewart on 2009-05-22
These lines are all about fans, right? 
That's true, I've never been able to control them manually. BIOS gives me no choice #-o
Anyway, the first speed starts at 60ºC, which is a reasonable temperature. It goes faster if the temp. is about 65-70 degrees. 
Well, I think these settings are right, but I'll do what you advise me ;)

The main question is about the heat it creates. Even with similar CPU usages to windows, it goes much hotter.

---

### Post by 67GTA on 2009-05-22
The temp looked ok, but if Ubuntu is trying to monitor your temp/fans, and only the BIOS controls the fans, there might be a conflict. It would be better if one or the other controlled both. If your BIOS doesn't give you the option, then you might want to try turning off acpi so Ubuntu doesn't try controlling this to see if it is any better. If the custom DSDT doesn't work, then undo what we did, and try adding some of these boot options to /boot/grub/menu.lst (one at a time) and reboot to see if it helps. To remove the DSDT, delete it from /etc/initramfs-tools, and rerun the update-initramfs command and delete the grub entry we added.


```

[LIST]
[*]Try booting with the "acpi=off" kernel parameter 
[LIST]
[*]This will disable ACPI support.  If the error is the same with acpi enabled and disabled, this may not be an ACPI issue. 
[/LIST]
[*]If "acpi=off" allows the system to boot, try to isolate the ACPI issue with the following boot parameters 
[LIST]
[*]Try booting with "acpi=ht" 
[LIST]
[*]This disables all of ACPI except just enough to enable Hyper Threading. If acpi=off works and acpi=ht fails, then the issue is in the ACPI table parsing code itself, or perhaps the SMP code. 
[/LIST]
[*]Try booting with "pci=noacpi" 
[LIST]
[*]This disables ACPI for IRQ routing and PCI scanning. 
[/LIST]
[*]Try booting with "acpi=noirq" 
[LIST]
[*]This disables ACPI for IRQ routing.  
[/LIST]
[*]Try booting with "pnpacpi=off" 
[LIST]
[*]This disables the ACPI component of the Linux Plug and Play code.  
[/LIST]
[*]Try booting with "noapic" 
[LIST]
[*]Disables the IO-APIC for IRQ routing or PCI scanning.  
[/LIST]
[*]Try booting with "nolapic" 
[LIST]
[*]Disables the local APIC
[/LIST]
[/LIST]
[/LIST]

```

---

### Post by hewart on 2009-05-22
Hi

I did it all with the modified dsdt. All the parameters have let me boot, but acpi=off (acpi=ht too, I think) have disabled my wireless connection.

---

### Post by 67GTA on 2009-05-22
Did any of the boot arguments fix the heat issue?

---

### Post by hewart on 2009-05-23
I didn't notice so. They seemed similar, and some deactivated cpu scaling or wifi connection. :(

Do you think an update will solve this problem?
Or perhaps the thing is about ext4?

---

### Post by 67GTA on 2009-05-23
Ext4 is just the filesystem type. It won't affect this. If there is an acpi update available, I would try it. You might want to file a bug on launchpad about your model and it overheating. Also, a stupid question, but have you checked to see if the fan exhaust is clean? Have you tried blowing air into it to see if it is clogged?

---

### Post by hewart on 2009-05-23
I cleaned the fan recently, checked it and works ok. What I'm looking for is a cool laptop, with the fan always off. That's possible with windows: even going to youtube, using java... the processor might be below 60ºC and the fan wouldn't start. In ubuntu, things like listening to music heat up the system and it's a bit disturbing for my hands and noisy.

Indeed, I've found this happening to many other people, and even worse. Laptops power off and things like that. I hope that it'll be fixed soon ;)

---

