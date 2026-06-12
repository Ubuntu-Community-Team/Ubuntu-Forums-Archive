---
title: "No sensors detected"
date: 2014-10-02
forum: Hardware
---

### Post by nickdc on 2014-10-02
I'd be very grateful for advice concerning possible cpu overheating issues and Ubuntu's monitoring capabilities.

 

 I'm dual booting to Ubuntu 12.04 and Windows XP sp3 on an old self-built desktop pc, with an MSI 865PE/G Neo2-P motherboard and an Intel Pentium 4 3.066GHz Prescott cpu cooled by a Zalman CNPS7000A-CU heatsink.
 

 Before I moved to Ubuntu I was using this machine regularly for fairly intensive video processing etc and rarely had overheating problems. It's very rare indeed these days that I boot into Windows, but the last few times that I have, even before attempting anything remotely demanding, sometimes within just a few minutes, a warning has come up re the cpu overheating and, if I'm not there to intervene, the pc has shut down. On the XP desktop there is proprietary MSI monitoring/tweaking software ('CoreCenter' – the mobo was partly aimed at overclockers, though I've never interfered on that front) and this shows the cpu temperature, fan speed etc. I can prevent the warning/shutdown situation by setting the cpu temperature threshold to its maximun: 100[FONT=Ubuntu]°, though I realise that's probably unwise. I also realise I can probably alleviate the situation by giving the pc a thorough internal clean, something I've not done for months. But first I thought I'd investigate on the Ubuntu front. I've read that Linux runs much more efficiently than Windows hardware-wise and I was interested to discover its capabilities for monitoring and managing temperature, fan speeds etc. So after a bit of reading it up I followed the instructions in the official ubuntu documentation SensorInstallHowto. I was very surprised when I ran sensors-detect and hardly anything was detected at all, and nothing that looks like a cpu thermal sensor:[/FONT]
```

   [FONT=Ubuntu]nick@nick-build-1:~$ sudo sensors-detect [/FONT] 

 [FONT=Ubuntu]# sensors-detect revision 5984 (2011-07-10 21:22:53 +0200) [/FONT] 
 [FONT=Ubuntu]# System: MICRO-STAR INC. MS-6728 [/FONT] 
 

 [FONT=Ubuntu]This program will help you determine which kernel modules you need [/FONT] 
 [FONT=Ubuntu]to load to use lm_sensors most effectively. It is generally safe [/FONT] 
 [FONT=Ubuntu]and recommended to accept the default answers to all questions, [/FONT] 
 [FONT=Ubuntu]unless you know what you're doing. [/FONT] 
 

 [FONT=Ubuntu]Some south bridges, CPUs or memory controllers contain embedded sensors. [/FONT] 
 [FONT=Ubuntu]Do you want to scan for them? This is totally safe. (YES/no): y [/FONT] 
 [FONT=Ubuntu]Module cpuid loaded successfully. [/FONT] 
 [FONT=Ubuntu]Silicon Integrated Systems SIS5595...                       No [/FONT] 
 [FONT=Ubuntu]VIA VT82C686 Integrated Sensors...                          No [/FONT] 
 [FONT=Ubuntu]VIA VT8231 Integrated Sensors...                            No [/FONT] 
 [FONT=Ubuntu]AMD K8 thermal sensors...                                   No [/FONT] 
 [FONT=Ubuntu]AMD Family 10h thermal sensors...                           No [/FONT] 
 [FONT=Ubuntu]AMD Family 11h thermal sensors...                           No [/FONT] 
 [FONT=Ubuntu]AMD Family 12h and 14h thermal sensors...                   No [/FONT] 
 [FONT=Ubuntu]AMD Family 15h thermal sensors...                           No [/FONT] 
 [FONT=Ubuntu]AMD Family 15h power sensors...                             No [/FONT] 
 [FONT=Ubuntu]Intel digital thermal sensor...                             No [/FONT] 
 [FONT=Ubuntu]Intel AMB FB-DIMM thermal sensor...                         No [/FONT] 
 [FONT=Ubuntu]VIA C7 thermal sensor...                                    No [/FONT] 
 [FONT=Ubuntu]VIA Nano thermal sensor...                                  No [/FONT] 
 

 [FONT=Ubuntu]Some Super I/O chips contain embedded sensors. We have to write to [/FONT] 
 [FONT=Ubuntu]standard I/O ports to probe them. This is usually safe. [/FONT] 
 [FONT=Ubuntu]Do you want to scan for Super I/O sensors? (YES/no): y [/FONT] 
 [FONT=Ubuntu]Probing for Super-I/O at 0x2e/0x2f [/FONT] 
 [FONT=Ubuntu]Trying family `National Semiconductor/ITE'...               No [/FONT] 
 [FONT=Ubuntu]Trying family `SMSC'...                                     No [/FONT] 
 [FONT=Ubuntu]Trying family `VIA/Winbond/Nuvoton/Fintek'...               Yes [/FONT] 
 [FONT=Ubuntu]Found `Winbond W83627THF/THG Super IO Sensors'              Success! [/FONT] 
     [FONT=Ubuntu](address 0x290, driver `w83627hf') [/FONT] 
 [FONT=Ubuntu]Probing for Super-I/O at 0x4e/0x4f [/FONT] 
 [FONT=Ubuntu]Trying family `National Semiconductor/ITE'...               Yes [/FONT] 
 [FONT=Ubuntu]Found unknown chip with ID 0xf7f7 [/FONT] 
 

 [FONT=Ubuntu]Some systems (mainly servers) implement IPMI, a set of common interfaces [/FONT] 
 [FONT=Ubuntu]through which system health data may be retrieved, amongst other things. [/FONT] 
 [FONT=Ubuntu]We first try to get the information from SMBIOS. If we don't find it [/FONT] 
 [FONT=Ubuntu]there, we have to read from arbitrary I/O ports to probe for such [/FONT] 
 [FONT=Ubuntu]interfaces. This is normally safe. Do you want to scan for IPMI [/FONT] 
 [FONT=Ubuntu]interfaces? (YES/no): y [/FONT] 
 [FONT=Ubuntu]Probing for `IPMI BMC KCS' at 0xca0...                      No [/FONT] 
 [FONT=Ubuntu]Probing for `IPMI BMC SMIC' at 0xca8...                     No [/FONT] 
 

 [FONT=Ubuntu]Some hardware monitoring chips are accessible through the ISA I/O ports. [/FONT] 
 [FONT=Ubuntu]We have to write to arbitrary I/O ports to probe them. This is usually [/FONT] 
 [FONT=Ubuntu]safe though. Yes, you do have ISA I/O ports even if you do not have any [/FONT] 
 [FONT=Ubuntu]ISA slots! Do you want to scan the ISA I/O ports? (yes/NO): y [/FONT] 
 [FONT=Ubuntu]Probing for `National Semiconductor LM78' at 0x290...       No [/FONT] 
 [FONT=Ubuntu]Probing for `National Semiconductor LM79' at 0x290...       No [/FONT] 
 [FONT=Ubuntu]Probing for `Winbond W83781D' at 0x290...                   No [/FONT] 
 [FONT=Ubuntu]Probing for `Winbond W83782D' at 0x290...                   No [/FONT] 
 

 [FONT=Ubuntu]Lastly, we can probe the I2C/SMBus adapters for connected hardware [/FONT] 
 [FONT=Ubuntu]monitoring devices. This is the most risky part, and while it works [/FONT] 
 [FONT=Ubuntu]reasonably well on most systems, it has been reported to cause trouble [/FONT] 
 [FONT=Ubuntu]on some systems. [/FONT] 
 [FONT=Ubuntu]Do you want to probe the I2C/SMBus adapters now? (YES/no): y [/FONT] 
 [FONT=Ubuntu]Using driver `i2c-i801' for device 0000:00:1f.3: Intel 82801EB ICH5 [/FONT] 
 [FONT=Ubuntu]Module i2c-i801 loaded successfully. [/FONT] 
 [FONT=Ubuntu]Module i2c-dev loaded successfully. [/FONT] 
 

 [FONT=Ubuntu]Now follows a summary of the probes I have just done. [/FONT] 
 [FONT=Ubuntu]Just press ENTER to continue: [/FONT] 
 

 [FONT=Ubuntu]Driver `w83627hf': [/FONT] 
   [FONT=Ubuntu]* ISA bus, address 0x290 [/FONT] 
     [FONT=Ubuntu]Chip `Winbond W83627THF/THG Super IO Sensors' (confidence: 9) [/FONT] 
 

 [FONT=Ubuntu]To load everything that is needed, add this to /etc/modules: [/FONT] 
 [FONT=Ubuntu]#----cut here---- [/FONT] 
 [FONT=Ubuntu]# Chip drivers [/FONT] 
 [FONT=Ubuntu]w83627hf [/FONT] 
 [FONT=Ubuntu]#----cut here---- [/FONT] 
 [FONT=Ubuntu]If you have some drivers built into your kernel, the list above will [/FONT] 
 [FONT=Ubuntu]contain too many modules. Skip the appropriate ones! [/FONT] 
 

 [FONT=Ubuntu]Do you want to add these lines automatically to /etc/modules? (yes/NO)[/FONT]


```

   [FONT=Ubuntu]I responded “No” this time as I first ran sensors-detect over 2 years ago and added the suggested lines then. My current /etc/modules file is very brief:

   [/FONT]
```
[FONT=Ubuntu]# /etc/modules: kernel modules to load at boot time. [/FONT] 

 [FONT=Ubuntu]# [/FONT] 
 [FONT=Ubuntu]# This file contains the names of kernel modules that should be loaded [/FONT] 

 [FONT=Ubuntu]# at boot time, one per line. Lines beginning with "#" are ignored. [/FONT] 
 

 [FONT=Ubuntu]lp [/FONT] 
 

 [FONT=Ubuntu]# Generated by sensors-detect on Tue Jun  5 21:22:18 2012 [/FONT] 
 [FONT=Ubuntu]# Chip drivers [/FONT] 
 [FONT=Ubuntu]w83627hf [/FONT] 
 [FONT=Ubuntu]ppa [/FONT] 

``` 


[FONT=Ubuntu][NB  I'm not sure where the “ppa” came from – is it safe to delete it?][/FONT]
 

 [FONT=Ubuntu]Which do I believe, 'CoreCenter' or 'sensors-detect'? How do I find out whether or not there really are embedded thermal sensors?[/FONT]
 

 [FONT=Ubuntu]A further problem arises when, even with the added the lines in /etc/modules, running the sensors command brings “No sensors found!”

   [/FONT]
```
[FONT=Ubuntu]nick@nick-build-1:~$ sudo sensors [/FONT] 

 [FONT=Ubuntu][sudo] password for nick: [/FONT] 
 [FONT=Ubuntu]No sensors found! [/FONT] 
 [FONT=Ubuntu]Make sure you loaded all the kernel drivers you need. [/FONT] 

 [FONT=Ubuntu]Try sensors-detect to find out which these are.[/FONT]


```[FONT=Ubuntu]
[/FONT]


[FONT=Ubuntu]I seem to be going round in circles! Where am I going wrong?[/FONT]

[FONT=Ubuntu]
[/FONT]

---

### Post by varunendra on 2014-10-04
Either I overlooked it, or you didn't mention clearly the overheating is happening in both operating systems or just one of them (XP?). If it is happening in both, it seems to be a case of loose heat-sink, or a heatsink completely stuffed with dust so it can't dissipate the heat.

In the former case, you'll need to detach the heat-sink > clean it > apply heat-sink compound on it > re-attach it firmly, so that there is no air-gap between the heat-sink and the CPU.

In the latter case, just cleaning of the heat-sink (with a pressurized air-can or a brush) should be sufficient.

Regarding the sensors, while it may be some issue with the software, it is not uncommon to have few or no heat sensors on the motherboard. If you have windows XP, you can try some software like 'hwmonitor' to see if it can monitor the temperature or not. If not, there are probably no sensors.

---

### Post by nickdc on 2014-10-04
Thanks for chipping in. I can't be sure whether the overheating is happening in Ubuntu, because I've no way of monitoring it! That's why I tried lm-sensors, but, as I say in my post, I don't seem to be getting anywhere with that. Thanks for your advice about sorting the heat-sink, and I will do that, but I like to know how things work, and at the moment I haven't a clue whether there actually is any overheating; I can't find a way in Ubuntu to find out, and I'm not sure if I can trust the 'Core-Center' software in Windows. I wonder if the temperature readings that gives are based on anything real at all? Hence my post, hoping someone who understands these things can throw some light.

---

### Post by tgalati4 on 2014-10-04
I don't think P4's have a thermal diode.  They were forged with stardust and are designed to operate at temperatures approaching the sun.  The motherboard might have a diode or thermister, but obviously, *sensors-detect* can't read it.  You can search the webz for more information on your sensor chip:

>      Chip `Winbond W83627THF/THG Super IO Sensors' (confidence: 9) 

and the module *w83627hf*.

As far as heating, as suggested, a thorough cleaning and replacement of the heat paste with a higher-quality paste (like Arctic Silver or Ceramic or something similar).  Watch some youtube videos for how to do it properly.  Don't use too much, don't use not enough.

Declock the computer in BIOS and run it at slower speeds.  It's possible that you have a bad capacitor or power supply problem as well with a machine of this age.

---

### Post by nickdc on 2014-10-04
Useful information and advice - many thanks. I've upgraded the psu a couple of times, so I expect that's still good. In the slightly longer run I intend to built an up-to date machine!

---

