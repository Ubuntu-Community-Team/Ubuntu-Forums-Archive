---
title: "Zotac IONITX-A vs. lm-sensors"
date: 2009-06-29
forum: Hardware
---

### Post by pgruber on 2009-06-29
Hi!
 
I have above mentioned ZOTAC ION ITX-A (Atom330 and Nvidia ION-Chipset) running here with Ubuntu 9.04.
 
My problem is that sensors-detect from lm-sensors-package does not find any sensor.
Downloaded Version 3.1.1 and compiled it. No effort...
 
Can someone point me to the right direction?`
 
Board must have a chip as in BIOS I can see a temp, the voltages and the fans...
 
Thanks,
Patrick

---

### Post by d-range on 2009-07-05
I would also like to know how to read the sensors on the Zotac ION board (and probably other boards using the ION chipset as well)

So far I've tried recompiling to the latest kernel with all sensor/i2c/smbus/etc drivers enabled as modules, and upgraded lm-sensors to the latest development snapshot. 

sensors-detect gives me:

```

# uname -a
Linux ionbox 2.6.30-ion #4 SMP PREEMPT Mon Jun 22 23:10:08 CEST 2009 i686 GNU/Linux

# sensors-detect revision 5249 (2008-05-11 22:56:25 +0200)

This program will help you determine which kernel modules you need
to load to use lm_sensors most effectively. It is generally safe
and recommended to accept the default answers to all questions,
unless you know what you're doing.

We can start with probing for (PCI) I2C or SMBus adapters.
Do you want to probe now? (YES/no): 
Probing for PCI bus adapters...
Found unknown SMBus adapter 10de:0aa2 at 0000:00:03.2.
Sorry, no supported PCI bus adapters found.

If you have undetectable or unsupported I2C/SMBus adapters, you can have
them scanned by manually loading the modules before running this script.

To continue, we need module `i2c-dev' to be loaded.
Do you want to load `i2c-dev' now? (YES/no): 
Module loaded successfully.

We are now going to do the I2C/SMBus adapter probings. Some chips may
be double detected; we choose the one with the highest confidence
value in that case.
If you found that the adapter hung after probing a certain address,
you can specify that address to remain unprobed.

Next adapter: SMBus nForce2 adapter at 4d00 (i2c-0)
Do you want to scan it? (YES/no/selectively): 
Client found at address 0x4c
Probing for `National Semiconductor LM75'...                No
Probing for `Dallas Semiconductor DS75'...                  No
Probing for `Analog Devices ADT7466'...                     No
Probing for `Andigilog aSC7511'...                          No
Probing for `Dallas Semiconductor DS1621/DS1631'...         No
Probing for `Analog Devices ADM1021'...                     No
Probing for `Analog Devices ADM1021A/ADM1023'...            No
Probing for `Maxim MAX1617'...                              No
Probing for `Maxim MAX1617A'...                             No
Probing for `Maxim MAX1668'...                              No
Probing for `Maxim MAX1805'...                              No
Probing for `Maxim MAX1989'...                              No
Probing for `Maxim MAX6655/MAX6656'...                      No
Probing for `TI THMC10'...                                  No
Probing for `National Semiconductor LM84'...                No
Probing for `Genesys Logic GL523SM'...                      No
Probing for `Onsemi MC1066'...                              No
Probing for `Maxim MAX1619'...                              No
Probing for `National Semiconductor LM82/LM83'...           No
Probing for `National Semiconductor LM90'...                No
Probing for `National Semiconductor LM89/LM99'...           No
Probing for `National Semiconductor LM86'...                No
Probing for `Analog Devices ADM1032'...                     No
Probing for `Maxim MAX6657/MAX6658/MAX6659'...              No
Probing for `Maxim MAX6648/MAX6692'...                      No
Probing for `Maxim MAX6680/MAX6681'...                      No
Probing for `Winbond W83L771W/G'...                         No
Probing for `Texas Instruments TMP401'...                   No
Probing for `National Semiconductor LM63'...                No
Probing for `Fintek F75363SG'...                            No
Probing for `Maxim MAX6633/MAX6634/MAX6635'...              No
Probing for `Analog Devices ADT7461'...                     No
Probing for `Fintek F75383S/M'...                           No
Client found at address 0x50
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 No
Probing for `EDID EEPROM'...                                No
Client found at address 0x51
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 No
Probing for `EDID EEPROM'...                                No
Client found at address 0x52
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 No
Probing for `EDID EEPROM'...                                No
Client found at address 0x53
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 No
Probing for `EDID EEPROM'...                                No

Next adapter: SMBus nForce2 adapter at 4e00 (i2c-1)
Do you want to scan it? (YES/no/selectively): 
Client found at address 0x50
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 Yes
    (confidence 8, not a hardware monitoring chip)
Probing for `EDID EEPROM'...                                No
Client found at address 0x51
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 Yes
    (confidence 8, not a hardware monitoring chip)
Probing for `EDID EEPROM'...                                No

Next adapter: NVIDIA i2c adapter  (i2c-2)
Do you want to scan it? (YES/no/selectively): 

Next adapter: NVIDIA i2c adapter  (i2c-3)
Do you want to scan it? (YES/no/selectively): 

Next adapter: NVIDIA i2c adapter  (i2c-4)
Do you want to scan it? (YES/no/selectively): 

Some chips are also accessible through the ISA I/O ports. We have to
write to arbitrary I/O ports to probe them. This is usually safe though.
Yes, you do have ISA I/O ports even if you do not have any ISA slots!
Do you want to scan the ISA I/O ports? (YES/no): 
Probing for `National Semiconductor LM78' at 0x290...       No
Probing for `National Semiconductor LM78-J' at 0x290...     No
Probing for `National Semiconductor LM79' at 0x290...       No
Probing for `Winbond W83781D' at 0x290...                   No
Probing for `Winbond W83782D' at 0x290...                   No
Probing for `IPMI BMC KCS' at 0xca0...                      No
Probing for `IPMI BMC SMIC' at 0xca8...                     No

Some Super I/O chips may also contain sensors. We have to write to
standard I/O ports to probe them. This is usually safe.
Do you want to scan for Super I/O sensors? (YES/no): 
Probing for Super-I/O at 0x2e/0x2f
Trying family `National Semiconductor'...                   No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Fintek'...                       No
Trying family `ITE'...                                      No
Probing for Super-I/O at 0x4e/0x4f
Trying family `National Semiconductor'...                   No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Fintek'...                       No
Trying family `ITE'...                                      No

Some south bridges, CPUs or memory controllers may also contain
embedded sensors. Do you want to scan for them? (YES/no): 
Silicon Integrated Systems SIS5595...                       No
VIA VT82C686 Integrated Sensors...                          No
VIA VT8231 Integrated Sensors...                            No
AMD K8 thermal sensors...                                   No
AMD K10 thermal sensors...                                  No
Intel Core family thermal sensor...                         No
Intel AMB FB-DIMM thermal sensor...                         No

Sorry, no sensors were detected.
Either your sensors are not supported, or they are connected to an
I2C or SMBus adapter that is not supported. See
http://www.lm-sensors.org/wiki/FAQ/Chapter3 for further information.
If you find out what chips are on your board, check
http://www.lm-sensors.org/wiki/Devices for driver status.

