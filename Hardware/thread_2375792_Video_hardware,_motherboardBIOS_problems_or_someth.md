---
title: "Video hardware, motherboard/BIOS problems or something else?"
date: 2017-10-27
forum: Hardware
---

### Post by A Traveller on 2017-10-27
Hi All.

Desktop PC
AMD PhenomII X6 1100T
GA-890GPA-UD3H Motherboard
4 x 2Gb G Skill RAM
NVIDIA GeForce GTX 460 Graphics Card

I am having problems with my pc and was hoping someone could point me in the right direction regarding which part of the pc is causing the problems.

I think it started with the pc freezing completely on YouTube videos. Then it started restarting on its own (whether on YouTube or not). The problem has slowly gotten worse and worse until it has reached the point where several restarts are required, allowing me to use the pc for a few minutes (or seconds) at a time before crashing or restarting. The pc stopped loading altogether, so I set the BIOS to use onchip graphics and disconnected the graphics card and removed it from the pc and attaching the monitor to the motherboard via VGA. This did allow the pc to start but it still has the same problems and even more! When it does decide it wants to get past the Gigabyte splash screen, the monitor will go blank, but not completely off, and then, in order to get a display again, the monitor has to be turned off and then on again (sometimes the monitor's button has to be pressed about six times for it to go off) and then the configuration options appear, e.g. reconfigure graphics, restart x, etc. The first option seems to work, can't remember the exact words, but I think it's an option to use basic settings or something (please note that at times, the monitor does go completely off, ie. no signal detected). This then allows the login screen to appear and I can log in.

I have also replaced the CMOS battery, which will have restored the BIOS to default settings but this hasn't made any difference.

Am I correct to assume this has nothing to do with the OS or the hard drive as the above processes do not involve these components?

Is there some part of the motherboard that would cause both a separate graphics card AS WELL AS the onboard graphics to stop working correctly if it were to fail? If so, what is it?

I have gotten to the point where I would consider a BIOS flash.

Any advice would be appreciated. If I do not respond to any replies promptly, you can safely assume that I cannot get into my pc!

Thanks.

EDIT: I haven't introduced any relevant new parts to the pc; have been using the same major setup for a number of years before the problem started.

---

### Post by Autodave on 2017-10-27
That sounds like a RAM chip(s) going bad. If it has more than one stick of memory, try removing one of them and running the PC. If still the same problem, try removing a different one. Alway make sure that you fill the slots in order. If and when you get a stick out and the PC runs OK, the bad stick is obviously the one not in the machine. :-)

---

### Post by Yellow Pasque on 2017-10-27
The possibility of overheating northbridge also comes to mind in addition to the above suggestion. Check the heatsink on it real good. Dust it out (compressed air) and make sure it has not come loose. Monitor temps closely:
```
sensors
```

---

### Post by A Traveller on 2017-10-28
Thanks for the replies.

Can't type much details; have barely managed to get this far after SEVERAL restarts! It cuts out in about five seconds after logging in at present.

Anyway, have tried the following but it didn't work.

Have four RAM sticks. Pulled out the 4th one, restarted, pulled out the third one, restarted, put the first and third one in the first and third slots and restarted, put the second and fourth one in the second and fourth slots and restarted, but all with the same problem. Graphics are also very wavy and unstable.

Have not got compressed air; will check this when the pc crashes next as I don't want to turn it off since it's worked for this long today (a few minutes). It worked for hours yesterday without crashing.

Thanks. Better hit reply now!

EDIT: Autodave, by "slots in order", do you mean I shouldn't have left a gap when testing two sticks?

---

### Post by Yellow Pasque on 2017-10-28
Please give the output of sensors command as requested. Note that if the CPU or another component is overheating, you risk damaging it beyond use if you continue to run the system.

>  by "slots in order", do you mean I shouldn't have left a gap when testing two sticks? 

I believe that's what he meant. Check the mobo manual to be sure.

---

### Post by Autodave on 2017-10-28
If you put memory sticks in slots 1 and 3, only the one in slot #1 will function. 2 sticks = slots 1 & 2 are being used.

