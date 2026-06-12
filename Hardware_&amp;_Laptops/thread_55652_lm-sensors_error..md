---
title: "lm-sensors error."
date: 2005-08-09
forum: Hardware &amp; Laptops
---

### Post by icecube76 on 2005-08-09
im trying to install lm-sensors on my hp laptop but i get few errors at the end of the progress 

root@ubuntu:/home/vega #  sudo ./mkdev.sh
/dev/i2c-0
/dev/i2c-1
/dev/i2c-2
/dev/i2c-3
/dev/i2c-4
/dev/i2c-5
/dev/i2c-6
/dev/i2c-7
/dev/i2c-8
/dev/i2c-9
/dev/i2c-10
/dev/i2c-11
/dev/i2c-12
/dev/i2c-13
/dev/i2c-14
/dev/i2c-15
/dev/i2c-16
/dev/i2c-17
/dev/i2c-18
/dev/i2c-19
/dev/i2c-20
/dev/i2c-21
/dev/i2c-22
/dev/i2c-23
/dev/i2c-24
/dev/i2c-25
/dev/i2c-26
/dev/i2c-27
/dev/i2c-28
/dev/i2c-29
/dev/i2c-30
/dev/i2c-31
root@ubuntu:/home/vega # sensors-detect

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

 IF THIS IS AN IBM THINKPAD, PRESS CTRL-C NOW!
 IBM Thinkpads have a severely broken i2c/SMBus implementation, just scanning
 the bus will break your Thinkpad forever!
 If this is a non-Thinkpad IBM, we still suggest you press CTRL+C. We have
 had users reporting system breakage on other IBM systems as well.

 We can start with probing for (PCI) I2C or SMBus adapters.
 You do not need any special privileges for this.
 Do you want to probe now? (YES/no): yes
Probing for PCI bus adapters...
Use driver `i2c-i801' for device 00:1f.3: Intel 82801DB ICH4
Probe succesfully concluded.

We will now try to load each adapter module in turn.
Module `i2c-i801' already loaded.
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

Next adapter: SMBus I801 adapter at 1880
Do you want to scan it? (YES/no/selectively): no

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
  Failed! (0xec11)
Probing for `ITE 8705F Super IO Sensors'
  Failed! (0xec11)
Probing for `ITE 8712F Super IO Sensors'
  Failed! (0xec11)
Probing for `Nat. Semi. PC87351 Super IO Fan Sensors'
  Failed! (0xec)
Probing for `Nat. Semi. PC87360 Super IO Fan Sensors'
  Failed! (0xec)
Probing for `Nat. Semi. PC87363 Super IO Fan Sensors'
  Failed! (0xec)
Probing for `Nat. Semi. PC87364 Super IO Fan Sensors'
  Failed! (0xec)
Probing for `Nat. Semi. PC87365 Super IO Fan Sensors'
  Failed! (0xec)
Probing for `Nat. Semi. PC87365 Super IO Voltage Sensors'
  Failed! (0xec)
Probing for `Nat. Semi. PC87365 Super IO Thermal Sensors'
  Failed! (0xec)
Probing for `Nat. Semi. PC87366 Super IO Fan Sensors'
  Failed! (0xec)
Probing for `Nat. Semi. PC87366 Super IO Voltage Sensors'
  Failed! (0xec)
Probing for `Nat. Semi. PC87366 Super IO Thermal Sensors'
  Failed! (0xec)
Probing for `Nat. Semi. PC87372 Super IO Fan Sensors'
  Failed! (0xec)
Probing for `Nat. Semi. PC87373 Super IO Fan Sensors'
  Failed! (0xec)
Probing for `Nat. Semi. PC8739x Super IO'
  Failed! (0xec)
Probing for `Nat. Semi. PC8741x Super IO'
  Failed! (0xec)
Probing for `SMSC 47B27x Super IO Fan Sensors'
  Failed! (0xec)
Probing for `SMSC 47M10x/13x Super IO Fan Sensors'
  Failed! (0xec)
Probing for `SMSC 47M14x Super IO Fan Sensors'
  Failed! (0xec)
Probing for `SMSC 47M15x/192 Super IO Fan Sensors'
  Failed! (0xec)
Probing for `SMSC 47S42x Super IO Fan Sensors'
  Failed! (0xec)
Probing for `SMSC 47S45x Super IO Fan Sensors'
  Failed! (0xec)
Probing for `SMSC 47M172 Super IO'
  Failed! (0xec)
Probing for `VT1211 Super IO Sensors'
  Failed! (0xec)
Probing for `Winbond W83627HF Super IO Sensors'
  Failed! (0xec)
Probing for `Winbond W83627THF Super IO Sensors'
  Failed! (0xec)
Probing for `Winbond W83637HF Super IO Sensors'
  Failed! (0xec)
Probing for `Winbond W83697HF Super IO Sensors'
  Failed! (0xec)