```

So it seems to find an nForce SMbus adapter and an nvidia i2c bus, but no sensors.

I know there's at least a temperature sensor on the board, because the nvidia control panel shows the gpu temperature (which I guess is also the CPU temperature because it's a single package). There are no entries in /proc/acpi/thermal_zone or /proc/acpi/fan though, so it seems the nvidia panel gets the temperature itself, probably via the nvidia-kernel module

This is all a little annoying because the Atom 330 doesn't support speedstep either, and I'd really like to have the fan spin only when it's absolutely necessary (I use the box as a media player but also as a private server that's always on but hardly ever doing anything that would make it sweat). Right now the CPU maxes out at 1.6Ghz all the time and the fan speed is always the same, with the nvidia control panel showing a temperature around 45C, so there should be quite some room for improvement.

---

### Post by domi55 on 2009-07-15
Hi All,

I'm also interested in this. I have exactly the same problem.
Does anybody have an idea?

---

### Post by kzanol on 2009-07-16
Just played around a bit with an acer revo, also based on nvidia ion platform. Obviously got identical results initialy - looks like the problems are mostly caused by lack of automatic detection, actually reading the sensors works if you load the right modules:
 
* running ubuntu jaunty, kernel 2.6.28-13-generic
 
* the MCP79 SMBus interface is supported by i2c_nforce2, module has to be told about new device id however
* the actual sensor seems to be mostly compatible with lm85
 
# modprobe i2c-dev
# modprobe i2c-nforce2
# echo "10de 0aa2" > /sys/bus/pci/drivers/nForce2_smbus/new_id
 
# i2cdetect -l should now show you two new nvidia SMBus adapters:
 
[FONT=Courier New]i2c-0 i2c NVIDIA i2c adapter I2C adapter[/FONT]
[FONT=Courier New]i2c-1 i2c NVIDIA i2c adapter I2C adapter[/FONT]
[FONT=Courier New]i2c-2 i2c NVIDIA i2c adapter I2C adapter[/FONT]
[FONT=Courier New]i2c-3 smbus SMBus nForce2 adapter at 4d00 SMBus adapter[/FONT]
[FONT=Courier New]i2c-4 smbus SMBus nForce2 adapter at 4e00 SMBus adapter[/FONT]
 
# modprobe lm85
 
# sensors 
[FONT=Courier New]lm85-i2c-3-2e[/FONT]
[FONT=Courier New]Adapter: SMBus nForce2 adapter at 4d00[/FONT]
[FONT=Courier New]V1.5: +1.84 V (min = +0.00 V, max = +3.32 V)[/FONT]
[FONT=Courier New]VCore: +1.20 V (min = +0.00 V, max = +2.99 V)[/FONT]
[FONT=Courier New]V3.3: +3.33 V (min = +0.00 V, max = +4.38 V)[/FONT]
[FONT=Courier New]V5: +5.08 V (min = +0.00 V, max = +6.64 V)[/FONT]
[FONT=Courier New]V12: +1.00 V (min = +0.00 V, max = +15.94 V)[/FONT]
[FONT=Courier New]CPU_Fan: 3590 RPM (min = 0 RPM)[/FONT]
[FONT=Courier New]fan2: 0 RPM (min = 0 RPM)[/FONT]
[FONT=Courier New]fan3: 0 RPM (min = 0 RPM)[/FONT]
[FONT=Courier New]fan4: 0 RPM (min = 0 RPM)[/FONT]
[FONT=Courier New]CPU Temp: +68.0°C (low = -127.0°C, high = +127.0°C)[/FONT]
[FONT=Courier New]Board Temp: +52.0°C (low = -127.0°C, high = +127.0°C)[/FONT]
[FONT=Courier New]Remote Temp: +59.0°C (low = -127.0°C, high = +127.0°C)[/FONT]
[FONT=Courier New]cpu0_vid: +0.000 V[/FONT]
 
Output looks fairly reasonable at first glance, not too sure about Board and Remote Temp though - Both CPU Temp & fan looks good & changes as expected with increased system load.
 
Bye, Martin

---

### Post by vikjon0 on 2009-07-16
This looks good, but when I do 
echo "10de 0aa2" > /sys/bus/pci/drivers/nForce2_smbus/new_id

I get 
-bash: /sys/bus/pci/drivers/nForce2_smbus/new_id: Permission denied


Any ideas?

Running Asrock ION 330
***
uname -r
2.6.28-13-generic

---

### Post by vikjon0 on 2009-07-17
Ok, thanks!

As root I can run all the commands and 
# i2cdetect -l 
gives the the expected result.

But
# sensors
still does not work.

Does it require this?:
> recompiling to the latest kernel with all sensor/i2c/smbus/etc drivers enabled as modules, and upgraded lm-sensors to the latest development snapshot.

//J

---

### Post by kzanol on 2009-07-17
looks like the sensors actually used on the boards are vendor specific. The acer revo 3600 I've got uses an ADT7476 sensor which can be handled by the lm85 module.
 
after you've enabled the SMBus interface, you can rerun sensors-detect to see if/which sensors are found on your board.
 
Bye, Martin

---

### Post by domi55 on 2009-07-17
@kzanol:

I can confirm that this procedure does **not **work for zotac ION ITX A boards:

i2cdetect seems to give the right output:
```
(T: XBMCLive)root@XBMCLive:/# i2cdetect -l
i2c-0   i2c             NVIDIA i2c adapter                      I2C adapter
i2c-1   i2c             NVIDIA i2c adapter                      I2C adapter
i2c-2   i2c             NVIDIA i2c adapter                      I2C adapter
i2c-3   smbus           SMBus nForce2 adapter at 4d00           SMBus adapter
i2c-4   smbus           SMBus nForce2 adapter at 4e00           SMBus adapter
```

But after re-running 'sensors-detect' I still get the message:
```
Sorry, no sensors were detected.
```

---

### Post by domi55 on 2009-07-20
@kzanol: Are you able to help us on this problem?

---

### Post by kzanol on 2009-07-20
Some more information: As stated in my first post, my results where obtained on an acer revo, not on the zotac board; both are nvidia ion boards but the zotac uses a different hardware sensor.  I haven't been able to figure out which one so far, will try to find some more info on this.  Some good news: regardless of hardware sensors all ion boards share at least one sensor, namely the on-chip sensor in the atom cpu. The coretemp module required for reading such sensors doesn't yet support the atom cpu, so it doesn't work out of tzhe box.  A patch to fix this has been available since 2.6.27; unfortunately it hasn't yet (as of 2.6.30) been integrated into the kernel source - there's an effort to get it included in one of the next kernel versions.   In the meantime you can either patch your kernel source to add coretemp support for the atom CPU ([http://mabene.icomedias.com/coretemp.patch](http://mabene.icomedias.com/coretemp.patch)) or you can use my patched coretemp.ko module (works with current jaunty kernel linux-image-2.6.28-13-generic, [http://mabene.icomedias.com/coretemp.ko](http://mabene.icomedias.com/coretemp.ko))  bye, Martin

---

### Post by domi55 on 2009-07-20
Thanks very much kzanol. Can you help me to install this module/patch? Because I'm not familiar with patching ubuntu.

I have the following kernel version:
```
(T: XBMCLive)xbmc@XBMCLive:/tmp$ uname -a
Linux XBMCLive 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686 GNU/Linux
(T: XBMCLive)xbmc@XBMCLive:/tmp$
```Its XBMC. Hopefully this is not a problem. 

> will try to find some more info on thisLet me know (PM) if you are interested to play around with a Zotac ION ITX A board. I can provide SSH access to my HTPC.

Thanks again for your help.

---

### Post by kzanol on 2009-07-21
> **domi55 said:**
> Thanks very much kzanol. Can you help me to install this module/patch? 
```
Linux XBMCLive 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686 GNU/Linux
```

The binary module should work for you.
[LIST]
[*]download
[*]sudo insmod coretemp.ko
[/LIST]if that works without error, the "sensors" command should now give you readings for your atoms core(s):
 
```
martin@mbe-revo:~$ sensors
coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +52.0°C  (crit = +95.0°C)
coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +52.0°C  (crit = +95.0°C)

