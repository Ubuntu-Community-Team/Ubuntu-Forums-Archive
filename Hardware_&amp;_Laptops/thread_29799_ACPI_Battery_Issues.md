---
title: "ACPI Battery Issues"
date: 2005-04-25
forum: Hardware &amp; Laptops
---

### Post by benrose on 2005-04-25
First I have to say how great everything's been running on my laptop right after a fresh install of Ubuntu 5.04. Sound, CPU throttling, most of the ACPI features work on my HP Pavilion ze4365. The only thing that didn't work was battery monitoring.

The following is a copy of my /proc/acpi/battery/BAT1/state file

> present:                 yes
capacity state:          ok
charging state:          discharging
present rate:            1152 mA
remaining capacity:      unknown
present voltage:         14848 mV


It correctly identifies when the battery is discharging (AC unplugged), when it is charging, and when it is fully charged... but I can't get remaining capacity to show anything. Does anyone know of any settings I can modify to get this to work? I looked in my BIOS setup and there were no ACPI options in it.

Any help is greatly appreciated! Thanks!

---

### Post by hacktix on 2005-04-26
Configure grub or lilo boot loader with the option acpi=force. I think that should fix it, Thats how i got the battery applet to work in gnome before i switched to blackbox.

---

### Post by benrose on 2005-04-26
Awesome! Thanks a bunch! That worked like a charm!

I can now safely say gooood bye Windows!

---

### Post by lorenzo on 2005-07-18
MMmmmmmm,
I've tried that but nothing changed (I have a compaq nx 9010). My laptop shuts down when the battery is fully discharged without any warning...

Any hint?
Thanks, 
Lorenzo

---

### Post by lorenzo on 2005-07-18
Don't know if it's related, but also cpu freq applet is not working, nor suspend/hibernate....

I'm totally lost...

Lorenzo

---

### Post by luca_linux on 2005-07-18
Is there any error in your dmesg?

---

### Post by DW5 on 2005-07-18
[QUOTE=lorenzo]Don't know if it's related, but also cpu freq applet is not working, nor suspend/hibernate....

I'm totally lost...

Lorenzo[/QUOTE]


I wonder if installing the custom HP-Ubuntu install, with HP specific ACPI support

see thread [http://www.ubuntuforums.org/showthread.php?t=35244](http://www.ubuntuforums.org/showthread.php?t=35244)

would help?

---

### Post by lorenzo on 2005-07-18
I,ve tried to compile and correct errors in DSDT and put it in initrd..... same as before.

Which kind of error should I look for in dmesg. The log is very long and I do not see the word "error".

thanks,
Lorenzo

---

### Post by luca_linux on 2005-07-18
[QUOTE=lorenzo]I,ve tried to compile and correct errors in DSDT and put it in initrd..... same as before.

Which kind of error should I look for in dmesg. The log is very long and I do not see the word "error".

thanks,
Lorenzo[/QUOTE]
 Something related to "AML".
Try:
```

dmesg | grep aml
dmesg | grep acpi
dmesg | grep bat

```

---

### Post by lorenzo on 2005-07-18
this is what I get:

$ dmesg | grep aml

$ dmesg | grep acpi
shpchp: acpi_shpchprm:\_SB_.PCI0 _CRS fail=0x3019
shpchp: acpi_shpchprm:\_SB_.PCI0 evaluate _CRS fail=0x3019
pciehp: acpi_pciehprm:\_SB_.PCI0 _CRS fail=0x3019
pciehp: acpi_pciehprm:\_SB_.PCI0 evaluate _CRS fail=0x3019
ibm_acpi: ec object not found

$ dmesg | grep bat
  DMA zone: 4096 pages, LIFO batch:1
  Normal zone: 110448 pages, LIFO batch:16
  HighMem zone: 0 pages, LIFO batch:1
ACPI: Battery Slot [BAT1] (battery present)

hope it means something to you.....

---

### Post by damonw5 on 2005-07-18
[QUOTE=lorenzo]MMmmmmmm,
I've tried that but nothing changed (I have a compaq nx 9010). My laptop shuts down when the battery is fully discharged without any warning...

Any hint?
Thanks, 
Lorenzo[/QUOTE]
 Try adding "acpi=on" to your GRUB options.

(idea from [http://pvanhoof.be/wiki/index.php/Installing_RH9_on_a_Compaq_nx9010_laptop](http://pvanhoof.be/wiki/index.php/Installing_RH9_on_a_Compaq_nx9010_laptop) )

---

### Post by luca_linux on 2005-07-18
Uhm...it seems fine, there are no errors.
Try booting with "nolapic" kernel parameter.

---

### Post by lorenzo on 2005-07-19
I,ve tried almost everything..... but still no luck. I've also tried "nolapic" and "acpi=force".....

Yesterday I've tried kde and..... it works (on kde).

It happens something I can't explain:

when in KDE, if I do:

>cat /proc/acpi/battery/BAT1/state

the results change depending if I am plugged or unplugged.

In GNOME, the result of 

>cat /proc/acpi/battery/BAT1/state

remains the same until I shut down my laptop!!!!!

Any clue?
Lorenzo

---

### Post by luca_linux on 2005-07-19
Have you ever tried to update the kernel to the latest release?

---

### Post by lorenzo on 2005-07-19
I had 2.6.10-5-386, now I'm trying 2.6.10-5-686 (same results) and 2.6.11-1-686 (it hangs my computer when starting gnome.

So, my latest working kernel is: 2.6.10-5-686

Still don't understand why it works under kde and not under gnome....



UPDATE: 
if under gnome I launch kcontrol and from kcontrol y launch Klaptop: voila! now battery status is updated in gnome too...
What does klaptop do better than gnome???? What does it activate????

---

### Post by luca_linux on 2005-07-19
Try:
1) Reboot
2) Type "lsmod" (without the quotes) to see what modules are loaded
3) Run KLaptop
4) Type "lsmod" (without the quotes) to see what modules are loaded

