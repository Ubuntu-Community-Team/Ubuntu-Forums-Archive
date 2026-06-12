---
title: "amd64 nforce4 939 lm-sensors"
date: 2005-05-04
forum: Hardware &amp; Laptops
---

### Post by flanker on 2005-05-04
Just wondering if anyone has had success with lm-sensors on a nforce4 mobo.

I tried to install it on hoary with my gigabyte nforce4 amd64 939 board without success.

I've tried running sensors-detect after loading the i2c-nforce2 module but if didnt make any difference.

cheers, Ian.


```
ian@amd64:~$ sensors
Can't access procfs/sysfs file
Unable to find i2c bus information;
For 2.6 kernels, make sure you have mounted sysfs and done
'modprobe i2c_sensor'!
For older kernels, make sure you have done 'modprobe i2c-proc'!
ian@amd64:~$ lsmod | grep i2c
ian@amd64:~$ sudo sensors-detect
Password:

This program will help you determine which I2C/SMBus modules you need to
load to use lm_sensors most effectively. You need to have i2c and
lm_sensors installed before running this program.
Also, you need to be `root', or at least have access to the /dev/i2c-*
files, for most things.
If you have patched your kernel and have some drivers built in, you can
safely answer NO if asked to load some modules. In this case, things may
seem a bit confusing, but they will still work.

It is generally safe and recommended to accept the default answers to all
questions, unless you know what you're doing.

 We can start with probing for (PCI) I2C or SMBus adapters.
 You do not need any special privileges for this.
 Do you want to probe now? (YES/no): yes
Probing for PCI bus adapters...
Sorry, no PCI bus adapters found.

We will now try to load each adapter module in turn.
If you have undetectable or unsupported adapters, you can have them
scanned by manually loading the modules before running this script.

 To continue, we need module `i2c-dev' to be loaded.
 If it is built-in into your kernel, you can safely skip this.
 i2c-dev is not loaded. Do you want to load it now? (YES/no): yes
 Module loaded succesfully.

 We are now going to do the adapter probings. Some adapters may hang halfway
 through; we can't really help that. Also, some chips will be double detected;
 we choose the one with the highest confidence value in that case.
 If you found that the adapter hung after probing a certain address, you can
 specify that address to remain unprobed. That often
 includes address 0x69 (clock chip).

Some chips are also accessible through the ISA bus. ISA probes are
typically a bit more dangerous, as we have to write to I/O ports to do
this. This is usually safe though.

Do you want to scan the ISA bus? (YES/no): yes
Probing for `National Semiconductor LM78'
  Trying address 0x0290... Failed!
Probing for `National Semiconductor LM78-J'
  Trying address 0x0290... Failed!
Probing for `National Semiconductor LM79'
  Trying address 0x0290... Failed!
Probing for `Winbond W83781D'
  Trying address 0x0290... Failed!
Probing for `Winbond W83782D'
  Trying address 0x0290... Failed!
Probing for `Winbond W83627HF'
  Trying address 0x0290... Failed!
Probing for `Winbond W83697HF'
  Trying address 0x0290... Failed!
Probing for `Silicon Integrated Systems SIS5595'
  Trying general detect... Failed!
Probing for `VIA Technologies VT82C686 Integrated Sensors'
  Trying general detect... Failed!
Probing for `VIA Technologies VT8231 Integrated Sensors'
  Trying general detect... Failed!
Probing for `ITE IT8705F / IT8712F / SiS 950'
  Trying address 0x0290... Failed!
Probing for `IPMI BMC KCS'
  Trying address 0x0ca0... Failed!
Probing for `IPMI BMC SMIC'
  Trying address 0x0ca8... Failed!

Some Super I/O chips may also contain sensors. Super I/O probes are
typically a bit more dangerous, as we have to write to I/O ports to do
this. This is usually safe though.

Do you want to scan for Super I/O sensors? (YES/no): yes
Probing for `ITE 8702F Super IO Sensors'
  Failed! (0x8712)
Probing for `ITE 8705F Super IO Sensors'
  Failed! (0x8712)
Probing for `ITE 8712F Super IO Sensors'
  Success... found at address 0x0290
Probing for `Nat. Semi. PC87351 Super IO Fan Sensors'
  Failed! (skipping family)
Probing for `SMSC 47B27x Super IO Fan Sensors'
  Failed! (skipping family)
Probing for `VT1211 Super IO Sensors'
  Failed! (skipping family)

Do you want to scan for secondary Super I/O sensors? (YES/no): yes
Probing for `ITE 8702F Super IO Sensors'
  Failed! (skipping family)
Probing for `Nat. Semi. PC87351 Super IO Fan Sensors'
  Failed! (skipping family)
Probing for `SMSC 47B27x Super IO Fan Sensors'
  Failed! (skipping family)
Probing for `VT1211 Super IO Sensors'
  Failed! (skipping family)

 Now follows a summary of the probes I have just done.
 Just press ENTER to continue:

Driver `it87' (should be inserted):
  Detects correctly:
  * ISA bus address 0x0290 (Busdriver `i2c-isa')
    Chip `ITE 8712F Super IO Sensors' (confidence: 9)


 I will now generate the commands needed to load the I2C modules.
 Sometimes, a chip is available both through the ISA bus and an I2C bus.
 ISA bus access is faster, but you need to load an additional driver module
 for it. If you have the choice, do you want to use the ISA bus or the
 I2C/SMBus (ISA/smbus)? isa

To make the sensors modules behave correctly, add these lines to
/etc/modules:

#----cut here----
# I2C adapter drivers
i2c-isa
# I2C chip drivers
it87
#----cut here----

Do you want to add these lines to /etc/modules automatically? (yes/NO)yes
ian@amd64:~$
ian@amd64:~$
ian@amd64:~$ sensors
No sensors found!
```