```

---

### Post by domi55 on 2009-07-21
> if that works without error, the "sensors" command should now give you readings for your atoms core(s)Ahaa! I see. I tried it yesterday with:

```
sudo sensors-detect
```But with no sucess. But if you're saying that it should work with the command 'sensors' I will try that tonight.

Will keep you posted. 

Thanks very much.

---

### Post by domi55 on 2009-07-21
Ok it **works**!

```
(T: XBMCLive)xbmc@XBMCLive:/tmp$ wget http://mabene.icomedias.com/coretemp.ko
--2009-07-21 16:02:11--  http://mabene.icomedias.com/coretemp.ko
Resolving mabene.icomedias.com... 62.99.232.79
Connecting to mabene.icomedias.com|62.99.232.79|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 97304 (95K) [text/plain]
Saving to: `coretemp.ko'

100%[=======================================================================================================>] 97,304       246K/s   in 0.4s

2009-07-21 16:02:12 (246 KB/s) - `coretemp.ko' saved [97304/97304]

(T: XBMCLive)xbmc@XBMCLive:/tmp$ sudo insmod coretemp.ko
(T: XBMCLive)xbmc@XBMCLive:/tmp$ sudo sensors
coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +30.0Â°C  (crit = +95.0Â°C)

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +28.0Â°C  (crit = +95.0Â°C)

coretemp-isa-0002
Adapter: ISA adapter
Core 2:      +30.0Â°C  (crit = +95.0Â°C)

coretemp-isa-0003
Adapter: ISA adapter
Core 3:      +28.0Â°C  (crit = +95.0Â°C)
```But as you probably can see there is always a **Â **between the temp and "°C". Do you know how to eliminate that?

And the second question is: Do I have to edit **/etc/modules** that it survives a reboot? How?

---

### Post by tg1 on 2009-07-21
Hi!

I've also got a Zotac ION, and I'm wondering if there's any way to control the cpu fan speed?
I'm using the box as a htpc, so I'd be happy if there's any way to reduce the fan speed when it's not needed.

sensors returns this:
```
coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +35.0°C  (crit = +95.0°C)

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +36.0°C  (crit = +95.0°C)

coretemp-isa-0002
Adapter: ISA adapter
Core 2:      +35.0°C  (crit = +95.0°C)

coretemp-isa-0003
Adapter: ISA adapter
Core 3:      +36.0°C  (crit = +95.0°C)
```

---

### Post by domi55 on 2009-07-21
hi tg1

Do you still have this output after a reboot?

I have to do 
```
sudo insmod coretemp.ko
```after each reboot.

---

### Post by tg1 on 2009-07-21
I had to place the coretemp.ko file in /lib/modules/2.6.28-13-generic/kernel/drivers/hwmon/ and add a line with "coretemp" in /etc/modules :-)

---

### Post by domi55 on 2009-07-21
thanks tg1. this works perfectly for me.

> I'm using the box as a htpc, so I'd be happy if there's any way to reduce the fan speed when it's not needed.

I'm also interested in this. I somebody around who can help us here?

---

### Post by tg1 on 2009-07-23
Anyone? :-)

---

### Post by d-range on 2009-07-26
Thanks for the help kzanol, I got the temperature readings working!

Now I'd be very interested in reading and controlling the fan speed as well, but I suppose someone needs to write ACPI support for the ION chipset for that?

---

### Post by Erhnam on 2009-07-29
> **kzanol said:**
> Some more information: As stated in my first post, my results where obtained on an acer revo, not on the zotac board; both are nvidia ion boards but the zotac uses a different hardware sensor.  I haven't been able to figure out which one so far, will try to find some more info on this.  Some good news: regardless of hardware sensors all ion boards share at least one sensor, namely the on-chip sensor in the atom cpu. The coretemp module required for reading such sensors doesn't yet support the atom cpu, so it doesn't work out of tzhe box.  A patch to fix this has been available since 2.6.27; unfortunately it hasn't yet (as of 2.6.30) been integrated into the kernel source - there's an effort to get it included in one of the next kernel versions.   In the meantime you can either patch your kernel source to add coretemp support for the atom CPU ([http://mabene.icomedias.com/coretemp.patch](http://mabene.icomedias.com/coretemp.patch)) or you can use my patched coretemp.ko module (works with current jaunty kernel linux-image-2.6.28-13-generic, [http://mabene.icomedias.com/coretemp.ko](http://mabene.icomedias.com/coretemp.ko))  bye, Martin

Thanks! But could you explain us how to apply the patch and how to build the module? Downloading a module directly from the Internet is not very safe.

---

### Post by d-range on 2009-07-29
@Erhnam
It's pretty easy. Suppose you have the kernel sources (I used 2.6.30) unpacked in /usr/src/linux-2.6.30, just do the following:

- Copy the patch to /usr/src/linux-2.6.30, let's assume you saved it as 'coretemp.patch'
- cd to /usr/src/linux-2.6.30
- Do a 'patch -p1 < coretemp.patch'
- Go on the internet and google for 'compile kernel ubuntu way', read the article that's listed as the top result and find out how to build a kernel .deb package you can install with aptitude or dpkg.

In short, to compile the kernel you will generally want to keep the kernel config of your currently working kernel, which means that you'll have to copy the configuration file that's stored in /boot (on my system it's called /boot/config-2.6.30-ion, but check your running kernel version first) to /usr/src/linux-2.6.30/.config 

After you've ensured the kernel configuration is all set do something like:

- 'make-kpkg clean'
- 'fakeroot make-kpg --initrd --append-to-version=-ion kernel-image kernel-headers'

And it should build the kernel and drop two .deb packages in /usr/src

Note that I'm typing this from the top of my head so these 'instructions' might not be 100% correct for your system and kernel, so don't use it as a step-by-step guide, just as a summary of the required steps. The 'how to build a kernel, the ubuntu way' is a good source to learn how to build a kernel.

Also, I might be mistaking about the -p1 switch to the patch command, it specifies how many path elements the patch tool will strip off the filenames in the patch file, to find the corresponding file on your system. For example: if someone who has it's kernel sources in '/usr/src/blergh' made the patch, there might be references to files called 'blergh/filename', patch -p1 would strip off 'blergh' and look for ./filename). If the patch command fails, try -p0 or -p2 (I don't have time to check how this particular patch file was made again right now).

---

### Post by sem7ex on 2009-08-08
Hi,

im also interested in this issue. i can see the temperatures with sensors, and also the gpu temperature with the gnome applet.

but i'd also like to be able to control the cpu speed because now if i connect the fan, the cpu stays below 20° but without it goes up to 70°. I would like it somewhere in the middle.

has anybody made any progress with this?!

---

### Post by Alfiegerner on 2009-08-22
> **sem7ex said:**
> Hi,

im also interested in this issue. i can see the temperatures with sensors, and also the gpu temperature with the gnome applet.

but i'd also like to be able to control the cpu speed because now if i connect the fan, the cpu stays below 20° but without it goes up to 70°. I would like it somewhere in the middle.

has anybody made any progress with this?!

Is it even possible to reduce the fan speed at all?  Just unpacked my ion A expecting it to be quiet and it's blowing at 3600 rpms and making a right bloody racket.

I haven't found a way to reduce the fan speed in the bios.

Any help much appreciated.

---

### Post by truant on 2009-08-26
As far as I know, fan control isn't possible unless you have entries in /proc/acpi/fan/  I don't have any, which makes sense as kzanol's patch only covers core temp.

See here for more info: [http://ubuntuforums.org/showthread.php?t=846480](http://ubuntuforums.org/showthread.php?t=846480)

That said - stock fans are always noisy.  I always ditch them right away.  Spend a few quid at quietpc.com and get a decent silenced fan, you won't regret it.

I have no fan on the board, but one of these on the case: [http://www.quietpc.com/gb-en-gbp/products/120mmfans/sy-kazejyuni-500](http://www.quietpc.com/gb-en-gbp/products/120mmfans/sy-kazejyuni-500)

You can't hear it unless you put your ear right next to the fan intake.  Even after I took the tiny whiny fan out of the psu, the case (and core) is still running nice and cool - and inaudible - in a hot room.

---

### Post by PaulMic on 2009-08-27
Hi everyone, I've tried but the patch doesn't work.  Would it be because i'm using the server version of the kernel?  Thanks.

> **tg1 said:**
> I had to place the coretemp.ko file in /lib/modules/2.6.28-13-generic/kernel/drivers/hwmon/ and add a line with "coretemp" in /etc/modules :-)

---

### Post by Alfiegerner on 2009-08-27
PaulMic what does uname -a give you?

Incidentally, I got a zalman fan mate 2 for my ion A, lowered the voltage to 5v and it runs effectively silent from a distance of a metre away.  Temps get as high as 55 with burnBX running 4 times over all the virtual cores for 1 hour - happy days!

---

### Post by falstaff on 2009-08-29
Hello,

Thanks guys for this thread... I just get my Zotac ION D Board and I tried to read the cpu temperature for two hours now :-)

But I also found out some interesting infos, so here's what i know (or belive to know :-))

The Zotac ION boards use MCP79 Chipsatz, which contains an SMBus Controller at PCI 00:03:2. This SMBus Controler has I2C buses, which are usully used to connect sensors, but sensors-detect doesn't detect any there (might be because not supported, or not available at all...)
So we have to find out if there is something, and if yes, what... (thats what kzanol allready said...
On 2.6.31 Kernel seem to be a problem with loading nForce2_smbus:
$ dmesg | grep SMB
[    0.509972] ACPI: PCI Interrupt Link [LSMB] (IRQs 20 21 22 23) *11
[    7.776088] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x4d00
[    7.776118] nForce2_smbus 0000:00:03.2: Error probing SMB2.

I could avoid this problem by appending acpi_enforce_resources=lax. Nevertheless, there is no sensor detected by sensors-detect...

ACPI also supports temperature reading, called ACPI Thermal Zones. Its often used in Laptops, and seldom in normal motherboards... Zotac doesn't supports ACPI Thermal Zones, so no way here...

But what I didn't knew was that there is a cpu internal sensor, thanks kzanol.

I use karmic, so i had to compile the modul. There is a simple(r) way to do this (copy-n'-paste-able):
```

