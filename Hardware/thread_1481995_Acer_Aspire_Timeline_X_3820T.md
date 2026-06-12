---
title: "Acer Aspire Timeline X 3820T"
date: 2010-05-13
forum: Hardware
---

### Post by peterlustig on 2010-05-13
Hi everyone,
I thought I'd start a thread on the Acer Aspire TimelineX 3820T - 334G32N since I ran into some small issues that at least partially can be solved:

**Fan** issue:
Running Ubuntu Lucid with the 64bit version of kernel 2.6.32-22, I first burnt my fingers and then realized that the CPU fan was either not working or working at very low speed.
I wasn't able to resolve that last night, since there were no entries in /proc/acpi/fan/
[I]EDIT:
using bios v 1.13 and ubuntu 10.04, 64bit, kernel 2.6.32-22 temperatures are still a bit high, but acceptable (40-45°C when idle and 65-70°C when running on maximum load for half an hour.[/I]

Running Ubuntu Lucid with the 2.6.32-22-generic-pae (32bit) kernel, the fan(s) is working as it should, but still no entries in /proc/acpi/fan/ or in /sys/...
However, I'm still not able to manually set or read the fan speed, which is not a problem, since the fan(s) is working. No overheating problems.

**Brightness** issue:
The brightness of the display can not be adjusted (that is true for the 64bit and 32bit kernel) using gnome-power-preferences or the Fn+arrow keys on the keyboard. Using the Fn+arrow keys, the brightness indicator in gnome is called and can be adjusted, but the actual brightness of the display does not change. There is a workaround for this problem that I found elsewhere (I don't remember):

```

sudo gedit /etc/default/grub

```

Change the line *GRUB_CMDLINE_LINUX=""* into
```

GRUB_CMDLINE_LINUX="acpi_osi=Linux"

```

then run
```
sudo update-grub
```

In my case this worked.

**Integrated microphone** issue:
I couldn't get the integrated microphone to work with pulse or alsa. But then again I haven't put much energy into that.

**Headphones** issue:
Wow, this is getting worse and worse: Headphones jack sense seems to work in the sense that when you plug in the headphones you don't get any sound from the integrated speakers. Unfortunately you don't get any sound from the headphones either... I really wonder what I am doing wrong... the system beep is clearly audible via the headphones when the system shuts down. #!%§&
[I]EDIT:
I ran the [ AlsaUpgrade script]("http://ubuntuforums.org/showpost.php?p=6589810&postcount=1") by soundcheck. No more headphone-issues.[/I]

**Suspend/Hibernate** issue:
After waking up from suspend, the CPU fan stops working and the CPU frequency is set to max, what an inconvenient combination...
*EDIT: Using bios v1.13 this doesn't happen so frequently any more. But it still does happen.*

**Multi touch** issue:
That multitouch touchpad stuff has become a bit complicated. I couldn't get that to work either... yet.
[I]EDIT:
workaround: [#6]("http://ubuntuforums.org/showpost.php?p=9301251&postcount=6")
[/I]
Everything else seems to work just fine and out of the box. SD-card reader, HDMI, cpu feq scaling. But it took me a while until I realized that I have to press the wireless toggle button (Fn+F3) to activate wlan AND again to activate bluetooth. 

I hope this is of some help to someone. If any of you have an idea how to tackle the integrated mic - problem, I'd be happy to hear about it.

Good luck,
Peter

---

### Post by josedb on 2010-05-13
> **peterlustig said:**
> 
**Multi touch** issue:
That multitouch touchpad stuff has become a bit complicated. I couldn't get that to work either... yet.


Alps touchpad doesnt work well in any noteboook.

---

### Post by giova.86 on 2010-05-14
Hy I have a timelinex 4820TG. FOr the touchpad I have used these:

xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Two-Finger Scrolling" 8 1
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Scrolling" 8 1 1
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Pressure" 32 10
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Width" 32 8

It works for me.

---

### Post by peterlustig on 2010-05-14
Hey Giova,
thanks. Works smoothly indeed. I was trying to integrate all this into a udev rule instead of writing a script yesterday. That's why I wrote that it has become a bit complicated (for me). I read somewhere that putting all this into udev (instead of xorg.conf or as a shell script somewhere else) is the way to do it now. The rule saved in /etc/udev/rules.d/99synaptic.rules looked like this and it didn't do the trick:

```

ACTION!="add|change", GOTO="my_synaptics_end"
KERNEL!="event*", GOTO="my_synaptics_end"
ENV{ID_INPUT_TOUCHPAD}!="1", GOTO="my_synaptics_end"

ENV{x11_driver}="synaptics"

ATTR{device/name}=="SynPS/2 Synaptics TouchPad", \
ENV{x11_options.SHMConfig}="on", \
ENV{x11_options.EmulateTwoFingerMinZ}="32", \
ENV{x11_options.EmulateTwoFingerMinW}="32", \
ENV{x11_options.VertTwoFingerScroll}="1", \
ENV{x11_options.HorizTwoFingerScroll}="1", \
ENV{x11_options.TapButton1}="1", \
ENV{x11_options.TapButton2}="2", \
ENV{x11_options.TapButton3}="3"

LABEL="my_synaptics_end"

```

Any suggestions?

Thanks,
Peter

---

### Post by giova.86 on 2010-05-14
I'm sorry but I can't help you, I'm not an expert about udev, but I have found some information here: [http://www.thinkwiki.org/wiki/How_to_configure_the_TrackPoint](http://www.thinkwiki.org/wiki/How_to_configure_the_TrackPoint) Try to see if this is what you need. I can tell you to don't use options in wich is wrote: EmulateTwoFinger.. because the emulation is used only for old touchpads that don't support native multitouch (and the timelinex supprort native multitouch).

---

### Post by peterlustig on 2010-05-14
Hi giova,
you're right, we don't need the emulation settings. According to the synaptics man page, the option
"EmulateTwoFingerMinZ" in my udev file is equivalent to the property "Synaptics Two-Finger Pressure"
and the option "EmulateTwoFingerMinW" is equivalent to "Synaptics Two-Finger Width".
Thanks for posting that [thinkwiki-link]("http://www.thinkwiki.org/wiki/How_to_configure_the_TrackPoint"). 

I made a tiny script /usr/local/bin/multitouch.sh

```

#!/bin/sh
sleep 5
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Scrolling" 8 1 1
exit 0

```

after making it executable with
```

chmod 755 /usr/local/bin/multitouch.sh

```

I entered the command /usr/local/bin/multitouch.sh in a new entry in System-->Startup Applications
Now it works

Thanks for your help! Turns out the touchpad works good enough for my purposes :)
Peter

---

### Post by giova.86 on 2010-05-15
I did the same script, but in my case with only 5 seconds wasn't enough, so I set a sleep time equals to 10 seconds.
I have a question. When you use ubuntu with the battery, works the command: ```
acpi -b
```?

---

### Post by peterlustig on 2010-05-15
yepp, works. I am using kernel 2.6.32-22-generic-pae. I'm not sure if it works with the 64bit one. But I'll try it later on.

acpi -b returns "Battery 0: Full, 100%" when the power supply is plugged in
and "Battery 0: Discharging, 100%, 295:00:00 remaining", when it's on battery.
In /etc/default/grub, did you try changing the variable GRUB_CMDLINE_LINUX="" to GRUB_CMDLINE_LINUX="acpi_osi=Linux" 
and then running sudo update-grub? I'm not sure if it helps, but it might be worth a try.

---

### Post by giova.86 on 2010-05-15
I'm using a 64bit lucid lynk with the kernel 2.6.34-020634rc7-generic, I'm using this kernel because with the 2.6.32 I have some problems with the wireless card.

With both the kernel if I digit the command acpi -b I receive nothing in output, and with acpi -t, i receive in every condition: Thermal 0: ok, 40.0 degrees C. I also tried as you suggest but nothing change.
There must be some problem somewhere with acpi, maybe because the notebook is new and I'm using a 64 bit edition.. but I don't know. In the ubuntu forum in Italy I found other people with a timelinex or a new acer notebook and the same problem.

PS: with ```
dmesg ! grep battery
``` i receive the following output:
```
[    1.512155] ACPI: Battery Slot [BAT1] (battery absent)
```
Also if the battery is plugin :D

---

### Post by peterlustig on 2010-05-15
After a BIOS update from ver1.05 to 1.08 I tried the 64bit kernel 2.6.32-21-generic. I get the same reading for acpi -b as I mentioned above. That part seems to be ok. In dmesg I can see that there is a battery present
```
 [    3.894836] ACPI: Battery Slot [BAT0] (battery present) 
```
I think my overheating problem and your battery problem are both a result of [acer_acpi]("http://code.google.com/p/aceracpi/wiki/SupportedHardware"), which doesn't not support either of our laptops yet. If I understand correctly, the kernel module acer_acpi/acer_wmi can communicate with our acer bios using wmi. acer_wmi seems to be the successor of acer_acpi. Unfortunately I don't know how to solve either of our bios-interfacing problems. Maybe this will be fixed in future kernel versions.

---

### Post by giova.86 on 2010-05-15
I hope you're right, new laptop equal to new problems :P
Thanks for everything.
Have a nice day.

---

### Post by admiral0 on 2010-06-10
Any news? I wanted to buy this laptop. I'm very interested in acpi working.

---

### Post by peterlustig on 2010-06-11
Hi admiral0,
acpi on this laptop is quite buggy. Don't expect a lot more than 4h of surfing the net without the power-supply plugged in. The system is generally quite hot. 40-45°C when idle and 65-70°C when re-encoding a movie at full load. I haven't yet found a way to manually control the cpu-fan. The problem appears to be acer_wmi. 
You might want to take a look at my acpi-relevant dmesg output:
```

[    0.000000]  BIOS-e820: 00000000b3470000 - 00000000b34f1000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000b377e000 - 00000000b379f000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000b37df000 - 00000000b37ff000 (ACPI data)
[    0.000000]  modified: 00000000b3470000 - 00000000b34f1000 (ACPI NVS)
[    0.000000]  modified: 00000000b377e000 - 00000000b379f000 (ACPI NVS)
[    0.000000]  modified: 00000000b37df000 - 00000000b37ff000 (ACPI data)
[    0.000000] ACPI: RSDP 00000000000f6ac0 00024 (v02 PTLTD )
[    0.000000] ACPI: XSDT 00000000b37f16cf 0005C (v01 ACRSYS ACRPRDCT 06040000 INNA 00000000)
[    0.000000] ACPI: FACP 00000000b37e1000 000F4 (v03 INTEL  CALPELLA 06040000 PTEC 00000001)
[    0.000000] ACPI: DSDT 00000000b37e2000 0D49F (v02 Intel  CALPELLA 06040000 INTL 20060912)
[    0.000000] ACPI: FACS 00000000b379afc0 00040
[    0.000000] ACPI: HPET 00000000b37fed6a 00038 (v01 INTEL  CALPELLA 06040000 PTEC 00000001)
[    0.000000] ACPI: MCFG 00000000b37feda2 0003C (v01 INTEL  CALPELLA 06040000 PTEC 00000001)
[    0.000000] ACPI: SLIC 00000000b37fedde 00176 (v01 ACRSYS ACRPRDCT 06040000 ANNI 00000001)
[    0.000000] ACPI: APIC 00000000b37fef54 00084 (v01 PTLTD  ? APIC   06040000  LTP 00000000)
[    0.000000] ACPI: BOOT 00000000b37fefd8 00028 (v01 PTLTD  $SBFTBL$ 06040000  LTP 00000001)
[    0.000000] ACPI: SSDT 00000000b37e0000 009F1 (v01  PmRef    CpuPm 00003000 INTL 20060912)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x04] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x05] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a701 base: 0xfed00000
[    0.000000] ACPI: Added _OSI(Linux)
[    0.004273] ACPI: Core revision 20090903
[    0.801400] ACPI: bus type pci registered
[    0.812502] ACPI: EC: Look up EC in DSDT
[    0.821273] ACPI: BIOS _OSI(Linux) query honored via cmdline
[    0.837123] ACPI: Interpreter enabled
[    0.837130] ACPI: (supports S0 S3 S4 S5)
[    0.837158] ACPI: Using IOAPIC for interrupt routing
[    0.852752] ACPI: EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62
[    0.853105] ACPI: No dock devices found.
[    0.854102] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.855539] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.855840] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.856098] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    0.856258] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    0.870362] ACPI: PCI Root Bridge [CPBG] (0000:ff)
[    0.870813] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    0.870953] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.871095] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[    0.871232] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 *5 6 7 11 12 14 15)
[    0.871370] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[    0.871507] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 11 12 14 15) *0, disabled.
[    0.871645] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 *7 10 12 14 15)
[    0.871781] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[    0.872395] ACPI: WMI: Mapper loaded
[    0.872397] PCI: Using ACPI for IRQ routing
[    0.890835] pnp: PnP ACPI init
[    0.890854] ACPI: bus type pnp registered
[    0.893727] pnp: PnP ACPI: found 11 devices
[    0.893729] ACPI: ACPI bus type pnp unregistered
[    0.917683] ACPI: AC Adapter [ADP1] (off-line)
[    0.919451] ACPI: Lid Switch [LID0]
[    0.919520] ACPI: Sleep Button [SLPB]
[    0.919594] ACPI: Power Button [PWRF]
[    0.920820] ACPI: SSDT 00000000b371ac18 003AE (v01  PmRef  Cpu0Ist 00003000 INTL 20060912)
[    0.921502] ACPI: SSDT 00000000b3718018 00891 (v01  PmRef  Cpu0Cst 00003001 INTL 20060912)
[    0.922738] ACPI: SSDT 00000000b3719a98 00303 (v01  PmRef    ApIst 00003000 INTL 20060912)
[    0.923252] ACPI: SSDT 00000000b3717d98 00119 (v01  PmRef    ApCst 00003000 INTL 20060912)
[    0.962081] ACPI: Thermal Zone [TZS0] (34 C)
[    0.968217] ACPI: Thermal Zone [TZS1] (27 C)
[    1.163390] ACPI: Battery Slot [BAT0] (battery present)
[   14.341189] acer-wmi: Acer Laptop ACPI-WMI Extras
[   15.541096] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[  144.126823] ACPI: EC: GPE storm detected, transactions will use polling mode

```
and 
```

[   14.341189] acer-wmi: Acer Laptop ACPI-WMI Extras
[   14.341431] acer-wmi: Unable to detect available WMID devices

```

Hope that helps a bit. 
Peter

---

### Post by admiral0 on 2010-06-11
Thanks a lot.

I was searching for that :>

Looks like it's not acer-wmi's fault about battery. First of all it's acer's fault. (i already saw a quirk in acpi/battery.c specific for acer computers.

At this point i cannot do anything without actual hardware,hours of printk() and recompiles :>

---

### Post by tehmike on 2010-06-23
Hey guys i was wondering whether any of you got a decent way to have switchable graphics in ubuntu for the 3820 or tried the on-chip intel gma of the i5.
Specs :
core i5-450m
HD 5650 HD 1GB
4GB
640GB
13.3"
Acer 3820TG-5454G64nks
Thx for replies
Mike

---

### Post by fperwth on 2010-06-23
Really "switchable" not yet, but at least there is a way to turn off the ATI card, saving a lot of power:
[http://ubuntuforums.org/showthread.php?p=9446283#post9446283](http://ubuntuforums.org/showthread.php?p=9446283#post9446283)

As far as I know, there is no support for switching graphics in the current X server, but there are people working on that:
[http://linux-hybrid-graphics.blogspot.com/](http://linux-hybrid-graphics.blogspot.com/)

---

### Post by DimasMz on 2010-06-30
del

---

### Post by lazerradial2003 on 2010-07-03
Has anyone had any luck with the battery level issue?

---

### Post by Nordmoen on 2010-07-03
First of all thanks so much for this post, it helped me solv my problems with the Aspire 3820, but for some grimmer news. Suddenly I lost all of networking under Kubuntu. The laptop was sleeping and the battery ran out and after that(and several reboots) there is no networking, neither wireless nor cable. Anyone have any suggestions?

---

### Post by Nordmoen on 2010-07-04
Never mind. It was a knetworkmanager problem :P

---

### Post by athost on 2010-07-06
> **peterlustig said:**
> 
I thought I'd start a thread on the Acer Aspire TimelineX 3820T - 334G32N since I ran into some small issues that at least partially can be solved:


Thank you, indeed.

I bought this laptop a few days ago, and your information was very useful.

But I don't quite understand Why do I need to configure the touchpad. Is this adds some extra features?

---

### Post by qetuR on 2010-07-13
Hi! I'm planning on buying this laptop, well not precise this, but 3820TG, and I needed to check how it works with Ubuntu systems. And I must say that I think it looks good, compared to the problems with my Dell m1330 that I bought a couple of years ago.

One thing that I haven't seen any information about is the battery time, with the performance switch put on AND off, how many hours depending on what graphic is put on.

Would be great if anyone could provide me with this information!

Cheers!

---

### Post by kashikai on 2010-07-26
Hi ! 

Sorry in advance for my bad english.

I bought a 3820T last week. I'm very glad of this laptop and the only unworking feature was the internal mic for skype.

I solved it :

Install parvucontrol to access the pulseaudio control pannel.
Then go to Input tab.
The problem is that pulseaudio detects the mic like a stereo device.
Just unlock the dual channel slide, and setup one channel to 90% and the other to 10%.

With that, the internal mic will work in gnome recorder and skype.

Note that the quality is bad but can be improve by alsamixer and mic boost fader.

If someone success to make the mic quality good, i'm very interested.

I hope it'll help you

:)

edit : alsa-backports-module required for last alsa version

---

### Post by Irubataru on 2010-07-29
Hello,

Anyone else have any problems with their audio and video suddenly stopping?

After some time my audio and video sort of just stops working. If I open rythmbox, or movie player, or mplayer and press play, nothing happens (the seek bar doesn't even move, so apparently it doesn't want to play anything). If I open youtube, the video plays, but no sound neither on the stereo nor the headset.

I still haven't found out what I do right before the sound stops, because I probably discover it some time after it stopped working.

So far, the only way I have found to make the sound work again is a reboot, which is kind of troublesome at times.

I'm running ubuntu 10.04, 64-bit, and I have run the alsaupgrader suggested in the first post to get my headset to work.

Thanks for any help :)

---

### Post by Marcellino on 2010-07-30
Hello Peter,
 

 Firstly, I want to thank you for useful informations. I bought this laptop and I would like to update BIOS such as you did, but I dont know what method is the best for this laptop.  
 How have you done update please?
 

 I have downloaded bios 1,13 from Acer-website.
 I am running Ubuntu Lucid 64bit, but after bios update I want to run Ubuntu 32bit .
 

 Thank you for advice and sorry for my English.
 

 Irubataru: my audio and video players work except Amarok.

---

### Post by Irubataru on 2010-08-05
Sorry to bother, but one more thing. Every time I do a system update, the headphones stop working again. If I check alsamixer, they're not there even if they're plugged in, so I run the alsa-upgrade script again to get them working. Any easier way of doing it?

---

### Post by Ace_NoOne on 2010-08-18
> Integrated microphone issue:
I couldn't get the integrated microphone to work with pulse or alsa. But then again I haven't put much energy into that.
Using PulseAudio Volume Control, I was able to unmute the mic:
[http://ubuntuforums.org/showthread.php?p=9567985#post9567985](http://ubuntuforums.org/showthread.php?p=9567985#post9567985)

---

### Post by voidman on 2010-08-19
Have anyone encountered problems with ati card (ATI Mobility Radeon HD 5650) and it's drivers? I plan to buy this laptop but ati cards  were always a big problem...

---

### Post by petunder on 2010-08-29
> **voidman said:**
> Have anyone encountered problems with ati card (ATI Mobility Radeon HD 5650) and it's drivers? I plan to buy this laptop but ati cards  were always a big problem...

all is good with proprietary drivers. That's work fine under Ubuntu

---

### Post by petunder on 2010-08-29
Tutorial, how to solve sound troubles for 3820:
1. Upgrade ALSA: [http://ubuntuforums.org/showthread.php?p=6589810#post6589810](http://ubuntuforums.org/showthread.php?p=6589810#post6589810)
2. To make internal mic work: [http://ubuntuforums.org/showthread.php?t=1501525](http://ubuntuforums.org/showthread.php?t=1501525)

---

### Post by hotwax on 2010-09-12
The brightness can be calibrated if you have compiz installed. 

```
sudo apt-get compiz
```

Start Menu > Preferences > Compizconfig settings manager > Accessibility > Set your Increase/Descrease brightness buttons to a custom key combination (in which case your Fn+LeftArrow and Fn+RightArrow)

---

### Post by Ace_NoOne on 2010-09-13
> **hotwax said:**
> The brightness can be calibrated if you have compiz installed.

As far as I can tell, this only applies to the currently active window.

---

### Post by stone1343 on 2010-09-13
I bought this machine and installed 10.04, no problems. I don't care about the webcam and mic, so for me everything works great. Fan works the same as with Windows, screen shuts off when idle, wifi, sound, Fn keys all worked out of the box. One happy user.

---

### Post by Marat89 on 2010-09-16
HI,
anyone testet the timeline 3810 with Ubuntu 10.10 ?
Thanks

---

### Post by GodLikeCreature on 2010-09-21
> **Marat89 said:**
> HI,
anyone testet the timeline 3810 with Ubuntu 10.10 ?
Thanks

Hey, I am interested as well!  

I would like to buy one computer from this line, but finding that there are so many issues is not really encouraging.  Curious to see what the feedback is once the new kernel versions are tested...

---

### Post by Darkhorse85 on 2010-09-21
Hi just wanted to say if anybody is having problems with the Acer Aspire 4741 brightness control, the solution in the first post works with no added problem. Im only saying this because other solutions I have used editing grub has rendered my laptop unbootable and i had to re edit grub and update it from the live cd. 

Thank you!!

---

### Post by rogman on 2010-09-21
i did on the 5820, differant model i know, but same issues were present.

---

### Post by gubbi.fisk on 2010-09-23
Hey

Is there any one who got the ATI Radeon HD5650 working?
Every time I install the driver (Auto download by Ubuntu OR downloaded from ATI website) the screen goes black at startup.
And there is nothing else to do but recovery mode and remove driver again...

I also had problems with the LAN, WLAN and headphone, but all easily solved! With WLAN the default driver worked. I haven't tested the build in mic.

- Gubbi.fisk

---

### Post by gmanic on 2010-09-30
My experience with TimelineX 3820TG on 10.10 - so far:

**WLAN** - works out of the box. Great.

**HD** - heads park every 5 seconds. No good. Adjusted via /etc/hdparm.conf

**Display** - Intel Integrated works flawlessly.

**Radeon** - I disabled the card by default via sysfsutils (not using games and Intel is fast enough for Compiz etc.).

**Backlight** - unable to adjust brightness - no good! Compiz did not help, any hints??

**Touchpad** - scroll up did not work, adjustment to protocol imps in /etc/modprobe.d/psmouse.conf fixed it.

**BT** - does not work, not further investigated, yet. Hints?

**Audio** - works out of the box, output level low.

**Mic** - works with fader adjusted.

**Webcam** - works out of the box.

Otherwise: nice little piece of powerful hardware...

---

### Post by tajuma on 2010-09-30
With TimelineX 3820TG Kubuntu 10.10 Beta something.

**WLAN** - works out of the box. Great.

Interesting, I had to manually get the bcmwl package and compile it. But it works anyway.


**HD** - heads park every 5 seconds. No good. Adjusted via /etc/hdparm.conf

Not happening for me...


**Display** - Intel Integrated works flawlessly.

Basically yes, but  glmark2 3D-benchmark shows lousy results, looks like fps gets capped to 60 fps, even cpu and gpu are only ~4% and 10% busy, respectively. I took these numbers using intel_gpu_time.


**Backlight** - unable to adjust brightness - no good! Compiz did not help, any hints??

Added acpi_osi=Linux in the kernel boot commands (as hinted somewhere in the web), so edit your /etc/default/grub contain line

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=Linux"

and then sudo update-grub and reboot.

Then at least the Fn+arrow keys work, reading via /sys works but not writing via /sys.


**BT** - does not work, not further investigated, yet. Hints?

Mine works by pressing Fn+F3. Not sure if I have to always press twice, but at least sometimes once is enough. I have BIOS version 1.13, that might affect things.


**Audio** - works out of the box, output level low.

My sound got routed to ATI HDMI by default, easy to fix once figured that out.

---

### Post by gmanic on 2010-10-01
> **tajuma said:**
> With TimelineX 3820TG Kubuntu 10.10 Beta something.

**WLAN** - works out of the box. Great.

Interesting, I had to manually get the bcmwl package and compile it. But it works anyway.

**HD** - heads park every 5 seconds. No good. Adjusted via /etc/hdparm.conf

Not happening for me...

Happened with mine after disconnecting AC (pm-utils switch hd with hdparm to -B 128, which parks heads after approx. 5 seconds. Because some apps write to disk regularly (e.g. firefox) disk was de-parked with next disk access. Not good for disk. It's that slight clicking sound on battery.

> **tajuma said:**
> 
**Display** - Intel Integrated works flawlessly.

Basically yes, but  glmark2 3D-benchmark shows lousy results, looks like fps gets capped to 60 fps, even cpu and gpu are only ~4% and 10% busy, respectively. I took these numbers using intel_gpu_time

True, but for my uses 60fps is more than enough. 

Just today I actually had a problem. initrd was failing with "no init" if BIOS was set to "switchable", but with "discrete" (== Radeon) it booted just fine and on glxgears I get approx. 550fps with 36% cpu usage. 

*edit 02.10.10* - It works again with both graphics adapters enabled and switchable and even brightness adjustement works on the Intel Graphics. Changes: grub commandline changed from acpi_osi="Linux" to acpi_osi=Linux (without the quotes).

> **tajuma said:**
> 
**Backlight** - unable to adjust brightness - no good! Compiz did not help, any hints??

Added acpi_osi=Linux in the kernel boot commands (as hinted somewhere in the web), so edit your /etc/default/grub contain line

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=Linux"

and then sudo update-grub and reboot.

Then at least the Fn+arrow keys work, reading via /sys works but not writing via /sys.

With 1st time Radeon used for Ubuntu I can confirm this now. Brightness can then obviously not be adjusted using Intel integrated graphics.

> **tajuma said:**
> 
**BT** - does not work, not further investigated, yet. Hints?

Mine works by pressing Fn+F3. Not sure if I have to always press twice, but at least sometimes once is enough. I have BIOS version 1.13, that might affect things.

I have updated to 1.17 even before really getting to a useful state ;). I toggled all wireless possibilities through - BT shows up extremely short as usb-device in syslog, but cannot be handled properly and gets deleted right afterwards:

[FONT=Courier New][SIZE=1]Oct  1 22:03:17 silpow kernel: [ 3360.426089] usb 1-1.4: new full speed USB device using ehci_hcd and address 5
Oct  1 22:03:18 silpow kernel: [ 3360.763564] usb 1-1.4: USB disconnect, address 5
Oct  1 22:03:19 silpow kernel: [ 3362.214237] usb 1-1.4: new full speed USB device using ehci_hcd and address 6
Oct  1 22:03:19 silpow bluetoothd[7038]: HCI dev 0 registered
Oct  1 22:03:19 silpow bluetoothd[7038]: Can't init device hci0: No such device (19)
Oct  1 22:03:19 silpow bluetoothd[7038]: HCI dev 0 unregistered
Oct  1 22:03:19 silpow bluetoothd[7038]: Unregister path: /org/bluez/7037/hci0
Oct  1 22:03:19 silpow bluetoothd[7096]: Can't init device hci0: Input/output error (5)
Oct  1 22:03:19 silpow kernel: [ 3362.527414] usb 1-1.4: USB disconnect, address 6
Oct  1 22:03:19 silpow kernel: [ 3362.527448] btusb_intr_complete: hci0 urb f5851700 failed to resubmit (19)
Oct  1 22:03:19 silpow kernel: [ 3362.527495] btusb_bulk_complete: hci0 urb f5851480 failed to resubmit (19)
Oct  1 22:03:19 silpow kernel: [ 3362.527504] btusb_bulk_complete: hci0 urb f5851000 failed to resubmit (19)
Oct  1 22:03:19 silpow kernel: [ 3362.530858] hub 1-1:1.0: hub_port_status failed (err = -32)
Oct  1 22:03:19 silpow kernel: [ 3362.530867] hub_port_connect_change: 9 callbacks suppressed
Oct  1 22:03:19 silpow kernel: [ 3362.530873] hub 1-1:1.0: connect-debounce failed, port 4 disa[/SIZE][/FONT]

Guess I should investigate on that further.

> **tajuma said:**
> 

**Audio** - works out of the box, output level low.

My sound got routed to ATI HDMI by default, easy to fix once figured that out.

True :)

---

### Post by efzwo on 2010-10-05
I have problems with die touchpad in my brand new apire 3820G on Ubuntu 10.10 RC

Scrolling down is working, if I want to scroll up it goes just down like pressing the page-down-button.
Touchpad configuration in Gnome is not working, the touchpad is recognized as
I: Bus=0011 Vendor=0002 Product=0005 Version=0000
N: Name="ImPS/2 Generic Wheel Mouse"
P: Phys=isa0060/serio1/input0
S: Sysfs=/devices/platform/i8042/serio1/input/input12
U: Uniq=
H: Handlers=mouse0 event5 
B: EV=7
B: KEY=70000 0 0 0 0
B: REL=103

if I reload psmouse-module scrolling is working for a few seconds.
any ideas? Thanks.

---

### Post by gmanic on 2010-10-06
Create a file /etc/modprobe.d/psmouse.conf with the following content:

options psmouse proto=imps

Then reload the psmouse module. That did the trick for me.

---

### Post by ginbuntu on 2010-10-06
I just install kubuntu 10.10 32bit and I got a GPU hung when enabled effects in kde 4.5. Does any one have this problem?

---

### Post by benbois on 2010-10-08
Hello,

I've just upgrade ubuntu to the RC 10.10 and discovered that alsa is working like a charm now!
No more patch or other fix is needed.

---

### Post by hotwax on 2010-10-20
does ubuntu 10.10 have wifi working out of the box? anyone tried it?

---

### Post by zemex34 on 2010-10-21
I recently installed Ubuntu 10.10 x86 in my Acer 3820TG. The laptop comes with the hard drive disk WDC WD3200BEVT-22A23T0. My problem is that it makes lots of noise when accessing data, like clicking really hard. The thing is that nothing of this happen in Windows 7.

Help would be appreciated ;)

---

### Post by podginater on 2010-10-23
[FONT="Arial"]I have recently bought the Acer Timeline X 3820t and installed Ubuntu 10.10 on it. Everything was working fine except the touchpad and the brightness, so I fixed both of them [COLOR="DarkSlateGray"]-touchpad by making the conf file and brightness by editing the grub file- [/COLOR]and rebooted but now the wireless has completely broken.

I have rebooted several times and when I click on the NetworkManager applet, it doesn't even show that I have a wireless card installed!

edit: I have just tried an external wireless card and it has worked perfectly so it must be the wireless card or driver itself.

Please help. Thank you[/FONT]

---

### Post by schmickey on 2010-10-28
I have the 3820T-7459 (no bluetooth, Core i3-370M CPU and Intel HD only).
I immediately replaced the wireless card with an Intel 6200 and replaced the HDD with a Corsair Nova 128GB SSD.

Amazing performance after making a few adjustments for proper SSD usage.  You can find all the SSD tweaks [HERE.]("http://cptl.org/wp/index.php/2010/03/30/tuning-solid-state-drives-in-linux/")
Note:  Be sure to read through all 3 pages there.

Boots to a usable desktop in 8 seconds.  Shuts down to full power-off in 3 seconds.  No problems after doing the grub update to get the brightness control working.
I haven't yet tried the mic, but that's not something I use much.  Webcam works great with Cheese, much better than with Windows and any Windows webcam app.

Very happy with this machine and Ubuntu 10.10.  Well, except for fan and heat issues which aren't much of a problem for me since I rarely stress the computer.  Hopefully a later kernel will help with this.  In any event, temps aren't really that high even under stress.

---

### Post by lamalta on 2010-10-29
Hello!
I have the 3820T-7459 too, with Ubuntu 10.10, Compiz and Cairo-dock. Amazing performance! I'm really happy with this laptop. 
I have a couple of problems:
1)Power consumption: monitoring with powertop, I cannot obtain less than 13 watts, and sometime, even if the cpu governor is setting on "powersave", I have 18-21 watts just using Chrome browse. I'm using granola and I tried also powernowd (that worked fine) and cpufreqd (that didn't work well).
2)Gnome CPU Frequency monitor: with this, I can select the frequency of the CPU and the governor, BUT the system recognize 4 CPUs (2 real and 2 HT). How can I set everything together? :confused:

Thank you!

Ale

---

### Post by schmickey on 2010-10-29
Wish I could help but I'm not very knowledgeable about power issues.  This appears to be a major weak spot in Ubuntu and I hope the developers can address it soon.  Since I rarely run my laptop on battery and it doesn't seem to get too hot I don't worry about it much.

---

### Post by fhteagle on 2010-12-17
For everyone looking to get lower power usage, longer battery life, and less heat from their 3820T:

Upgrade to kernel 2.6.36 from Ubuntu Kernel-PPA. It has a multi-core scheduler patch that really drove down interrupts, wakeups, and therefore power. I'm seeing 11W typical with display full dim in Xubuntu 10.10 (high compositor effects). Had the computer up over 5 hours taking notes, skimming pdfs, and surfing over wifi today and still had 30+% battery left.

2.6.37 does not allow screen dimming even with grub edits, and isnt stable enough yet in my opinion, so stick with 2.6.36.

Last thing I will recommend is ditching Adobe Flash if you can. Even an "idle" npviewer.bin (no sites with any flash content open in Firefox or Chrome) by itself is responsible for more wakeups/interrupts than all other processes combined on my system... 

Hope this helps.

---

### Post by Ace_NoOne on 2010-12-18
Thanks fhteagle, that sounds promising!

> **fhteagle said:**
> For everyone looking to get lower power usage, longer battery life, and less heat from their 3820T:

Upgrade to kernel 2.6.36 from Ubuntu Kernel-PPA. [...] 2.6.37 [...] isnt stable enough yet in my opinion, so stick with 2.6.36.
Excuse my ignorance, but 2.6.36 doesn't seem to be available:
After adding the PPA (*sudo add-apt-repository ppa:kernel-ppa/ppa; sudo apt-get update*), a search for "2.6.36" only returns "linux-backports-modules-compat-wireless-2.6.36-2.6.35-23-ge", which doesn't seem like the right thing?

---

### Post by AbiGeuS on 2010-12-28
Hi all.
I am from Russia, so sorry for my English.
I have acer aspire 3820T without bluetooth. I installed ubuntu 10.10. I was found some bug. After I push fn+7 to disable touchpad, keyboard stops responding to keystrokes, and ceases to operate the menu on the main panel. If someone else have the same problem and know how to solve it, please let me know.

---
With Best Wishes AbiGeuS

---

### Post by jossec on 2011-01-02
I have the 3820T only with Intel HD graphics, without optical drive and the 9-cell battery and changed the HD for a 120 GB Intel SSD and put Ubuntu 10.10 (64 bits) on it.  It is very fast.  I need to do some SSD tweaking yet and will add 4 GB of RAM.  I applied the changes in GRUB for the LED dimming (only tweak really needed).  In Powertop I can easily go below 10 W (Idle of course, capacity of 9-cell is around 90 Wh)  and it is even suggesting things for powering down the sound adapter.  I don't know if powersave options on a SSD make a lot of difference.  Replacing the HD is a breeze if you can unscrew the big plastic plate  where the memory and HD sits.  The memory banks are pretty large.  

The notebook is really silent and you only hear the fan when under heavy load and even then it must be really silent before you can hear it.  

Right now, I would advise this notebook to any Ubuntu 10.10 user.

---

### Post by jlh68 on 2011-01-03
I have the 14-inch screen 4820T TimelineX.  I can not get the HDMI out put to work correctly.  The colors are off.  I get pink for where the white is and some other strange colors. 

Does anyone know what the problem is?

Also this unit does not have the ATI graphics card, I mention this as there are several posts in this thread asking about it. Mine has the  Intel HD Graphics. I have most everything working except the special "P" key and the HDMI output.  The VGA output works fine.  I do not have the multi-gesture working yet.

I can't get my power usage down below 11-Watts, but I almost always have the WIFI on.  I use Intel's Powertop to reduce load.

---

### Post by BreenLantern on 2011-01-08
I recently bought the 3820T-7459
My experience with on 10.10 with 2.6.35-24-generic

**WLAN** - works out of the box. Great.
**Display/brightness** - Brightness didn't work out of the box, but was easily fixed with the default grub fix on the first page.
**Audio** - works out of the box, and SPDIF headphone jack output hooked up pretty easily to my logitech speakers.
**Mic** - works with fader adjusted...Quality is ok enough for webcam chat
**Webcam** - Quality is meh, but nice to not have to carry around an external webcam

Touchpad - this is probably what bugs me the most, does anyone have any idea on how to turn off tap to click? it bugs the crap out of me when I try and type, i found it was easy when I had a synaptics touchpad, but this has an ALPS, and it is recognized as a PS/2 mouse.  Any idea on if any of this can be fixed?

Overall I am pretty happy with it... trying to see how much fixing the display increases the battery life.

---

### Post by jlh68 on 2011-01-09
Have you tried [system] > [mouse] > [touchpad], click under [general] "disable touchpad when typing"?

Yes having a active tap on touchpad is annoying.

---

### Post by BreenLantern on 2011-01-09
Well there is no touchpad section due to the system recognizing the ALPS as a ps/2 mouse...

---

### Post by jlh68 on 2011-01-10
Go to software center and install > Configuration module for laptop touchpad.

Maybe that will provide the solution.

---

### Post by NHaGa on 2011-01-13
I can only start X with the Discrete settings in BIOS. If I use Switchable, I boot straight to terminal. 

Can someone please post the correct xorg.conf settings?

---

### Post by dinutu on 2011-01-15
> **NHaGa said:**
> I can only start X with the Discrete settings in BIOS. If I use Switchable, I boot straight to terminal. 

Can someone please post the correct xorg.conf settings?

This is the only way i am booting, cannot find any solution for this issue so far.

---

### Post by rimez on 2011-01-28
> **jlh68 said:**
> Go to software center and install .

Maybe that will provide the solution.

Is there a Gnome solution. The mentioned app is for KDE. I have installed Touchpad-Indicator but it's not working either :(

---

### Post by Chrilleee on 2011-02-02
> **fhteagle said:**
> For everyone looking to get lower power usage, longer battery life, and less heat from their 3820T:

Upgrade to kernel 2.6.36 from Ubuntu Kernel-PPA. It has a multi-core scheduler patch that really drove down interrupts, wakeups, and therefore power. I'm seeing 11W typical with display full dim in Xubuntu 10.10 (high compositor effects). Had the computer up over 5 hours taking notes, skimming pdfs, and surfing over wifi today and still had 30+% battery left.

2.6.37 does not allow screen dimming even with grub edits, and isnt stable enough yet in my opinion, so stick with 2.6.36.

Last thing I will recommend is ditching Adobe Flash if you can. Even an "idle" npviewer.bin (no sites with any flash content open in Firefox or Chrome) by itself is responsible for more wakeups/interrupts than all other processes combined on my system... 

Hope this helps.

I've just installed kernel 2.6.36 by the packages:
linux-headers-2.6.36-020636_2.6.36-020636.201010210905_all.deb
linux-headers-2.6.36-020636-generic_2.6.36-020636.201010210905_i386.deb
linux-image-2.6.36-020636-generic_2.6.36-020636.201010210905_i386.deb

But... if I remove my A/C-cable it says two hours when doing nothing and having the screen dimmed to max!
Also running on FluxBox which should be lower power consuming than Gnome.

Just found out another thing to, in Ubuntu it says I only have like 2.3GB of RAM! It's supposed to be 4GB!
Could this be because I'm running 32bit version?

---

### Post by lamalta on 2011-02-18
I'd really like to change the Atheros wifi module, it's horrible! The drivers for linux really works bad. Sometime, when the signal is not so good, I cannot connect using linux, but windows can!
I tried madwifi and ndiswrapper with no luck.

Ale

---

### Post by dtox77 on 2011-02-23
Did anyone get the ALPS touch pad working properly?
It's recognized as a normal PS2 mouse. Using the touch pad for mouse button clicks isn't working properly. Sometimes I need to click the pad multiple times for a single mouse click. It's software thing as it's working flawless in Win7.

Anyone have any tweaks for this until the alps pads are properly recognized?

---

### Post by ginbuntu on 2011-02-26
Just installed kernel version 2.6.38 on Ubuntu 10.10. everything seems to work fine including screen dimming. Startup time is 6 seconds with SSD.

---

### Post by lamalta on 2011-03-05
> **ginbuntu said:**
> Just installed kernel version 2.6.38 on Ubuntu 10.10. everything seems to work fine including screen dimming. Startup time is 6 seconds with SSD.

I'm using the 2.6.37.2 : looks great, the battery now lasts longer!

---

### Post by andregus on 2011-03-11
When i run the command
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Scrolling" 8 1 1

on my 3820tg running 10.10 it say's "unable to find device SynPS/2 Synaptics TouchPad"

xinput list returns

&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; ImPS/2 Generic Wheel Mouse              	id=12	[slave  pointer  (2)]

Anyone knows why?  I thought "SynPS/2 Synaptics TouchPad" were there by default, do I have to install some package for that to work?

---

### Post by bernd on 2011-03-16
I think this xinput stuff is obsolet. anyway, I get the same message.

On my 3820TG this post fixed the touchpad issue :
[http://ubuntuforums.org/showpost.php?p=9932462&postcount=43](http://ubuntuforums.org/showpost.php?p=9932462&postcount=43)

---

### Post by cptNightrain on 2011-04-13
For those interested, I have been able to get Ubuntu working quite well on the Timeline 3820TG-3022. Basic usage was possible out of the box (Intel card only, no multitouch scrolling, no brightness control, broadcom WiFi drivers available in "Additional Drivers") but required a bit of tweaking. F

First off, as many people have found out, if you install the proprietary ATI drivers for the 5470 you'll be presented with a black screen on reboot. This is because the device uses *switchable graphics* - to fix this, go into your BIOS settings and switch "switchable" to "discrete" - essentially disabling the switchable feature as it is not yet supported in Ubuntu. Doing so should fix that problem and you should be rocking Warsow in no time. It's also important to note that I gained an additional hour or so in battery life after doing this. *However, the ATI driver isn't perfect - I'm unable to play any no-flash video with it enabled (audio still plays, video is black). Flash videos, such as Youtube, all play fine but avi's, ogv's, mpg's, and et cetera do not. This problem seems wide-spread so hopefully there will be a fix soon (maybe there already is - I haven't really looked into it too much).

It is possible to enable multitouch for the trackpad, and can be done quite simply through the install of a single deb: [synaptics-dkms]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/308191/+attachment/1735234/+files/synaptics-dkms_1.0.0_all.deb"). Once installed, I just rebooted, went into System->Preferences->Mouse, enabled two-finger scrolling and everything worked as it was supposed to.

I've tried the webcam and microphone - both work under Cheese and Sound Recorder respectively. Bluetooth can be turned on by counter-intuitively pressing fn+F3 which doesn't actually seem to have anything to do with WiFi, despite how it's labeled (I have not yet tried to transfer files over Bluetooth, but the icon does appear in the indicator applet and tells me that Bluetooth has been "enabled").

Media keys work just fine, though I wish Acer had put the multimedia controls on the arrow keys rather than the brightness/volume controls - my previous laptop placed those on I think F7-F10 and, as there are four unused F keys, Acer could have done so with the Timeline as well. From what I see, though, this is what Acer normally does for those keys.

Lastly, and perhaps the most annoying thing about the notebook, is that the keyboard does not support more than three simultaneous key presses. What does that mean? It means when I'm playing Supertuxkart and I want to accelerate, turn, look back, and fire a bowling ball at Konqi I can't because the keyboard only inputs the first three keys I press. From a quick Google search, it seems this is the fault of the actual keyboard itself and, therefore, not fixable :(. Poop.

---

### Post by datenraffzahn on 2011-04-16
> It is possible to enable multitouch for the trackpad, and can be done quite simply through the install of a single deb: synaptics-dkms. Once installed, I just rebooted, went into System->Preferences->Mouse, enabled two-finger scrolling and everything worked as it was supposed to.

This solution is not working on Kernel 2.6.38-8-generic of Natty. You will get something like this [Bug]("https://bugs.launchpad.net/xorg-driver-synaptics/+bug/308191/comments/134")

Newer synaptics-dkms (1.1.0, 1.1.1) packages will not work either.

There is no fix for this because Kernel 2.6.38 already includes it. 

But I still did not figure out how to get use of it. Touchpad is still detected as PS/2 Mouse. With psmouse.conf -> 

```
options psmouse proto=imps
```

I got it partially to work.

Any suggestions?

Laptop: Acer Aspire TimelineX 3820 TG
Ubuntu: latest Natty Narwhal x64

[Update]
I also tested all possible combinations of Kernel boot options i8024.reset, i8024.nomux=1 and irqpoll as suggested in [Ubuntu Wiki Touchpad]("http://wiki.ubuntuusers.de/touchpad"). But I still get just a stupid generic PS2/Mouse detected.

---

### Post by cptNightrain on 2011-04-16
You have me concerned about upgrading now - I hadn't considered synaptics-dkms support in Natty until now. I'm not running 11.04 yet - I'm holding off for final release - but I'll definitely do some research.  From looking at launchpad, the team seems quite active and has other projects in the works for Natty - hopefully they will update the package for 11.04. Just in case, I'll also look at alternative fixes.

---

### Post by datenraffzahn on 2011-04-17
Its not that bad.
I upgrade because I wanted to try out GNOME 3.
Its pretty awesome so far but this still unstable port gives me more headache than the touchpad.
I didn't convince  the multitouch trackpad to work on maverick anyway so I actually don't miss it.
Nice if it works but its not a "must have".

I can tell the 3820TG works pretty well on natty.
Nearly all of the advises in this thread still work or are obsolete.

Only things I adjusted :

- Turn off the AMD Graphics device
- Touchpad (generic scrolling)
- Brightness Control

anything else works out of the box

Only ath9k driver makes smaller problems though.
It works but the data rates are quite low for a N-Draft WLAN Card (around 80KB/s).
Its an official issue so there will be a patch out soon.

Anything else works fine.
And with AMD Graphics turned off, the battery holds 6 Hours.
Long enough to survive a college day :D

---

### Post by mediamind on 2011-04-19
> Only ath9k driver makes smaller problems though.
It works but the data rates are quite low for a N-Draft WLAN Card (around 80KB/s).
Its an official issue so there will be a patch out soon.

Fortunately there's an easy workaround...

Create the following file:
```
sudo gedit /etc/modprobe.d/ath9.conf
```

And add this line:
```
options ath9k nohwcrypt=1
```

Then restart networking (or reboot) to initiate:
```
sudo /etc/init.d/networking restart
```

More info on **[this Ubuntu Natty on the Acer 3820T wiki page]("http://wiki.daviddarts.com/Ubuntu_Natty_on_the_Acer_TimelineX_3820T")**.

---

### Post by datenraffzahn on 2011-04-19
Thanks that does the trick.

Just one problem, the trackpad, to go :)

---

### Post by mediamind on 2011-04-19
> Thanks that does the trick.

Great!

> Just one problem, the trackpad, to go 

I've activated two-finger scrolling (via "Mouse Preferences") and have found that the trackpad works pretty well under Natty. The one caveat is that your fingers need to be spaced apart in order to scroll smoothly (I often end up doing three-finger scrolling).

---

### Post by datenraffzahn on 2011-04-20
> I've activated two-finger scrolling (via "Mouse Preferences") and have found that the trackpad works pretty well under Natty. The one caveat is that your fingers need to be spaced apart in order to scroll smoothly (I often end up doing three-finger scrolling).

Hm ok seems to be a Gnome issue then. I will look into it, next time I've some free hours.

Edit: Do you have a T or a TG Model of you notebook? I ask because the T model works out of the box on natty another guy told me. The TG model makes more trouble here.

---

### Post by mediamind on 2011-04-20
> Edit: Do you have a T or a TG Model of you notebook? I ask because the T model works out of the box on natty another guy told me. The TG model makes more trouble here.

I have the 3820T-7459. 

For the TG, have you tried gmanic's solution from [post 43 in this thread]("http://ubuntuforums.org/showpost.php?p=9932462&postcount=43")?

---

### Post by datenraffzahn on 2011-04-20
> **mediamind said:**
> For the TG, have you tried gmanic's solution from [post 43 in this thread]("http://ubuntuforums.org/showpost.php?p=9932462&postcount=43")?

Yes so far the touchpad works but covers no multitouch features or further configuration.
My initial post mentions this.
The article in your previous post only mentions the T model with out of box working multitouch trackpad.
Mine doesn't because its a different one no Synaptics its from Alps.

There hopefully will be a solution soon.
I currently mostly use a mouse anyway.

---

### Post by podginater on 2011-04-23
Has anyone got hibernate working without the login screen on 10.10? Whenever, I try and hibernate, it takes me to the login screen and then hibernates after I type in my password.

---

### Post by datenraffzahn on 2011-04-26
> Has anyone got hibernate working without the login screen on 10.10? Whenever, I try and hibernate, it takes me to the login screen and then hibernates after I type in my password.

As far as I can tell hibernation works flawlessly.

If I understand your statement correctly you either:
-  get asked you for root permission because you are not allowed to hibernate
  (which indicates a sudo configuration problem)
or
- get the normal password screen the computer shows when it gets locked
  (which usually happens if you hibernate or suspend by default).

In case of the second explanation: you can configure GNOME,
not to show this screen after suspend or hibernating at all.
Look up Power-Settings or Screensaver-Settings to set this option.
If you want this screen for security just click hibernate and let Ubuntu do its magic.
It takes a few seconds before hibernation really kicks in.

Falling back to the real GDM login screen (screen after (re-) boot)
means your problem causes to crash the whole X-Window-System.
(which would be the worst case)
In this case you need to examine your /var/log/Xorg.0.log after reproducing this problem.
Attach it to the next  post (or your first post) and I(we)'ll see if there are any clues for the solution in it.

In general we need more information than "it don't works".

---

### Post by podginater on 2011-04-26
Thanks for your response. The hibernation does work in the fact that it does hibernate and re-wake fine. However my problem is that after pressing hibernate in the first case, it takes me to the lock screen in order for me to type my password in. After typing it in, then in hibernates. I was just wondering if it were possible to hibernate straight away without it taking me to the lock screen for me to authorise the hibernation. I haven't a problem with the lock screen coming up after the hibernation; I have changed the power management to my requirements. I realise this probably has something to do with root privileges but I wouldn't have the slightest clue about how to go about changing these hence the first query. Apologies for my previous vagueness.

---

### Post by cptNightrain on 2011-04-26
> I'm unable to play any no-flash video with it enabled (audio still plays, video is black)
So I found out the stupid reason I was having this problem...my contrast was, for some unknown reason, set at zero! After not getting any error output when I played a video through Totem in the terminal, I decided to check the program's preferences menu just in case. Thats where I noticed my slider for video contrast was set as low as possible. Setting contrast back to normal returned my video. Not sure what caused my contrast to be set to 0, but I'm happy to have videos working again.

Still no luck finding a solution for multi-touch in Natty...

---

### Post by datenraffzahn on 2011-04-27
> I realise this probably has something to do with root privileges but I wouldn't have the slightest clue about how to go about changing these hence the first query.

I can not remember that I ever was forced to change something like that on an Ubuntu System. I do not assume you either.
Nevermind. Lets see if you are in the same user groups as I am.
Open a terminal and type :

```
groups
```

Response should be something like this: 

```
$username adm dialout cdrom plugdev lpadmin admin sambashare
```

Its just a wild guess rather than a real solution.
But my research on this topic had come up empty.
I really don't know where to start.
Also you can try to find out if the Ubuntu Groups-Settings (System->Settings(?)-> User and Groups) solves this.

If you just installed Ubuntu and created a User while installation you should be fine.
May be another application causes this.
A propper solution may take some time.
If all fails just reinstall Ubuntu.

Natty releases tomorrow may be a good reason to "upgrade". ;)

