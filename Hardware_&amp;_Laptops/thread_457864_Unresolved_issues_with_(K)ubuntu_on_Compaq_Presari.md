---
title: "Unresolved issues with (K)ubuntu on Compaq Presario V6000 Series"
date: 2007-05-29
forum: Hardware &amp; Laptops
---

### Post by MobiusNZ on 2007-05-29
I have a Presario V6302AU laptop, which has reasonable specs, and works well under Kubuntu, with a few exceptions. Any help on these matters would be greatly appreciated.

Here goes:
[LIST]
[*]Booting - for the machine to boot, I have to have the "noapic" option appended to my boot command. Other options, such as "acpi=noirq" worked as well, but I found out later that this caused my wireless card to stop functioning. I have no idea what effect the noapic option has on my system, Also, sometimes when I do not have a network cable plugged in, it hangs at the configuring network devices stage
[*]Wireless - I found using the bcm43xx drivers with the firmware cutter to work, but only at about 10kb/sec. Using ndiswrapper works fast, but sometimes when I boot Knetworkmanager and ifconfig doesn't show my wireless card at all. Other times knetworkmanager seems to be  unable to negotiate a link with my AP.
[*]USB - Hotplugging doesn't work. My mouse will work if it is plugged in at boot, but not if it is unplugged and then plugged in again, or if I put the laptop to sleep. Also usb sticks are only detected if present at boot.
[*]Touchpad - A synaptics one, works fine, except for when I turn the pad back on using the hardware button, the KDE help center starts. Odd!
[/LIST]

Many thanks to anyone who can help with this!

EDIT: Have resolved USB issue thanks to jcaveman, however I have found another one: KPowerSave claims that my hardware doesn't support display dimming. The pre-installed Vista does, and it is running on the same hardware...

---

### Post by jcaveman on 2007-05-29
Can't help on the touchpad or wireless, as I don't use KDE, and haven't experienced the problems.  However, the USB problem results from the use of the noapic parameter.  Noapic is necessary because of some buggy bioses (usually created because the manufacturer used the Microsoft compiler instead of the Intel compiler when building the BIOS).  Unfortunately, noapic stands for something like Advanced Programmable Interrupt Controller, which means you've partially disabled part of the interrupt control system, which is where your USB problem comes from.  Add "irqpoll noirqdebug" after the noapic parameter in the kernel options  should solve your USB problem.

---

### Post by soapytheclown on 2007-05-29
fantastic!!! i just finally got my v6133eu working bugfree (hopefully) now! i was literally just about to post a new thread about this anyways but just to confirm the:

Add "irqpoll noirqdebug" flag to the kernel option in the grub bootloadter works

for anyone who doesnt know if you opena  terminal and type

sudo gedit /boot/grub/menu.lst 

then go to the bottom of the document and look for the grub boot options and look for something like this:

"title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=16badbe3-91d7-4ba1-9446-e874976aea45 ro splash noapic vga=792
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault"

then add the string "irqpoll noirqdebug" into the kernel option so u end up with the new line as:-

kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=16badbe3-91d7-4ba1-9446-e874976aea45 ro splash noapic irqpoll noirqdebug

(mine has an extra vga thing beucase ive modified my start up using "SUM" (startup manager)

but ya that is it really, save the file then restart!!

---

### Post by MobiusNZ on 2007-05-29
Cheers guys, I just used noapic irqpoll (didn't use irqnodebug) and that sorted out the usb.
Other problems still there though....

---

### Post by MobiusNZ on 2007-05-29
@Jcaveman: do you think then it's possible to install an open source bios? ;)

@soapytheclown: When you edit boot options under ubuntu (and any other system that uses automagic kernel listing), you need to make sure you do it in two places so the options are carried through kernel upgrades.

Look for a section similar to this in your menu.lst file and edit it (leave the comments)
```
## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash
```

Mine looks like this:
```
## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash noapic irqpoll
```

---

### Post by soapytheclown on 2007-06-02
ohh thanks didnt know that!! has anyone got cpu scaling done properly yet on thier v6000? and im using the i386 version of fiesty, does that have dual core support or do i need to do something else?

---

### Post by menollo on 2007-06-04
I'm using fedora 7 at the moment.. with only nolapic, (nolapic and irqpoll doesn't work without noapic).. cpu scaling is working now.. but i don't think usb is working.. and often the ndiswrapper module doesn't load :S.. 

I'm beginning to hate this laptop.. I'll never buy a compaq/hp anymore i think (is this the only hp or are there more (i've the compaq presario v6066ea).. and what is the reason of all this? the bios??

---

### Post by joaoeb on 2007-06-04
The how to in this thread worked for me: [http://ubuntuforums.org/showthread.php?p=2783177](http://ubuntuforums.org/showthread.php?p=2783177)

Hope it helps

---