sudo aptitude install linux-source build-essential
cd /usr/src
sudo tar xvjf linux-source-2.6.31.tar.bz2
sudo wget http://mabene.icomedias.com/coretemp.patch
cd linux-source-2.6.31
sudo patch -p1 < ../coretemp.patch
sudo make -j 4 -C /lib/modules/2.6.31-8-generic/build M=/usr/src/linux-source-2.6.31/drivers/hwmon/ modules
# Test the driver:
sudo insmod drivers/hwmon/coretemp.ko
sensors
# Copy the driver and let it load on startup...
sudo cp drivers/hwmon/coretemp.ko /lib/modules/2.6.31-8-generic/kernel/drivers/hwmon/coretemp.ko
sudo su -c "echo coretemp.ko >> /etc/modules"

```


sensors shows:
```
$ sensors
coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +56.0°C  (crit = +95.0°C)                  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +52.0°C  (crit = +95.0°C)                  

coretemp-isa-0002
Adapter: ISA adapter
Core 2:      +56.0°C  (crit = +95.0°C)                  

coretemp-isa-0003
Adapter: ISA adapter
Core 3:      +52.0°C  (crit = +95.0°C)
```

Without active CPU-Cooling!
:guitar:

Bye
falstaff

---

### Post by graysky on 2009-09-04
Great thread!  I'm compiling right now on an Arch box (takes a LONG time on this Atom 330).

---

### Post by graysky on 2009-09-04
Is it possible to read the GPU temp and MB temp?

Nvclock doesn't recognize the GPU temp for example and I cannot find out which module is required for the motherboard's temp.

Thanks!

---

### Post by falstaff on 2009-09-07
@graysky: Motherboard Temp is not possible, we don't know which type it is (or it isn't supported)... We even doesn't know if there is any... 

I can read Nvidia temperature through gnome applet "sensors-applet"... But nvclock doesn't work for me too... I wrote the author an email...

Bye
falstaff

---

### Post by melado on 2009-09-09
Hey falstaff, thanks for your simple how-to.

I have Ubuntu Jaunty installed, with kernel 2.6.28-15. I tried your method, adapting the paths, and it kinda worked... 'sensors-detect' doesn't detect anything at all, but if I run 'sensors' I get only two -wrong- temperatures:

```
$ sensors
coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +20.0°C  (crit = +95.0°C)                  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +20.0°C  (crit = +95.0°C)        
```

Any ideas?

---

### Post by graysky on 2009-09-11
> **falstaff said:**
> @graysky: Motherboard Temp is not possible, we don't know which type it is (or it isn't supported)... We even doesn't know if there is any... 

I can read Nvidia temperature through gnome applet "sensors-applet"... But nvclock doesn't work for me too... I wrote the author an email...

Bye
falstaff

I posted at the zotac forums and [got this reply](http://www.zotacusa.com/forum/index.php?showtopic=1727).

> The sensor data is reported by the board, however the modules used to read this data must have support for the I2C/SMBus adapter used, in this case the NVIDIA MCP79 chipset.

---

### Post by falstaff on 2009-09-15
@melado:
Do you have loaded the newly compiled module? It seems you have only two cores detected by coretemp, do you have an Atom N230? Which board do you have? Maybe the author of the patch can help you, he is noted in the patch...

@graysky:
I didn't get any reply so far from nvclock's author... Its possible that nvidia uses only one sensor for both, northbridge and GPU. As I said, the closed source nvidia driver detects the temperatur sensor... I don't know if there is a difference between GPU temperatur sensors and northbridge temperature sensors...
The answer from Zotac is pretty useless. The kernel has support for I2C/SMBus from NVIDIA's MCP79 chipset. It is also detected by Kernel, see here (dmesg output):
...
[    7.871933] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x4d00
...

But sensor-detect doesnt find a sensor at the other side of the I2C/SMBus...

Next adapter: SMBus nForce2 adapter at 4d00 (i2c-0)
Do you want to scan it? (YES/no/selectively): 
Client found at address 0x4c
Probing for `National Semiconductor LM75'...                No
Probing for `Dallas Semiconductor DS75'...                  No
Probing for `Analog Devices ADT7466'...                     No
Probing for `Andigilog aSC7511'...                          No
Probing for `Dallas Semiconductor DS1621/DS1631'...         No
Probing for `Analog Devices ADM1021'...                     No
Probing for `Analog Devices ADM1021A/ADM1023'...            No
Probing for `Maxim MAX1617'...                              No
...

So interessting would be what kind of chip there is... 

Would be cool if you could ask this Zotac, I think they should know that.

Disclamer: I'm not an expert in such things, thats just the way I see the things... Might be that I am wrong :-)

Bye falstaff

---

### Post by falstaff on 2009-09-15
I found out something more...

The MCP79 Chipset is definitly supported by sensors-detect:
[http://www.lm-sensors.org/wiki/Devices]("http://www.lm-sensors.org/wiki/Devices")

I run the latest sensors-detect script, but no results...

Btw, it seems that Zotac forgot to fill in [DMI]("http://en.wikipedia.org/wiki/Desktop_Management_Interface") System/Board name (output of latest sensors-detect, which reads DMI):
```