---

### Post by podginater on 2011-04-27
The 'groups' were exactly as you said and the 'users and groups' didn't resolve anything but it's a minor inconvenience at best I was just trying to get my system exactly as I wanted it. As far as I can see, my user account is just a normal account with some elevated privileges. I might install 11.04 if I get used to unity a bit more because at first glance I think I still prefer gnome but time will tell and the strange force, which seems to compel me to be up-to-date and upgrade whether the product is better or not, will probably work its magic. Thank you anyway.

---

### Post by datenraffzahn on 2011-04-28
> I might install 11.04 if I get used to unity a bit more because at first glance I think I still prefer gnome but time will tell and the strange force, which seems to compel me to be up-to-date and upgrade whether the product is better or not, will probably work its magic.

You can use the good old GNOME anyway.
You just need to select it from the login-screen because Canonical decided to preselect the Unity Desktop for you.
There are 2 Sessions available "Ubuntu Desktop" and "Ubuntu Desktop Classic" of which the second provides the old GNOME 2.3x desktop

I screwed up my system by installing Gnome 3 so I can not provide information if it really works with all features you know back from maverick, its just what I read from countless Unity refugees. :D

---

### Post by podginater on 2011-04-29
Yeah, I realised that when I tried to run it in VirtualBox when it came out. For some reason, VirtualBox doesn't like unity. It didn't seem different enough for me change straight away but I might in a few months.