Probing for `Winbond W83697SF/UF Super IO PWM'
  Failed! (0xec)
Probing for `Winbond W83L517D Super IO'
  Failed! (0xec)

Do you want to scan for secondary Super I/O sensors? (YES/no): yes
Probing for `ITE 8702F Super IO Sensors'
  Failed! (skipping family)
Probing for `Nat. Semi. PC87351 Super IO Fan Sensors'
  Failed! (skipping family)
Probing for `SMSC 47B27x Super IO Fan Sensors'
  Failed! (skipping family)
Probing for `VT1211 Super IO Sensors'
  Failed! (skipping family)

 Sorry, no chips were detected.
 Either your sensors are not supported, or they are
 connected to an I2C bus adapter that we do not support.
 See doc/FAQ, doc/lm_sensors-FAQ.html, or
 [http://www2.lm-sensors.nu/~lm78/cvs/lm_sensors2/doc/lm_sensors-FAQ.html](http://www2.lm-sensors.nu/~lm78/cvs/lm_sensors2/doc/lm_sensors-FAQ.html)
 (FAQ #4.24.3) for further information.
 If you find out what chips are on your board, see
 [http://secure.netroedge.com/~lm78/newdrivers.html](http://secure.netroedge.com/~lm78/newdrivers.html) for driver status.


any help

regards

---

### Post by gmc on 2005-08-10
Hi.

Laptop's as far as I'm aware, do not use I2C chips to monitor CPU temprature. What you're looking for it ACPI support. Check and see if you have a the following file: /proc/acpi/thermal_zone/THRM/temperature? You can cat that file and see what your CPU temprature is.

I you are using gnome desktop, you can monitor your CPU temprature with a program called emifreq (available from the ubuntu repositories).

Hope this helps

G.

---

### Post by icecube76 on 2005-08-10
thank you for your reply
yes i have the file i did what you asked and it's working but my problem is that the fan  is not working at all ,,the temp now 35C  but afer few min it well rise tell 65C and no fan working.
so all i need is controling the fan and make it start when t reaches 60 or 55C

regards

---

### Post by gmc on 2005-08-10
[QUOTE=icecube76]thank you for your reply
yes i have the file i did what you asked and it's working but my problem is that the fan  is not working at all ,,the temp now 35C  but afer few min it well rise tell 65C and no fan working.
so all i need is controling the fan and make it start when t reaches 60 or 55C

regards[/QUOTE]
 What brand and model of laptop are we talking about here. I'm using an old toshiba satellite pro 4600. My fan kicks in when the temp reaches 68C, but I can turn it on manually with a utility called toshset, and I also installed fnfx-client and fnfxd, which allows me to turn on the fan with function-key-3.

G.

PS. Although I've never been able to set the trip points for the fan, if you search the forums and google for information on /proc/acpi/thermal_zone/THRM/trip_points. Apparently you can set the tempratures for the fan and automatic shutdown.

G.

---

### Post by srijith on 2005-08-10
I always thought that lm_sensors do not support HP laptops.

---

### Post by icecube76 on 2005-08-10
im using HP pavilion ze4927ea
now im downloading the ubuntu hp 
i hope it'll work .
what is the max temp for centrino prossesors?

---

### Post by gmc on 2005-08-10
[QUOTE=icecube76]im using HP pavilion ze4927ea
now im downloading the ubuntu hp 
i hope it'll work .
what is the max temp for centrino prossesors?[/QUOTE]

I have no idea about maximum [safe] temprature for a Centrino based laptop. I know I have 3 AMD 2600XP's (desktop) that start to get flaky when they hit 55C, but as I say this P3 based laptop that I'm on now seems fairly happy at anything upto 75C. I guess you could check the HP or INTELs website for the specs. Anyhow, good luck with the HP version of Ubuntu.

G.

---

### Post by icecube76 on 2005-08-11
ok so i burned and installed Ubuntu hp on my laptop
it was not good i know that my hp model no in the list .im using za4927ea .
sound did not work,wiereless not working .so i switched back to 5.4 
it works fine except for the wireless led ,any idea hw to switch it on and of

regards

---

### Post by gmc on 2005-08-12
[QUOTE=icecube76]ok so i burned and installed Ubuntu hp on my laptop
it was not good i know that my hp model no in the list .im using za4927ea .
sound did not work,wiereless not working .so i switched back to 5.4 
it works fine except for the wireless led ,any idea hw to switch it on and of

regards[/QUOTE]
 Hi Icecube,

  A quick google search indicates that your laptop is using an Intel PRO/Wireless 2200. You might be able to verify this by opening a terminal window and issuing the following command.

'sudo lspci'

This link gives a pretty good description on how to compile/install drivers for that wireless chipset.

[http://www.ubuntuforums.org/showthread.php?t=26623&highlight=Intel+PRO%2FWireless+2200](http://www.ubuntuforums.org/showthread.php?t=26623&highlight=Intel+PRO%2FWireless+2200)

Hope this helps some...

G.

---