# System: To Be Filled By O.E.M. To Be Filled By O.E.M.
# Board: To be filled by O.E.M. To be filled by O.E.M.

```
:lolflag:


bye
falstaff

---

### Post by Anonimoes on 2009-09-16
Thanks for this thread!

I'm actually not using a Zotac but the Point of View POV ION 330 mini itx mainboard. sensors detect does show a sensor detected but claims the module for it is nog developed yet. I'll post more info about this when I get home in a couple of hours. I'll try to compile the kernel patch as well then. (I'm using Suse so I'll have to compile i guess)

Just reading the cpu sensor would be a great thing! System would be nice but I guess it will take a while before the module is ready.

Edit:
Well, i got coretemp working, by piecing together information in this topic and other, more Opensuse specific, pages. I won't post my method here as it probably only works on opensuse and the ubuntu way was already described here. I will however note that when you are building the coretemp.ko mod you have to do this from kernel sources that are -exactly- the same version as the kernel you are currently using. I noticed this because at first I started to play around with kernel sources downloaded from the web as instructed here but it turned out that Opensuse employs their own specific kernel version. Once I was able to get this exact version by installing it through the package manager Yast2 everything came together and the new module loads nicely into the existing kernel using 'insmod'.

I can now see the following, wich is great!
```
coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +45.0°C  (crit = +95.0°C)

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +54.0°C  (crit = +95.0°C)

coretemp-isa-0002
Adapter: ISA adapter
Core 2:      +45.0°C  (crit = +95.0°C)

coretemp-isa-0003
Adapter: ISA adapter
Core 3:      +54.0°C  (crit = +95.0°C)
```

I don't think monitoring the northbridge/gpu temperatures will work as long as lm_sensors has no driver for it. A 'sensors-detect' on the POV ION 330 board returns this:
```
# sensors-detect revision 5337 (2008-09-19 17:05:28 +0200)

This program will help you determine which kernel modules you need
to load to use lm_sensors most effectively. It is generally safe  
and recommended to accept the default answers to all questions,   
unless you know what you're doing.                                

We can start with probing for (PCI) I2C or SMBus adapters.
Do you want to probe now? (YES/no): y                     
Probing for PCI bus adapters...                           
Found unknown SMBus adapter 10de:0aa2 at 0000:00:03.2.    
Sorry, no supported PCI bus adapters found.               

If you have undetectable or unsupported I2C/SMBus adapters, you can have
them scanned by manually loading the modules before running this script.

We are now going to do the I2C/SMBus adapter probings. Some chips may
be double detected; we choose the one with the highest confidence    
value in that case.                                                  
If you found that the adapter hung after probing a certain address,  
you can specify that address to remain unprobed.                     

Some chips are also accessible through the ISA I/O ports. We have to
write to arbitrary I/O ports to probe them. This is usually safe though.
Yes, you do have ISA I/O ports even if you do not have any ISA slots!   
Do you want to scan the ISA I/O ports? (YES/no): y                      
Probing for `National Semiconductor LM78' at 0x290...       No          
Probing for `National Semiconductor LM78-J' at 0x290...     No          
Probing for `National Semiconductor LM79' at 0x290...       No          
Probing for `Winbond W83781D' at 0x290...                   No          
Probing for `Winbond W83782D' at 0x290...                   No          
Probing for `IPMI BMC KCS' at 0xca0...                      No          
Probing for `IPMI BMC SMIC' at 0xca8...                     No          

Some Super I/O chips may also contain sensors. We have to write to
standard I/O ports to probe them. This is usually safe.
Do you want to scan for Super I/O sensors? (YES/no): y
Probing for Super-I/O at 0x2e/0x2f
Trying family `National Semiconductor'...                   No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Fintek'...                       Yes
Found `Fintek F71858DG Super IO Sensors'                    Success!
    (address 0xa00, driver `to-be-written')
Probing for Super-I/O at 0x4e/0x4f
Trying family `National Semiconductor'...                   No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Fintek'...                       No
Trying family `ITE'...                                      No

Some south bridges, CPUs or memory controllers may also contain
embedded sensors. Do you want to scan for them? (YES/no): y
Silicon Integrated Systems SIS5595...                       No
VIA VT82C686 Integrated Sensors...                          No
VIA VT8231 Integrated Sensors...                            No
AMD K8 thermal sensors...                                   No
AMD K10 thermal sensors...                                  No
Intel Core family thermal sensor...                         No
Intel AMB FB-DIMM thermal sensor...                         No
VIA C7 thermal and voltage sensors...                       No

Now follows a summary of the probes I have just done.
Just press ENTER to continue:

Driver `to-be-written' (should be inserted):
  Detects correctly:
  * ISA bus, address 0xa00
    Chip `Fintek F71858DG Super IO Sensors' (confidence: 9)

Do you want to overwrite /etc/sysconfig/lm_sensors? (YES/no): n
To load everything that is needed, add this to one of the system
initialization scripts (e.g. /etc/rc.d/rc.local):

#----cut here----
# Chip drivers
# no driver for Fintek F71858DG Super IO Sensors yet
/usr/bin/sensors -s
#----cut here----

If you have some drivers built into your kernel, the list above will
contain too many modules. Skip the appropriate ones! You really
should try these commands right now to make sure everything is
working properly. Monitoring programs won't work until the needed
modules are loaded.

```

This shows Super IO Sensors are detected but their values can't be read by lm_sensors. I know their must be a tempsensor for the northbridge because the BIOS shows a tempereture for it. I've done a little searching with regard to this Fintek super io sensors and have found that a section for it's detection has already been added to lm_sensors a couple of years ago but eversince the status of the driver remains 'to be written' so I doubt the lm_sensors team is giving the development of this driver any priority.

With regard to what I wrote above: Does someone have ideas about how one would be able to read the northbridge temp another way around?

---

### Post by Drikus on 2009-09-27
I see that multiple ion boards are discussed here so I might aswell put the ASUS AT3N7A-I to the list. It has an [_ITE_]("http://www.lm-sensors.org/wiki/Devices") sensor

```

sudo apt-get install lm-sensors

sudo sensors-detect

and check if you see this

Found unknown SMBus adapter 10de:0aa2 at 0000:00:03.2.

then