---

### Post by jodsalz on 2005-05-18
I've got the same board and the same problems. I used this howto: [http://ubuntuforums.org/showthread.php?t=2780](http://ubuntuforums.org/showthread.php?t=2780) but I couldn't get it work.

I only loaded the modules for the detected sensors (it87 and i2c-isa) and not i2c-nforce2. But when doing "sensors" or "sudo sensors" the output was each time "No sensors found!"...

But there are! mbmon and xmbmon are doing fine... but I want to see a bit more.

Hope we will find a solution. May it have something to do with acpi-settings??

---

### Post by pointym5 on 2005-05-18
[QUOTE=jodsalz]I've got the same board and the same problems. I used this howto: [http://ubuntuforums.org/showthread.php?t=2780](http://ubuntuforums.org/showthread.php?t=2780) but I couldn't get it work.

I only loaded the modules for the detected sensors (it87 and i2c-isa) and not i2c-nforce2. But when doing "sensors" or "sudo sensors" the output was each time "No sensors found!"...

But there are! mbmon and xmbmon are doing fine... but I want to see a bit more.

Hope we will find a solution. May it have something to do with acpi-settings??[/QUOTE]

Do you actually have the modules loaded?   In other words, do the modules that sensors-detect tells you that you need show up when you run *lsmod*?  If not, then that'd be a problem.

---

### Post by jodsalz on 2005-05-18
```

To make the sensors modules behave correctly, add these lines to
/etc/modules:

#----cut here----
# I2C adapter drivers
i2c-isa
# I2C chip drivers
it87
#----cut here----

```
```

$ sudo modprobe i2c-isa
$ sudo modprobe it87
$ sensors
No sensors found!
$ lsmod
Module                  Size  Used by
it87                   19748  0
i2c_sensor              3584  1 it87
i2c_isa                 2176  0
i2c_dev                 9856  0
i2c_core               21264  4 it87,i2c_sensor,i2c_isa,i2c_dev
.
.
.

```

I uninstalled lm-sensors and started from beginning. But again without success, see above. Modules are loaded, but "No sensors detected!"...

---

### Post by pointym5 on 2005-05-18
[QUOTE=jodsalz]

I uninstalled lm-sensors and started from beginning. But again without success, see above. Modules are loaded, but "No sensors detected!"...[/QUOTE]

Hmm.  Well, I've had experience on some motherboards with *sensors-detect* picking the wrong driver.

My Epox 9NDA board (nForce4) works fine with the *w83627hf* module.  You might try loading that and seeing if it does anything.

---

### Post by jodsalz on 2005-05-18
```

$ sudo modprobe w83627hf
FATAL: Error inserting w83627hf (/lib/modules/2.6.10-5-386/kernel/drivers/i2c/chips/w83627hf.ko): No such device

```

Strange, cause I can see w83627.ko at the expected place...

---

### Post by regulator on 2005-07-05
I have this mobo (GA-K8NSC-939) and installing lm-sensors works, but i didnt think the temps were right (MB hotter than CPU, but BIOS says its the other way around !?)

Then, when it reboots, when the lm-sensors line says "Setting lm-sensors limits" my system starts making a loud buzzing sound like a warning or something. 

This happen to anyone else???

EDIT: Arghh mbmon does the same thing!!!

---

### Post by wantilles on 2005-07-05
Put the following modules to load on start-up in your **/etc/modules** file:

```
i2c-isa
it87
```

I have it working flawlessly on my DFI nF4-SLI motherboard.

---

### Post by regulator on 2005-07-05
Those two entries are the reason the problem occurs. Removing them solved the problem. And the mbmon program does the same thing...

Has anyone had success monitoring temps on this board (GA-K8NSC-939)???

---

### Post by negatory on 2005-09-07
After installing lmsensors and running sensors-detect add this line to your /etc/fstab:
```
sys              /sys             sysfs       default          0   0
```
and then: sudo mount /sys
Everything should be ok!Attention for those motherboards the motherboard and CPU temperatures are switched make the appropriate changes in /etc/sensors.conf.
Hope that helps
Pedro Carrico

---

### Post by jodsalz on 2005-09-07
[QUOTE=negatory]After installing lmsensors and running sensors-detect add this line to your /etc/fstab:
```
sys              /sys             sysfs       default          0   0
```
and then: sudo mount /sys
Everything should be ok!Attention for those motherboards the motherboard and CPU temperatures are switched make the appropriate changes in /etc/sensors.conf.
Hope that helps
Pedro Carrico[/QUOTE]

didn't help me. when doing "sudo mount /sys" it says "according to mtab sysfs is already mounted on /sys"...

---

### Post by idn on 2005-10-08
Hye everyone, I still havent got this working, I have a nforce4 motherboard, the above post didnt help. Anyone hhad any success with this? mbmon and xmbmon seem to work fine, although I dont believe my CPU tem - 70!

---

### Post by jodsalz on 2005-10-10
[QUOTE=idn]Hye everyone, I still havent got this working, I have a nforce4 motherboard, the above post didnt help. Anyone hhad any success with this? mbmon and xmbmon seem to work fine, although I dont believe my CPU tem - 70![/QUOTE]


i have exactly the same problem! 70°C can't be true, cause in bios i configured that it should beep at 60 or 50°C... in bios it shows me never more than 40°C...

---

### Post by Alives on 2005-10-15
I have the same problem, Gigabyte GA-K8N Ultra 9.  Modules are all loaded.  Sensors detect shos it87 and i2c_isa (i even found the IT8712F-A chip on the board).   I am running CentOS 4.2.  

# sensors
No sensors found!

---

