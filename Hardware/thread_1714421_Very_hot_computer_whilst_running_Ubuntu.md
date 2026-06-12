---
title: "Very hot computer whilst running Ubuntu"
date: 2011-03-25
forum: Hardware
---

### Post by deini on 2011-03-25
I have an Acer Aspire 6930G, with both Windows XP and Ubuntu 10.10 installed.

When I'm running Ubuntu my laptop gets very hot.
It's at about 60-70°C when in little use, between 70-80°C when in normal use and between 80-90°C when in "heavy" use (not really heavy at all), and has at some points gone to 92°C

On Windows it's not like this.

I have fancontrol on my Ubuntu, but I can't seem to get lm-sensors to work correctly

I have tried to install lm-sensors many times using this link:
[http://ubuntuforums.org/showthread.php?t=2780](http://ubuntuforums.org/showthread.php?t=2780)
but all I get is this:

acpitz-virtual-0
Adapter: Virtual device
temp1:       +49.0°C  (crit = +105.0°C)                  

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +69.0°C  (high = +100.0°C, crit = +100.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +70.0°C  (high = +100.0°C, crit = +100.0°C)  

What can I do to fix this before my CPU fries?

---

### Post by snafu006 on 2011-03-25
Did you try installing ls-sensor from Synaptic? and did you update everything.

---

### Post by deini on 2011-03-25
> **snafu006 said:**
> Did you try installing ls-sensor from Synaptic? and did you update everything.

Can't seem to find ls-sensor

---

### Post by snafu006 on 2011-03-25
sorry its lm-sensors and go to terminal type sudo apt-get install lm-sensors after that has installed go back to terminal and type sensors-detect. and yes to everything that applys

---

### Post by deini on 2011-03-26
> **snafu006 said:**
> sorry its lm-sensors and go to terminal type sudo apt-get lm-sensors after that has installed go back to terminal and type sensors-detect. and yes to everything that applys

I have tried to install lm-sensors many times using this link:
[http://ubuntuforums.org/showthread.php?t=2780](http://ubuntuforums.org/showthread.php?t=2780)
but all I get is this:

acpitz-virtual-0
Adapter: Virtual device
temp1:       +49.0°C  (crit = +105.0°C)                  

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +69.0°C  (high = +100.0°C, crit = +100.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +70.0°C  (high = +100.0°C, crit = +100.0°C)

---

### Post by deini on 2011-03-26
Shameless self bump

---

### Post by d3v1150m471c on 2011-03-26
> **snafu006 said:**
> type sudo apt-get lm-sensors

need to put install in there

```

sudo apt-get install lm-sensors

```

---

### Post by snafu006 on 2011-03-26
thank you for that go to terminal type sudo apt-get install lm-sensors.--- type your password fallow the install.

---

### Post by snafu006 on 2011-03-26
[LEFT]Howto Install and Configure lm-sensors
     ========================
     
     1. I**nstall lm-sensors** using apt-get or the Synaptic GUI.
     
     sudo apt-get install lm-sensors
     
     
     2. **Run the mkdev.sh script** in the lm-sensors source. It is extacted below:
     
     a. Copy the script file below to a text editor and save it to a file named mkdev.sh.
     
     #!/bin/bash
     
     # Here you can set several defaults.
     
     # The number of devices to create (max: 256)
     NUMBER=32
     
     # The owner and group of the devices
     OUSER=root
     OGROUP=root
     # The mode of the devices
     MODE=600
     
     # This script doesn't need to be run if devfs is used
     if [ -r /proc/mounts ] ; then
         if grep -q "/dev devfs" /proc/mounts ; then
             echo "You do not need to run this script as your system uses devfs."
             exit;
         fi
     fi
     
     i=0;
     
     while [ $i -lt $NUMBER ] ; do
         echo /dev/i2c-$i
         mknod -m $MODE /dev/i2c-$i c 89 $i || exit
         chown "$OUSER:$OGROUP" /dev/i2c-$i || exit
         i=$[$i + 1]
     done
     #end of file
     
     b. Make the file executable:
     
     chmod 755 mkdev.sh
     
     c. Run mkdev.sh from the current directory
     
     sudo ./mkdev.sh
     
     
   3. Now** run sensors-detect** and answer YES to all YES/no  questions. I generally use the ISA bus rather than the SMBus bus, your  choice to this question!. At the end of the detection phase, a list of  modules that needs to be loaded will displayed. You will need to write  these down or print the list for the next steps.
     
     sudo sensors-detect
     
     Below is an example of results from sensors-detect:
     #*************************************************  *****************************
     To make the sensors modules behave correctly, add these lines to
     /etc/modules:
     
     #----cut here----
     # I2C adapter drivers
     i2c-viapro
     i2c-isa
     # I2C chip drivers
     eeprom
     it87
     #----cut here----
     
     Then, run /etc/init.d/module-init-tools
     
     To make the sensors modules behave correctly, add these lines to
     /etc/modprobe.d/local and run update-modules:
     
     #----cut here----
     # I2C module options
     alias char-major-89 i2c-dev
     #----cut here----
     #*************************************************  *******************************
     
  
     4. In this example, we [B]add the modules in reverse order (order is critical!) in "/etc/modules".
  [/B]    
     #*************************************************  *********************** 
     # /etc/modules: kernel modules to load at boot time.
     #
     # This file should contain the names of kernel modules that are
     # to be loaded at boot time, one per line.  Comments begin with
     # a "#", and everything on the line after them are ignored.
     
     psmouse
     mousedev
     ide-cd
     ide-disk
     ide-generic
     lp
     
     #For lm-sensors, i2c modules
     it87
     i2c-viapro
     i2c-isa
     
     #end of file!
     #*************************************************  ****************
     
     
 4. I found that there was no "/etc/modprobe.d/local" and that "alias  char-major-89 i2c-dev" was already listed in "/etc/modprobe.d/aliases".  So, nothing to do here.
     
     
     5.Now** load the modules manually using modprobe and update the dependencies.**
     
     sudo modprobe i2c-sensor
     sudo modprobe i2c-viapro
     sudo modprobe i2c-isa
     sudo modprobe it87
     
     sudo depmod -a           <may not be needed!>
     sudo update-modules      <may not be needed!>
     
     
     6. Now [B]test the sensor output using the lm-sensors utility "sensors".
 [/B]      
     sensors
     
     **************************************************  *****************
     it87-isa-0290
     Adapter: ISA adapter
     VCore 1:   +1.57 V  (min =  +1.42 V, max =  +1.57 V)   ALARM
     VCore 2:   +2.66 V  (min =  +2.40 V, max =  +2.61 V)   ALARM
     +3.3V:     +6.59 V  (min =  +3.14 V, max =  +3.46 V)   ALARM
     +5V:       +5.11 V  (min =  +4.76 V, max =  +5.24 V)
     +12V:     +11.78 V  (min = +11.39 V, max = +12.61 V)
     -12V:     -19.14 V  (min = -12.63 V, max = -11.41 V)   ALARM
     -5V:       +0.77 V  (min =  -5.26 V, max =  -4.77 V)   ALARM
     Stdby:     +5.00 V  (min =  +4.76 V, max =  +5.24 V)
     VBat:      +3.12 V
     fan1:     3668 RPM  (min =    0 RPM, div = :cool:
     fan2:        0 RPM  (min =  664 RPM, div = :cool:          ALARM
     fan3:        0 RPM  (min = 2657 RPM, div = 2)          ALARM
     M/B Temp:    +39°C  (low  =   +15°C, high =   +40°C)   sensor = thermistor
     CPU Temp:    +36°C  (low  =   +15°C, high =   +45°C)   sensor = thermistor
     Temp3:       +96°C  (low  =   +15°C, high =   +45°C)   sensor = diode
     **************************************************  ********************
     
     7. **Reboot** Ubuntu and the sensors should now be detected during the boot process properly!
     
   8. The **sensor output may be tweaked by editing the "/etc/sensors.conf" file**. It is possible to correct inacurate scaling too. For details check "man sensors.conf[/LEFT]

---

### Post by deini on 2011-03-26
> **snafu006 said:**
> [LEFT]Howto Install and Configure lm-sensors
     ========================
     
     1. I**nstall lm-sensors** using apt-get or the Synaptic GUI.
     
     sudo apt-get install lm-sensors
     
     
     2. **Run the mkdev.sh script** in the lm-sensors source. It is extacted below:
     
     a. Copy the script file below to a text editor and save it to a file named mkdev.sh.
     
     #!/bin/bash
     
     # Here you can set several defaults.
     
     # The number of devices to create (max: 256)
     NUMBER=32
     
     # The owner and group of the devices
     OUSER=root
     OGROUP=root
     # The mode of the devices
     MODE=600
     
     # This script doesn't need to be run if devfs is used
     if [ -r /proc/mounts ] ; then
         if grep -q "/dev devfs" /proc/mounts ; then
             echo "You do not need to run this script as your system uses devfs."
             exit;
         fi
     fi
     
     i=0;
     
     while [ $i -lt $NUMBER ] ; do
         echo /dev/i2c-$i
         mknod -m $MODE /dev/i2c-$i c 89 $i || exit
         chown "$OUSER:$OGROUP" /dev/i2c-$i || exit
         i=$[$i + 1]
     done
     #end of file
     
     b. Make the file executable:
     
     chmod 755 mkdev.sh
     
     c. Run mkdev.sh from the current directory
     
     sudo ./mkdev.sh
     
     
   3. Now** run sensors-detect** and answer YES to all YES/no  questions. I generally use the ISA bus rather than the SMBus bus, your  choice to this question!. At the end of the detection phase, a list of  modules that needs to be loaded will displayed. You will need to write  these down or print the list for the next steps.
     
     sudo sensors-detect
     
     Below is an example of results from sensors-detect:
     #*************************************************  *****************************
     To make the sensors modules behave correctly, add these lines to
     /etc/modules:
     
     #----cut here----
     # I2C adapter drivers
     i2c-viapro
     i2c-isa
     # I2C chip drivers
     eeprom
     it87
     #----cut here----
     
     Then, run /etc/init.d/module-init-tools
     
     To make the sensors modules behave correctly, add these lines to
     /etc/modprobe.d/local and run update-modules:
     
     #----cut here----
     # I2C module options
     alias char-major-89 i2c-dev
     #----cut here----
     #*************************************************  *******************************
     
  
     4. In this example, we [B]add the modules in reverse order (order is critical!) in "/etc/modules".
  [/B]    
     #*************************************************  *********************** 
     # /etc/modules: kernel modules to load at boot time.
     #
     # This file should contain the names of kernel modules that are
     # to be loaded at boot time, one per line.  Comments begin with
     # a "#", and everything on the line after them are ignored.
     
     psmouse
     mousedev
     ide-cd
     ide-disk
     ide-generic
     lp
     
     #For lm-sensors, i2c modules
     it87
     i2c-viapro
     i2c-isa
     
     #end of file!
     #*************************************************  ****************
     
     
 4. I found that there was no "/etc/modprobe.d/local" and that "alias  char-major-89 i2c-dev" was already listed in "/etc/modprobe.d/aliases".  So, nothing to do here.
     
     
     5.Now** load the modules manually using modprobe and update the dependencies.**
     
     sudo modprobe i2c-sensor
     sudo modprobe i2c-viapro
     sudo modprobe i2c-isa
     sudo modprobe it87
     
     sudo depmod -a           <may not be needed!>
     sudo update-modules      <may not be needed!>
     
     
     6. Now [B]test the sensor output using the lm-sensors utility "sensors".
 [/B]      
     sensors
     
     **************************************************  *****************
     it87-isa-0290
     Adapter: ISA adapter
     VCore 1:   +1.57 V  (min =  +1.42 V, max =  +1.57 V)   ALARM
     VCore 2:   +2.66 V  (min =  +2.40 V, max =  +2.61 V)   ALARM
     +3.3V:     +6.59 V  (min =  +3.14 V, max =  +3.46 V)   ALARM
     +5V:       +5.11 V  (min =  +4.76 V, max =  +5.24 V)
     +12V:     +11.78 V  (min = +11.39 V, max = +12.61 V)
     -12V:     -19.14 V  (min = -12.63 V, max = -11.41 V)   ALARM
     -5V:       +0.77 V  (min =  -5.26 V, max =  -4.77 V)   ALARM
     Stdby:     +5.00 V  (min =  +4.76 V, max =  +5.24 V)
     VBat:      +3.12 V
     fan1:     3668 RPM  (min =    0 RPM, div = :cool:
     fan2:        0 RPM  (min =  664 RPM, div = :cool:          ALARM
     fan3:        0 RPM  (min = 2657 RPM, div = 2)          ALARM
     M/B Temp:    +39°C  (low  =   +15°C, high =   +40°C)   sensor = thermistor
     CPU Temp:    +36°C  (low  =   +15°C, high =   +45°C)   sensor = thermistor
     Temp3:       +96°C  (low  =   +15°C, high =   +45°C)   sensor = diode
     **************************************************  ********************
     
     7. **Reboot** Ubuntu and the sensors should now be detected during the boot process properly!
     
   8. The **sensor output may be tweaked by editing the "/etc/sensors.conf" file**. It is possible to correct inacurate scaling too. For details check "man sensors.conf[/LEFT]


What the **** am I doing wrong?

Still getting this

acpitz-virtual-0
Adapter: Virtual device
temp1:       +52.0°C  (crit = +105.0°C)                  

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +69.0°C  (high = +100.0°C, crit = +100.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +71.0°C  (high = +100.0°C, crit = +100.0°C)

---

### Post by deini on 2011-03-26
> **deini said:**
> What the **** am I doing wrong?

Still getting this

acpitz-virtual-0
Adapter: Virtual device
temp1:       +52.0°C  (crit = +105.0°C)                  

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +69.0°C  (high = +100.0°C, crit = +100.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +71.0°C  (high = +100.0°C, crit = +100.0°C)

Got this:

Module i2c_sensor not found.

---

### Post by snafu006 on 2011-03-27
[SensorInstallHowto - Community Ubuntu Documentation ]("https://help.ubuntu.com/community/SensorInstallHowto")

---

### Post by deini on 2011-03-28
> **snafu006 said:**
> [SensorInstallHowto - Community Ubuntu Documentation ]("https://help.ubuntu.com/community/SensorInstallHowto")

Still nothing :/

---

### Post by deini on 2011-03-28
Here is the outcome of my sudo sensors-detect and sudo /etc/init.d/module-init-tools start:

deini@ubuntu:~$ sudo sensors-detect
# sensors-detect revision 5818 (2010-01-18 17:22:07 +0100)
# System: Acer, inc. Aspire 6930G
# Board: Acer, Inc. Makalu

This program will help you determine which kernel modules you need
to load to use lm_sensors most effectively. It is generally safe
and recommended to accept the default answers to all questions,
unless you know what you're doing.

Some south bridges, CPUs or memory controllers contain embedded sensors.
Do you want to scan for them? This is totally safe. (YES/no): y
Silicon Integrated Systems SIS5595...                       No
VIA VT82C686 Integrated Sensors...                          No
VIA VT8231 Integrated Sensors...                            No
AMD K8 thermal sensors...                                   No
AMD Family 10h thermal sensors...                           No
AMD Family 11h thermal sensors...                           No
Intel Core family thermal sensor...                         Success!
    (driver `coretemp')
Intel Atom thermal sensor...                                No
Intel AMB FB-DIMM thermal sensor...                         No
VIA C7 thermal sensor...                                    No
VIA Nano thermal sensor...                                  No

Some Super I/O chips contain embedded sensors. We have to write to
standard I/O ports to probe them. This is usually safe.
Do you want to scan for Super I/O sensors? (YES/no): y
Probing for Super-I/O at 0x2e/0x2f
Trying family `National Semiconductor'...                   Yes
Found unknown chip with ID 0xfc11
Probing for Super-I/O at 0x4e/0x4f
Trying family `National Semiconductor'...                   No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Nuvoton/Fintek'...               No
Trying family `ITE'...                                      No

Some systems (mainly servers) implement IPMI, a set of common interfaces
through which system health data may be retrieved, amongst other things.
We first try to get the information from SMBIOS. If we don't find it
there, we have to read from arbitrary I/O ports to probe for such
interfaces. This is normally safe. Do you want to scan for IPMI
interfaces? (YES/no): y
Probing for `IPMI BMC KCS' at 0xca0...                      No
Probing for `IPMI BMC SMIC' at 0xca8...                     No

Some hardware monitoring chips are accessible through the ISA I/O ports.
We have to write to arbitrary I/O ports to probe them. This is usually
safe though. Yes, you do have ISA I/O ports even if you do not have any
ISA slots! Do you want to scan the ISA I/O ports? (YES/no): y
Probing for `National Semiconductor LM78' at 0x290...       No
Probing for `National Semiconductor LM79' at 0x290...       No
Probing for `Winbond W83781D' at 0x290...                   No
Probing for `Winbond W83782D' at 0x290...                   No

Lastly, we can probe the I2C/SMBus adapters for connected hardware
monitoring devices. This is the most risky part, and while it works
reasonably well on most systems, it has been reported to cause trouble
on some systems.
Do you want to probe the I2C/SMBus adapters now? (YES/no): y
Using driver `i2c-i801' for device 0000:00:1f.3: Intel ICH9
Module i2c-i801 loaded successfully.
Module i2c-dev loaded successfully.

Next adapter: NVIDIA i2c adapter  (i2c-0)
Do you want to scan it? (YES/no/selectively): y

Next adapter: NVIDIA i2c adapter  (i2c-1)
Do you want to scan it? (YES/no/selectively): y

Next adapter: NVIDIA i2c adapter  (i2c-2)
Do you want to scan it? (YES/no/selectively): y
Client found at address 0x50
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 No
Probing for `EDID EEPROM'...                                Yes
    (confidence 8, not a hardware monitoring chip)

Next adapter: NVIDIA i2c adapter  (i2c-3)
Do you want to scan it? (YES/no/selectively): y

Next adapter: NVIDIA i2c adapter  (i2c-4)
Do you want to scan it? (YES/no/selectively): y

Next adapter: NVIDIA i2c adapter  (i2c-5)
Do you want to scan it? (YES/no/selectively): y
Client found at address 0x50
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 No
Probing for `EDID EEPROM'...                                No
Client found at address 0x51
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 No
Client found at address 0x52
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 No
Client found at address 0x53
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 No

Now follows a summary of the probes I have just done.
Just press ENTER to continue: 

Driver `coretemp':
  * Chip `Intel Core family thermal sensor' (confidence: 9)

To load everything that is needed, add this to /etc/modules:
#----cut here----
# Chip drivers
coretemp
#----cut here----
If you have some drivers built into your kernel, the list above will
contain too many modules. Skip the appropriate ones!

Do you want to add these lines automatically to /etc/modules? (yes/NO)y
Successful!

Monitoring programs won't work until the needed modules are
loaded. You may want to run '/etc/init.d/module-init-tools start'
to load them.

Unloading i2c-dev... OK
Unloading i2c-i801... OK

deini@ubuntu:~$ sudo /etc/init.d/module-init-tools start
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service module-init-tools start

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the start(8) utility, e.g. start module-init-tools
module-init-tools stop/waiting

---

### Post by deini on 2011-03-30
Bump

---

### Post by snafu006 on 2011-03-31
Ok i need you to try this OPEN TERMINAL 

type: and then hit enter
[FONT=monospace]cd /etc/default

Then type: sudo cp grub grub.bk press enter

Type: sudo gedit grub enter
[/FONT]Then change this line:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
To:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash  acpi_osi=Linux"
then save a close window and terminal reopen terminal and type
sudo update-grub press enter type your password then wait for terminal to finish and restart computer.

---

### Post by deini on 2011-04-01
> **snafu006 said:**
> Ok i need you to try this OPEN TERMINAL 

type: and then hit enter
[FONT=monospace]cd /etc/default

Then type: sudo cp grub grub.bk press enter

Type: sudo gedit grub enter
[/FONT]Then change this line:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
To:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash  acpi_osi=Linux"
then save a close window and terminal reopen terminal and type
sudo update-grub press enter type your password then wait for terminal to finish and restart computer.

What is this supposed to do?

My computer is still hot :/

---

### Post by snafu006 on 2011-04-02
did you do it?

---

### Post by deini on 2011-04-02
> **snafu006 said:**
> did you do it?

Yes I did it

---

### Post by Hedgehog1 on 2011-04-03
That version of the command is outdated.

Please do this to get it to work with the current grub:

```
gksudo gedit /etc/default/grub
```

```
GRUB_CMDLINE_LINUX_DEFAULT=**"**quiet splash **acpi_osi=\\\"Linux\\\""**
```

There are a total of **4 double quotes** in this line (2 side-by-side at the end)

Then do:

```
sudo update-grub
```

**And reboot. The operation of this will keep your computer running cooler.**

In case you are wondering WHY all these slashes, it is because this text string gets processed twice before it is used to boot the kernel:

In /etc/default/grub it looks like this:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=\\\"Linux\\\""
```

Which gets converted by the update-grub in /boot/grub/grub.cfg as:
```
linux /boot/vmlinuz-2.6.31-8-generic root=UUID=78b161e2-4d82-4df7-a423-8289fe6cc704
ro quiet splash acpi_osi=\"Linux\"
```

The command is then passed to the kernel when run by grub as:
```
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-8-generic root=UUID=78b161e2-4d82-4df7-a423-8289fe6cc704
ro quiet splash acpi_osi="Linux"
```

See how easy that (isn't) to follow?


***The Hedge***

:KS

---

### Post by deini on 2011-04-03
> **Hedgehog1 said:**
> That version of the command is outdated.

Please do this to get it to work with the current grub:

```
gksudo gedit /etc/default/grub
``````
GRUB_CMDLINE_LINUX_DEFAULT=**"**quiet splash **acpi_osi=\\\"Linux\\\""**
```There are a total of **4 double quotes** in this line (2 side-by-side at the end)

Then do:

```
sudo update-grub
```**And reboot. The operation of this will keep your computer running cooler.**

In case you are wondering WHY all these slashes, it is because this text string gets processed twice before it is used to boot the kernel:

In /etc/default/grub it looks like this:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=\\\"Linux\\\""
```Which gets converted by the update-grub in /boot/grub/grub.cfg as:
```
linux /boot/vmlinuz-2.6.31-8-generic root=UUID=78b161e2-4d82-4df7-a423-8289fe6cc704
ro quiet splash acpi_osi=\"Linux\"
```The command is then passed to the kernel when run by grub as:
```
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-8-generic root=UUID=78b161e2-4d82-4df7-a423-8289fe6cc704
ro quiet splash acpi_osi="Linux"
```See how easy that (isn't) to follow?


***The Hedge***

:KS

Still hot :/

---

### Post by deini on 2011-04-05
bump

---

### Post by Marcelush on 2011-04-05
I think that you have to go on your laptop's bios and make some changes at the CPU temperature and then you'll not have any problem.

---

### Post by deini on 2011-04-05
> **Marcelush said:**
> I think that you have to go on your laptop's bios and make some changes at the CPU temperature and then you'll not have any problem.

I don't think I can do that in my BIOS, at least I can't seem to find that option

---

### Post by deini on 2011-04-06
Bumping again

---

### Post by Hedgehog1 on 2011-04-07
Please post the current text of your **/etc/default/grub** file.

Also - what are the temperatures your PC is now running on Ubuntu after the various changes you have been asked to make?



***The Hedge***

---

### Post by deini on 2011-04-07
> **Hedgehog1 said:**
> Please post the current text of your **/etc/default/grub** file.

Also - what are the temperatures your PC is now running on Ubuntu after the various changes you have been asked to make?



***The Hedge***

My /etc/default/grub:[B]

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=\\\"Linux\\\""
GRUB_CMDLINE_LINUX="acpi.power_nocheck=1"

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"




[/B]Temperature is: 
acpitz-virtual-0
Adapter: Virtual device
temp1:       +40.0°C  (crit = +92.0°C)                  

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +56.0°C  (high = +100.0°C, crit = +100.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +58.0°C  (high = +100.0°C, crit = +100.0°C)  

Pretty "low" ATM, but that's just because I just turned it on.

---

### Post by deini on 2011-04-09
Bump

---

### Post by Yellow Pasque on 2011-04-09
About the temp monitoring - that's probably all of the usable sensors your laptop has (ACPI and core sensors). [http://www.lm-sensors.org/ticket/2337](http://www.lm-sensors.org/ticket/2337)

Anyway, there seems to be a large difference between the core sensors and the ACPI one. Do you have temp monitoring in the BIOS to help verify sensor accuracy?

Also, can you detect a difference in fan speed between Windows and Ubuntu?

---

### Post by deini on 2011-04-10
> **Temüjin said:**
> About the temp monitoring - that's probably all of the usable sensors your laptop has (ACPI and core sensors). [http://www.lm-sensors.org/ticket/2337](http://www.lm-sensors.org/ticket/2337)

Anyway, there seems to be a large difference between the core sensors and the ACPI one. Do you have temp monitoring in the BIOS to help verify sensor accuracy?

Also, can you detect a difference in fan speed between Windows and Ubuntu?

The power section in the BIOS is gone all together.

I don't know if I can detect the fan running slower/faster, but I do know that my CPU is hotter running Ubuntu.

---

### Post by deini on 2011-04-10
Please someone help me.

I'm considering installing Ubuntu on my entire system, but I need to get rid of this problem first.

---

### Post by deini on 2011-04-12
Bump

---

### Post by deini on 2011-04-19
I have now installed Ubuntu 11.04 beta on my entire computer.

The computer is still too hot, so please help me : )

---

### Post by deini on 2011-04-26
Bump

---

### Post by jmcbri on 2011-04-30
> **deini said:**
> Bump

If you find an answer to this, please post it.  I seem to have the same problem.  Ubuntu 10.10 seems to run cooler even tho I would think that I have more going on with the old setup.  The new setup is basically vanilla.

It's so bad that the system shuts down after a while.  I suspect that it's graphics related, but that's weird too as I'm not doing anything when it happens.  The system is an Aspire 5672, and it's got an old ATI card in it.  

- Jim

---

### Post by deini on 2011-05-02
> **jmcbri said:**
> If you find an answer to this, please post it.  I seem to have the same problem.  Ubuntu 10.10 seems to run cooler even tho I would think that I have more going on with the old setup.  The new setup is basically vanilla.

It's so bad that the system shuts down after a while.  I suspect that it's graphics related, but that's weird too as I'm not doing anything when it happens.  The system is an Aspire 5672, and it's got an old ATI card in it.  

- Jim

I will, and I hope you will do the same :)

There must be a solution.

---

### Post by Mars73 on 2011-05-03
I'm also watching this space (and the phoronix site) to see if there's any news. For now I've gone back to 10.04 and it's much better.
The fan sometimes even stops in my laptop when idle, exactly how it should be imo.
With 11.04, even when just opening a terminal, it started to blow at high speed and it never stopped. (plus I tried to like Unity but it's not for me so the decision was easy).

---

### Post by deini on 2011-05-04
> **Mars73 said:**
> I'm also watching this space (and the phoronix site) to see if there's any news. For now I've gone back to 10.04 and it's much better.
The fan sometimes even stops in my laptop when idle, exactly how it should be imo.
With 11.04, even when just opening a terminal, it started to blow at high speed and it never stopped. (plus I tried to like Unity but it's not for me so the decision was easy).

Maybe I'll do that, but I want to try to fix it.

When it comes to Unity, it's not for me (or for anyone imo, because, it, quite frankly, sucks balls) either.

---

### Post by deini on 2011-05-10
Bump

---

### Post by Lupajz on 2011-05-10
I have Acer 5535 with Ati HD 3200 and I run 10.10
As I am not doing anything and with none processes running in the background I get this temperature :
```
# sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:       +72.0°C  (crit = +100.0°C)                  
temp2:       +65.0°C  (crit = +110.0°C)                  

k10temp-pci-00c3
Adapter: PCI adapter
temp1:       +69.5°C  (high = +70.0°C)  
```
any solutions ? :/

---

### Post by deini on 2011-05-12
> **Lupajz said:**
> I have Acer 5535 with Ati HD 3200 and I run 10.10
As I am not doing anything and with none processes running in the background I get this temperature :
```
# sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:       +72.0°C  (crit = +100.0°C)                  
temp2:       +65.0°C  (crit = +110.0°C)                  

k10temp-pci-00c3
Adapter: PCI adapter
temp1:       +69.5°C  (high = +70.0°C)  
```any solutions ? :/

Mine:

acpitz-virtual-0
Adapter: Virtual device
temp1:       +48.0°C  (crit = +92.0°C)                  

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +66.0°C  (high = +100.0°C, crit = +100.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +68.0°C  (high = +100.0°C, crit = +100.0°C)

---