sudo modprobe i2c-dev
sudo modprobe i2c-nforce2
sudo su - 
echo "10de 0aa2" > /sys/bus/pci/drivers/nForce2_smbus/new_id 
ctrl ^D
i2cdetect -l 
sudo modprobe it87  
sensors 

it8720-isa-0290
Adapter: ISA adapter
in0:         +1.10 V  (min =  +0.00 V, max =  +4.08 V)   
in1:         +1.81 V  (min =  +0.00 V, max =  +4.08 V)   
in2:         +3.28 V  (min =  +0.00 V, max =  +4.08 V)   
in3:         +2.96 V  (min =  +0.00 V, max =  +4.08 V)   
in4:         +2.16 V  (min =  +3.95 V, max =  +4.08 V)   ALARM
in5:         +2.16 V  (min =  +0.00 V, max =  +4.08 V)   
in6:         +2.16 V  (min =  +0.00 V, max =  +4.08 V)   
in7:         +2.96 V  (min =  +0.00 V, max =  +4.08 V)   
in8:         +3.20 V
fan1:       6136 RPM  (min =    0 RPM)
fan2:          0 RPM  (min =    0 RPM)
fan3:          0 RPM  (min =    0 RPM)
temp1:       +22.0°C  (low  =  -1.0°C, high = +127.0°C)  sensor = thermistor
temp2:       +41.0°C  (low  =  -1.0°C, high = +127.0°C)  sensor = thermal diode
temp3:       +42.0°C  (low  =  -1.0°C, high = +127.0°C)  sensor = thermistor
cpu0_vid:   +2.050 
```

---

### Post by -Thomas- on 2009-09-30
Hey Drikus,  thanks for sharing these infos. I have an AT3N7A-I board and tried hard to get the sensors up and running with Kernel version 2.6.31. In addition to your steps I had to append "acpi_enforce_resources=lax" as a Kernel parameter to get the it87 module loaded correctly. I hope this info can be of help for some other people.  Best regards Thomas

---

### Post by Arlukin on 2009-10-10
> **kzanol said:**
> n the meantime you can either patch your kernel source to add coretemp support for the atom CPU ([http://mabene.icomedias.com/coretemp.patch](http://mabene.icomedias.com/coretemp.patch)) or you can use my patched coretemp.ko module (works with current jaunty kernel linux-image-2.6.28-13-generic, [http://mabene.icomedias.com/coretemp.ko](http://mabene.icomedias.com/coretemp.ko))  bye, Martin
Looks like Martins has removed the files from his server. Did anyone else store the files? Or atleast the contents of the patch?

---

### Post by djondjoe on 2009-10-22
I tried this on the Asrock ION 330, but it did not work, as it just showed 20 degrees for all the sensors.
Does anyone have a working kernel for this yet?

---

### Post by eversteegt on 2009-10-22
@Drikus: Thanks for posting the sensors-detect procedure for  ASUS AT3N7A-I. On my system it was not necessary. Apparently, my previous mainboard also had the exact same module for sensors :D

The custom-compiled coretemp module also works, but posts error messages in the kernel log about an unrecognized CPU. After that, the sensor output gives temperatures for 4 cores, though, of which 2 pairs have the same temps (it tries to detect a CPU for all 4 "logical cpu's" detected by the kernel?). 

Anyway, I think it is just a matter of waiting before the Atom 330 gets supported fully. For now, I only have to monitor the temperatures for a while, because I let the little fan run a lot quieter by putting a resistor between the fan and the cpu_fan header.

---

### Post by slider257 on 2009-10-23
I compiled 2.6.32-rc5 today and the coretemp.patch seems to be included now, but my core temperature appears 2-3° less than before.
sensors-detect still shows "no sensors detected", but running "sensors" shows 4 core temperatures.
still nothing about fan speed though...

btw: Zotac IONITX-A-E

---

### Post by twoofseven on 2009-11-02
Maybe this is not new for you. But I didn't found this in the thread.

I had a look at latest lm-sensor trunk file [http://www.lm-sensors.org/browser/lm-sensors/trunk/prog/detect/sensors-detect](http://www.lm-sensors.org/browser/lm-sensors/trunk/prog/detect/sensors-detect). As you can see at line 1715, lm-sensor would load module "f71882fg".

Therefore I tried the following on my Point Of View ION330 with Ubuntu 9.10 Karmic Koala.

```
$ sudo modprobe f71882fg

$ sudo dmesg | tail

[38738.846664] i2c /dev entries driver
[40928.976351] f71882fg: Found f71858fg chip at 0xa00, revision 35
[40928.976710] f71882fg f71882fg.2560: Fan: 1 is in duty-cycle mode
[40928.976717] f71882fg f71882fg.2560: Fan: 2 is in duty-cycle mode
[40928.976723] f71882fg f71882fg.2560: Fan: 3 is in duty-cycle mode

$ sudo sensors
f71858fg-isa-0a00
Adapter: ISA adapter
in0:         +1.66 V
in1:         +1.66 V
in2:         +1.58 V
fan1:        628 RPM
fan2:          0 RPM  ALARM
fan3:          0 RPM  ALARM
temp1:       +48.6°C  (high = +70.0°C, hyst = +60.0°C)  
temp2:       +52.6°C  (high = +100.0°C, hyst = +85.0°C)  sensor = transistor
temp3:       +63.9°C  (high = +100.0°C, hyst = +85.0°C) 

$ sudo echo "f71882fg" >> /etc/modules
```I hope this will help.

---

### Post by jbernardo on 2009-11-02
Unfortunately that sensor doesn't work on my Point of View ION-MB330-1. It seems they changed sensors between revisions. :(

---

### Post by ZioNemo on 2009-11-05
FYI:
I tried to revive the thread on Zotac forums: [reading-gpu-temp-and-mb-temp]("http://www.zotacusa.com/forum/index.php?/topic/1727-reading-gpu-temp-and-mb-temp").

Let's hope some kind soul will answer...

Regards
ZioNemo

---

### Post by Gudi on 2009-11-13
Has anyone figured it out?

I've tryed to get some readings out of my Asrock ION 330 but I'm pretty sure my readings are incorrect:

coretemp-isa-0000
Adapter: ISA adapter
Core 0:       +8.0Â°C  (crit = +95.0Â°C)

coretemp-isa-0001
Adapter: ISA adapter
Core 1:       +5.0Â°C  (crit = +95.0Â°C)

coretemp-isa-0002
Adapter: ISA adapter
Core 2:       +8.0Â°C  (crit = +95.0Â°C)

coretemp-isa-0003
Adapter: ISA adapter
Core 3:       +5.0Â°C  (crit = +95.0Â°C)

If they are correct, then i guess the reading should be 95-8=87degrees... I just don't believe that!...

Has anyone figures to use lm-sensors on their ION 330?

---

### Post by Gudi on 2009-11-13
xbmc@xbmc:~$ uname -a
Linux xbmc 2.6.28-16-generic #55-Ubuntu SMP Tue Oct 20 19:48:24 UTC 2009 i686 GNU/Linux

apt-get install lm-sensors

----------------------------------

cd /tmp
wget [http://www.lm-sensors.org/svn/lm-sensors/trunk/prog/detect/sensors-detect](http://www.lm-sensors.org/svn/lm-sensors/trunk/prog/detect/sensors-detect)
perl sensors-detect

# sensors-detect revision $Revision$
# System: To Be Filled By O.E.M. To Be Filled By O.E.M.
# Board: ASRock AMCP7A-ION

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
AMD Family 11h thermal sensors...                           No
Intel Core family thermal sensor...                         Success!
    (driver `coretemp')