---

### Post by BreenLantern on 2011-05-07
Upgraded to 11.04..however touchpad still recognized as a PS/2 mouse.  Has anyone found a way to get the touchpad "tap to click" turned off?? It is very frustrating.

---

### Post by zombolo on 2011-05-07
My touchpad (alps) after a couple of hours goes grazy randomly
Tapping to click is almost impossibile.
I have already used the proto=imps + modproble -r psmouse + reboot etc... workaround ,but no effects on this bug. Is there a solution out there? Anyone tried kernel 2.6.39?

Please help, Ubuntu is fantastic but without working touchpad is useless.
It's a very strange bug. O__0

P.S. with windows 7 I don't have any problem with this damned touchpad.

---

### Post by datenraffzahn on 2011-05-09
Hello ubunturians, 
I'm experiencing bigger issues on booting ubuntu natty lately.
Let me explain:

I reinstalled Ubuntu Natty because I pretty screwed my last installation.

The installation did well everything works I added the fixes and
workarounds for Ubuntu on an Acer Aspire Timeline X 3820 TG which
includes the the Graphics switched off. (On boot described
[here]("http://asusm51ta-with-linux.blogspot.com/"), added echo OFF > ... to rc.local)

But now my System crashes nearly 2 times in 3 boots with a blackscreen.
I can switch the TTYs but I am not to login and find out whats going on
 as well as do something about it.