---

### Post by A Traveller on 2017-10-29
OK, thanks. Will re-try.

In the meantime, latest symptoms are, IF the splash screen appears in full (without technicolour/black banding), screen goes blank before login. Monitor has to be turned off and on to see login. Monitor goes off within a second or two. Have to keep turning the monitor off and on to see/do anything. The pc seems to be working off-screen, i.e. can listen to media whilst screen is blank. At the moment it has finally afforded me some time again! If it does need a motherboard flash, will have to do so pretty quick before pc goes completely! My OS is old so couldn't see the file at the Gigabyte website for my version 2.1 board. Is it there?

Thanks.

---

### Post by Yellow Pasque on 2017-10-29
If your system has worked for years and begins to experience issues, a BIOS update isn't the answer. Furthermore, if the system isn't stable, flashing it is like playing Russian roulette.

---

### Post by A Traveller on 2017-10-31
Thanks for your reply, Temujin.

I have now tried RAMs 3 and 4 in slots 1 and 2. I had previosuly tried RAMs 1 and 2 in slots 1 and 2, but this hasn't worked either. If a BIOS flash isn't the solution, then I'm thinking that whatever part of the motherboard that controls the graphics card and the onboard graphics is causing the problem and the motherboard needs changing, unless there's anything else that could be the cause. With the graphics card, the pc kept restarting itself so I'm thinking it's not the monitor. Now there is not much restarting (if any) with the onboard graphics but the monitor going off (not totally off, where the monitor LED changes colour (standby?) but totally black.

Thanks.

---

### Post by Autodave on 2017-10-31
Power supply is another common issue that will give you those symptoms.

---

### Post by Autodave on 2017-10-31
Unfortunately, ther are quite a few different things that could cause the issue that you are having. Without any spare parts laying around, there is not much more that you can do.

---

### Post by A Traveller on 2017-10-31
OK thanks Autodave.

---

### Post by Yellow Pasque on 2017-10-31
Yeah, without a spare PSU and/or CPU, it's tough to troubleshoot. If it was just the monitor shutting off, I'd suggest trying a different monitor and video cable, but your description tells us it's deeper than a pure video problem.

> then I'm thinking that whatever part of the motherboard that controls the graphics card and the onboard graphics is causing the problem

Once again, I would double check that the heatsinks on the northbrige and power delivery (the heatsinks that say 'Gigabyte' and 'Ultra Durable' respectively) have not come loose.
I would also look at temps. (I asked you for the sensors output twice, but you ignored me). My motherboard uses the same AMD 890 chipset (the FX version without onboard graphics) and the chipset sits at about 60C at idle.

---

### Post by coldraven on 2017-11-01
Regarding power supplies, I recently bought one of these testers on eBay. In the youtube video he forgets to say that the Standby 5 volt is shown on the screen as 5VSB.
I too had no idea how to use it until I watched a couple of videos, it's a handy tool for diagnosing problems.
[https://www.youtube.com/watch?v=T-jG3vqRQHM](https://www.youtube.com/watch?v=T-jG3vqRQHM)

Edit for clarity: Exactly the same tester as shown in the video.

---

### Post by poorguy on 2017-11-01
The power supply testers you buy only show the output voltages which is helpful.

The only way to reliably to test a power supply is while it is under a load.

The only way to make certain is to replace the existing power supply with a known good working power supply.

And yes this is a gamble but a sure way to eliminate a faulty power supply.

My 2 cents worth.

---

### Post by A Traveller on 2017-11-02
Temujin, really sorry, I somehow missed your request both times! I just looked back in the thread an noticed them. I'm going to put this down to trying to look at the replies as fast as I can and reply as fast as I can while the monitor stays on.

Thanks for your advice coldraven and poorguy. Before I consider your suggestions, I'd like to provide an update, which may or may not affect whether I need to follow your advice or not.

All day today, despite numerous restarts of the pc and the monitor, it only stayed on for a few seconds at a time. The pc doesn't seem to restart on it's own any more (as far as I know). This could be to do with using onboard graphics instead of the card. Anyhow, managed to get into BIOS and load failsafe defaults. This seems to have worked (except of course the display is in low graphics), bit it WORKS!

Does this info help narrow down the issue?

Also, will the load failsafe defaults setting now be saved permanently or will I have to enter BIOS and load them again IF I dare to turn my pc off?

Thanks.

---

### Post by A Traveller on 2017-11-03
Hi All.

I have learnt that the load failsafe defaults have been set permanently, which is good!

Even though the monitor stayed on for 2 or 3 hours (before I shut down), it was flickering at times and I felt like it was trying its best to go off. It didn't, but when I turned my pc back on, the problem reappeared, although it only required about 3 restarts of the monitor and it also flashed the display on and off without restarting the monitor, which did not happen before. Before, a monitor restart was always required to get any display at all.

Anyway, below is the output from sensors.

Thanks.


root@computer:/home/mycomputer# sudo sensors-detect
# sensors-detect revision 5818 (2010-01-18 17:22:07 +0100)
# System: Gigabyte Technology Co., Ltd. GA-890GPA-UD3H

This program will help you determine which kernel modules you need
to load to use lm_sensors most effectively. It is generally safe
and recommended to accept the default answers to all questions,
unless you know what you're doing.

Some south bridges, CPUs or memory controllers contain embedded sensors.
Do you want to scan for them? This is totally safe. (YES/no): YES
Silicon Integrated Systems SIS5595...                       No
VIA VT82C686 Integrated Sensors...                          No
VIA VT8231 Integrated Sensors...                            No
AMD K8 thermal sensors...                                   No
AMD Family 10h thermal sensors...                           Success!
    (driver `k10temp')
AMD Family 11h thermal sensors...                           No
Intel Core family thermal sensor...                         No
Intel Atom thermal sensor...                                No
Intel AMB FB-DIMM thermal sensor...                         No
VIA C7 thermal sensor...                                    No
VIA Nano thermal sensor...                                  No

Some Super I/O chips contain embedded sensors. We have to write to
standard I/O ports to probe them. This is usually safe.
Do you want to scan for Super I/O sensors? (YES/no): YES
Probing for Super-I/O at 0x2e/0x2f
Trying family `National Semiconductor'...                   No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Nuvoton/Fintek'...               No
Trying family `ITE'...                                      Yes
Found `ITE IT8720F Super IO Sensors'                        Success!
    (address 0x228, driver `it87')
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
interfaces? (YES/no): YES
Probing for `IPMI BMC KCS' at 0xca0...                      No
Probing for `IPMI BMC SMIC' at 0xca8...                     No

Some hardware monitoring chips are accessible through the ISA I/O ports.
We have to write to arbitrary I/O ports to probe them. This is usually
safe though. Yes, you do have ISA I/O ports even if you do not have any
ISA slots! Do you want to scan the ISA I/O ports? (yes/NO): yes
Probing for `National Semiconductor LM78' at 0x290...       No
Probing for `National Semiconductor LM79' at 0x290...       No
Probing for `Winbond W83781D' at 0x290...                   No
Probing for `Winbond W83782D' at 0x290...                   No

Lastly, we can probe the I2C/SMBus adapters for connected hardware
monitoring devices. This is the most risky part, and while it works
reasonably well on most systems, it has been reported to cause trouble
on some systems.
Do you want to probe the I2C/SMBus adapters now? (YES/no): YES
Using driver `i2c-piix4' for device 0000:00:14.0: ATI Technologies Inc SB600/SB700/SB800 SMBus
WARNING: Deprecated config file /etc/modprobe.conf, all config files belong into /etc/modprobe.d/.
Module i2c-dev loaded successfully.

Now follows a summary of the probes I have just done.
Just press ENTER to continue: 

Driver `it87':
  * ISA bus, address 0x228
    Chip `ITE IT8720F Super IO Sensors' (confidence: 9)

Driver `k10temp':
  * Chip `AMD Family 10h thermal sensors' (confidence: 9)

Warning: the required module k10temp is not currently installed
on your system. If it is built into the kernel then it's OK.
Otherwise, check [http://www.lm-sensors.org/wiki/Devices](http://www.lm-sensors.org/wiki/Devices) for
driver availability.

To load everything that is needed, add this to /etc/modules:
#----cut here----
# Chip drivers
it87
#----cut here----
If you have some drivers built into your kernel, the list above will
contain too many modules. Skip the appropriate ones!

Do you want to add these lines automatically to /etc/modules? (yes/NO)yes
Successful!

Monitoring programs won't work until the needed modules are
loaded. You may want to run '/etc/init.d/module-init-tools start'
to load them.

Unloading i2c-dev... OK

root@computer:/home/mycomputer# sudo sensors-detect/etc/init.d/module-init-tools start
sudo: sensors-detect/etc/init.d/module-init-tools: command not found
root@computer:/home/mycomputer# /etc/init.d/module-init-tools start
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service module-init-tools start

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the start(8) utility, e.g. start module-init-tools
module-init-tools stop/waiting
root@computer:/home/mycomputer# module-init-tools stop/waiting
module-init-tools: command not found
root@computer:/home/mycomputer#

---

### Post by because7892 on 2017-11-04
could be a number of things, one thing i would check is for over heating of either the processors such as the CPU and also check to make sure that the north bridge is not overheating. it could also be bad ram so try switching the dim slots that the ram is in. it could also just be a dying board. it should not be caused bu the OS or HDD because you said that it is happening in the bios flash screen and the hard drive would be used right after that when it is booting into the OS. if you can find a another board that supports your hardware like ram and CPU you should try that because it sounds like a motherboard issue.

---

### Post by A Traveller on 2017-11-04
Thanks for your reply, because7892.

Thanks for the advice everyone. Will post back if I find the problem.

---

### Post by A Traveller on 2017-11-09
STRANGE UPDATE.

As the issue was happening even before the BIOS/splash screen, as you said, it can't be the OS or HD, HOWEVER, the resolution on my second Ubuntu drive seems normal. How can I be on failsafe defaults with one HD on expected low resolution but the other normal??

Thanks.

---

### Post by A Traveller on 2018-05-21
Hi all.

I never got to the bottom of this issue and I've been putting up with the symptoms all this time. The latest behaviour (for the past few months) is when the PC is turned on, the monitor flashes on and off several times until it decides to stay on, which can be after several minutes. The pc works as normal in the background, i.e. whilst the monitor is black, I can guess which stage the startup process is at and can type my login details and press Enter, etc, at the correct times to login, then just wait until the monitor stops flashing and allows me to use the PC.

The latest output from 'sensors' is as follows.

it8720-isa-0228
Adapter: ISA adapter
in0:         +1.22 V  (min =  +0.00 V, max =  +4.08 V)   
in1:         +1.50 V  (min =  +0.00 V, max =  +4.08 V)   
in2:         +3.36 V  (min =  +0.00 V, max =  +4.08 V)   
in3:         +2.98 V  (min =  +0.00 V, max =  +4.08 V)   
in4:         +3.04 V  (min =  +0.00 V, max =  +4.08 V)   
in5:         +2.29 V  (min =  +0.00 V, max =  +4.08 V)   
in6:         +4.08 V  (min =  +0.00 V, max =  +4.08 V)   
in7:         +2.96 V  (min =  +0.00 V, max =  +4.08 V)   
Vbat:        +3.31 V
fan1:       1328 RPM  (min =    0 RPM)
fan2:        432 RPM  (min =    0 RPM)
fan3:          0 RPM  (min =    0 RPM)
fan5:          0 RPM  (min =    0 RPM)
temp1:       +40.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermistor
temp2:       +44.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermal diode
temp3:       +48.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermistor
cpu0_vid:   +0.513 V


Anyway, this is just an update. I think it's time I got a new motherboard.

---