Intel AMB FB-DIMM thermal sensor...                         No
VIA C7 thermal and voltage sensors...                       No

Some Super I/O chips contain embedded sensors. We have to write to
standard I/O ports to probe them. This is usually safe.
Do you want to scan for Super I/O sensors? (YES/no): y
Probing for Super-I/O at 0x2e/0x2f
Trying family `National Semiconductor'...                   No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Nuvoton/Fintek'...               No
Trying family `ITE'...                                      No
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
Using driver `i2c-nforce2' for device 0000:00:03.2: nVidia Corporation nForce SMBus (MCP79)

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

Next adapter: SMBus nForce2 adapter at 4d00 (i2c-3)
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

Next adapter: SMBus nForce2 adapter at 4e00 (i2c-4)
Do you want to scan it? (YES/no/selectively): y
Client found at address 0x50
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 Yes
    (confidence 8, not a hardware monitoring chip)
Probing for `EDID EEPROM'...                                No
Client found at address 0x51
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 Yes
    (confidence 8, not a hardware monitoring chip)

Now follows a summary of the probes I have just done.
Just press ENTER to continue:

Driver `coretemp':
  * Chip `Intel Core family thermal sensor' (confidence: 9)

Do you want to overwrite /etc/sysconfig/lm_sensors? (YES/no): y
Copy prog/init/lm_sensors.init to /etc/init.d/lm_sensors
for initialization at boot time.
You should now start the lm_sensors service to load the required
kernel modules.


------------------

sudo modprobe coretemp

sensors

coretemp-isa-0000
Adapter: ISA adapter
Core 0:       +8.0Â°C  (crit = +95.0Â°C)

coretemp-isa-0001
Adapter: ISA adapter
Core 1:       +7.0Â°C  (crit = +95.0Â°C)

coretemp-isa-0002
Adapter: ISA adapter
Core 2:       +8.0Â°C  (crit = +95.0Â°C)

coretemp-isa-0003
Adapter: ISA adapter
Core 3:       +8.0Â°C  (crit = +95.0Â°C)

..... This can't be right?

---

### Post by ZedThou on 2009-11-13
No Gudi, those are well below room temp and quite chilly so unlikely to be correct. Have you tried the 2.6.32-rc7 kernel? That has shown some small improvement with coretemp on my IONITX-A CPU. And the GPU temp has always been available with 'nvidia-settings -q GPUCoreTemp'

---

### Post by evlas on 2009-12-03
> **jbernardo said:**
> Unfortunately that sensor doesn't work on my Point of View ION-MB330-1. It seems they changed sensors between revisions. :(

I wrote a POV. This is the answer:

Dear Sir,

Thank you for having our product.

Unfortunately the motherboard is not capable of controlling the fanspeed.


Kind Regards,

Point of View
Technical Department

Don't buy the POV ION-MB330-1!!!!

---

### Post by falstaff on 2009-12-06
I wrote a support request to Zotac with the link to ZioNemo's forum thread. I complained about no ability to control fan's and read temperatur values. This is what I get replied. 

> 
I have read your forum topic.

You are correct about not knowing where the other side of the phone cable leads too.

The ION board uses "Hardware Monitoring Logic" for temp, fan speed control. Inside the Nvidia MCP7A Chipset's internal registers are not the same or found lm-sensor software.

A solution is to read the temp of the cpu by placing an external sensor near it. Also, modifying the cpu's fan speed using a third party solution.

The BIOS can read the chips data and control the fan internally but it is using a different address.

Currently, a BIOS update is planned to address this issue for third-party software. Please update to the latests update. I believe the latests BIOS currently allows you to read the cpu temp if I am not mistaken.

bye
falstaff

---

### Post by dk75 on 2009-12-06
The latest BIOS is pa108.zip from 13 august 2009 and ironically I have it inside as production version but still I can't monitor fans under system. BIOS only and it reports SYS fan only, zero CPU fan (which is fabrically mounted).

So no monitoring by lm-sensors and BIOS even can't monitor CPU fan to.

---

### Post by ThomasNovin on 2009-12-15
This coretemp.ko doesn't load under Karmic (2.6.31-16 currently). Has anyone compiled a version for this kernel?

---

### Post by dk75 on 2009-12-15
yes

---

### Post by ThomasNovin on 2009-12-16
Looks OK but doesn't load.

```

$ uname -r
2.6.31-16-generic
$ strings coretemp.ko | grep vermagic
vermagic=2.6.31.4 SMP mod_unload modversions 
$ sudo modprobe coretemp
FATAL: Error inserting coretemp (/lib/modules/2.6.31-16-generic/kernel/drivers/hwmon/coretemp.ko): Invalid module format

```

---

### Post by ThomasNovin on 2009-12-16
OK since the above attachment didn't work and it's pretty stupid to load kernel modules from random people/forums (your system could be rootkited) I decided to compile it myself.

```

$ cd /usr/src
$ sudo wget http://mabene.icomedias.com/coretemp.patch
$ sudo aptitude install linux-source-$(uname -r | awk -F'-' '{print $1}')
$ sudo tar jxvf linux-source-$(uname -r | awk -F'-' '{print $1}').tar.bz2
$ cd linux-source-$(uname -r | awk -F'-' '{print $1}')
$ sudo patch -p1 <../coretemp.patch
$ cd drivers/hwmon
$ cat <<_EOF_ | sudo tee Makefile
obj-m += coretemp.o

all:
	make -C /lib/modules/\$(shell uname -r)/build M=\$(PWD) modules

clean:
	make -C /lib/modules/\$(shell uname -r)/build M=\$(PWD) clean
_EOF_
$ sudo make
$ sudo cp coretemp.ko /lib/modules/$(uname -r)/kernel/drivers/hwmon/
$ sudo rm Makefile
$ sudo modprobe coretemp

```

To also automatically load it at startup

```

$ echo -e "#Load coretemp to be able to read values with sensors(1)\ncoretemp" | sudo tee -a /etc/modules

```

This works! 

(Although, on my ION 330-HT which is different from the old 330 I just get very low temperature readings, between 9-17 degrees centigrade.)

Edit: Pretty much this was already suggested in [post 28]("http://ubuntuforums.org/showpost.php?p=7865731&postcount=28")

Edit2: Updated to work on any kernel.

---

