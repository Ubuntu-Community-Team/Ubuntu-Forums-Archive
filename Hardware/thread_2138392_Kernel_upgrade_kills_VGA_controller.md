---
title: "Kernel upgrade kills VGA controller"
date: 2013-04-23
forum: Hardware
---

### Post by hencelence on 2013-04-23
Hey guys,

I upgraded from Xubuntu 12.10 to 13.04 tonight by running 
```
sudo do-release-upgrade -d
``` and thus the kernel from 3.5.x to 3.8.x

I'm on a Dell Studio Laptop, (Core 2 Duo, 3GB RAM, ATI Mobilty Radeon 3000 Series).
When rebooting back in, the system didnt recognize my VGA controller anymore (*-display UNCLAIMED when "lshw").
I tried hundreds of different solutions to fix it, amongst them:
[LIST]
[*]installing fglrx and reinstalling 
[*]installation via amdccl and aticonfig 
[*]complete reinstall of kubuntu-desktop 
[*]fix the packages 
[*]dpkg-configure xserver-xorg 
[*]... 
[/LIST]

Nothing helped. I guess the kernel update's the problem?
Anyone else having similar issues?

For now it's okay, I just manually boot into the older kernel in grub.

Anything else I could do?

---

### Post by matt_symes on 2013-04-23
HI

Have you looked in your log files ?

```
/var/log/Xorg.0.log
```

That is where is would start looking for clues as to what is happening.

Narrow down the search by using grep.

```
grep "EE" /var/log/Xorg.{0,1,2,3}.log{,.old}
```

If that returns nothing, you'll need a visual inspection of one of the log files where you know the boot was bad.

That's where i would start.

How far into the boot process does it get BTW ?

Kind regards

---

### Post by hencelence on 2013-04-24
> **matt_symes said:**
> 
Have you looked in your log files ?
That is where is would start looking for clues as to what is happening.
Narrow down the search by using grep.


Great idea, thank you.
The grep command returns
```

lenz@dell-studio:~$ grep "EE" /var/log/Xorg.0.log
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    26.697] Initializing built-in extension MIT-SCREEN-SAVER
[    27.147] (EE) No supported AMD display adapters were found
[    27.147] (EE) open /dev/dri/card0: No such file or directory
[    27.147] (EE) Screen 0 deleted because of no matching config section.
[    27.382] (EE) GLX error: Can not get required symbols.

```

> **matt_symes said:**
> 
How far into the boot process does it get BTW ?

It actually boots into a fully operational system, as you can see in the log file.
It just doesn't recognize my card, so it puts me into a failsafe graphics mode with a resolution of 800x600.

Thanks a lot for your help, Matt.

---

### Post by hencelence on 2013-04-24
For a comparison, here's the output on the 3.5.x kernel version:
```

lenz@dell-studio:~$ grep "EE" /var/log/Xorg.0.log
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    29.966] Initializing built-in extension MIT-SCREEN-SAVER
[    30.391] (EE) No supported AMD display adapters were found
[    30.536] (EE) GLX error: Can not get required symbols.

```

So for a strange reason, the same error occurs. 
Nonetheless, it puts me into a normal graphics mode with decent resolution and higher refresh rate.

Is this maybe an easy fix using xrandr or something?
Sorry if it's something incredibly essential, I'm fairly new to Ubuntu.

[ATTACH=CONFIG]241711[/ATTACH]

---

### Post by matt_symes on 2013-04-24
Hi

Can get get more info on your display adaptor.

Can you post the output of this command

```
sudo lshw -c display
```

and also this one

```
lspci -nnk | grep -iA2 vga
```

Capital A above. 

Kind regards

---

### Post by hencelence on 2013-04-24
Thanks Matt for being caring and helpful:

sudo lshw -c display:

```

lenz@dell-studio:~$ sudo lshw -c display
[sudo] password for lenz: 
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: RV620/M82 [Mobility Radeon HD 3450/3470]
       vendor: Advanced Micro Devices [AMD] nee ATI
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list
       configuration: latency=0
       resources: memory:d0000000-dfffffff ioport:2000(size=256) memory:cfef0000-cfefffff memory:cfe00000-cfe1ffff
```

lspci -nnk | grep -iA2 vga:

```

lenz@dell-studio:~$ lspci -nnk | grep -iA2 vga
01:00.0 VGA compatible controller [0300]: Advanced Micro Devices [AMD] nee ATI RV620/M82 [Mobility Radeon HD 3450/3470] [1002:95c4]
    Subsystem: Dell Device [1028:029f]
01:00.1 Audio device [0403]: Advanced Micro Devices [AMD] nee ATI RV620 HDMI Audio [Radeon HD 3400 Series] [1002:aa28]

```

Does that help you?

---

### Post by hencelence on 2013-04-24
xrandr  -s 1280x800 returns:

```

Size 1280x800 not found in available modes

```

This mode is obviously available in the 12.10 version with kernel 3.5.x, though.

---

### Post by matt_symes on 2013-04-24
Hi

I may have some bad news for you. Your card may not work in 13.04.

Take a look at this page and the section 'Older RadeonHD' - this site is pretty good.