Is there any diff?

---

### Post by lorenzo on 2005-07-19
before:

button                  6480  0
battery                 9988  0

after launching klaptop:

button                  6480  4
battery                 9988  6


it's the only difference I see....

does this means anything to you?

---

### Post by luca_linux on 2005-07-19
It could be a bug of the gnome battery monitor since the modules are not used until you run KLaptop.

---

### Post by GerritKok on 2005-07-19
Dealing with the same problem on Acer Aspire 3503 WLMi laptop, Hoary 5.04, kernel 2.6.10-5-386.

/proc/acpi/battery/Bat1/info-file gives:
present:                 yes
design capacity:         2000 mAh
last full capacity:      1794 mAh
battery technology:      rechargeable
design voltage:          14800 mV
design capacity warning: 300 mAh
design capacity low:     71 mAh
capacity granularity 1:  32 mAh
capacity granularity 2:  32 mAh
model number:            10ZL
serial number:           50094
battery type:            LION
OEM info:                SANYO

but the /state-file gives:
present:                 yes
ERROR: Unable to read battery status

*dmesg* gives:
_node 00000000
    ACPI-1138: *** Error: Method execution failed [\_SB_.BAT1._BST] (Node db9a1180), AE_NOT_FOUND
    ACPI-0352: *** Error: Looking up [Z004] in namespace, AE_NOT_FOUND
search_node db9a1280 start_node db9a1280 return_node 00000000

Gerrit Kok

---

### Post by luca_linux on 2005-07-19
We can try to customize the DSDT...do you feel like trying it?

---

### Post by GerritKok on 2005-07-19
[QUOTE=luca_linux]We can try to customize the DSDT...do you feel like trying it?[/QUOTE]
 O.K., only this is terra incognita for me, so I hope you don't mind me relying on your hints ;-)

Gerrit

---

### Post by lorenzo on 2005-07-20
Customize the DSDT? I suppose this is necessary **if** acpi does not work. What if _the battery applett works in kde but not under gnome_?

What does kde/klapto does that gnome doesn't?

I tend to prefer gnome to kde but the battery issue is quite important if you have a laptop. Having your computer shutting down all of a sudden without any warning is quite frustrating.... I'm seriously thinking of switching to kde....

Does anyone knows more details on how battery appletts works in kde/gnome?

Thanks,
Lorenzo

UPDATE:
I'm starting to see the light.

My gnome recognize the changes in state plugged/unplugged if I do:

>**cat /proc/acpi/button/lid/LID/state**

every time I do it, the battery state is updated. Questions:

what does button/lid has to do with battery?
why doing /proc/acpi/battery..../state it doesn't do anything?

Any clue?

---

### Post by GerritKok on 2005-07-20
[QUOTE=GerritKok]*dmesg* gives:
ACPI-1138: *** Error: Method execution failed [\_SB_.BAT1._BST] (Node db9a1180), AE_NOT_FOUND
ACPI-0352: *** Error: Looking up [Z004] in namespace, AE_NOT_FOUND
search_node db9a1280 start_node db9a1280 return_node 00000000[/QUOTE]

On [http://acpi.sourceforge.net/dsdt/view.php](http://acpi.sourceforge.net/dsdt/view.php) i found a minimal fix for a very similar error message:

[I]ACPI-0352: *** Error: Looking up [Z007] in namespace, AE_NOT_FOUND search_node cbd30140 start_node cbd30140 return_node 00000000 
ACPI-1138: *** Error: Method execution failed [\_SB_.BAT1._BST] (Node cbd30f20), AE_NOT_FOUND  

so I made the minimal changes required: _I replaced 'Z007' with 'Ones' twice. _  Now my battery works like a charm.[/I] 

Since i cannot contact the the man who wrote this, i'm putting my question in this forum: does anybody know how to do this?

Gerrit

---