### Post by AMMOnium on 2010-01-04
I can confirm the behavior of "coretemp" module on **Zotac IONITX-D-E** and Karmic **2.6.31-16**-generic. ([https://bugs.launchpad.net/ubuntu/+source/linux/+bug/296478]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/296478")) 

As for motherboard integrated sensors, 
lm-sensors rev 5813 from SVN outputs the following:
```

...
Driver `to-be-written':
  * Bus `SMBus nForce2 adapter at 4d00'
    Busdriver `i2c_nforce2', I2C address 0x4c
    Chip `[COLOR="Red"]Winbond W83L771AWG/ASG[/COLOR]' (confidence: 6)

Driver `coretemp':
  * Chip `Intel Atom thermal sensor' (confidence: 9)
...

```

The changes for this chip were introduced after this thread [http://lists.lm-sensors.org/pipermail/lm-sensors/2009-December/027406.html]("http://lists.lm-sensors.org/pipermail/lm-sensors/2009-December/027406.html") 
One can temporarily force the chip as lm86 with "lm90" module (and/or wait for a proper solution). 

I got the following:

```

...
# modprobe lm90 force_lm86=0,0x4c
# sensors
coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +26.0°C  (crit = +95.0°C)

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +27.0°C  (crit = +95.0°C)

coretemp-isa-0002
Adapter: ISA adapter
Core 2:      +26.0°C  (crit = +95.0°C)

coretemp-isa-0003
Adapter: ISA adapter
Core 3:      +27.0°C  (crit = +95.0°C)

lm86-i2c-0-4c
Adapter: SMBus nForce2 adapter at 4d00
M/B Temp:    +32.0°C  (low  = -40.0°C, high = +70.0°C)
                      (crit = +85.0°C, hyst = +75.0°C)
CPU Temp:    +41.1°C  (low  = -40.0°C, high = +70.0°C)
                      (crit = +110.0°C, hyst = +100.0°C)
...

```

coretemp readings seem to be correct (plausible increase when manually slowing down the case fan with an external voltage regulator)

But the 15° gap between coretemp readings and CPU temp from i2c is somewhat suspicious.  
Maybe the "CPU" sensor is physically located in a hotter area of the board (or maybe in fact it is a GPU sensor :) ).

---

### Post by dk75 on 2010-01-04
at RICOTZ PPA's there's Lucid kernel ( 2.6.32-9.13 ) among other stuff ( ALSA and PulseAudio Lucid backported - HDMI sound for ION ) and coretemp is already patched.

---

### Post by tcchris on 2010-02-04
Not really into rebuilding or patching kernals .
Will this be resolved in lucid ?
If so I will wait till April

---

### Post by dk75 on 2010-02-05
yes
```
ppa:ricotz/unstable
```
ALSA,PulseAudio and kernel from Lucid

---

### Post by tcchris on 2010-02-05
great !! I don't mind waiting a couple months

---

### Post by graysky on 2010-06-06
Any updates on this issue?  I have an Arch Linux box running on a Zotac IONITX A-U.

Kernel version: 2.6.34
Sensors version: 3.1.2

```
# sensors-detect 
# sensors-detect revision 5818 (2010-01-18 17:22:07 +0100)
# System: To Be Filled By O.E.M. To Be Filled By O.E.M.
# Board: To be filled by O.E.M. To be filled by O.E.M.

This program will help you determine which kernel modules you need
to load to use lm_sensors most effectively. It is generally safe
and recommended to accept the default answers to all questions,
unless you know what you're doing.

Some south bridges, CPUs or memory controllers contain embedded sensors.
Do you want to scan for them? This is totally safe. (YES/no): 
Silicon Integrated Systems SIS5595...                       No
VIA VT82C686 Integrated Sensors...                          No
VIA VT8231 Integrated Sensors...                            No
AMD K8 thermal sensors...                                   No
AMD Family 10h thermal sensors...                           No
AMD Family 11h thermal sensors...                           No
Intel Core family thermal sensor...                         No
Intel Atom thermal sensor...                                Success!
    (driver `coretemp')
Intel AMB FB-DIMM thermal sensor...                         No
VIA C7 thermal sensor...                                    No
VIA Nano thermal sensor...                                  No

Some Super I/O chips contain embedded sensors. We have to write to
standard I/O ports to probe them. This is usually safe.
Do you want to scan for Super I/O sensors? (YES/no): 
Probing for Super-I/O at 0x2e/0x2f
Trying family `National Semiconductor'...                   No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Nuvoton/Fintek'...               No
Trying family `ITE'...                                      No
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
interfaces? (YES/no): 
Probing for `IPMI BMC KCS' at 0xca0...                      No
Probing for `IPMI BMC SMIC' at 0xca8...                     No

Some hardware monitoring chips are accessible through the ISA I/O ports.
We have to write to arbitrary I/O ports to probe them. This is usually
safe though. Yes, you do have ISA I/O ports even if you do not have any
ISA slots! Do you want to scan the ISA I/O ports? (YES/no): 
Probing for `National Semiconductor LM78' at 0x290...       No
Probing for `National Semiconductor LM79' at 0x290...       No
Probing for `Winbond W83781D' at 0x290...                   No
Probing for `Winbond W83782D' at 0x290...                   No

Lastly, we can probe the I2C/SMBus adapters for connected hardware
monitoring devices. This is the most risky part, and while it works
reasonably well on most systems, it has been reported to cause trouble
on some systems.
Do you want to probe the I2C/SMBus adapters now? (YES/no): 
Using driver `i2c-nforce2' for device 0000:00:03.2: nVidia Corporation nForce SMBus (MCP79)
Module i2c-dev loaded successfully.

Next adapter: SMBus nForce2 adapter at 4d00 (i2c-0)
Do you want to scan it? (YES/no/selectively): 
Client found at address 0x4c
Handled by driver `lm90' (already loaded), chip type `w83l771'
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

Next adapter: SMBus nForce2 adapter at 4e00 (i2c-1)
Do you want to scan it? (YES/no/selectively): 
Client found at address 0x50
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 Yes
    (confidence 8, not a hardware monitoring chip)
Probing for `EDID EEPROM'...                                No
Client found at address 0x51
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 Yes
    (confidence 8, not a hardware monitoring chip)

Now follows a summary of the probes I have just done.
Just press ENTER to continue: 

Driver `coretemp':
  * Chip `Intel Atom thermal sensor' (confidence: 9)

Driver `lm90':
  * Bus `SMBus nForce2 adapter at 4d00'
    Busdriver `i2c_nforce2', I2C address 0x4c
    Chip `w83l771' (confidence: 6)

Do you want to overwrite /etc/conf.d/lm_sensors? (YES/no): n
To load everything that is needed, add this to one of the system
initialization scripts (e.g. /etc/rc.d/rc.local):

#----cut here----
# Chip drivers
modprobe coretemp
modprobe lm90
/usr/bin/sensors -s
#----cut here----

If you have some drivers built into your kernel, the list above will
contain too many modules. Skip the appropriate ones! You really
should try these commands right now to make sure everything is
working properly. Monitoring programs won't work until the needed
modules are loaded.

Unloading i2c-dev... OK
```

With both the coretemp and lm90 modules loaded, I get the following output:

```
$ sensors
coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +24.0°C  (crit = +90.0°C)                  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +22.0°C  (crit = +90.0°C)                  

coretemp-isa-0002
Adapter: ISA adapter
Core 2:      +24.0°C  (crit = +90.0°C)                  

coretemp-isa-0003
Adapter: ISA adapter
Core 3:      +22.0°C  (crit = +90.0°C)                  

w83l771-i2c-0-4c
Adapter: SMBus nForce2 adapter at 4d00
temp1:       +29.0°C  (low  = -40.0°C, high = +70.0°C)  
                      (crit = +85.0°C, hyst = +75.0°C)  
temp2:       +41.1°C  (low  = -40.0°C, high = +70.0°C)  
                      (crit = +110.0°C, hyst = +100.0°C)
```

Summary of what's working:
[LIST]
[*]Coretemp sensor
[*]CPU temp sensor
[*]M/B temp sensor
[/LIST]

Summary of what's NOT working: 
[LIST]
[*]CPU fan RPM
[*]M/B fan RPM
[/LIST]
Both of these appear in the BIOS. Thoughts?

---

### Post by dk75 on 2010-06-06
It seems that there will be not a new BIOS for ZOTAC old ION boards so we are in slump with that.

---