[http://wiki.cchtml.com/index.php/Hardware](http://wiki.cchtml.com/index.php/Hardware)

> [COLOR=#000000][FONT=sans-serif]These cards are now supported with the later released Catalyst 13-1 legacy, but you MUST use a kernel <= 3.4 and Xserver <= 1.12. For example, you can use Catalyst 13-1 legacy if you're running Ubuntu 12.04 or Debian Squeeze/6.0.

<snip>
[/FONT][/COLOR]
* RV620       Radeon HD 3450/3470, M82

You may have been lucky running Quantal and that may explain the error message you were getting about 'no AMD adaptors found'. 

Please post the output of

```
X -version
```

Capital X, single dash. Also

```
uname -r
```

Also, what version of fglrx did you install ?

To be totally honest, your best bet may be to use the Radeon open source driver as i would be very surprised if that did not still support your card (i would have to double check).

Post back the results of your X server, kernel and fglrx versions and we can take it from there.

Kind regards

---

### Post by hencelence on 2013-04-24
X version:

```

X.Org X Server 1.13.3
Release Date: 2013-03-07
X Protocol Version 11, Revision 0
Build Operating System: Linux 3.2.0-37-generic i686 Ubuntu
Current Operating System: Linux dell-studio 3.8.0-19-generic #29-Ubuntu SMP Wed Apr 17 18:19:42 UTC 2013 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.8.0-19-generic root=UUID=cd38ed06-9c26-429f-a47b-70f74a3b4ed9 ro quiet splash vt.handoff=7
Build Date: 17 April 2013  10:42:56PM
xorg-server 2:1.13.3-0ubuntu6 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.28.2

```

Kernel version:

```

3.8.0-19-generic

```

fglrx version (according to synaptic):

2:9.010ubuntu3

> 
I may have some bad news for you. Your card may not work in 13.04
.

Aw man! My laptop is not even that old... and I thought DELL would be one of the best-supported companies.
:(


How would I install the Open-Source drivers?
Remove the fglrx via synaptic and then?

---

### Post by matt_symes on 2013-04-24
Hi

Sorry to be the bearer of bad news :(

BTW: It's AMD and not dell who are responsible for maintaining the fglrx drivers on Linux.

How did you install the flgrx drivers in the first place ? Using the additional drivers or from the AMD website ? (I suspect i know the answer but i would like to triple check).

BTW: The Radeon drivers are not all that bad otherwise i would not use them :D

```
matthew-S206:/home/matthew/storage % lspci -nnk | grep -iA2 vga
00:01.0 VGA compatible controller [0300]: Advanced Micro Devices [AMD] nee ATI Wrestler [Radeon HD 6310] [1002:9802]
        Subsystem: Lenovo Device [17aa:397b]
        Kernel driver in use: **radeon**
matthew-S206:/home/matthew/storage % 
```

... and my card can use fglrx under 13.4.

Kind regards

---

### Post by hencelence on 2013-04-24
> **matt_symes said:**
> 
Sorry to be the bearer of bad news :(

Dude, no! I am thankful for for very quick and competent support.

> **matt_symes said:**
> 
BTW: It's AMD and not dell who are responsible for maintaining the fglrx drivers on Linux.

Well then: AMD, f you!
My laptop is not even 5 years old.

> **matt_symes said:**
> 
How did you install the flgrx drivers in the first place ? Using the additional drivers or from the AMD website ? (I suspect i know the answer but i would like to triple check).

First via additional drivers, then via synaptic, then with the website.
What's the 'right' way?

SoI just manually removed the fglrx drivers and when I try to boot now; I boot into a graphical glitch just before the login manager.

These outputs are from the 3.5.x kernel.

```

lenz@dell-studio:~$ grep "EE" /var/log/Xorg.0.log
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    37.621] Initializing built-in extension MIT-SCREEN-SAVER
[    38.048] (EE) Failed to load module "fglrx" (module does not exist, 0)
[    38.791] (EE) Failed to load module "fglrx" (module does not exist, 0)

```

```
lenz@dell-studio:~$ sudo lspci -nnk | grep -iA2 vga
01:00.0 VGA compatible controller [0300]: Advanced Micro Devices [AMD] nee ATI RV620/M82 [Mobility Radeon HD 3450/3470] [1002:95c4]
    Subsystem: Dell Device [1028:029f]
    Kernel driver in use: radeon

```
It's a beautiful driver indeed, but it doesn't seem to work in 13.04.

Is there anyway I can boot into 13.04 or do I need to "downgrade" via reinstall?

---

### Post by matt_symes on 2013-04-24
Hi
> 
First via additional drivers, then via synaptic, then with the website.
What's the 'right' way?

To be honest, there is no right way although it's easier from the additional drivers section.

There is an uninstall script you can run with fglrx from the AMD website. With 'additional drivers' or synaptic you will not need to run this script.

If you uninstalled from the 'additional drivers' window then you should have been able to remove it from there.

However as you installed it from the AMD website you may have to do some additional steps.

Have a read of this

[http://wiki.cchtml.com/index.php/Ubuntu_Quantal_Installation_Guide#Removing_Catalyst.2Ffglrx](http://wiki.cchtml.com/index.php/Ubuntu_Quantal_Installation_Guide#Removing_Catalyst.2Ffglrx)

You should still be able to follow the steps to get you back to Radeon working.

Uninstalling fglrx correctly and completely will ensure you use the Radeon driver.

If you need any help with that guide then post back. 

No need to reinstall just yet :)

**EDIT:**

> I boot into a graphical glitch just before the login manager.

What do you mean by this ? Can you post a photo of the graphical glitch please.

Kind regards

---

### Post by hencelence on 2013-04-25
> **matt_symes said:**
> 
[http://wiki.cchtml.com/index.php/Ubuntu_Quantal_Installation_Guide#Removing_Catalyst.2Ffglrx](http://wiki.cchtml.com/index.php/Ubuntu_Quantal_Installation_Guide#Removing_Catalyst.2Ffglrx)
You should still be able to follow the steps to get you back to Radeon working.
Uninstalling fglrx correctly and completely will ensure you use the Radeon driver.

Followed the instructions, it seems to be outdated though, there's no file named xorg.conf nor in my /etc/X11 nor anywhere else on my system (according to 'locate'),


So here are the complete scenarios:

**1. I boot into kernel version 3.5.0-27 or 3.5.0-17** with either *fglrx _or_ the open-source driver.*
Everything goes smoothly, I boot into a fully operational, nicely (3d) accelerated system.
See image attached to post #4.
[B]
2. I boot into kernel version 3.8.0-19[/B] with *fglrx* drivers installed.
I boot into an operational system, but with graphics from 1995 (screen resolution 800x600)
See image attached to post #3.

I tried some xrandr commands, none of them work.

**3. I boot into kernelversion 3.8.0-19** _without_ the *fglrx* drivers

The system shows me the new xubuntu booting screen (the one with the circle), then glitches and locks up.

[ATTACH=CONFIG]241760[/ATTACH]

> **matt_symes said:**
> 
What do you mean by this ? Can you post a photo of the graphical glitch please.


[ATTACH=CONFIG]241764[/ATTACH]

I tried to type my password blindly after a minute or so, no response.



It seems that my graphics card just isn't supported anymore in 13.04, am I right?
That kind of sucks, I will have to use an outdated system until I can eventually get my hands on a new compatible vga module.

Thanks for your caring, fast, creative and competent instructions and help so far, you're one of the guys who make Ubuntu's community the excellent one that it is. :>

I will now back up my home folder on an external drive (to then possibly move to 12.10).
...and maybe try out a new DE, is KDE worth giving a chance (trick question, I know)?

---

### Post by matt_symes on 2013-04-25
Hi

> It seems that my graphics card just isn't supported anymore in 13.04, am I right?
That kind of sucks, I will have to use an outdated system until I can eventually get my hands on a new compatible vga module.

Fglrx will not work under the 3.8 kernel however the Radeon driver should work. We can investigate the hang if you'd like to.

> Thanks for your caring, fast, creative and competent instructions and  help so far, you're one of the guys who make Ubuntu's community the  excellent one that it is. :>

No problem at all :)

> I will now back up my home folder on an external drive (to then possibly move to 12.10).
...and maybe try out a new DE, is KDE worth giving a chance (trick question, I know)?

This may be the quickest option for you depending on how much customisation you have done.

If you'd like to try to fix the current install then we would need to look at you log files when booting into Xubuntu using the Radeon driver. We would need to see

```
/var/log/dmesg
```

and 

```
/var/log/Xorg.0.log
```

You can get them from a LiveCD/USB or from a root command prompt selected from the grub menu.

It depends what you would like to do. This is fixable and if you'd like to go down that route then i'll help you through it. It may take a day or two to sort it though.

Kind regards

---

### Post by hencelence on 2013-04-25
> **matt_symes said:**
> 
This is fixable and if you'd like to go down that route then i'll help you through it. It may take a day or two to sort it though.


Yeah, let's take the red pill and see how deep the rabbit hole goes.
I'm sure I won't be the only one who will run into this problem.

Let me get this straight:
I will now:
[LIST]
[*]boot into new kernel
[*]let it crash
[*]reboot to recovery console
[*]get the output of those 2 commands (should be '**cat** /var...' right?)
[/LIST]

right?

---

### Post by matt_symes on 2013-04-25
Hi

> **hencelence said:**
> Yeah, let's take the red pill and see how deep the rabbit hole goes.
I'm sure I won't be the only one who will run into this problem.

Let me get this straight:
I will now:
[LIST]
[*]boot into new kernel 
[*]let it crash 
[*]reboot to recovery console 
[*]get the output of those 2 commands (should be '**cat** /var...' right?) 
[/LIST]

right?

It would be easier from a LiveCD/USB. Do you have one ? If you do then boot into that from the BIOS. Mount the hard drive using nautilus and you will be able to copy and paste the contents of the logs from the hard drive into your next post. Make sure it's the logs from the hard drive and not from the live environment :) That's a mistake i've made before :oops:

You may have to make it 2 posts, one for each log. You'll be able to use Firefox right from the live environment and it should make it much easier for you.

If you to do it from the recovery console then yes, your steps are right but you will not have a desktop to work with. Any desktop would start X from the hard drive, creating a new Xorg log file. It would also create a new dmesg file so you would have to get an older ones. If you do want to do it this way then i would mount a USB stick and copy all the logs onto that. Then i would boot into a working desktop and post the logs from there.

I hope this make sense.

Kind regards

---

### Post by hencelence on 2013-04-25
> **matt_symes said:**
> 
I hope this make sense.

Sure does.

Sorrz for delay, had to make another live stick.

```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.8.0-19-generic (buildd@panlong) (gcc version 4.7.3 (Ubuntu/Linaro 4.7.3-1ubuntu1) ) #29-Ubuntu SMP Wed Apr 17 18:19:42 UTC 2013 (Ubuntu 3.8.0-19.29-generic 3.8.8)
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   NSC Geode by NSC
[    0.000000]   Cyrix CyrixInstead
[    0.000000]   Centaur CentaurHauls
[    0.000000]   Transmeta GenuineTMx86
[    0.000000]   Transmeta TransmetaCPU
[    0.000000]   UMC UMC UMC UMC
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009c3ff] usable
[    0.000000] BIOS-e820: [mem 0x000000000009c400-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000000d2000-0x00000000000d3fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000000e0000-0x00000000000fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x00000000bf8a0fff] usable
[    0.000000] BIOS-e820: [mem 0x00000000bf8a1000-0x00000000bf8a6fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000bf8a7000-0x00000000bf9b9fff] usable
[    0.000000] BIOS-e820: [mem 0x00000000bf9ba000-0x00000000bfa0efff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000bfa0f000-0x00000000bfb07fff] usable
[    0.000000] BIOS-e820: [mem 0x00000000bfb08000-0x00000000bfd0efff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000bfd0f000-0x00000000bfd17fff] usable
[    0.000000] BIOS-e820: [mem 0x00000000bfd18000-0x00000000bfd1efff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000bfd1f000-0x00000000bfd62fff] usable
[    0.000000] BIOS-e820: [mem 0x00000000bfd63000-0x00000000bfd9efff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000bfd9f000-0x00000000bfde3fff] usable
[    0.000000] BIOS-e820: [mem 0x00000000bfde4000-0x00000000bfdfefff] ACPI data
[    0.000000] BIOS-e820: [mem 0x00000000bfdff000-0x00000000bfdfffff] usable
[    0.000000] BIOS-e820: [mem 0x00000000bfe00000-0x00000000bfffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000e0000000-0x00000000efffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec0ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed00000-0x00000000fed003ff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed10000-0x00000000fed13fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed18000-0x00000000fed19fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed1c000-0x00000000fed8ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fee00000-0x00000000fee00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ff800000-0x00000000ffffffff] reserved
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] SMBIOS 2.5 present.
[    0.000000] DMI: Dell Inc. Studio 1537/0P132H, BIOS A07 12/03/2008
[    0.000000] e820: update [mem 0x00000000-0x0000ffff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] e820: last_pfn = 0xbfe00 max_arch_pfn = 0x1000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 base 080000000 mask FC0000000 write-back
[    0.000000]   2 base 0FFE00000 mask FFFE00000 write-protect
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] found SMP MP-table at [mem 0x000f79b0-0x000f79bf] mapped at [c00f79b0]
[    0.000000] initial memory mapped: [mem 0x00000000-0x01ffffff]
[    0.000000] Base memory trampoline at [c0098000] 98000 size 16384
[    0.000000] init_memory_mapping: [mem 0x00000000-0x37bfdfff]
[    0.000000]  [mem 0x00000000-0x001fffff] page 4k
[    0.000000]  [mem 0x00200000-0x379fffff] page 2M
[    0.000000]  [mem 0x37a00000-0x37bfdfff] page 4k
[    0.000000] kernel direct mapping tables up to 0x37bfdfff @ [mem 0x01ffa000-0x01ffffff]
[    0.000000] RAMDISK: [mem 0x3445a000-0x36224fff]
[    0.000000] ACPI: RSDP 000f7900 00024 (v02 PTLTD )
[    0.000000] ACPI: XSDT bfdf7e84 00074 (v01 DELL    M09     06040000  LTP 00000000)
[    0.000000] ACPI: FACP bfde8000 000F4 (v03 INTEL  CRESTLNE 06040000 ALAN 00000001)
[    0.000000] ACPI: DSDT bfde9000 06C8E (v02 Intel  CANTIGA  06040000 INTL 20050624)
[    0.000000] ACPI: FACS bfd9efc0 00040
[    0.000000] ACPI: HPET bfdfed16 00038 (v01 INTEL  CRESTLNE 06040000 LOHR 0000005A)
[    0.000000] ACPI: MCFG bfdfed4e 0003C (v01 INTEL  CRESTLNE 06040000 LOHR 0000005A)
[    0.000000] ACPI: APIC bfdfed8a 00068 (v01 PTLTD  ? APIC   06040000  LTP 00000000)
[    0.000000] ACPI: BOOT bfdfedf2 00028 (v01 PTLTD  $SBFTBL$ 06040000  LTP 00000001)
[    0.000000] ACPI: SLIC bfdfee1a 00176 (v01 DELL    M09     06040000  LTP 00000000)
[    0.000000] ACPI: OSFR bfdfef90 00070 (v01 DELL   DELL     06040000 ASL  00000061)
[    0.000000] ACPI: SSDT bfde7000 00655 (v01  PmRef    CpuPm 00003000 INTL 20050624)
[    0.000000] ACPI: SSDT bfde6000 00259 (v01  PmRef  Cpu0Tst 00003000 INTL 20050624)
[    0.000000] ACPI: SSDT bfde5000 0020F (v01  PmRef    ApTst 00003000 INTL 20050624)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 2178MB HIGHMEM available.
[    0.000000] 891MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 37bfe000
[    0.000000]   low ram: 0 - 37bfe000
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x00010000-0x00ffffff]
[    0.000000]   Normal   [mem 0x01000000-0x37bfdfff]
[    0.000000]   HighMem  [mem 0x37bfe000-0xbfdfffff]
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x00010000-0x0009bfff]
[    0.000000]   node   0: [mem 0x00100000-0xbf8a0fff]
[    0.000000]   node   0: [mem 0xbf8a7000-0xbf9b9fff]
[    0.000000]   node   0: [mem 0xbfa0f000-0xbfb07fff]
[    0.000000]   node   0: [mem 0xbfd0f000-0xbfd17fff]
[    0.000000]   node   0: [mem 0xbfd1f000-0xbfd62fff]
[    0.000000]   node   0: [mem 0xbfd9f000-0xbfde3fff]
[    0.000000]   node   0: [mem 0xbfdff000-0xbfdfffff]
[    0.000000] On node 0 totalpages: 785100
[    0.000000] free_area_init_node: node 0, pgdat c18f6100, node_mem_map f63fd200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3948 pages, LIFO batch:0
[    0.000000]   Normal zone: 1752 pages used for memmap
[    0.000000]   Normal zone: 222502 pages, LIFO batch:31
[    0.000000]   HighMem zone: 4357 pages used for memmap
[    0.000000]   HighMem zone: 552509 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] smpboot: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009c000 - 000000000009d000
[    0.000000] PM: Registered nosave memory: 000000000009d000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000d2000
[    0.000000] PM: Registered nosave memory: 00000000000d2000 - 00000000000d4000
[    0.000000] PM: Registered nosave memory: 00000000000d4000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] e820: [mem 0xc0000000-0xdfffffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @f63ce000 s35008 r0 d22336 u57344
[    0.000000] pcpu-alloc: s35008 r0 d22336 u57344 alloc=14*4096
[    0.000000] pcpu-alloc: [0] 0 [0] 1 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 778959
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.8.0-19-generic root=UUID=cd38ed06-9c26-429f-a47b-70f74a3b4ed9 ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] __ex_table already sorted, skipping sort
[    0.000000] Initializing CPU#0
[    0.000000] allocated 6287232 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (00037bfe:000bfe00)
[    0.000000] Memory: 3067200k/3143680k available (6251k kernel code, 73200k reserved, 2973k data, 784k init, 2227464k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff14000 - 0xfffff000   ( 940 kB)
[    0.000000]     pkmap   : 0xffc00000 - 0xffe00000   (2048 kB)
[    0.000000]     vmalloc : 0xf83fe000 - 0xffbfe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf7bfe000   ( 891 MB)
[    0.000000]       .init : 0xc1903000 - 0xc19c7000   ( 784 kB)
[    0.000000]       .data : 0xc161ad30 - 0xc19023c0   (2973 kB)
[    0.000000]       .text : 0xc1000000 - 0xc161ad30   (6251 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]     RCU restricting CPUs from NR_CPUS=8 to nr_cpu_ids=2.
[    0.000000] NR_IRQS:2304 nr_irqs:512 16
[    0.000000] CPU 0 irqstacks, hard=f3808000 soft=f380a000
[    0.000000] Extended CMOS year: 2000
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] tsc: Fast TSC calibration using PIT
[    0.000000] tsc: Detected 2260.935 MHz processor
[    0.004001] Calibrating delay loop (skipped), value calculated using timer frequency.. 4521.87 BogoMIPS (lpj=9043740)
[    0.004004] pid_max: default: 32768 minimum: 301
[    0.004032] Security Framework initialized
[    0.004041] AppArmor: AppArmor initialized
[    0.004042] Yama: becoming mindful.
[    0.004089] Mount-cache hash table entries: 512
[    0.004289] Initializing cgroup subsys cpuacct
[    0.004292] Initializing cgroup subsys memory
[    0.004299] Initializing cgroup subsys devices
[    0.004301] Initializing cgroup subsys freezer
[    0.004303] Initializing cgroup subsys blkio
[    0.004305] Initializing cgroup subsys perf_event
[    0.004308] Initializing cgroup subsys hugetlb
[    0.004336] CPU: Physical Processor ID: 0
[    0.004338] CPU: Processor Core ID: 0
[    0.004341] mce: CPU supports 6 MCE banks
[    0.004347] CPU0: Thermal monitoring enabled (TM2)
[    0.004350] process: using mwait in idle threads
[    0.004357] Last level iTLB entries: 4KB 128, 2MB 4, 4MB 4
[    0.004357] Last level dTLB entries: 4KB 256, 2MB 0, 4MB 32
[    0.004357] tlb_flushall_shift: -1
[    0.004622] Freeing SMP alternatives: 24k freed
[    0.009260] ACPI: Core revision 20121018
[    0.016011] ftrace: allocating 26115 entries in 52 pages
[    0.024084] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.024505] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.067037] smpboot: CPU0: Intel(R) Core(TM)2 Duo CPU     P8400  @ 2.26GHz (fam: 06, model: 17, stepping: 06)
[    0.068000] APIC calibration not consistent with PM-Timer: 291ms instead of 100ms
[    0.068000] APIC delta adjusted to PM-Timer: 1662495 (4854432)
[    0.068000] Performance Events: PEBS fmt0+, 4-deep LBR, Core2 events, Intel PMU driver.
[    0.068000] ... version:                2
[    0.068000] ... bit width:              40
[    0.068000] ... generic registers:      2
[    0.068000] ... value mask:             000000ffffffffff
[    0.068000] ... max period:             000000007fffffff
[    0.068000] ... fixed-purpose events:   3
[    0.068000] ... event mask:             0000000700000003
[    0.068000] CPU 1 irqstacks, hard=f38d8000 soft=f38da000
[    0.068000] smpboot: Booting Node   0, Processors  #1 OK
[    0.008000] Initializing CPU#1
[    0.078259] Brought up 2 CPUs
[    0.078263] smpboot: Total of 2 processors activated (9043.74 BogoMIPS)
[    0.078355] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.080083] devtmpfs: initialized
[    0.080229] EVM: security.selinux
[    0.080231] EVM: security.SMACK64
[    0.080233] EVM: security.capability
[    0.080249] PM: Registering ACPI NVS region [mem 0xbfd63000-0xbfd9efff] (245760 bytes)
[    0.081130] regulator-dummy: no parameters
[    0.081185] NET: Registered protocol family 16
[    0.081340] EISA bus registered
[    0.081442] ACPI: bus type pci registered
[    0.081508] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.081511] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
[    0.081512] PCI: Using MMCONFIG for extended config space
[    0.081514] PCI: Using configuration type 1 for base access
[    0.081524] dmi type 0xB1 record - unknown flag
[    0.081634] mtrr: your CPUs had inconsistent variable MTRR settings
[    0.081636] mtrr: probably your BIOS does not setup all CPUs.
[    0.081637] mtrr: corrected configuration.
[    0.082606] bio: create slab <bio-0> at 0
[    0.082606] ACPI: Added _OSI(Module Device)
[    0.082606] ACPI: Added _OSI(Processor Device)
[    0.082606] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.082606] ACPI: Added _OSI(Processor Aggregator Device)
[    0.082606] ACPI: EC: Look up EC in DSDT
[    0.088023] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.089245] ACPI: SSDT bfd1ac20 00265 (v01  PmRef  Cpu0Ist 00003000 INTL 20050624)
[    0.089655] ACPI: Dynamic OEM Table Load:
[    0.089658] ACPI: SSDT   (null) 00265 (v01  PmRef  Cpu0Ist 00003000 INTL 20050624)
[    0.089792] ACPI: SSDT bfd18620 00575 (v01  PmRef  Cpu0Cst 00003001 INTL 20050624)
[    0.090186] ACPI: Dynamic OEM Table Load:
[    0.090188] ACPI: SSDT   (null) 00575 (v01  PmRef  Cpu0Cst 00003001 INTL 20050624)
[    0.090201] ACPI: SSDT bfd19ca0 001CF (v01  PmRef    ApIst 00003000 INTL 20050624)
[    0.090201] ACPI: Dynamic OEM Table Load:
[    0.090201] ACPI: SSDT   (null) 001CF (v01  PmRef    ApIst 00003000 INTL 20050624)
[    0.090201] ACPI: SSDT bfd19f20 0008D (v01  PmRef    ApCst 00003000 INTL 20050624)
[    0.090201] ACPI: Dynamic OEM Table Load:
[    0.090201] ACPI: SSDT   (null) 0008D (v01  PmRef    ApCst 00003000 INTL 20050624)
[    0.092330] ACPI: Interpreter enabled
[    0.092340] ACPI: (supports S0 S3 S4 S5)
[    0.092359] ACPI: Using IOAPIC for interrupt routing
[    0.096395] ACPI: EC: GPE = 0x1c, I/O: command/status = 0x66, data = 0x62
[    0.096395] ACPI: No dock devices found.
[    0.096395] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.096428] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.096431] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.097095] PCI host bridge to bus 0000:00
[    0.097099] pci_bus 0000:00: root bus resource [bus 00-ff]
[    0.097101] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7]
[    0.097104] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff]
[    0.097106] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
[    0.097109] pci_bus 0000:00: root bus resource [mem 0x000d4000-0x000d7fff]
[    0.097111] pci_bus 0000:00: root bus resource [mem 0x000d8000-0x000dbfff]
[    0.097113] pci_bus 0000:00: root bus resource [mem 0x000dc000-0x000dffff]
[    0.097116] pci_bus 0000:00: root bus resource [mem 0xc0000000-0xfebfffff]
[    0.097126] pci 0000:00:00.0: [8086:2a40] type 00 class 0x060000
[    0.097148] DMAR: Forcing write-buffer flush capability
[    0.097150] DMAR: Disabling IOMMU for graphics on this chipset
[    0.097177] pci 0000:00:01.0: [8086:2a41] type 01 class 0x060400
[    0.097222] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.097279] pci 0000:00:1a.0: [8086:2937] type 00 class 0x0c0300
[    0.097340] pci 0000:00:1a.0: reg 20: [io  0x1800-0x181f]
[    0.097411] pci 0000:00:1a.1: [8086:2938] type 00 class 0x0c0300
[    0.097472] pci 0000:00:1a.1: reg 20: [io  0x1820-0x183f]
[    0.097544] pci 0000:00:1a.2: [8086:2939] type 00 class 0x0c0300
[    0.097604] pci 0000:00:1a.2: reg 20: [io  0x1840-0x185f]
[    0.097690] pci 0000:00:1a.7: [8086:293c] type 00 class 0x0c0320
[    0.097717] pci 0000:00:1a.7: reg 10: [mem 0xfc404800-0xfc404bff]
[    0.097836] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    0.097871] pci 0000:00:1b.0: [8086:293e] type 00 class 0x040300
[    0.097894] pci 0000:00:1b.0: reg 10: [mem 0xfc400000-0xfc403fff 64bit]
[    0.097996] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.098028] pci 0000:00:1c.0: [8086:2940] type 01 class 0x060400
[    0.098136] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.098170] pci 0000:00:1c.1: [8086:2942] type 01 class 0x060400
[    0.098278] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.098314] pci 0000:00:1c.3: [8086:2946] type 01 class 0x060400
[    0.098422] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.098458] pci 0000:00:1c.5: [8086:294a] type 01 class 0x060400
[    0.098566] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
[    0.098601] pci 0000:00:1d.0: [8086:2934] type 00 class 0x0c0300
[    0.098662] pci 0000:00:1d.0: reg 20: [io  0x1860-0x187f]
[    0.098734] pci 0000:00:1d.1: [8086:2935] type 00 class 0x0c0300
[    0.098794] pci 0000:00:1d.1: reg 20: [io  0x1880-0x189f]
[    0.098865] pci 0000:00:1d.2: [8086:2936] type 00 class 0x0c0300
[    0.098925] pci 0000:00:1d.2: reg 20: [io  0x18a0-0x18bf]
[    0.099008] pci 0000:00:1d.7: [8086:293a] type 00 class 0x0c0320
[    0.099036] pci 0000:00:1d.7: reg 10: [mem 0xfc404c00-0xfc404fff]
[    0.100089] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.100119] pci 0000:00:1e.0: [8086:2448] type 01 class 0x060401
[    0.100215] pci 0000:00:1f.0: [8086:2919] type 00 class 0x060100
[    0.100384] pci 0000:00:1f.2: [8086:2929] type 00 class 0x010601
[    0.100414] pci 0000:00:1f.2: reg 10: [io  0x18f0-0x18f7]
[    0.100427] pci 0000:00:1f.2: reg 14: [io  0x18e4-0x18e7]
[    0.100439] pci 0000:00:1f.2: reg 18: [io  0x18e8-0x18ef]
[    0.100451] pci 0000:00:1f.2: reg 1c: [io  0x18e0-0x18e3]
[    0.100463] pci 0000:00:1f.2: reg 20: [io  0x18c0-0x18df]
[    0.100476] pci 0000:00:1f.2: reg 24: [mem 0xfc404000-0xfc4047ff]
[    0.100550] pci 0000:00:1f.2: PME# supported from D3hot
[    0.100576] pci 0000:00:1f.3: [8086:2930] type 00 class 0x0c0500
[    0.100599] pci 0000:00:1f.3: reg 10: [mem 0x00000000-0x000000ff 64bit]
[    0.100631] pci 0000:00:1f.3: reg 20: [io  0x1c00-0x1c1f]
[    0.100713] pci 0000:01:00.0: [1002:95c4] type 00 class 0x030000
[    0.100729] pci 0000:01:00.0: reg 10: [mem 0xd0000000-0xdfffffff pref]
[    0.100741] pci 0000:01:00.0: reg 14: [io  0x2000-0x20ff]
[    0.100753] pci 0000:01:00.0: reg 18: [mem 0xcfef0000-0xcfefffff]
[    0.100793] pci 0000:01:00.0: reg 30: [mem 0x00000000-0x0001ffff pref]
[    0.100845] pci 0000:01:00.0: supports D1 D2
[    0.100876] pci 0000:01:00.1: [1002:aa28] type 00 class 0x040300
[    0.100892] pci 0000:01:00.1: reg 10: [mem 0xcfeec000-0xcfeeffff]
[    0.101001] pci 0000:01:00.1: supports D1 D2
[    0.108014] pci 0000:00:01.0: PCI bridge to [bus 01]
[    0.108018] pci 0000:00:01.0:   bridge window [io  0x2000-0x2fff]
[    0.108022] pci 0000:00:01.0:   bridge window [mem 0xcfe00000-0xcfefffff]
[    0.108026] pci 0000:00:01.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.108087] pci 0000:00:1c.0: PCI bridge to [bus 02-03]
[    0.108092] pci 0000:00:1c.0:   bridge window [io  0x3000-0x3fff]
[    0.108097] pci 0000:00:1c.0:   bridge window [mem 0xf6000000-0xf7ffffff]
[    0.108105] pci 0000:00:1c.0:   bridge window [mem 0xf0000000-0xf1ffffff 64bit pref]
[    0.108225] pci 0000:04:00.0: [8086:4232] type 00 class 0x028000
[    0.108269] pci 0000:04:00.0: reg 10: [mem 0xf8000000-0xf8001fff 64bit]
[    0.108476] pci 0000:04:00.0: PME# supported from D0 D3hot D3cold
[    0.116043] pci 0000:00:1c.1: PCI bridge to [bus 04-05]
[    0.116049] pci 0000:00:1c.1:   bridge window [io  0x4000-0x4fff]
[    0.116054] pci 0000:00:1c.1:   bridge window [mem 0xf8000000-0xf9ffffff]
[    0.116062] pci 0000:00:1c.1:   bridge window [mem 0xf2000000-0xf3ffffff 64bit pref]
[    0.116123] pci 0000:00:1c.3: PCI bridge to [bus 06-07]
[    0.116128] pci 0000:00:1c.3:   bridge window [io  0x5000-0x5fff]
[    0.116133] pci 0000:00:1c.3:   bridge window [mem 0xfa000000-0xfbffffff]
[    0.116141] pci 0000:00:1c.3:   bridge window [mem 0xf4000000-0xf5ffffff 64bit pref]
[    0.116397] pci 0000:08:00.0: [14e4:1698] type 00 class 0x020000
[    0.116440] pci 0000:08:00.0: reg 10: [mem 0xfc000000-0xfc00ffff 64bit]
[    0.116701] pci 0000:08:00.0: PME# supported from D3hot D3cold
[    0.124175] pci 0000:00:1c.5: PCI bridge to [bus 08]
[    0.124183] pci 0000:00:1c.5:   bridge window [mem 0xfc000000-0xfc0fffff]
[    0.124236] pci 0000:09:01.0: [1180:0832] type 00 class 0x0c0010
[    0.124263] pci 0000:09:01.0: reg 10: [mem 0xfc100000-0xfc1007ff]
[    0.124374] pci 0000:09:01.0: supports D1 D2
[    0.124377] pci 0000:09:01.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.124402] pci 0000:09:01.1: [1180:0822] type 00 class 0x080501
[    0.124427] pci 0000:09:01.1: reg 10: [mem 0xfc100800-0xfc1008ff]
[    0.124538] pci 0000:09:01.1: supports D1 D2
[    0.124541] pci 0000:09:01.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.124567] pci 0000:09:01.2: [1180:0592] type 00 class 0x088000
[    0.124592] pci 0000:09:01.2: reg 10: [mem 0xfc100c00-0xfc100cff]
[    0.124704] pci 0000:09:01.2: supports D1 D2
[    0.124706] pci 0000:09:01.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.124732] pci 0000:09:01.3: [1180:0852] type 00 class 0x088000
[    0.124756] pci 0000:09:01.3: reg 10: [mem 0xfc101000-0xfc1010ff]
[    0.124870] pci 0000:09:01.3: supports D1 D2
[    0.124873] pci 0000:09:01.3: PME# supported from D0 D1 D2 D3hot D3cold
[    0.124944] pci 0000:00:1e.0: PCI bridge to [bus 09] (subtractive decode)
[    0.124952] pci 0000:00:1e.0:   bridge window [mem 0xfc100000-0xfc1fffff]
[    0.124961] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.124963] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.124966] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.124968] pci 0000:00:1e.0:   bridge window [mem 0x000d4000-0x000d7fff] (subtractive decode)
[    0.124971] pci 0000:00:1e.0:   bridge window [mem 0x000d8000-0x000dbfff] (subtractive decode)
[    0.124973] pci 0000:00:1e.0:   bridge window [mem 0x000dc000-0x000dffff] (subtractive decode)
[    0.124976] pci 0000:00:1e.0:   bridge window [mem 0xc0000000-0xfebfffff] (subtractive decode)
[    0.125010] pci_bus 0000:00: on NUMA node 0
[    0.125019] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P2._PRT]
[    0.125065] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.125134] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    0.125183] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    0.125227] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT]
[    0.125263] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP06._PRT]
[    0.125311]  pci0000:00: ACPI _OSC support notification failed, disabling PCIe ASPM
[    0.125314]  pci0000:00: Unable to request _OSC control (_OSC support mask: 0x08)
[    0.126548] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 *5 6 7 10 12 14 15)
[    0.126599] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.126650] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[    0.126699] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.126749] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[    0.126799] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[    0.126849] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    0.126898] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 *7 11 12 14 15)
[    0.128018] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.128022] vgaarb: loaded
[    0.128023] vgaarb: bridge control possible 0000:01:00.0
[    0.128254] SCSI subsystem initialized
[    0.128256] ACPI: bus type scsi registered
[    0.128265] libata version 3.00 loaded.
[    0.128265] ACPI: bus type usb registered
[    0.128265] usbcore: registered new interface driver usbfs
[    0.128265] usbcore: registered new interface driver hub
[    0.128265] usbcore: registered new device driver usb
[    0.128265] PCI: Using ACPI for IRQ routing
[    0.138198] PCI: pci_cache_line_size set to 64 bytes
[    0.138495] e820: reserve RAM buffer [mem 0x0009c400-0x0009ffff]
[    0.138498] e820: reserve RAM buffer [mem 0xbf8a1000-0xbfffffff]
[    0.138501] e820: reserve RAM buffer [mem 0xbf9ba000-0xbfffffff]
[    0.138504] e820: reserve RAM buffer [mem 0xbfb08000-0xbfffffff]
[    0.138506] e820: reserve RAM buffer [mem 0xbfd18000-0xbfffffff]
[    0.138509] e820: reserve RAM buffer [mem 0xbfd63000-0xbfffffff]
[    0.138511] e820: reserve RAM buffer [mem 0xbfde4000-0xbfffffff]
[    0.138513] e820: reserve RAM buffer [mem 0xbfe00000-0xbfffffff]
[    0.138605] NetLabel: Initializing
[    0.138607] NetLabel:  domain hash size = 128
[    0.138608] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.138618] NetLabel:  unlabeled traffic allowed by default
[    0.140089] HPET: 4 timers in total, 0 timers will be used for per-cpu timer
[    0.140096] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    0.140101] hpet0: 4 comparators, 64-bit 14.318180 MHz counter
[    0.140101] Switching to clocksource hpet
[    0.147814] AppArmor: AppArmor Filesystem Enabled
[    0.147844] pnp: PnP ACPI init
[    0.147859] ACPI: bus type pnp registered
[    0.147947] pnp 00:00: [dma 4]
[    0.147973] pnp 00:00: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.148118] system 00:01: [mem 0xfed00000-0xfed003ff] has been reserved
[    0.148122] system 00:01: Plug and Play ACPI device, IDs PNP0103 PNP0c01 (active)
[    0.148165] pnp 00:02: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.148226] system 00:03: [io  0x0400-0x047f] has been reserved
[    0.148229] system 00:03: [io  0x0680-0x069f] has been reserved
[    0.148232] system 00:03: [io  0x0480-0x048f] has been reserved
[    0.148235] system 00:03: [io  0xffff] has been reserved
[    0.148238] system 00:03: [io  0xffff] has been reserved
[    0.148241] system 00:03: [io  0x1000-0x107f] has been reserved
[    0.148243] system 00:03: [io  0x1180-0x11ff] has been reserved
[    0.148246] system 00:03: [io  0x164e-0x164f] has been reserved
[    0.148249] system 00:03: [io  0xfe00] has been reserved
[    0.148252] system 00:03: [io  0x0900-0x097f] has been reserved
[    0.148256] system 00:03: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.148296] pnp 00:04: Plug and Play ACPI device, IDs ITE8708 (active)
[    0.148328] pnp 00:05: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.148362] pnp 00:06: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.148399] pnp 00:07: Plug and Play ACPI device, IDs PNP0f13 (active)
[    0.148583] system 00:08: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.148586] system 00:08: [mem 0xfed10000-0xfed13fff] has been reserved
[    0.148589] system 00:08: [mem 0xfed18000-0xfed18fff] has been reserved
[    0.148592] system 00:08: [mem 0xfed19000-0xfed19fff] has been reserved
[    0.148595] system 00:08: [mem 0xe0000000-0xefffffff] has been reserved
[    0.148598] system 00:08: [mem 0xfeb00000-0xfeb03fff] has been reserved
[    0.148601] system 00:08: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.148604] system 00:08: [mem 0xfed40000-0xfed44fff] has been reserved
[    0.148607] system 00:08: [mem 0xfed45000-0xfed8ffff] has been reserved
[    0.148611] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.149584] pnp: PnP ACPI: found 9 devices
[    0.149586] ACPI: ACPI bus type pnp unregistered
[    0.149589] PnPBIOS: Disabled by ACPI PNP
[    0.186370] pci 0000:00:1c.5: bridge window [io  0x1000-0x0fff] to [bus 08] add_size 1000
[    0.186375] pci 0000:00:1c.5: bridge window [mem 0x00100000-0x000fffff 64bit pref] to [bus 08] add_size 200000
[    0.186391] pci 0000:00:1c.5: res[15]=[mem 0x00100000-0x000fffff 64bit pref] get_res_add_size add_size 200000
[    0.186394] pci 0000:00:1c.5: res[13]=[io  0x1000-0x0fff] get_res_add_size add_size 1000
[    0.186401] pci 0000:00:1c.5: BAR 15: assigned [mem 0xc0000000-0xc01fffff 64bit pref]
[    0.186405] pci 0000:00:1c.5: BAR 13: assigned [io  0x6000-0x6fff]
[    0.186409] pci 0000:00:1f.3: BAR 0: assigned [mem 0xc0200000-0xc02000ff 64bit]
[    0.186424] pci 0000:01:00.0: BAR 6: assigned [mem 0xcfe00000-0xcfe1ffff pref]
[    0.186426] pci 0000:00:01.0: PCI bridge to [bus 01]
[    0.186430] pci 0000:00:01.0:   bridge window [io  0x2000-0x2fff]
[    0.186434] pci 0000:00:01.0:   bridge window [mem 0xcfe00000-0xcfefffff]
[    0.186438] pci 0000:00:01.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.186442] pci 0000:00:1c.0: PCI bridge to [bus 02-03]
[    0.186446] pci 0000:00:1c.0:   bridge window [io  0x3000-0x3fff]
[    0.186453] pci 0000:00:1c.0:   bridge window [mem 0xf6000000-0xf7ffffff]
[    0.186458] pci 0000:00:1c.0:   bridge window [mem 0xf0000000-0xf1ffffff 64bit pref]
[    0.186466] pci 0000:00:1c.1: PCI bridge to [bus 04-05]
[    0.186469] pci 0000:00:1c.1:   bridge window [io  0x4000-0x4fff]
[    0.186476] pci 0000:00:1c.1:   bridge window [mem 0xf8000000-0xf9ffffff]
[    0.186481] pci 0000:00:1c.1:   bridge window [mem 0xf2000000-0xf3ffffff 64bit pref]
[    0.186489] pci 0000:00:1c.3: PCI bridge to [bus 06-07]
[    0.186492] pci 0000:00:1c.3:   bridge window [io  0x5000-0x5fff]
[    0.186499] pci 0000:00:1c.3:   bridge window [mem 0xfa000000-0xfbffffff]
[    0.186504] pci 0000:00:1c.3:   bridge window [mem 0xf4000000-0xf5ffffff 64bit pref]
[    0.186512] pci 0000:00:1c.5: PCI bridge to [bus 08]
[    0.186516] pci 0000:00:1c.5:   bridge window [io  0x6000-0x6fff]
[    0.186522] pci 0000:00:1c.5:   bridge window [mem 0xfc000000-0xfc0fffff]
[    0.186527] pci 0000:00:1c.5:   bridge window [mem 0xc0000000-0xc01fffff 64bit pref]
[    0.186535] pci 0000:00:1e.0: PCI bridge to [bus 09]
[    0.186542] pci 0000:00:1e.0:   bridge window [mem 0xfc100000-0xfc1fffff]
[    0.186593] pci 0000:00:1e.0: setting latency timer to 64
[    0.186598] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.186601] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.186603] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.186606] pci_bus 0000:00: resource 7 [mem 0x000d4000-0x000d7fff]
[    0.186608] pci_bus 0000:00: resource 8 [mem 0x000d8000-0x000dbfff]
[    0.186611] pci_bus 0000:00: resource 9 [mem 0x000dc000-0x000dffff]
[    0.186613] pci_bus 0000:00: resource 10 [mem 0xc0000000-0xfebfffff]
[    0.186616] pci_bus 0000:01: resource 0 [io  0x2000-0x2fff]
[    0.186618] pci_bus 0000:01: resource 1 [mem 0xcfe00000-0xcfefffff]
[    0.186621] pci_bus 0000:01: resource 2 [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.186623] pci_bus 0000:02: resource 0 [io  0x3000-0x3fff]
[    0.186626] pci_bus 0000:02: resource 1 [mem 0xf6000000-0xf7ffffff]
[    0.186628] pci_bus 0000:02: resource 2 [mem 0xf0000000-0xf1ffffff 64bit pref]
[    0.186631] pci_bus 0000:04: resource 0 [io  0x4000-0x4fff]
[    0.186633] pci_bus 0000:04: resource 1 [mem 0xf8000000-0xf9ffffff]
[    0.186636] pci_bus 0000:04: resource 2 [mem 0xf2000000-0xf3ffffff 64bit pref]
[    0.186638] pci_bus 0000:06: resource 0 [io  0x5000-0x5fff]
[    0.186641] pci_bus 0000:06: resource 1 [mem 0xfa000000-0xfbffffff]
[    0.186643] pci_bus 0000:06: resource 2 [mem 0xf4000000-0xf5ffffff 64bit pref]
[    0.186646] pci_bus 0000:08: resource 0 [io  0x6000-0x6fff]
[    0.186648] pci_bus 0000:08: resource 1 [mem 0xfc000000-0xfc0fffff]
[    0.186651] pci_bus 0000:08: resource 2 [mem 0xc0000000-0xc01fffff 64bit pref]
[    0.186653] pci_bus 0000:09: resource 1 [mem 0xfc100000-0xfc1fffff]
[    0.186656] pci_bus 0000:09: resource 4 [io  0x0000-0x0cf7]
[    0.186658] pci_bus 0000:09: resource 5 [io  0x0d00-0xffff]
[    0.186660] pci_bus 0000:09: resource 6 [mem 0x000a0000-0x000bffff]
[    0.186663] pci_bus 0000:09: resource 7 [mem 0x000d4000-0x000d7fff]
[    0.186665] pci_bus 0000:09: resource 8 [mem 0x000d8000-0x000dbfff]
[    0.186667] pci_bus 0000:09: resource 9 [mem 0x000dc000-0x000dffff]
[    0.186670] pci_bus 0000:09: resource 10 [mem 0xc0000000-0xfebfffff]
[    0.186708] NET: Registered protocol family 2
[    0.186861] TCP established hash table entries: 8192 (order: 4, 65536 bytes)
[    0.186890] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[    0.186916] TCP: Hash tables configured (established 8192 bind 8192)
[    0.186942] TCP: reno registered
[    0.186945] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.186954] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.187003] NET: Registered protocol family 1
[    0.187237] pci 0000:01:00.0: Boot video device
[    0.187433] PCI: CLS 64 bytes, default 64
[    0.187471] Trying to unpack rootfs image as initramfs...
[    0.778498] Freeing initrd memory: 30508k freed
[    0.790402] Simple Boot Flag at 0x36 set to 0x1
[    0.790702] Initialise module verification
[    0.790754] audit: initializing netlink socket (disabled)
[    0.790768] type=2000 audit(1366912575.788:1): initialized
[    0.813698] bounce pool size: 64 pages
[    0.813713] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.815365] VFS: Disk quotas dquot_6.5.2
[    0.815416] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.815994] fuse init (API version 7.20)
[    0.816093] msgmni has been set to 1699
[    0.816516] Key type asymmetric registered
[    0.816519] Asymmetric key parser 'x509' registered
[    0.816554] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    0.816584] io scheduler noop registered
[    0.816587] io scheduler deadline registered (default)
[    0.816594] io scheduler cfq registered
[    0.816744] pcieport 0000:00:01.0: irq 40 for MSI/MSI-X
[    0.816843] pcieport 0000:00:1c.0: irq 41 for MSI/MSI-X
[    0.816967] pcieport 0000:00:1c.1: irq 42 for MSI/MSI-X
[    0.817089] pcieport 0000:00:1c.3: irq 43 for MSI/MSI-X
[    0.817212] pcieport 0000:00:1c.5: irq 44 for MSI/MSI-X
[    0.817307] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.817324] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.817387] intel_idle: does not run on family 6 model 23
[    1.016036] ACPI: AC Adapter [ADP1] (on-line)
[    1.016097] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    1.016102] ACPI: Power Button [PWRB]
[    1.016138] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1
[    1.016141] ACPI: Sleep Button [SLPB]
[    1.016181] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input2
[    1.017804] ACPI: Lid Switch [LID0]
[    1.017848] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    1.017851] ACPI: Power Button [PWRF]
[    1.017925] ACPI: Requesting acpi_cpufreq
[    1.020150] Monitor-Mwait will be used to enter C-1 state
[    1.020157] Monitor-Mwait will be used to enter C-2 state
[    1.020161] Monitor-Mwait will be used to enter C-3 state
[    1.020164] tsc: Marking TSC unstable due to TSC halts in idle
[    1.020175] ACPI: acpi_idle registered with cpuidle
[    1.027385] thermal LNXTHERM:00: registered as thermal_zone0
[    1.027387] ACPI: Thermal Zone [TZ00] (53 C)
[    1.030140] thermal LNXTHERM:01: registered as thermal_zone1
[    1.030142] ACPI: Thermal Zone [TZ01] (48 C)
[    1.032537] thermal LNXTHERM:02: registered as thermal_zone2
[    1.032540] ACPI: Thermal Zone [TZ02] (68 C)
[    1.032567] GHES: HEST is not enabled!
[    1.032632] isapnp: Scanning for PnP cards...
[    1.036085] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    1.043213] Linux agpgart interface v0.103
[    1.044835] brd: module loaded
[    1.046143] loop: module loaded
[    1.046597] libphy: Fixed MDIO Bus: probed
[    1.046670] tun: Universal TUN/TAP device driver, 1.6
[    1.046672] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.046711] PPP generic driver version 2.4.2
[    1.046773] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.046776] ehci-pci: EHCI PCI platform driver
[    1.046803] ehci-pci 0000:00:1a.7: setting latency timer to 64
[    1.046807] ehci-pci 0000:00:1a.7: EHCI Host Controller
[    1.046813] ehci-pci 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    1.046828] ehci-pci 0000:00:1a.7: debug port 1
[    1.050733] ehci-pci 0000:00:1a.7: cache line size of 64 is not supported
[    1.050784] ehci-pci 0000:00:1a.7: irq 19, io mem 0xfc404800
[    1.056313] ACPI: Battery Slot [BAT0] (battery present)
[    1.060023] ehci-pci 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    1.060043] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    1.060045] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.060048] usb usb1: Product: EHCI Host Controller
[    1.060050] usb usb1: Manufacturer: Linux 3.8.0-19-generic ehci_hcd
[    1.060053] usb usb1: SerialNumber: 0000:00:1a.7
[    1.060144] hub 1-0:1.0: USB hub found
[    1.060149] hub 1-0:1.0: 6 ports detected
[    1.060280] ehci-pci 0000:00:1d.7: setting latency timer to 64
[    1.060284] ehci-pci 0000:00:1d.7: EHCI Host Controller
[    1.060289] ehci-pci 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    1.060303] ehci-pci 0000:00:1d.7: debug port 1
[    1.064197] ehci-pci 0000:00:1d.7: cache line size of 64 is not supported
[    1.064212] ehci-pci 0000:00:1d.7: irq 23, io mem 0xfc404c00
[    1.076023] ehci-pci 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    1.076037] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[    1.076040] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.076042] usb usb2: Product: EHCI Host Controller
[    1.076044] usb usb2: Manufacturer: Linux 3.8.0-19-generic ehci_hcd
[    1.076047] usb usb2: SerialNumber: 0000:00:1d.7
[    1.076128] hub 2-0:1.0: USB hub found
[    1.076132] hub 2-0:1.0: 6 ports detected
[    1.076247] ehci-platform: EHCI generic platform driver
[    1.076255] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.076273] uhci_hcd: USB Universal Host Controller Interface driver
[    1.076291] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    1.076295] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    1.076300] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    1.076336] uhci_hcd 0000:00:1a.0: irq 16, io base 0x00001800
[    1.076367] usb usb3: New USB device found, idVendor=1d6b, idProduct=0001
[    1.076370] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.076372] usb usb3: Product: UHCI Host Controller
[    1.076375] usb usb3: Manufacturer: Linux 3.8.0-19-generic uhci_hcd
[    1.076377] usb usb3: SerialNumber: 0000:00:1a.0
[    1.076458] hub 3-0:1.0: USB hub found
[    1.076463] hub 3-0:1.0: 2 ports detected
[    1.076541] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    1.076545] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    1.076550] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    1.076585] uhci_hcd 0000:00:1a.1: irq 21, io base 0x00001820
[    1.076617] usb usb4: New USB device found, idVendor=1d6b, idProduct=0001
[    1.076620] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.076622] usb usb4: Product: UHCI Host Controller
[    1.076624] usb usb4: Manufacturer: Linux 3.8.0-19-generic uhci_hcd
[    1.076627] usb usb4: SerialNumber: 0000:00:1a.1
[    1.076710] hub 4-0:1.0: USB hub found
[    1.076713] hub 4-0:1.0: 2 ports detected
[    1.076790] uhci_hcd 0000:00:1a.2: setting latency timer to 64
[    1.076793] uhci_hcd 0000:00:1a.2: UHCI Host Controller
[    1.076798] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 5
[    1.076823] uhci_hcd 0000:00:1a.2: irq 19, io base 0x00001840
[    1.076853] usb usb5: New USB device found, idVendor=1d6b, idProduct=0001
[    1.076856] usb usb5: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.076858] usb usb5: Product: UHCI Host Controller
[    1.076860] usb usb5: Manufacturer: Linux 3.8.0-19-generic uhci_hcd
[    1.076862] usb usb5: SerialNumber: 0000:00:1a.2
[    1.076943] hub 5-0:1.0: USB hub found
[    1.076947] hub 5-0:1.0: 2 ports detected
[    1.077034] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    1.077038] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    1.077043] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 6
[    1.077068] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00001860
[    1.077098] usb usb6: New USB device found, idVendor=1d6b, idProduct=0001
[    1.077101] usb usb6: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.077103] usb usb6: Product: UHCI Host Controller
[    1.077105] usb usb6: Manufacturer: Linux 3.8.0-19-generic uhci_hcd
[    1.077108] usb usb6: SerialNumber: 0000:00:1d.0
[    1.077187] hub 6-0:1.0: USB hub found
[    1.077191] hub 6-0:1.0: 2 ports detected
[    1.077267] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    1.077271] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    1.077275] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 7
[    1.077302] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00001880
[    1.077333] usb usb7: New USB device found, idVendor=1d6b, idProduct=0001
[    1.077335] usb usb7: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.077338] usb usb7: Product: UHCI Host Controller
[    1.077340] usb usb7: Manufacturer: Linux 3.8.0-19-generic uhci_hcd
[    1.077342] usb usb7: SerialNumber: 0000:00:1d.1
[    1.077421] hub 7-0:1.0: USB hub found
[    1.077425] hub 7-0:1.0: 2 ports detected
[    1.077503] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    1.077507] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    1.077512] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 8
[    1.077547] uhci_hcd 0000:00:1d.2: irq 18, io base 0x000018a0
[    1.077579] usb usb8: New USB device found, idVendor=1d6b, idProduct=0001
[    1.077582] usb usb8: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.077584] usb usb8: Product: UHCI Host Controller
[    1.077586] usb usb8: Manufacturer: Linux 3.8.0-19-generic uhci_hcd
[    1.077588] usb usb8: SerialNumber: 0000:00:1d.2
[    1.077667] hub 8-0:1.0: USB hub found
[    1.077671] hub 8-0:1.0: 2 ports detected
[    1.077804] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.085754] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.085760] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.085853] mousedev: PS/2 mouse device common for all mice
[    1.086005] rtc_cmos 00:05: RTC can wake from S4
[    1.086130] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    1.086161] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    1.086253] device-mapper: uevent: version 1.0.3
[    1.086312] device-mapper: ioctl: 4.23.1-ioctl (2012-12-18) initialised: dm-devel@redhat.com
[    1.086328] EISA: Probing bus 0 at eisa.0
[    1.086331] EISA: Cannot allocate resource for mainboard
[    1.086333] Cannot allocate resource for EISA slot 1
[    1.086334] Cannot allocate resource for EISA slot 2
[    1.086336] Cannot allocate resource for EISA slot 3
[    1.086337] Cannot allocate resource for EISA slot 4
[    1.086339] Cannot allocate resource for EISA slot 5
[    1.086341] Cannot allocate resource for EISA slot 6
[    1.086342] Cannot allocate resource for EISA slot 7
[    1.086344] Cannot allocate resource for EISA slot 8
[    1.086345] EISA: Detected 0 cards.
[    1.086354] cpufreq-nforce2: No nForce2 chipset.
[    1.086405] cpuidle: using governor ladder
[    1.086460] cpuidle: using governor menu
[    1.086463] ledtrig-cpu: registered to indicate activity on CPUs
[    1.086465] EFI Variables Facility v0.08 2004-May-17
[    1.086619] ashmem: initialized
[    1.086740] TCP: cubic registered
[    1.086850] NET: Registered protocol family 10
[    1.087032] NET: Registered protocol family 17
[    1.087041] Key type dns_resolver registered
[    1.087194] Using IPI No-Shortcut mode
[    1.087262] Loading module verification certificates
[    1.091362] MODSIGN: Loaded cert 'Magrathea: Glacier signing key: fceb9fd088cf158e29d83343e1c98bf8ab23d94a'
[    1.091374] registered taskstats version 1
[    1.093684] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    1.094206] Key type trusted registered
[    1.096270] Key type encrypted registered
[    1.099801] rtc_cmos 00:05: setting system clock to 2013-04-25 17:56:17 UTC (1366912577)
[    1.100337] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.100339] EDD information not available.
[    1.387701] isapnp: No Plug & Play device found
[    1.387776] Freeing unused kernel memory: 784k freed
[    1.388033] Write protecting the kernel text: 6252k
[    1.388101] Write protecting the kernel read-only data: 2432k
[    1.388102] NX-protecting the kernel data: 3988k
[    1.402035] udevd[99]: starting version 175
[    1.412062] usb 1-6: new high-speed USB device number 2 using ehci-pci
[    1.552110] usb 1-6: New USB device found, idVendor=05ca, idProduct=18a0
[    1.552116] usb 1-6: New USB device strings: Mfr=1, Product=2, SerialNumber=9
[    1.552119] usb 1-6: Product: Integrated Webcam
[    1.552123] usb 1-6: Manufacturer: Ricoh co. Ltd.
[    1.552126] usb 1-6: SerialNumber: CN0TX6137248789PA0H0
[    1.621124] Disabling lock debugging due to kernel taint
[    1.621494] ACPI: Video Device [M86] (multi-head: yes  rom: no  post: no)
[    1.621547] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:00/LNXVIDEO:00/input/input5
[    1.637965] wmi: Mapper loaded
[    1.657956] ahci 0000:00:1f.2: version 3.0
[    1.658022] ahci 0000:00:1f.2: irq 45 for MSI/MSI-X
[    1.658105] ahci 0000:00:1f.2: AHCI 0001.0200 32 slots 4 ports 3 Gbps 0x33 impl SATA mode
[    1.658109] ahci 0000:00:1f.2: flags: 64bit ncq sntf led clo pmp pio slum part ccc sxs 
[    1.658114] ahci 0000:00:1f.2: setting latency timer to 64
[    1.668138] scsi0 : ahci
[    1.670411] pps_core: LinuxPPS API ver. 1 registered
[    1.670414] pps_core: Software ver. 5.3.6 - Copyright 2005-2007 Rodolfo Giometti <giometti@linux.it>
[    1.672427] scsi1 : ahci
[    1.675982] scsi2 : ahci
[    1.682095] scsi3 : ahci
[    1.683048] [drm] Initialized drm 1.1.0 20060810
[    1.684906] PTP clock support registered
[    1.685183] scsi4 : ahci
[    1.693732] scsi5 : ahci
[    1.693789] ata1: SATA max UDMA/133 abar m2048@0xfc404000 port 0xfc404100 irq 45
[    1.693793] ata2: SATA max UDMA/133 abar m2048@0xfc404000 port 0xfc404180 irq 45
[    1.693795] ata3: DUMMY
[    1.693797] ata4: DUMMY
[    1.693800] ata5: SATA max UDMA/133 abar m2048@0xfc404000 port 0xfc404300 irq 45
[    1.693803] ata6: SATA max UDMA/133 abar m2048@0xfc404000 port 0xfc404380 irq 45
[    1.701250] tg3.c:v3.128 (December 03, 2012)
[    1.705722] sdhci: Secure Digital Host Controller Interface driver
[    1.705724] sdhci: Copyright(c) Pierre Ossman
[    1.752428] tg3 0000:08:00.0 eth0: Tigon3 [partno(BCM95784M) rev 5784100] (PCI Express) MAC address 00:22:19:d8:ec:72
[    1.752433] tg3 0000:08:00.0 eth0: attached PHY is 5784 (10/100/1000Base-T Ethernet) (WireSpeed[1], EEE[0])
[    1.752436] tg3 0000:08:00.0 eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[1]
[    1.752439] tg3 0000:08:00.0 eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[    1.764097] firewire_ohci 0000:09:01.0: added OHCI v1.10 device as card 0, 4 IR + 4 IT contexts, quirks 0x11
[    1.764517] sdhci-pci 0000:09:01.1: SDHCI controller found [1180:0822] (rev 22)
[    1.765553] mmc0: no vqmmc regulator found
[    1.765555] mmc0: no vmmc regulator found
[    1.775273] [drm] radeon defaulting to kernel modesetting.
[    1.775277] [drm] radeon kernel modesetting enabled.
[    1.775512] [drm] initializing kernel modesetting (RV620 0x1002:0x95C4 0x1028:0x029F).
[    1.775533] [drm] register mmio base: 0xCFEF0000
[    1.775535] [drm] register mmio size: 65536
[    1.775651] ATOM BIOS: Dell_HepburnFM6
[    1.775669] radeon 0000:01:00.0: VRAM: 256M 0x0000000000000000 - 0x000000000FFFFFFF (256M used)
[    1.775672] radeon 0000:01:00.0: GTT: 512M 0x0000000010000000 - 0x000000002FFFFFFF
[    1.777311] [drm] Detected VRAM RAM=256M, BAR=256M
[    1.777314] [drm] RAM width 64bits DDR
[    1.777381] [TTM] Zone  kernel: Available graphics memory: 435526 kiB
[    1.777384] [TTM] Zone highmem: Available graphics memory: 1549258 kiB
[    1.777385] [TTM] Initializing pool allocator
[    1.777391] [TTM] Initializing DMA pool allocator
[    1.777416] [drm] radeon: 256M of VRAM memory ready
[    1.777418] [drm] radeon: 512M of GTT memory ready.
[    1.777435] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[    1.777436] [drm] Driver supports precise vblank timestamp query.
[    1.777494] radeon 0000:01:00.0: irq 46 for MSI/MSI-X
[    1.777507] radeon 0000:01:00.0: radeon: using MSI.
[    1.777537] [drm] radeon: irq initialized.
[    1.777541] [drm] GART: num cpu pages 131072, num gpu pages 131072
[    1.778244] [drm] probing gen 2 caps for device 8086:2a41 = 1/0
[    1.778292] [drm] Loading RV620 Microcode
[    1.805084] mmc0: SDHCI controller on PCI [0000:09:01.1] using DMA
[    1.806342] [drm] PCIE GART of 512M enabled (table at 0x0000000000040000).
[    1.806393] radeon 0000:01:00.0: WB enabled
[    1.806397] radeon 0000:01:00.0: fence driver on ring 0 use gpu addr 0x0000000010000c00 and cpu addr 0xffc89c00
[    1.806400] radeon 0000:01:00.0: fence driver on ring 3 use gpu addr 0x0000000010000c0c and cpu addr 0xffc89c0c
[    1.838052] [drm] ring test on 0 succeeded in 1 usecs
[    1.838116] [drm] ring test on 3 succeeded in 1 usecs
[    1.838275] [drm] ib test on ring 0 succeeded in 0 usecs
[    1.838291] [drm] ib test on ring 3 succeeded in 0 usecs
[    1.860097] [drm] radeon atom DIG backlight initialized
[    1.860101] [drm] Radeon Display Connectors
[    1.860103] [drm] Connector 0:
[    1.860106] [drm]   VGA-1
[    1.860109] [drm]   DDC: 0x7e20 0x7e20 0x7e24 0x7e24 0x7e28 0x7e28 0x7e2c 0x7e2c
[    1.860111] [drm]   Encoders:
[    1.860113] [drm]     CRT1: INTERNAL_KLDSCP_DAC1
[    1.860116] [drm] Connector 1:
[    1.860118] [drm]   LVDS-1
[    1.860121] [drm]   DDC: 0x7e40 0x7e40 0x7e44 0x7e44 0x7e48 0x7e48 0x7e4c 0x7e4c
[    1.860123] [drm]   Encoders:
[    1.860125] [drm]     LCD1: INTERNAL_KLDSCP_LVTMA
[    1.860127] [drm] Connector 2:
[    1.860129] [drm]   HDMI-A-1
[    1.860131] [drm]   HPD1
[    1.860135] [drm]   DDC: 0x7e60 0x7e60 0x7e64 0x7e64 0x7e68 0x7e68 0x7e6c 0x7e6c
[    1.860136] [drm]   Encoders:
[    1.860139] [drm]     DFP1: INTERNAL_UNIPHY
[    1.860185] [drm] radeon: power management initialized
[    2.044055] ata6: SATA link down (SStatus 0 SControl 300)
[    2.044083] ata5: SATA link down (SStatus 0 SControl 300)
[    2.184100] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.184124] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.185203] ata1.00: ATA-8: Hitachi HTS543232L9A300, FB4OC40C, max UDMA/133
[    2.185207] ata1.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    2.186492] ata1.00: configured for UDMA/133
[    2.186721] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HTS54323 FB4O PQ: 0 ANSI: 5
[    2.186876] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.186889] sd 0:0:0:0: [sda] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[    2.186943] sd 0:0:0:0: [sda] Write Protect is off
[    2.186946] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.186967] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.188150] ata2.00: ATAPI: HL-DT-ST DVD+/-RW GA10N, A102, max UDMA/133
[    2.192961] ata2.00: configured for UDMA/133
[    2.197349] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVD+-RW GA10N    A102 PQ: 0 ANSI: 5
[    2.202213] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda caddy
[    2.202216] cdrom: Uniform CD-ROM driver Revision: 3.20
[    2.202421] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    2.202479] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    2.244311]  sda: sda1 < sda5 > sda2
[    2.244755] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.264113] firewire_core 0000:09:01.0: created device fw0: GUID 0000000000000000, S400
[    2.455107] vesafb: mode is 1024x768x32, linelength=4096, pages=0
[    2.455110] vesafb: scrolling: redraw
[    2.455113] vesafb: Truecolor: size=0:8:8:8, shift=0:16:8:0
[    2.455517] vesafb: framebuffer at 0xd0000000, mapped to 0xf8d80000, using 3072k, total 3072k
[    2.455631] Console: switching to colour frame buffer device 128x48
[    2.458672] fb0: VESA VGA frame buffer device
[    2.864908] [drm] fb mappable at 0xD0142000
[    2.864910] [drm] vram apper at 0xD0000000
[    2.864912] [drm] size 4096000
[    2.864913] [drm] fb depth is 24
[    2.864915] [drm]    pitch is 5120
[    2.864918] checking generic (d0000000 300000) vs hw (d0000000 10000000)
[    2.864920] fb: conflicting fb hw usage radeondrmfb vs VESA VGA - removing generic driver
[    2.864933] Console: switching to colour dummy device 80x25
[    2.865288] fbcon: radeondrmfb (fb0) is primary device
[    3.128143] Console: switching to colour frame buffer device 160x50
[    3.131868] radeon 0000:01:00.0: fb0: radeondrmfb frame buffer device
[    3.131870] radeon 0000:01:00.0: registered panic notifier
[    3.131883] [drm] Initialized radeon 2.29.0 20080528 for 0000:01:00.0 on minor 0
[    3.901095] xor: automatically using best checksumming function:
[    3.940016]    pIII_sse  :  8685.000 MB/sec
[    3.946841] device-mapper: dm-raid45: initialized v0.2594b
[    9.147682] EXT4-fs (sda2): mounted filesystem with ordered data mode. Opts: (null)
[   20.956384] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   21.115097] udevd[418]: starting version 175
[   21.881385] type=1400 audit(1366912598.276:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=585 comm="apparmor_parser"
[   21.881395] type=1400 audit(1366912598.276:3): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=586 comm="apparmor_parser"
[   21.881847] type=1400 audit(1366912598.276:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=585 comm="apparmor_parser"
[   21.881857] type=1400 audit(1366912598.276:5): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=586 comm="apparmor_parser"
[   21.882093] type=1400 audit(1366912598.276:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=585 comm="apparmor_parser"
[   21.882106] type=1400 audit(1366912598.276:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=586 comm="apparmor_parser"
[   22.001116] microcode: CPU0 sig=0x10676, pf=0x80, revision=0x60c
[   22.254819] cfg80211: Calling CRDA to update world regulatory domain
[   22.268672] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   22.326223] microcode: CPU1 sig=0x10676, pf=0x80, revision=0x60c
[   22.327884] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[   22.358304] device-mapper: multipath: version 1.5.1 loaded
[   22.372690] lp: driver loaded but no devices found
[   22.389371] ACPI Warning: 0x00000428-0x0000042f SystemIO conflicts with Region \PMIO 1 (20121018/utaddress-251)
[   22.389379] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   22.389383] ACPI Warning: 0x000011b0-0x000011bf SystemIO conflicts with Region \GPIO 1 (20121018/utaddress-251)
[   22.389387] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   22.389389] ACPI Warning: 0x00001180-0x000011af SystemIO conflicts with Region \GPIO 1 (20121018/utaddress-251)
[   22.389393] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   22.389395] lpc_ich: Resource conflict(s) found affecting gpio_ich
[   22.493723] r592: driver successfully loaded
[   22.502429] ite_cir: Auto-detected model: ITE8708 CIR transceiver
[   22.502433] ite_cir: Using model: ITE8708 CIR transceiver
[   22.502435] ite_cir: TX-capable: 1
[   22.502437] ite_cir: Sample period (ns): 8680
[   22.502438] ite_cir: TX carrier frequency (Hz): 38000
[   22.502440] ite_cir: TX duty cycle (%): 33
[   22.502441] ite_cir: RX low carrier frequency (Hz): 0
[   22.502443] ite_cir: RX high carrier frequency (Hz): 0
[   22.578045] Linux video capture interface: v2.00
[   22.592862] Intel(R) Wireless WiFi driver for Linux, in-tree:
[   22.592866] Copyright(c) 2003-2012 Intel Corporation
[   22.593114] iwlwifi 0000:04:00.0: irq 47 for MSI/MSI-X
[   22.593390] iwlwifi 0000:04:00.0: loaded firmware version 8.83.5.1 build 33692
[   22.663590] input: Dell WMI hotkeys as /devices/virtual/input/input6
[   22.696020] Registered IR keymap rc-rc6-mce
[   22.696180] input: ITE8708 CIR transceiver as /devices/virtual/rc/rc0/input7
[   22.696368] rc0: ITE8708 CIR transceiver as /devices/virtual/rc/rc0
[   22.699168] ite_cir: driver has been successfully loaded
[   22.728368] IR NEC protocol handler initialized
[   22.816054] IR RC5(x) protocol handler initialized
[   22.861673] kvm: disabled by bios
[   22.862900] kvm: disabled by bios
[   22.899140] cfg80211: World regulatory domain updated:
[   22.899144] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   22.899147] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   22.899149] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   22.899151] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   22.899153] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   22.899155] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   22.954078] IR RC6 protocol handler initialized
[   22.988741] IR JVC protocol handler initialized
[   23.033348] IR Sony protocol handler initialized
[   23.035548] r852: driver loaded successfully
[   23.073620] uvcvideo: Found UVC 1.00 device Integrated Webcam (05ca:18a0)
[   23.074940] input: Integrated Webcam as /devices/pci0000:00/0000:00:1a.7/usb1/1-6/1-6:1.0/input/input8
[   23.075773] usbcore: registered new interface driver uvcvideo
[   23.075776] USB Video Class driver (1.1.1)
[   23.100984] IR SANYO protocol handler initialized
[   23.136044] iwlwifi 0000:04:00.0: CONFIG_IWLWIFI_DEBUG disabled
[   23.136049] iwlwifi 0000:04:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[   23.136051] iwlwifi 0000:04:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[   23.136053] iwlwifi 0000:04:00.0: CONFIG_IWLWIFI_DEVICE_TESTMODE enabled
[   23.136055] iwlwifi 0000:04:00.0: CONFIG_IWLWIFI_P2P disabled
[   23.136058] iwlwifi 0000:04:00.0: Detected Intel(R) WiFi Link 5100 AGN, REV=0x54
[   23.136158] iwlwifi 0000:04:00.0: L1 Enabled; Disabling L0S
[   23.139964] iwlwifi 0000:04:00.0: RF_KILL bit toggled to enable radio.
[   23.152475] input: MCE IR Keyboard/Mouse (ite-cir) as /devices/virtual/input/input9
[   23.166968] IR MCE Keyboard/mouse protocol handler initialized
[   23.231969] snd_hda_intel 0000:00:1b.0: irq 48 for MSI/MSI-X
[   23.235152] lirc_dev: IR Remote Control driver registered, major 248 
[   23.243152] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[   23.301892] input: HDA Intel Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[   23.302359] hda-intel 0000:01:00.1: Handle VGA-switcheroo audio client
[   23.302442] snd_hda_intel 0000:01:00.1: irq 49 for MSI/MSI-X
[   23.338120] rc rc0: lirc_dev: driver ir-lirc-codec (ite-cir) registered at minor = 0
[   23.338124] IR LIRC bridge handler initialized
[   23.349799] input: HDA ATI HDMI HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input11
[   23.585726] input: PS/2 Mouse as /devices/platform/i8042/serio1/input/input12
[   23.603250] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio1/input/input13
[   24.004779] EXT4-fs (sda2): re-mounted. Opts: errors=remount-ro
[   24.420632] init: failsafe main process (912) killed by TERM signal
[   24.942901] type=1400 audit(1366912601.336:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=979 comm="apparmor_parser"
[   24.943253] type=1400 audit(1366912601.336:9): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper//chromium_browser" pid=979 comm="apparmor_parser"
[   24.944884] type=1400 audit(1366912601.340:10): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=980 comm="apparmor_parser"
[   24.945345] type=1400 audit(1366912601.340:11): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=980 comm="apparmor_parser"
[   25.673074] Bluetooth: Core ver 2.16
[   25.673107] NET: Registered protocol family 31
[   25.673109] Bluetooth: HCI device and connection manager initialized
[   25.673117] Bluetooth: HCI socket layer initialized
[   25.673120] Bluetooth: L2CAP socket layer initialized
[   25.673127] Bluetooth: SCO socket layer initialized
[   25.742770] init: avahi-cups-reload main process (1016) terminated with status 1
[   25.877504] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   25.877508] Bluetooth: BNEP filters: protocol multicast
[   25.877515] Bluetooth: BNEP socket layer initialized
[   25.888044] Bluetooth: RFCOMM TTY layer initialized
[   25.888056] Bluetooth: RFCOMM socket layer initialized
[   25.888058] Bluetooth: RFCOMM ver 1.11
[   25.890300] ppdev: user-space parallel port driver

```

I hope thats not the live environment, shouldnt be though, as it says kernel 3.8 (livedisk is 12.10).

---

### Post by hencelence on 2013-04-25
```
[    27.704] 
X.Org X Server 1.13.3
Release Date: 2013-03-07
[    27.704] X Protocol Version 11, Revision 0
[    27.704] Build Operating System: Linux 3.2.0-37-generic i686 Ubuntu
[    27.704] Current Operating System: Linux dell-studio 3.8.0-19-generic #29-Ubuntu SMP Wed Apr 17 18:19:42 UTC 2013 i686
[    27.704] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.8.0-19-generic root=UUID=cd38ed06-9c26-429f-a47b-70f74a3b4ed9 ro quiet splash vt.handoff=7
[    27.704] Build Date: 17 April 2013  10:42:56PM
[    27.704] xorg-server 2:1.13.3-0ubuntu6 (For technical support please see http://www.ubuntu.com/support) 
[    27.705] Current version of pixman: 0.28.2
[    27.705]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    27.705] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    27.705] (==) Log file: "/var/log/Xorg.0.log", Time: Thu Apr 25 19:56:44 2013
[    27.758] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    27.758] (==) No Layout section.  Using the first Screen section.
[    27.758] (==) No screen section available. Using defaults.
[    27.758] (**) |-->Screen "Default Screen Section" (0)
[    27.758] (**) |   |-->Monitor "<default monitor>"
[    27.759] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    27.759] (==) Automatically adding devices
[    27.759] (==) Automatically enabling devices
[    27.759] (==) Automatically adding GPU devices
[    27.759] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    27.759]     Entry deleted from font path.
[    27.759] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    27.759]     Entry deleted from font path.
[    27.759] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    27.759]     Entry deleted from font path.
[    27.759] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    27.759]     Entry deleted from font path.
[    27.759] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    27.759]     Entry deleted from font path.
[    27.759] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[    27.759]     Entry deleted from font path.
[    27.759] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[    27.759] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    27.759] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    27.759] (II) Loader magic: 0xb77ef6a0
[    27.759] (II) Module ABI versions:
[    27.759]     X.Org ANSI C Emulation: 0.4
[    27.759]     X.Org Video Driver: 13.1
[    27.759]     X.Org XInput driver : 18.0
[    27.759]     X.Org Server Extension : 7.0
[    27.759] (II) config/udev: Adding drm device (/dev/dri/card0)
[    27.761] (--) PCI:*(0:1:0:0) 1002:95c4:1028:029f rev 0, Mem @ 0xd0000000/268435456, 0xcfef0000/65536, I/O @ 0x00002000/256, BIOS @ 0x????????/131072
[    27.762] (II) Open ACPI successful (/var/run/acpid.socket)
[    27.762] Initializing built-in extension Generic Event Extension
[    27.762] Initializing built-in extension SHAPE
[    27.762] Initializing built-in extension MIT-SHM
[    27.762] Initializing built-in extension XInputExtension
[    27.762] Initializing built-in extension XTEST
[    27.762] Initializing built-in extension BIG-REQUESTS
[    27.762] Initializing built-in extension SYNC
[    27.762] Initializing built-in extension XKEYBOARD
[    27.762] Initializing built-in extension XC-MISC
[    27.762] Initializing built-in extension SECURITY
[    27.762] Initializing built-in extension XINERAMA
[    27.762] Initializing built-in extension XFIXES
[    27.762] Initializing built-in extension RENDER
[    27.762] Initializing built-in extension RANDR
[    27.762] Initializing built-in extension COMPOSITE
[    27.762] Initializing built-in extension DAMAGE
[    27.762] Initializing built-in extension MIT-SCREEN-SAVER
[    27.762] Initializing built-in extension DOUBLE-BUFFER
[    27.762] Initializing built-in extension RECORD
[    27.762] Initializing built-in extension DPMS
[    27.762] Initializing built-in extension X-Resource
[    27.762] Initializing built-in extension XVideo
[    27.762] Initializing built-in extension XVideo-MotionCompensation
[    27.762] Initializing built-in extension SELinux
[    27.762] Initializing built-in extension XFree86-VidModeExtension
[    27.762] Initializing built-in extension XFree86-DGA
[    27.762] Initializing built-in extension XFree86-DRI
[    27.762] Initializing built-in extension DRI2
[    27.762] (II) LoadModule: "glx"
[    27.887] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    27.887] (II) Module glx: vendor="X.Org Foundation"
[    27.887]     compiled for 1.13.3, module version = 1.0.0
[    27.887]     ABI class: X.Org Server Extension, version 7.0
[    27.887] (==) AIGLX enabled
[    27.887] Loading extension GLX
[    27.887] (==) Matched fglrx as autoconfigured driver 0
[    27.887] (==) Matched ati as autoconfigured driver 1
[    27.887] (==) Matched fglrx as autoconfigured driver 2
[    27.887] (==) Matched ati as autoconfigured driver 3
[    27.887] (==) Matched vesa as autoconfigured driver 4
[    27.887] (==) Matched modesetting as autoconfigured driver 5
[    27.887] (==) Matched fbdev as autoconfigured driver 6
[    27.887] (==) Assigned the driver to the xf86ConfigLayout
[    27.887] (II) LoadModule: "fglrx"
[    27.887] (WW) Warning, couldn't open module fglrx
[    27.887] (II) UnloadModule: "fglrx"
[    27.887] (II) Unloading fglrx
[    27.887] (EE) Failed to load module "fglrx" (module does not exist, 0)
[    27.887] (II) LoadModule: "ati"
[    27.888] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[    27.888] (II) Module ati: vendor="X.Org Foundation"
[    27.888]     compiled for 1.13.3, module version = 7.1.0
[    27.888]     Module class: X.Org Video Driver
[    27.888]     ABI class: X.Org Video Driver, version 13.1
[    27.888] (II) LoadModule: "radeon"
[    27.888] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[    28.068] (II) Module radeon: vendor="X.Org Foundation"
[    28.068]     compiled for 1.13.3, module version = 7.1.0
[    28.068]     Module class: X.Org Video Driver
[    28.068]     ABI class: X.Org Video Driver, version 13.1
[    28.068] (II) LoadModule: "vesa"
[    28.068] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    28.068] (II) Module vesa: vendor="X.Org Foundation"
[    28.068]     compiled for 1.12.99.902, module version = 2.3.2
[    28.068]     Module class: X.Org Video Driver
[    28.068]     ABI class: X.Org Video Driver, version 13.0
[    28.068] (II) LoadModule: "modesetting"
[    28.068] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    28.068] (II) Module modesetting: vendor="X.Org Foundation"
[    28.068]     compiled for 1.13.3, module version = 0.7.0
[    28.069]     Module class: X.Org Video Driver
[    28.069]     ABI class: X.Org Video Driver, version 13.1
[    28.069] (II) LoadModule: "fbdev"
[    28.069] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    28.069] (II) Module fbdev: vendor="X.Org Foundation"
[    28.069]     compiled for 1.12.99.902, module version = 0.4.3
[    28.069]     Module class: X.Org Video Driver
[    28.069]     ABI class: X.Org Video Driver, version 13.0
[    28.069] (==) Matched fglrx as autoconfigured driver 0
[    28.069] (==) Matched ati as autoconfigured driver 1
[    28.069] (==) Matched fglrx as autoconfigured driver 2
[    28.069] (==) Matched ati as autoconfigured driver 3
[    28.069] (==) Matched vesa as autoconfigured driver 4
[    28.069] (==) Matched modesetting as autoconfigured driver 5
[    28.069] (==) Matched fbdev as autoconfigured driver 6
[    28.069] (==) Assigned the driver to the xf86ConfigLayout
[    28.069] (II) LoadModule: "fglrx"
[    28.069] (WW) Warning, couldn't open module fglrx
[    28.069] (II) UnloadModule: "fglrx"
[    28.069] (II) Unloading fglrx
[    28.069] (EE) Failed to load module "fglrx" (module does not exist, 0)
[    28.069] (II) LoadModule: "ati"
[    28.070] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[    28.070] (II) Module ati: vendor="X.Org Foundation"
[    28.070]     compiled for 1.13.3, module version = 7.1.0
[    28.070]     Module class: X.Org Video Driver
[    28.070]     ABI class: X.Org Video Driver, version 13.1
[    28.070] (II) LoadModule: "vesa"
[    28.070] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    28.070] (II) Module vesa: vendor="X.Org Foundation"
[    28.070]     compiled for 1.12.99.902, module version = 2.3.2
[    28.070]     Module class: X.Org Video Driver
[    28.070]     ABI class: X.Org Video Driver, version 13.0
[    28.070] (II) UnloadModule: "vesa"
[    28.070] (II) Unloading vesa
[    28.070] (II) Failed to load module "vesa" (already loaded, 0)
[    28.070] (II) LoadModule: "modesetting"
[    28.070] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    28.070] (II) Module modesetting: vendor="X.Org Foundation"
[    28.070]     compiled for 1.13.3, module version = 0.7.0
[    28.070]     Module class: X.Org Video Driver
[    28.070]     ABI class: X.Org Video Driver, version 13.1
[    28.070] (II) UnloadModule: "modesetting"
[    28.070] (II) Unloading modesetting
[    28.070] (II) Failed to load module "modesetting" (already loaded, 0)
[    28.070] (II) LoadModule: "fbdev"
[    28.070] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    28.070] (II) Module fbdev: vendor="X.Org Foundation"
[    28.071]     compiled for 1.12.99.902, module version = 0.4.3
[    28.071]     Module class: X.Org Video Driver
[    28.071]     ABI class: X.Org Video Driver, version 13.0
[    28.071] (II) UnloadModule: "fbdev"
[    28.071] (II) Unloading fbdev
[    28.071] (II) Failed to load module "fbdev" (already loaded, 0)
[    28.071] (II) RADEON: Driver for ATI Radeon chipsets:
    ATI Radeon Mobility X600 (M24) 3150 (PCIE), ATI FireMV 2400 (PCI),
    ATI Radeon Mobility X300 (M24) 3152 (PCIE),
    ATI FireGL M24 GL 3154 (PCIE), ATI FireMV 2400 3155 (PCI),
    ATI Radeon X600 (RV380) 3E50 (PCIE),
    ATI FireGL V3200 (RV380) 3E54 (PCIE), ATI Radeon IGP320 (A3) 4136,
    ATI Radeon IGP330/340/350 (A4) 4137, ATI Radeon 9500 AD (AGP),
    ATI Radeon 9500 AE (AGP), ATI Radeon 9600TX AF (AGP),
    ATI FireGL Z1 AG (AGP), ATI Radeon 9800SE AH (AGP),
    ATI Radeon 9800 AI (AGP), ATI Radeon 9800 AJ (AGP),
    ATI FireGL X2 AK (AGP), ATI Radeon 9600 AP (AGP),
    ATI Radeon 9600SE AQ (AGP), ATI Radeon 9600XT AR (AGP),
    ATI Radeon 9600 AS (AGP), ATI FireGL T2 AT (AGP), ATI Radeon 9650,
    ATI FireGL RV360 AV (AGP), ATI Radeon 7000 IGP (A4+) 4237,
    ATI Radeon 8500 AIW BB (AGP), ATI Radeon IGP320M (U1) 4336,
    ATI Radeon IGP330M/340M/350M (U2) 4337,
    ATI Radeon Mobility 7000 IGP 4437, ATI Radeon 9000/PRO If (AGP/PCI),
    ATI Radeon 9000 Ig (AGP/PCI), ATI Radeon X800 (R420) JH (AGP),
    ATI Radeon X800PRO (R420) JI (AGP),
    ATI Radeon X800SE (R420) JJ (AGP), ATI Radeon X800 (R420) JK (AGP),
    ATI Radeon X800 (R420) JL (AGP), ATI FireGL X3 (R420) JM (AGP),
    ATI Radeon Mobility 9800 (M18) JN (AGP),
    ATI Radeon X800 SE (R420) (AGP), ATI Radeon X800XT (R420) JP (AGP),
    ATI Radeon X800 VE (R420) JT (AGP), ATI Radeon X850 (R480) (AGP),
    ATI Radeon X850 XT (R480) (AGP), ATI Radeon X850 SE (R480) (AGP),
    ATI Radeon X850 PRO (R480) (AGP), ATI Radeon X850 XT PE (R480) (AGP),
    ATI Radeon Mobility M7 LW (AGP),
    ATI Mobility FireGL 7800 M7 LX (AGP),
    ATI Radeon Mobility M6 LY (AGP), ATI Radeon Mobility M6 LZ (AGP),
    ATI FireGL Mobility 9000 (M9) Ld (AGP),
    ATI Radeon Mobility 9000 (M9) Lf (AGP),
    ATI Radeon Mobility 9000 (M9) Lg (AGP), ATI FireMV 2400 PCI,
    ATI Radeon 9700 Pro ND (AGP), ATI Radeon 9700/9500Pro NE (AGP),
    ATI Radeon 9600TX NF (AGP), ATI FireGL X1 NG (AGP),
    ATI Radeon 9800PRO NH (AGP), ATI Radeon 9800 NI (AGP),
    ATI FireGL X2 NK (AGP), ATI Radeon 9800XT NJ (AGP),
    ATI Radeon Mobility 9600/9700 (M10/M11) NP (AGP),
    ATI Radeon Mobility 9600 (M10) NQ (AGP),
    ATI Radeon Mobility 9600 (M11) NR (AGP),
    ATI Radeon Mobility 9600 (M10) NS (AGP),
    ATI FireGL Mobility T2 (M10) NT (AGP),
    ATI FireGL Mobility T2e (M11) NV (AGP), ATI Radeon QD (AGP),
    ATI Radeon QE (AGP), ATI Radeon QF (AGP), ATI Radeon QG (AGP),
    ATI FireGL 8700/8800 QH (AGP), ATI Radeon 8500 QL (AGP),
    ATI Radeon 9100 QM (AGP), ATI Radeon 7500 QW (AGP/PCI),
    ATI Radeon 7500 QX (AGP/PCI), ATI Radeon VE/7000 QY (AGP/PCI),
    ATI Radeon VE/7000 QZ (AGP/PCI), ATI ES1000 515E (PCI),
    ATI Radeon Mobility X300 (M22) 5460 (PCIE),
    ATI Radeon Mobility X600 SE (M24C) 5462 (PCIE),
    ATI FireGL M22 GL 5464 (PCIE), ATI Radeon X800 (R423) UH (PCIE),
    ATI Radeon X800PRO (R423) UI (PCIE),
    ATI Radeon X800LE (R423) UJ (PCIE),
    ATI Radeon X800SE (R423) UK (PCIE),
    ATI Radeon X800 XTP (R430) (PCIE), ATI Radeon X800 XL (R430) (PCIE),
    ATI Radeon X800 SE (R430) (PCIE), ATI Radeon X800 (R430) (PCIE),
    ATI FireGL V7100 (R423) (PCIE), ATI FireGL V5100 (R423) UQ (PCIE),
    ATI FireGL unknown (R423) UR (PCIE),
    ATI FireGL unknown (R423) UT (PCIE),
    ATI Mobility FireGL V5000 (M26) (PCIE),
    ATI Mobility FireGL V5000 (M26) (PCIE),
    ATI Mobility Radeon X700 XL (M26) (PCIE),
    ATI Mobility Radeon X700 (M26) (PCIE),
    ATI Mobility Radeon X700 (M26) (PCIE),
    ATI Radeon X550XTX 5657 (PCIE), ATI Radeon 9100 IGP (A5) 5834,
    ATI Radeon Mobility 9100 IGP (U3) 5835,
    ATI Radeon XPRESS 200 5954 (PCIE),
    ATI Radeon XPRESS 200M 5955 (PCIE), ATI Radeon 9250 5960 (AGP),
    ATI Radeon 9200 5961 (AGP), ATI Radeon 9200 5962 (AGP),
    ATI Radeon 9200SE 5964 (AGP), ATI FireMV 2200 (PCI),
    ATI ES1000 5969 (PCI), ATI Radeon XPRESS 200 5974 (PCIE),
    ATI Radeon XPRESS 200M 5975 (PCIE),
    ATI Radeon XPRESS 200 5A41 (PCIE),
    ATI Radeon XPRESS 200M 5A42 (PCIE),
    ATI Radeon XPRESS 200 5A61 (PCIE),
    ATI Radeon XPRESS 200M 5A62 (PCIE),
    ATI Radeon X300 (RV370) 5B60 (PCIE),
    ATI Radeon X600 (RV370) 5B62 (PCIE),
    ATI Radeon X550 (RV370) 5B63 (PCIE),
    ATI FireGL V3100 (RV370) 5B64 (PCIE),
    ATI FireMV 2200 PCIE (RV370) 5B65 (PCIE),
    ATI Radeon Mobility 9200 (M9+) 5C61 (AGP),
    ATI Radeon Mobility 9200 (M9+) 5C63 (AGP),
    ATI Mobility Radeon X800 XT (M28) (PCIE),
    ATI Mobility FireGL V5100 (M28) (PCIE),
    ATI Mobility Radeon X800 (M28) (PCIE), ATI Radeon X850 5D4C (PCIE),
    ATI Radeon X850 XT PE (R480) (PCIE),
    ATI Radeon X850 SE (R480) (PCIE), ATI Radeon X850 PRO (R480) (PCIE),
    ATI unknown Radeon / FireGL (R480) 5D50 (PCIE),
    ATI Radeon X850 XT (R480) (PCIE),
    ATI Radeon X800XT (R423) 5D57 (PCIE),
    ATI FireGL V5000 (RV410) (PCIE), ATI Radeon X700 XT (RV410) (PCIE),
    ATI Radeon X700 PRO (RV410) (PCIE),
    ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X700 (RV410) (PCIE),
    ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X1800,
    ATI Mobility Radeon X1800 XT, ATI Mobility Radeon X1800,
    ATI Mobility FireGL V7200, ATI FireGL V7200, ATI FireGL V5300,
    ATI Mobility FireGL V7100, ATI Radeon X1800, ATI Radeon X1800,
    ATI Radeon X1800, ATI Radeon X1800, ATI Radeon X1800,
    ATI FireGL V7300, ATI FireGL V7350, ATI Radeon X1600, ATI RV505,
    ATI Radeon X1300/X1550, ATI Radeon X1550, ATI M54-GL,
    ATI Mobility Radeon X1400, ATI Radeon X1300/X1550,
    ATI Radeon X1550 64-bit, ATI Mobility Radeon X1300,
    ATI Mobility Radeon X1300, ATI Mobility Radeon X1300,
    ATI Mobility Radeon X1300, ATI Radeon X1300, ATI Radeon X1300,
    ATI RV505, ATI RV505, ATI FireGL V3300, ATI FireGL V3350,
    ATI Radeon X1300, ATI Radeon X1550 64-bit, ATI Radeon X1300/X1550,
    ATI Radeon X1600, ATI Radeon X1300/X1550, ATI Mobility Radeon X1450,
    ATI Radeon X1300/X1550, ATI Mobility Radeon X2300,
    ATI Mobility Radeon X2300, ATI Mobility Radeon X1350,
    ATI Mobility Radeon X1350, ATI Mobility Radeon X1450,
    ATI Radeon X1300, ATI Radeon X1550, ATI Mobility Radeon X1350,
    ATI FireMV 2250, ATI Radeon X1550 64-bit, ATI Radeon X1600,
    ATI Radeon X1650, ATI Radeon X1600, ATI Radeon X1600,
    ATI Mobility FireGL V5200, ATI Mobility Radeon X1600,
    ATI Radeon X1650, ATI Radeon X1650, ATI Radeon X1600,
    ATI Radeon X1300 XT/X1600 Pro, ATI FireGL V3400,
    ATI Mobility FireGL V5250, ATI Mobility Radeon X1700,
    ATI Mobility Radeon X1700 XT, ATI FireGL V5200,
    ATI Mobility Radeon X1700, ATI Radeon X2300HD,
    ATI Mobility Radeon HD 2300, ATI Mobility Radeon HD 2300,
    ATI Radeon X1950, ATI Radeon X1900, ATI Radeon X1950,
    ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
    ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
    ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
    ATI AMD Stream Processor, ATI Radeon X1900, ATI Radeon X1950,
    ATI RV560, ATI RV560, ATI Mobility Radeon X1900, ATI RV560,
    ATI Radeon X1950 GT, ATI RV570, ATI RV570, ATI FireGL V7400,
    ATI RV560, ATI Radeon X1650, ATI Radeon X1650, ATI RV560,
    ATI Radeon 9100 PRO IGP 7834, ATI Radeon Mobility 9200 IGP 7835,
    ATI Radeon X1200, ATI Radeon X1200, ATI Radeon X1200,
    ATI Radeon X1200, ATI Radeon X1200, ATI RS740, ATI RS740M, ATI RS740,
    ATI RS740M, ATI Radeon HD 2900 XT, ATI Radeon HD 2900 XT,
    ATI Radeon HD 2900 XT, ATI Radeon HD 2900 Pro, ATI Radeon HD 2900 GT,
    ATI FireGL V8650, ATI FireGL V8600, ATI FireGL V7600,
    ATI Radeon 4800 Series, ATI Radeon HD 4870 x2,
    ATI Radeon 4800 Series, ATI Radeon HD 4850 x2,
    ATI FirePro V8750 (FireGL), ATI FirePro V7760 (FireGL),
    ATI Mobility RADEON HD 4850, ATI Mobility RADEON HD 4850 X2,
    ATI Radeon 4800 Series, ATI FirePro RV770, AMD FireStream 9270,
    AMD FireStream 9250, ATI FirePro V8700 (FireGL),
    ATI Mobility RADEON HD 4870, ATI Mobility RADEON M98,
    ATI Mobility RADEON HD 4870, ATI Radeon 4800 Series,
    ATI Radeon 4800 Series, ATI FirePro M7750, ATI M98, ATI M98, ATI M98,
    ATI Mobility Radeon HD 4650, ATI Radeon RV730 (AGP),
    ATI Mobility Radeon HD 4670, ATI FirePro M5750,
    ATI Mobility Radeon HD 4670, ATI Radeon RV730 (AGP),
    ATI RV730XT [Radeon HD 4670], ATI RADEON E4600,
    ATI Radeon HD 4600 Series, ATI RV730 PRO [Radeon HD 4650],
    ATI FirePro V7750 (FireGL), ATI FirePro V5700 (FireGL),
    ATI FirePro V3750 (FireGL), ATI Mobility Radeon HD 4830,
    ATI Mobility Radeon HD 4850, ATI FirePro M7740, ATI RV740,
    ATI Radeon HD 4770, ATI Radeon HD 4700 Series, ATI Radeon HD 4770,
    ATI FirePro M5750, ATI RV610, ATI Radeon HD 2400 XT,
    ATI Radeon HD 2400 Pro, ATI Radeon HD 2400 PRO AGP, ATI FireGL V4000,
    ATI RV610, ATI Radeon HD 2350, ATI Mobility Radeon HD 2400 XT,
    ATI Mobility Radeon HD 2400, ATI RADEON E2400, ATI RV610,
    ATI FireMV 2260, ATI RV670, ATI Radeon HD3870,
    ATI Mobility Radeon HD 3850, ATI Radeon HD3850,
    ATI Mobility Radeon HD 3850 X2, ATI RV670,
    ATI Mobility Radeon HD 3870, ATI Mobility Radeon HD 3870 X2,
    ATI Radeon HD3870 X2, ATI FireGL V7700, ATI Radeon HD3850,
    ATI Radeon HD3690, AMD Firestream 9170, ATI Radeon HD 4550,
    ATI Radeon RV710, ATI Radeon RV710, ATI Radeon RV710,
    ATI Radeon HD 4350, ATI Mobility Radeon 4300 Series,
    ATI Mobility Radeon 4500 Series, ATI Mobility Radeon 4500 Series,
    ATI FirePro RG220, ATI Mobility Radeon 4330, ATI RV630,
    ATI Mobility Radeon HD 2600, ATI Mobility Radeon HD 2600 XT,
    ATI Radeon HD 2600 XT AGP, ATI Radeon HD 2600 Pro AGP,
    ATI Radeon HD 2600 XT, ATI Radeon HD 2600 Pro, ATI Gemini RV630,
    ATI Gemini Mobility Radeon HD 2600 XT, ATI FireGL V5600,
    ATI FireGL V3600, ATI Radeon HD 2600 LE,
    ATI Mobility FireGL Graphics Processor, ATI Radeon HD 3470,
    ATI Mobility Radeon HD 3430, ATI Mobility Radeon HD 3400 Series,
    ATI Radeon HD 3450, ATI Radeon HD 3450, ATI Radeon HD 3430,
    ATI Radeon HD 3450, ATI FirePro V3700, ATI FireMV 2450,
    ATI FireMV 2260, ATI FireMV 2260, ATI Radeon HD 3600 Series,
    ATI Radeon HD 3650 AGP, ATI Radeon HD 3600 PRO,
    ATI Radeon HD 3600 XT, ATI Radeon HD 3600 PRO,
    ATI Mobility Radeon HD 3650, ATI Mobility Radeon HD 3670,
    ATI Mobility FireGL V5700, ATI Mobility FireGL V5725,
    ATI Radeon HD 3200 Graphics, ATI Radeon 3100 Graphics,
    ATI Radeon HD 3200 Graphics, ATI Radeon 3100 Graphics,
    ATI Radeon HD 3300 Graphics, ATI Radeon HD 3200 Graphics,
    ATI Radeon 3000 Graphics, SUMO, SUMO, SUMO2, SUMO2, SUMO2, SUMO2,
    SUMO, SUMO, SUMO, SUMO, SUMO, SUMO, SUMO, SUMO, ATI Radeon HD 4200,
    ATI Radeon 4100, ATI Mobility Radeon HD 4200,
    ATI Mobility Radeon 4100, ATI Radeon HD 4290, ATI Radeon HD 4250,
    AMD Radeon HD 6310 Graphics, AMD Radeon HD 6310 Graphics,
    AMD Radeon HD 6250 Graphics, AMD Radeon HD 6250 Graphics,
    AMD Radeon HD 6300 Series Graphics,
    AMD Radeon HD 6200 Series Graphics, PALM, PALM, PALM, CYPRESS,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI FirePro (FireGL) Graphics Adapter, AMD Firestream 9370,
    AMD Firestream 9350, ATI Radeon HD 5800 Series,
    ATI Radeon HD 5800 Series, ATI Radeon HD 5800 Series,
    ATI Radeon HD 5800 Series, ATI Radeon HD 5900 Series,
    ATI Radeon HD 5900 Series, ATI Mobility Radeon HD 5800 Series,
    ATI Mobility Radeon HD 5800 Series,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI Mobility Radeon HD 5800 Series, ATI Radeon HD 5700 Series,
    ATI Radeon HD 5700 Series, ATI Radeon HD 6700 Series,
    ATI Radeon HD 5700 Series, ATI Radeon HD 6700 Series,
    ATI Mobility Radeon HD 5000 Series,
    ATI Mobility Radeon HD 5000 Series, ATI Mobility Radeon HD 5570,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI FirePro (FireGL) Graphics Adapter, ATI Radeon HD 5670,
    ATI Radeon HD 5570, ATI Radeon HD 5500 Series, REDWOOD,
    ATI Mobility Radeon HD 5000 Series,
    ATI Mobility Radeon HD 5000 Series, ATI Mobility Radeon Graphics,
    ATI Mobility Radeon Graphics, CEDAR,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI FirePro (FireGL) Graphics Adapter, ATI FirePro 2270, CEDAR,
    ATI Radeon HD 5450, CEDAR, CEDAR, CAYMAN, CAYMAN, CAYMAN, CAYMAN,
    CAYMAN, CAYMAN, CAYMAN, CAYMAN, CAYMAN, CAYMAN,
    AMD Radeon HD 6900 Series, AMD Radeon HD 6900 Series, CAYMAN, CAYMAN,
    CAYMAN, AMD Radeon HD 6900M Series, Mobility Radeon HD 6000 Series,
    BARTS, BARTS, Mobility Radeon HD 6000 Series,
    Mobility Radeon HD 6000 Series, BARTS, BARTS, BARTS, BARTS,
    AMD Radeon HD 6800 Series, AMD Radeon HD 6800 Series,
    AMD Radeon HD 6700 Series, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS,
    TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS,
    TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS,
    CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS,
    CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, ARUBA, ARUBA,
    ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA,
    ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA,
    ARUBA, ARUBA, TAHITI, TAHITI, TAHITI, TAHITI, TAHITI, TAHITI, TAHITI,
    TAHITI, TAHITI, TAHITI, TAHITI, TAHITI, TAHITI, PITCAIRN, PITCAIRN,
    PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN,
    PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, VERDE, VERDE, VERDE, VERDE,
    VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE,
    VERDE, VERDE, VERDE, VERDE, VERDE, VERDE
[    28.075] (II) VESA: driver for VESA chipsets: vesa
[    28.075] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    28.075] (II) FBDEV: driver for framebuffer: fbdev
[    28.075] (++) using VT number 7

[    28.075] (II) [KMS] Kernel modesetting enabled.
[    28.075] (WW) Falling back to old probe method for vesa
[    28.075] (WW) Falling back to old probe method for modesetting
[    28.075] (WW) Falling back to old probe method for fbdev
[    28.075] (II) Loading sub module "fbdevhw"
[    28.075] (II) LoadModule: "fbdevhw"
[    28.075] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    28.075] (II) Module fbdevhw: vendor="X.Org Foundation"
[    28.075]     compiled for 1.13.3, module version = 0.0.2
[    28.075]     ABI class: X.Org Video Driver, version 13.1
[    28.076] (II) RADEON(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    28.076] (==) RADEON(0): Depth 24, (--) framebuffer bpp 32
[    28.076] (II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[    28.076] (==) RADEON(0): Default visual is TrueColor
[    28.076] (==) RADEON(0): RGB weight 888
[    28.076] (II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
[    28.076] (--) RADEON(0): Chipset: "ATI Mobility Radeon HD 3400 Series" (ChipID = 0x95c4)
[    28.076] (II) Loading sub module "dri2"
[    28.076] (II) LoadModule: "dri2"
[    28.076] (II) Module "dri2" already built-in
[    28.076] (II) Loading sub module "exa"
[    28.076] (II) LoadModule: "exa"
[    28.076] (II) Loading /usr/lib/xorg/modules/libexa.so
[    28.076] (II) Module exa: vendor="X.Org Foundation"
[    28.076]     compiled for 1.13.3, module version = 2.6.0
[    28.076]     ABI class: X.Org Video Driver, version 13.1
[    28.076] (II) RADEON(0): KMS Color Tiling: enabled
[    28.076] (II) RADEON(0): KMS Color Tiling 2D: enabled
[    28.076] (II) RADEON(0): KMS Pageflipping: enabled
[    28.076] (II) RADEON(0): SwapBuffers wait for vsync: enabled
[    28.100] (II) RADEON(0): Output VGA-0 has no monitor section
[    28.100] (II) RADEON(0): Output LVDS has no monitor section
[    28.102] (II) RADEON(0): Output HDMI-0 has no monitor section
[    28.124] (II) RADEON(0): EDID for output VGA-0
[    28.124] (II) RADEON(0): EDID for output LVDS
[    28.124] (II) RADEON(0): Manufacturer: AUO  Model: 9274  Serial#: 0
[    28.124] (II) RADEON(0): Year: 2008  Week: 1
[    28.124] (II) RADEON(0): EDID Version: 1.3
[    28.124] (II) RADEON(0): Digital Display Input
[    28.124] (II) RADEON(0): Max Image Size [cm]: horiz.: 33  vert.: 21
[    28.124] (II) RADEON(0): Gamma: 2.20
[    28.124] (II) RADEON(0): No DPMS capabilities specified
[    28.124] (II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    28.124] (II) RADEON(0): First detailed timing is preferred mode
[    28.124] (II) RADEON(0): redX: 0.590 redY: 0.345   greenX: 0.340 greenY: 0.570
[    28.124] (II) RADEON(0): blueX: 0.150 blueY: 0.120   whiteX: 0.313 whiteY: 0.329
[    28.124] (II) RADEON(0): Manufacturer's mask: 0
[    28.124] (II) RADEON(0): Supported detailed timing:
[    28.124] (II) RADEON(0): clock: 73.0 MHz   Image Size:  331 x 207 mm
[    28.124] (II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1476 h_border: 0
[    28.124] (II) RADEON(0): v_active: 800  v_sync: 803  v_sync_end 809 v_blanking: 824 v_border: 0
[    28.124] (II) RADEON(0): Supported detailed timing:
[    28.124] (II) RADEON(0): clock: 73.0 MHz   Image Size:  331 x 207 mm
[    28.124] (II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1476 h_border: 0
[    28.124] (II) RADEON(0): v_active: 800  v_sync: 803  v_sync_end 809 v_blanking: 824 v_border: 0
[    28.124] (II) RADEON(0):  H709H€B154EW9
[    28.124] (II) RADEON(0): Unknown vendor-specific block 0
[    28.124] (II) RADEON(0): EDID (in hex):
[    28.124] (II) RADEON(0):     00ffffffffffff0006af749200000000
[    28.124] (II) RADEON(0):     01120103902115780a10b59758579226
[    28.124] (II) RADEON(0):     1e505400000001010101010101010101
[    28.124] (II) RADEON(0):     010101010101841c00c4502018303020
[    28.124] (II) RADEON(0):     36004bcf1000001a841c00c450201830
[    28.124] (II) RADEON(0):     302036004bcf1000001a000000fe0048
[    28.124] (II) RADEON(0):     37303948804231353445573900000000
[    28.124] (II) RADEON(0):     00000000000000000001010a202000e0
[    28.124] (II) RADEON(0): Printing probed modes for output LVDS
[    28.124] (II) RADEON(0): Modeline "1280x800"x60.0   73.00  1280 1328 1360 1476  800 803 809 824 +hsync -vsync (49.5 kHz eP)
[    28.124] (II) RADEON(0): Modeline "1280x720"x59.9   74.50  1280 1344 1472 1664  720 723 728 748 -hsync +vsync (44.8 kHz)
[    28.124] (II) RADEON(0): Modeline "1152x768"x59.8   71.75  1152 1216 1328 1504  768 771 781 798 -hsync +vsync (47.7 kHz)
[    28.124] (II) RADEON(0): Modeline "1024x768"x59.9   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync (47.8 kHz)
[    28.124] (II) RADEON(0): Modeline "800x600"x59.9   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync (37.4 kHz)
[    28.124] (II) RADEON(0): Modeline "848x480"x59.7   31.50  848 872 952 1056  480 483 493 500 -hsync +vsync (29.8 kHz)
[    28.124] (II) RADEON(0): Modeline "720x480"x59.7   26.75  720 744 808 896  480 483 493 500 -hsync +vsync (29.9 kHz)
[    28.124] (II) RADEON(0): Modeline "640x480"x59.4   23.75  640 664 720 800  480 483 487 500 -hsync +vsync (29.7 kHz)
[    28.127] (II) RADEON(0): EDID for output HDMI-0
[    28.127] (II) RADEON(0): Output VGA-0 disconnected
[    28.127] (II) RADEON(0): Output LVDS connected
[    28.127] (II) RADEON(0): Output HDMI-0 disconnected
[    28.127] (II) RADEON(0): Using exact sizes for initial modes
[    28.127] (II) RADEON(0): Output LVDS using initial mode 1280x800
[    28.127] (II) RADEON(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    28.127] (II) RADEON(0): mem size init: gart size :1fdef000 vram size: s:10000000 visible:fbd8000
[    28.127] (II) RADEON(0): EXA: Driver will allow EXA pixmaps in VRAM
[    28.127] (==) RADEON(0): DPI set to (96, 96)
[    28.127] (II) Loading sub module "fb"
[    28.127] (II) LoadModule: "fb"
[    28.127] (II) Loading /usr/lib/xorg/modules/libfb.so
[    28.127] (II) Module fb: vendor="X.Org Foundation"
[    28.127]     compiled for 1.13.3, module version = 1.0.0
[    28.127]     ABI class: X.Org ANSI C Emulation, version 0.4
[    28.127] (II) Loading sub module "ramdac"
[    28.127] (II) LoadModule: "ramdac"
[    28.127] (II) Module "ramdac" already built-in
[    28.127] (II) UnloadModule: "vesa"
[    28.127] (II) Unloading vesa
[    28.127] (II) UnloadModule: "modesetting"
[    28.127] (II) Unloading modesetting
[    28.127] (II) UnloadModule: "fbdev"
[    28.127] (II) Unloading fbdev
[    28.127] (II) UnloadSubModule: "fbdevhw"
[    28.127] (II) Unloading fbdevhw
[    28.127] (--) Depth 24 pixmap format is 32 bpp
[    28.128] (II) RADEON(0): [DRI2] Setup complete
[    28.128] (II) RADEON(0): [DRI2]   DRI driver: r600
[    28.128] (II) RADEON(0): [DRI2]   VDPAU driver: r600
[    28.128] (II) RADEON(0): Front buffer size: 4000K
[    28.128] (II) RADEON(0): VRAM usage limit set to 228470K
[    28.128] (==) RADEON(0): Backing store disabled
[    28.128] (II) RADEON(0): Direct rendering enabled
[    28.128] (II) EXA(0): Driver allocated offscreen pixmaps
[    28.128] (II) EXA(0): Driver registered support for the following operations:
[    28.128] (II)         Solid
[    28.128] (II)         Copy
[    28.128] (II)         Composite (RENDER acceleration)
[    28.128] (II)         UploadToScreen
[    28.128] (II)         DownloadFromScreen
[    28.128] (II) RADEON(0): Acceleration enabled
[    28.128] (==) RADEON(0): DPMS enabled
[    28.128] (==) RADEON(0): Silken mouse enabled
[    28.128] (II) RADEON(0): Set up textured video
[    28.128] (II) RADEON(0): [XvMC] Associated with Radeon Textured Video.
[    28.128] (II) RADEON(0): [XvMC] Extension initialized.
[    28.128] (II) RADEON(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    28.128] (--) RandR disabled
[    28.136] (II) SELinux: Disabled on system
[    29.765] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    29.765] (II) AIGLX: enabled GLX_INTEL_swap_event
[    29.765] (II) AIGLX: enabled GLX_ARB_create_context
[    29.765] (II) AIGLX: enabled GLX_ARB_create_context_profile
[    29.765] (II) AIGLX: enabled GLX_EXT_create_context_es2_profile
[    29.765] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    29.765] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    29.766] (II) AIGLX: Loaded and initialized r600
[    29.766] (II) GLX: Initialized DRI2 GL provider for screen 0
[    29.767] (II) RADEON(0): Setting screen physical size to 338 x 211
[    29.777] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    29.780] (II) config/udev: Adding input device Power Button (/dev/input/event3)
[    29.780] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    29.780] (II) LoadModule: "evdev"
[    29.780] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    29.824] (II) Module evdev: vendor="X.Org Foundation"
[    29.824]     compiled for 1.13.3, module version = 2.7.3
[    29.824]     Module class: X.Org XInput Driver
[    29.824]     ABI class: X.Org XInput driver, version 18.0
[    29.824] (II) Using input driver 'evdev' for 'Power Button'
[    29.824] (**) Power Button: always reports core events
[    29.824] (**) evdev: Power Button: Device: "/dev/input/event3"
[    29.824] (--) evdev: Power Button: Vendor 0 Product 0x1
[    29.824] (--) evdev: Power Button: Found keys
[    29.824] (II) evdev: Power Button: Configuring as keyboard
[    29.824] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input3/event3"
[    29.824] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    29.824] (**) Option "xkb_rules" "evdev"
[    29.824] (**) Option "xkb_model" "pc105"
[    29.824] (**) Option "xkb_layout" "de"
[    29.829] (II) XKB: reuse xkmfile /var/lib/xkb/server-808BBA3D4C227BDB44C370226C34E44C5D69A4A9.xkm
[    29.830] (II) config/udev: Adding input device Video Bus (/dev/input/event5)
[    29.830] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    29.830] (II) Using input driver 'evdev' for 'Video Bus'
[    29.830] (**) Video Bus: always reports core events
[    29.830] (**) evdev: Video Bus: Device: "/dev/input/event5"
[    29.830] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    29.830] (--) evdev: Video Bus: Found keys
[    29.830] (II) evdev: Video Bus: Configuring as keyboard
[    29.830] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:00/LNXVIDEO:00/input/input5/event5"
[    29.830] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[    29.830] (**) Option "xkb_rules" "evdev"
[    29.830] (**) Option "xkb_model" "pc105"
[    29.830] (**) Option "xkb_layout" "de"
[    29.830] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    29.831] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    29.831] (II) Using input driver 'evdev' for 'Power Button'
[    29.831] (**) Power Button: always reports core events
[    29.831] (**) evdev: Power Button: Device: "/dev/input/event0"
[    29.831] (--) evdev: Power Button: Vendor 0 Product 0x1
[    29.831] (--) evdev: Power Button: Found keys
[    29.831] (II) evdev: Power Button: Configuring as keyboard
[    29.831] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0/event0"
[    29.831] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 8)
[    29.831] (**) Option "xkb_rules" "evdev"
[    29.831] (**) Option "xkb_model" "pc105"
[    29.831] (**) Option "xkb_layout" "de"
[    29.831] (II) config/udev: Adding input device Lid Switch (/dev/input/event2)
[    29.831] (II) No input driver specified, ignoring this device.
[    29.831] (II) This device may have been added with another device file.
[    29.831] (II) config/udev: Adding input device Sleep Button (/dev/input/event1)
[    29.832] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    29.832] (II) Using input driver 'evdev' for 'Sleep Button'
[    29.832] (**) Sleep Button: always reports core events
[    29.832] (**) evdev: Sleep Button: Device: "/dev/input/event1"
[    29.832] (--) evdev: Sleep Button: Vendor 0 Product 0x3
[    29.832] (--) evdev: Sleep Button: Found keys
[    29.832] (II) evdev: Sleep Button: Configuring as keyboard
[    29.832] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1/event1"
[    29.832] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD, id 9)
[    29.832] (**) Option "xkb_rules" "evdev"
[    29.832] (**) Option "xkb_model" "pc105"
[    29.832] (**) Option "xkb_layout" "de"
[    29.832] (II) config/udev: Adding drm device (/dev/dri/card0) card0 /sys/devices/pci0000:00/0000:00:01.0/0000:01:00.0/drm/card0
[    29.832] (II) config/udev: Ignoring already known drm device (/dev/dri/card0)
[    29.832] (II) config/udev: Adding input device HDA ATI HDMI HDMI/DP,pcm=3 (/dev/input/event11)
[    29.832] (II) No input driver specified, ignoring this device.
[    29.832] (II) This device may have been added with another device file.
[    29.833] (II) config/udev: Adding input device Integrated Webcam (/dev/input/event8)
[    29.833] (**) Integrated Webcam: Applying InputClass "evdev keyboard catchall"
[    29.833] (II) Using input driver 'evdev' for 'Integrated Webcam'
[    29.833] (**) Integrated Webcam: always reports core events
[    29.833] (**) evdev: Integrated Webcam: Device: "/dev/input/event8"
[    29.833] (--) evdev: Integrated Webcam: Vendor 0x5ca Product 0x18a0
[    29.833] (--) evdev: Integrated Webcam: Found keys
[    29.833] (II) evdev: Integrated Webcam: Configuring as keyboard
[    29.833] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.7/usb1/1-6/1-6:1.0/input/input8/event8"
[    29.833] (II) XINPUT: Adding extended input device "Integrated Webcam" (type: KEYBOARD, id 10)
[    29.833] (**) Option "xkb_rules" "evdev"
[    29.833] (**) Option "xkb_model" "pc105"
[    29.833] (**) Option "xkb_layout" "de"
[    29.834] (II) config/udev: Adding input device HDA Intel Mic (/dev/input/event10)
[    29.834] (II) No input driver specified, ignoring this device.
[    29.834] (II) This device may have been added with another device file.
[    29.834] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event4)
[    29.834] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    29.834] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    29.834] (**) AT Translated Set 2 keyboard: always reports core events
[    29.834] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event4"
[    29.834] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    29.834] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    29.834] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    29.834] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input4/event4"
[    29.834] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 11)
[    29.834] (**) Option "xkb_rules" "evdev"
[    29.834] (**) Option "xkb_model" "pc105"
[    29.834] (**) Option "xkb_layout" "de"
[    29.835] (II) config/udev: Adding input device PS/2 Mouse (/dev/input/event12)
[    29.835] (**) PS/2 Mouse: Applying InputClass "evdev pointer catchall"
[    29.835] (II) Using input driver 'evdev' for 'PS/2 Mouse'
[    29.835] (**) PS/2 Mouse: always reports core events
[    29.835] (**) evdev: PS/2 Mouse: Device: "/dev/input/event12"
[    29.835] (--) evdev: PS/2 Mouse: Vendor 0x2 Product 0x8
[    29.835] (--) evdev: PS/2 Mouse: Found 3 mouse buttons
[    29.835] (--) evdev: PS/2 Mouse: Found relative axes
[    29.835] (--) evdev: PS/2 Mouse: Found x and y relative axes
[    29.835] (II) evdev: PS/2 Mouse: Configuring as mouse
[    29.835] (**) evdev: PS/2 Mouse: YAxisMapping: buttons 4 and 5
[    29.835] (**) evdev: PS/2 Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    29.835] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input12/event12"
[    29.835] (II) XINPUT: Adding extended input device "PS/2 Mouse" (type: MOUSE, id 12)
[    29.835] (II) evdev: PS/2 Mouse: initialized for relative axes.
[    29.835] (**) PS/2 Mouse: (accel) keeping acceleration scheme 1
[    29.835] (**) PS/2 Mouse: (accel) acceleration profile 0
[    29.835] (**) PS/2 Mouse: (accel) acceleration factor: 2.000
[    29.835] (**) PS/2 Mouse: (accel) acceleration threshold: 4
[    29.835] (II) config/udev: Adding input device PS/2 Mouse (/dev/input/mouse1)
[    29.835] (II) No input driver specified, ignoring this device.
[    29.835] (II) This device may have been added with another device file.
[    29.836] (II) config/udev: Adding input device AlpsPS/2 ALPS GlidePoint (/dev/input/event13)
[    29.836] (**) AlpsPS/2 ALPS GlidePoint: Applying InputClass "evdev touchpad catchall"
[    29.836] (**) AlpsPS/2 ALPS GlidePoint: Applying InputClass "touchpad catchall"
[    29.836] (**) AlpsPS/2 ALPS GlidePoint: Applying InputClass "Default clickpad buttons"
[    29.836] (II) LoadModule: "synaptics"
[    29.836] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    29.836] (II) Module synaptics: vendor="X.Org Foundation"
[    29.836]     compiled for 1.13.1.901, module version = 1.6.2
[    29.836]     Module class: X.Org XInput Driver
[    29.836]     ABI class: X.Org XInput driver, version 18.0
[    29.836] (II) Using input driver 'synaptics' for 'AlpsPS/2 ALPS GlidePoint'
[    29.836] (**) AlpsPS/2 ALPS GlidePoint: always reports core events
[    29.836] (**) Option "Device" "/dev/input/event13"
[    29.836] (--) synaptics: AlpsPS/2 ALPS GlidePoint: x-axis range 0 - 1023
[    29.836] (--) synaptics: AlpsPS/2 ALPS GlidePoint: y-axis range 0 - 767
[    29.836] (--) synaptics: AlpsPS/2 ALPS GlidePoint: pressure range 0 - 127
[    29.836] (II) synaptics: AlpsPS/2 ALPS GlidePoint: device does not report finger width.
[    29.836] (--) synaptics: AlpsPS/2 ALPS GlidePoint: buttons: left right middle
[    29.836] (--) synaptics: AlpsPS/2 ALPS GlidePoint: Vendor 0x2 Product 0x8
[    29.836] (--) synaptics: AlpsPS/2 ALPS GlidePoint: invalid finger width range.  defaulting to 0 - 15
[    29.836] (--) synaptics: AlpsPS/2 ALPS GlidePoint: touchpad found
[    29.837] (**) AlpsPS/2 ALPS GlidePoint: always reports core events
[    29.840] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input13/event13"
[    29.840] (II) XINPUT: Adding extended input device "AlpsPS/2 ALPS GlidePoint" (type: TOUCHPAD, id 13)
[    29.840] (**) synaptics: AlpsPS/2 ALPS GlidePoint: (accel) MinSpeed is now constant deceleration 2.5
[    29.840] (**) synaptics: AlpsPS/2 ALPS GlidePoint: MaxSpeed is now 1.75
[    29.840] (**) synaptics: AlpsPS/2 ALPS GlidePoint: AccelFactor is now 0.156
[    29.840] (**) AlpsPS/2 ALPS GlidePoint: (accel) keeping acceleration scheme 1
[    29.840] (**) AlpsPS/2 ALPS GlidePoint: (accel) acceleration profile 1
[    29.840] (**) AlpsPS/2 ALPS GlidePoint: (accel) acceleration factor: 2.000
[    29.840] (**) AlpsPS/2 ALPS GlidePoint: (accel) acceleration threshold: 4
[    29.840] (--) synaptics: AlpsPS/2 ALPS GlidePoint: touchpad found
[    29.840] (II) config/udev: Adding input device AlpsPS/2 ALPS GlidePoint (/dev/input/mouse2)
[    29.840] (**) AlpsPS/2 ALPS GlidePoint: Ignoring device from InputClass "touchpad ignore duplicates"
[    29.843] (II) config/udev: Adding input device Dell WMI hotkeys (/dev/input/event6)
[    29.843] (**) Dell WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[    29.843] (II) Using input driver 'evdev' for 'Dell WMI hotkeys'
[    29.843] (**) Dell WMI hotkeys: always reports core events
[    29.843] (**) evdev: Dell WMI hotkeys: Device: "/dev/input/event6"
[    29.843] (--) evdev: Dell WMI hotkeys: Vendor 0 Product 0
[    29.843] (--) evdev: Dell WMI hotkeys: Found keys
[    29.843] (II) evdev: Dell WMI hotkeys: Configuring as keyboard
[    29.843] (**) Option "config_info" "udev:/sys/devices/virtual/input/input6/event6"
[    29.843] (II) XINPUT: Adding extended input device "Dell WMI hotkeys" (type: KEYBOARD, id 14)
[    29.843] (**) Option "xkb_rules" "evdev"
[    29.843] (**) Option "xkb_model" "pc105"
[    29.843] (**) Option "xkb_layout" "de"
[    29.843] (II) config/udev: Adding input device MCE IR Keyboard/Mouse (ite-cir) (/dev/input/event9)
[    29.843] (**) MCE IR Keyboard/Mouse (ite-cir): Applying InputClass "evdev pointer catchall"
[    29.843] (**) MCE IR Keyboard/Mouse (ite-cir): Applying InputClass "evdev keyboard catchall"
[    29.843] (II) Using input driver 'evdev' for 'MCE IR Keyboard/Mouse (ite-cir)'
[    29.843] (**) MCE IR Keyboard/Mouse (ite-cir): always reports core events
[    29.843] (**) evdev: MCE IR Keyboard/Mouse (ite-cir): Device: "/dev/input/event9"
[    29.843] (--) evdev: MCE IR Keyboard/Mouse (ite-cir): Vendor 0 Product 0
[    29.843] (--) evdev: MCE IR Keyboard/Mouse (ite-cir): Found 3 mouse buttons
[    29.843] (--) evdev: MCE IR Keyboard/Mouse (ite-cir): Found relative axes
[    29.843] (--) evdev: MCE IR Keyboard/Mouse (ite-cir): Found x and y relative axes
[    29.843] (--) evdev: MCE IR Keyboard/Mouse (ite-cir): Found keys
[    29.843] (II) evdev: MCE IR Keyboard/Mouse (ite-cir): Configuring as mouse
[    29.843] (II) evdev: MCE IR Keyboard/Mouse (ite-cir): Configuring as keyboard
[    29.843] (**) evdev: MCE IR Keyboard/Mouse (ite-cir): YAxisMapping: buttons 4 and 5
[    29.843] (**) evdev: MCE IR Keyboard/Mouse (ite-cir): EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    29.843] (**) Option "config_info" "udev:/sys/devices/virtual/input/input9/event9"
[    29.844] (II) XINPUT: Adding extended input device "MCE IR Keyboard/Mouse (ite-cir)" (type: KEYBOARD, id 15)
[    29.844] (**) Option "xkb_rules" "evdev"
[    29.844] (**) Option "xkb_model" "pc105"
[    29.844] (**) Option "xkb_layout" "de"
[    29.844] (II) evdev: MCE IR Keyboard/Mouse (ite-cir): initialized for relative axes.
[    29.844] (**) MCE IR Keyboard/Mouse (ite-cir): (accel) keeping acceleration scheme 1
[    29.844] (**) MCE IR Keyboard/Mouse (ite-cir): (accel) acceleration profile 0
[    29.844] (**) MCE IR Keyboard/Mouse (ite-cir): (accel) acceleration factor: 2.000
[    29.844] (**) MCE IR Keyboard/Mouse (ite-cir): (accel) acceleration threshold: 4
[    29.844] (II) config/udev: Adding input device MCE IR Keyboard/Mouse (ite-cir) (/dev/input/mouse0)
[    29.844] (II) No input driver specified, ignoring this device.
[    29.844] (II) This device may have been added with another device file.
[    29.844] (II) config/udev: Adding input device ITE8708 CIR transceiver (/dev/input/event7)
[    29.845] (**) ITE8708 CIR transceiver: Applying InputClass "evdev keyboard catchall"
[    29.845] (II) Using input driver 'evdev' for 'ITE8708 CIR transceiver'
[    29.845] (**) ITE8708 CIR transceiver: always reports core events
[    29.845] (**) evdev: ITE8708 CIR transceiver: Device: "/dev/input/event7"
[    29.845] (--) evdev: ITE8708 CIR transceiver: Vendor 0x1283 Product 0
[    29.845] (--) evdev: ITE8708 CIR transceiver: Found keys
[    29.845] (II) evdev: ITE8708 CIR transceiver: Configuring as keyboard
[    29.845] (**) Option "config_info" "udev:/sys/devices/virtual/rc/rc0/input7/event7"
[    29.845] (II) XINPUT: Adding extended input device "ITE8708 CIR transceiver" (type: KEYBOARD, id 16)
[    29.845] (**) Option "xkb_rules" "evdev"
[    29.845] (**) Option "xkb_model" "pc105"
[    29.845] (**) Option "xkb_layout" "de"

```

I was almost able to pull it off from the recovery console, but I didnt know which dmesg file it would have been.

---

### Post by matt_symes on 2013-04-25
Hi

I'm still analysing the log files but i have a question.

What version of Xubuntu are you running on the LiveUSB and what is the kernel version ?

```
cat /etc/lsb-release
```

```
uname -a
```

I need to check something.

Kind regards

---

### Post by hencelence on 2013-04-26
```
xubuntu@xubuntu:~$ uname -a
Linux xubuntu 3.5.0-17-generic #28-Ubuntu SMP Tue Oct 9 19:32:08 UTC 2012 i686 i686 i686 GNU/Linux

```

```
xubuntu@xubuntu:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.10
DISTRIB_CODENAME=quantal
DISTRIB_DESCRIPTION="Ubuntu 12.10"

```

It was the latest stable release before 13.04.

---

### Post by matt_symes on 2013-04-26
Hi

I can't see anything immediately wrong with both the log files you have posted. 

Something must be off though. It looks like it may be a scan line timing issue. 

One thing you may want to do is compare the Xorg.0.log files from the liveCD/USB boot against the ones on the drive to see if there are any differences.

The other thing you may want to do is post your lightdm.log file. 

You will need elevated privileges to view it so type 

```
gksudo gedit /var/log/lightdm/lightdm.log
```

(the above may not work in 13.04) or

```
sudo cat /var/log/lightdm/lightdm.log
```

Before posting it, you may want to remove any sensitive data such as you user name.

Kind regards

---

### Post by hencelence on 2013-04-30
Sorry, I have been busy in the last days, but I am back.

> **matt_symes said:**
> 
One thing you may want to do is compare the Xorg.0.log files from the liveCD/USB boot against the ones on the drive to see if there are any differences.


I compared them, all the hundreds of lines, couldnt find a difference.
Are you sure my system keeps the log files when I reboot the crash?

Heres the output from lightdm.

```

[+0.08s] DEBUG: X server :0 will replace Plymouth
[+0.11s] DEBUG: Using VT 7
[+0.11s] DEBUG: Logging to /var/log/lightdm/x-0.log
[+0.11s] DEBUG: Writing X server authority to /var/run/lightdm/root/:0
[+0.11s] DEBUG: Launching X Server
[+0.11s] DEBUG: Launching process 1211: /usr/bin/X :0 -core -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch -background none
[+0.11s] DEBUG: Waiting for ready signal from X server :0
[+0.11s] DEBUG: Acquired bus name org.freedesktop.DisplayManager
[+0.11s] DEBUG: Registering seat with bus path /org/freedesktop/DisplayManager/Seat0
[+3.29s] DEBUG: Got signal 10 from process 1211
[+3.29s] DEBUG: Got signal from X server :0
[+3.29s] DEBUG: Stopping Plymouth, X server is ready
[+3.37s] DEBUG: Connecting to XServer :0
[+3.37s] DEBUG: Starting greeter
[+3.37s] DEBUG: Started session 2387 with service 'lightdm-greeter', username 'lightdm'
[+3.74s] DEBUG: Session 2387 authentication complete with return value 0: Success
[+3.74s] DEBUG: Greeter authorized
[+3.74s] DEBUG: Logging to /var/log/lightdm/x-0-greeter.log
[+3.74s] DEBUG: Session 2387 running command /usr/lib/lightdm/lightdm-greeter-session /usr/sbin/lightdm-gtk-greeter
[+4.15s] DEBUG: Greeter connected version=1.6.0
[+4.15s] DEBUG: Greeter connected, display is ready
[+4.15s] DEBUG: New display ready, switching to it
[+4.15s] DEBUG: Activating VT 7

```
No problems again, it seems?

A friend of mine had a similar issue when he installed ubuntu Gnome 13.04 on his system.
He too, had a rather old laptop.
I dont know how many people have upgraded yet but I think this might be a thing...

---

### Post by matt_symes on 2013-04-30
> **hencelence said:**
> Sorry, I have been busy in the last days, but I am back.

I compared them, all the hundreds of lines, couldnt find a difference.
Are you sure my system keeps the log files when I reboot the crash?

Heres the output from lightdm.

```

<snip>
[+4.15s] DEBUG: New display ready, switching to it
[+4.15s] DEBUG: Activating VT 7

```
No problems again, it seems?

Apart from the fact you are missing half the log from when it changes to VT7 and crashes.

```

[+18.32s] DEBUG: Activating VT 7
[+24.22s] DEBUG: Greeter start authentication for matthew
[+24.22s] DEBUG: Started session 2372 with service 'lightdm', username 'matthew'
[+24.33s] DEBUG: Session 2372 got 1 message(s) from PAM
[+24.33s] DEBUG: Prompt greeter with 1 message(s)
[+30.03s] DEBUG: Continue authentication
[+30.09s] DEBUG: Session 2372 authentication complete with return value 0: Success
[+30.09s] DEBUG: Authenticate result for user matthew: Success
[+30.10s] DEBUG: User matthew authorized
<snip>
```

> 
A friend of mine had a similar issue when he installed ubuntu Gnome 13.04 on his system.
He too, had a rather old laptop.
I dont know how many people have upgraded yet but I think this might be a thing...

I'll continue to look into this and post back.

What happens of you boot into the console and run

```
sudo service lightdm start
```

Does it still crash ?

EDIT:

Try booting to a different VT.

Add this to the start of the file

```
sudo nano /etc/lightdm/lightdm.conf
```

```
[LightDM]
minimum-display-number=0
minimum-vt=8
```

Reboot your PC. Does it crash this time ?

Kind regards

---

### Post by hencelence on 2013-06-18
This issue appears to be fixed by now.
I reinstalled Ubuntu GNOME 13.04 5 days ago and it runs like a charm out of the box.

Thanks for helping, Matt!
I will tag this as solved.

Lenz

---