TTY 7 shows me a Stacktrace for Kernel-Module radeon.
So I guess this vgaswitcheroo thing messes this up.
If it boots correctly anything works, but if I reboot
there is a chance that I have to reboot several times
before it ends up with a gdm screen.

I try to grab the stack trace and attach it to this post.
EDIT : No way to grab this thing need to set up kdump or something like that...

On my previous installation sometimes booting fails
(Same Blackscreen with stacktrace) too, but not that often.

Is there a anything I missed or a fix which removes this issue once and for all?

EDIT:
I reverted my rc.local to default and my system keeps crashing after all.
Odd in this situation is the installation works fine first boots too.
Only thing I added so far was the psmouse.conf and the
Linux "acpi_os=Linux" Kernel parameter.
Even if I revert everything to default the system keeps crashing ...

---

### Post by zombolo on 2011-05-12
> **dtox77 said:**
> Did anyone get the ALPS touch pad working properly?
It's recognized as a normal PS2 mouse. Using the touch pad for mouse button clicks isn't working properly. Sometimes I need to click the pad multiple times for a single mouse click. It's software thing as it's working flawless in Win7.

Anyone have any tweaks for this until the alps pads are properly recognized?

Same problem here.
No solutions yet? :(

---

### Post by zombolo on 2011-05-14
Bump

---

### Post by lamalta on 2011-05-20
I installed the kernel 2.6.39 on my Natty: FINALLY, the WI-FI works fine!

---

### Post by zombolo on 2011-05-23
What about touchpad fixings (see above posts)?

---

### Post by datenraffzahn on 2011-05-23
> What about touchpad fixings (see above posts)?

Still not fixed.
At least under natty with Gnome 3.

> I installed the kernel 2.6.39 on my Natty: FINALLY, the WI-FI works fine!
Can not confirm this.
I still get around 140 KB/s on a N-Draft Network.
Unacceptable.

But at least my startup crashing issue seems not to occur as often as under kernel 2.6.38.
So thanks for this hint. :D

---

### Post by zombolo on 2011-05-24
Many thanks datenraffzahn.
I hope Alps touchpad prolem will be fixed as soon as possibile (the bug is not related only in Ubuntu, I have tried different distros). I am waiting for a fix or a workaround... I prefer to use an external usb mouse and not to come back to Win7.

---

### Post by zombolo on 2011-06-05
Anyone tried 3.0 kernel? Any news on ALPS touchpad?
Thanks in advance.

---

### Post by zombolo on 2011-06-06
EDIT: after 2 days, touchpad problem still perxists. :/

---

### Post by Zevaka on 2011-06-06
i installed kernel 3.0.0 (rc1) on my acer. Now it boots 100 times from 100 (on 2.6.38 and 2.6.39 booted 1 times from 4)

---

### Post by zombolo on 2011-06-07
> **Zevaka said:**
> i installed kernel 3.0.0 (rc1) on my acer. Now it boots 100 times from 100 (on 2.6.38 and 2.6.39 booted 1 times from 4)

Do you have ALPS touchpad?

---

### Post by datenraffzahn on 2011-06-07
I just booted the RC1 of Kernel 3.0 and got no crash at all very good. Only the virtualbox Module reports a crash though.

Touchpad is still recognized as a stupid little generic mouse.


At least the crash issue is gone...

so long

---

### Post by wjamoore on 2011-06-14
> **peterlustig said:**
> Hi everyone,
I thought I'd start a thread on the Acer Aspire TimelineX 3820T - 334G32N since I ran into some small issues that at least partially can be solved:

**Fan** issue:
Running Ubuntu Lucid with the 64bit version of kernel 2.6.32-22, I first burnt my fingers and then realized that the CPU fan was either not working or working at very low speed.
I wasn't able to resolve that last night, since there were no entries in /proc/acpi/fan/
[I]EDIT:
using bios v 1.13 and ubuntu 10.04, 64bit, kernel 2.6.32-22 temperatures are still a bit high, but acceptable (40-45°C when idle and 65-70°C when running on maximum load for half an hour.[/I]

Running Ubuntu Lucid with the 2.6.32-22-generic-pae (32bit) kernel, the fan(s) is working as it should, but still no entries in /proc/acpi/fan/ or in /sys/...
However, I'm still not able to manually set or read the fan speed, which is not a problem, since the fan(s) is working. No overheating problems.

**Brightness** issue:
The brightness of the display can not be adjusted (that is true for the 64bit and 32bit kernel) using gnome-power-preferences or the Fn+arrow keys on the keyboard. Using the Fn+arrow keys, the brightness indicator in gnome is called and can be adjusted, but the actual brightness of the display does not change. There is a workaround for this problem that I found elsewhere (I don't remember):

```

sudo gedit /etc/default/grub

```Change the line *GRUB_CMDLINE_LINUX=""* into
```

GRUB_CMDLINE_LINUX="acpi_osi=Linux"

```then run
```
sudo update-grub
```In my case this worked.

**Integrated microphone** issue:
I couldn't get the integrated microphone to work with pulse or alsa. But then again I haven't put much energy into that.

**Headphones** issue:
Wow, this is getting worse and worse: Headphones jack sense seems to work in the sense that when you plug in the headphones you don't get any sound from the integrated speakers. Unfortunately you don't get any sound from the headphones either... I really wonder what I am doing wrong... the system beep is clearly audible via the headphones when the system shuts down. #!%§&
[I]EDIT:
I ran the [ AlsaUpgrade script]("http://ubuntuforums.org/showpost.php?p=6589810&postcount=1") by soundcheck. No more headphone-issues.[/I]

**Suspend/Hibernate** issue:
After waking up from suspend, the CPU fan stops working and the CPU frequency is set to max, what an inconvenient combination...
*EDIT: Using bios v1.13 this doesn't happen so frequently any more. But it still does happen.*

**Multi touch** issue:
That multitouch touchpad stuff has become a bit complicated. I couldn't get that to work either... yet.
[I]EDIT:
workaround: [#6]("http://ubuntuforums.org/showpost.php?p=9301251&postcount=6")
[/I]
Everything else seems to work just fine and out of the box. SD-card reader, HDMI, cpu feq scaling. But it took me a while until I realized that I have to press the wireless toggle button (Fn+F3) to activate wlan AND again to activate bluetooth. 

I hope this is of some help to someone. If any of you have an idea how to tackle the integrated mic - problem, I'd be happy to hear about it.

Good luck,
Peter 

Many thanks.. worked fine for me on ACER 3820TZ.   the brightness issue that is..  Now seeing an incredible 8 hours 45 battery life on lowest brighness!

---

### Post by CarlGWatts on 2011-07-05
I've been using natty on my Timeline X 3820T for quite awhile now and most thinks work OK.

One annoying thing is that when I don't move my mouse cursor for 20 seconds or more and then try to move it, the cursor on the screen moves in a halting/stuttering way for 2-3 seconds and then starts moving smoothly again.

This machine has the crappy ALPS touchpad so Ubuntu has never quite been able to configure it properly. But I didn't notice this problem until I installed natty.

Has anyone else noticed this problem and found a solution for it?

---

### Post by datenraffzahn on 2011-07-07
I notice the same issue if my notebook runs on battery.
On normal AC-power everything works fine.

So I assume its related to power saving mechanisms.

If you don't use your touch pad its suspended to conserve energy.

Unfortunately the wake up time is quite long
so this "stuttering" occurs.

May be you do a little research on that...

---

### Post by mediamind on 2011-07-07
I also experience this issue when running on battery...

---

### Post by datenraffzahn on 2011-07-15
I did a little more research
and have to correct my previous post.
It's not the track pad waking up from suspension
it's the graphics chip.

If you have compiz (Gnome 3 or whatever) active
you will note the same stuttering
while switching between desktops (on wake up)
which runs usually smoothly.

So its a good thing though...

---

### Post by zombolo on 2011-07-23
> **zombolo said:**
> Anyone tried 3.0 kernel? Any news on ALPS touchpad?
Thanks in advance.

Final build of 3.0 kernel is out: any luck about ALPS touchpad?

[https://launchpad.net/ubuntu/+source/linux/3.0.0-7.8/+build/2640215](https://launchpad.net/ubuntu/+source/linux/3.0.0-7.8/+build/2640215)

---

### Post by Halzen on 2011-07-23
> **zombolo said:**
> Final build of 3.0 kernel is out: any luck about ALPS touchpad?

[https://launchpad.net/ubuntu/+source/linux/3.0.0-7.8/+build/2640215](https://launchpad.net/ubuntu/+source/linux/3.0.0-7.8/+build/2640215)

The touchpad on my 3820T-6480 performed no better on kernel 3.0. However, my Vertex 2's transfer rate was cut in half on benchmarks, so SSD users beware.

---

### Post by zombolo on 2011-07-24
Too bad... :/

---

### Post by skamithi on 2011-10-02
Just tested out the psmouse driver documented at
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/550625](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/550625) on my acer 3820T-6480.

[http://people.canonical.com/~sforshee/alps-touchpad/psmouse-alps-0.9/psmouse-alps-dkms_0.9_all.deb](http://people.canonical.com/~sforshee/alps-touchpad/psmouse-alps-0.9/psmouse-alps-dkms_0.9_all.deb)

Removed the imps workaround from the /etc/modprobe.d/psmouse.conf

Vertical scrolling now works without the workaround.

this is my current natty version.
2.6.38-11-generic #50-Ubuntu SMP Mon Sep 12 21:17:25 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

```
 xinput list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; PS/2 Mouse                              	id=11	[slave  pointer  (2)]
&#9116;   &#8627; AlpsPS/2 ALPS GlidePoint                	id=12	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=8	[slave  keyboard (3)]
    &#8627; 1.3M WebCam                             	id=9	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=10	[slave  keyboard (3)]
```

---

### Post by Kakitus on 2011-10-09
Hello guys,
I've owned my ACer 3820TG for over a year now, but only recently I decided to switch to Ubuntu. I hope you will be able to help me with the following problem:

I've been using Ubuntu 11.04 on "dedicated only" mode with fglrx for over a month. Because from now on I'm planning to use the notebook on battery frequently , I followed this guide and unlocked the "Intel only" mode. Due to the fglrx drivers, however, the system does not boot up in IGP-mode. I just end up at a Linux terminal. Switching over to PEG (i.e. dedicated only) solves that problem. But by doing so I'm stuck with the ATI HD5650 again.

I would love to be able to choose between the two cards in BIOS. For that to work, however, the linux drivers would have to support both ATI and Intel. That does not seem to be the case with fglrx.

Do you know of any linux driver that could do that?

Solving this problem is crucial to my staying with Ubuntu.

Thank you very much in advance

---

### Post by isumi on 2011-10-20
Hello, i'm using ubuntu 11.10 on my 3820tg with ati5470 and i've some troubles with disabling ati card.
Before 11.10 i had 11.04 and somehow managed to disable the ati card in the catalyst menu, as far as i can remember, i had about 4-5h battery life. After reparation i tried it again, but i can't find this option any more. Then it must have been version 11.7 of catalyst. Now if i am on switchable mode in bios, then i get an error-message (like run aticonfig, what doesn't help) while accessing the ati catalyst software. 
Switching in bios to discrete mode enables only the ati card.

I just tried and the battery life increased to 5h...

sudo su 
echo OFF > /sys/kernel/debug/vgaswitcheroo/switch

---

### Post by jeannieburt on 2012-01-22
:D  This worked like a champ on my Acer Aspire One Model ZG5. I tried a lot of other threads and none but this one worked.  Thanks so much.  You have a fan

Jeannie

> **peterlustig said:**
> Hi everyone,
I thought I'd start a thread on the Acer Aspire TimelineX 3820T - 334G32N since I ran into some small issues that at least partially can be solved:

**Fan** issue:
Running Ubuntu Lucid with the 64bit version of kernel 2.6.32-22, I first burnt my fingers and then realized that the CPU fan was either not working or working at very low speed.
I wasn't able to resolve that last night, since there were no entries in /proc/acpi/fan/
[I]EDIT:
using bios v 1.13 and ubuntu 10.04, 64bit, kernel 2.6.32-22 temperatures are still a bit high, but acceptable (40-45°C when idle and 65-70°C when running on maximum load for half an hour.[/I]

Running Ubuntu Lucid with the 2.6.32-22-generic-pae (32bit) kernel, the fan(s) is working as it should, but still no entries in /proc/acpi/fan/ or in /sys/...
However, I'm still not able to manually set or read the fan speed, which is not a problem, since the fan(s) is working. No overheating problems.

**Brightness** issue:
The brightness of the display can not be adjusted (that is true for the 64bit and 32bit kernel) using gnome-power-preferences or the Fn+arrow keys on the keyboard. Using the Fn+arrow keys, the brightness indicator in gnome is called and can be adjusted, but the actual brightness of the display does not change. There is a workaround for this problem that I found elsewhere (I don't remember):

```

sudo gedit /etc/default/grub

```Change the line *GRUB_CMDLINE_LINUX=""* into
```

GRUB_CMDLINE_LINUX="acpi_osi=Linux"

```then run
```
sudo update-grub
```In my case this worked.

**Integrated microphone** issue:
I couldn't get the integrated microphone to work with pulse or alsa. But then again I haven't put much energy into that.

**Headphones** issue:
Wow, this is getting worse and worse: Headphones jack sense seems to work in the sense that when you plug in the headphones you don't get any sound from the integrated speakers. Unfortunately you don't get any sound from the headphones either... I really wonder what I am doing wrong... the system beep is clearly audible via the headphones when the system shuts down. #!%§&
[I]EDIT:
I ran the [ AlsaUpgrade script]("http://ubuntuforums.org/showpost.php?p=6589810&postcount=1") by soundcheck. No more headphone-issues.[/I]

**Suspend/Hibernate** issue:
After waking up from suspend, the CPU fan stops working and the CPU frequency is set to max, what an inconvenient combination...
*EDIT: Using bios v1.13 this doesn't happen so frequently any more. But it still does happen.*

**Multi touch** issue:
That multitouch touchpad stuff has become a bit complicated. I couldn't get that to work either... yet.
[I]EDIT:
workaround: [#6]("http://ubuntuforums.org/showpost.php?p=9301251&postcount=6")
[/I]
Everything else seems to work just fine and out of the box. SD-card reader, HDMI, cpu feq scaling. But it took me a while until I realized that I have to press the wireless toggle button (Fn+F3) to activate wlan AND again to activate bluetooth. 

I hope this is of some help to someone. If any of you have an idea how to tackle the integrated mic - problem, I'd be happy to hear about it.

Good luck,
Peter

---

### Post by datenraffzahn on 2012-01-24
> **skamithi said:**
> Just tested out the psmouse driver documented at
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/550625](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/550625) on my acer 3820T-6480.

[http://people.canonical.com/~sforshee/alps-touchpad/psmouse-alps-0.9/psmouse-alps-dkms_0.9_all.deb](http://people.canonical.com/~sforshee/alps-touchpad/psmouse-alps-0.9/psmouse-alps-dkms_0.9_all.deb)

Removed the imps workaround from the /etc/modprobe.d/psmouse.conf

Vertical scrolling now works without the workaround.

this is my current natty version.
2.6.38-11-generic #50-Ubuntu SMP Mon Sep 12 21:17:25 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

```
 xinput list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; PS/2 Mouse                              	id=11	[slave  pointer  (2)]
&#9116;   &#8627; AlpsPS/2 ALPS GlidePoint                	id=12	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=8	[slave  keyboard (3)]
    &#8627; 1.3M WebCam                             	id=9	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=10	[slave  keyboard (3)]
```

Because its to funny fixing up the same things all and all over again.
I recently (today) noticed that my trackpad of the Acer TimelineX 3820TG now fails after logging in to Unity/Gnome/Gnome3 (using Ubuntu 11.10).

Its working on the login screen after starting the session the mouse cursor wouldn't move.

The cause in my case was the solution mentioned by "skamithi".
After dropping the package it works again.
Maybe the package is crappy and needs a manual reinstallation each time the kernel is updated.
I didn't try it out, since the track pad didn't work complete anyway using this module.
So I rarely miss it.

I just wanted to post the fix here in case somebody else runs into this.

---

### Post by jlh68 on 2012-01-24
I have a TimelineX 4820T which is similar.  I upgraded my BIOS to version 1.19 and that cured a lot of ills.  I still have no use of the "P" key that is to the left of the drive eject button.  My CPU temps stay around 45 degrees C and the Hard drive is usually around 35 degrees C.  So no real fan problems.

---

### Post by kolslorr on 2012-05-01
Now that 12.04 LTS is out.... has anyone managed to get 3820TG running well with Radeon 5650 card turn on???

I tried the restricted extras fglrx drivers, it didnt allow me to run anything 3D at all... not even unity 3D.

I also tried the latest Catalyst driver, that is worse, it boots directly to commandline mode.

Is this machine doomed for Ubuntu?

---

### Post by Cabalbl4 on 2012-05-09
Got all 3D graphics working with generic drivers, using vgaswitcheroo (with self-made gui scripts for wrapping) to switch intel/radeon (in 11.04 and now in 12.04). Fglrx did very bad on my Acer - accel. problems on internal card, card switch problem etc... So I just live happily without it ^^

---

