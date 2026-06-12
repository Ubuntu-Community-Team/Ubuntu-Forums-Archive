---
title: "Never used linux before, error MP-BIOS bug : 8254 please help"
date: 2009-01-26
forum: Installation &amp; Upgrades
---

### Post by jamesreece on 2009-01-26
**MP-BIOS bug : 8254 timer not connected to IO-APIC**

as soon as i load ubuntu i get this code come up then it goes into a sort of command line, im not entirely sure what this is called.

i also try pressing escape on load, then it gives me options to run and i have tried all and in some i get this error message.

[B]File "/usr/bin/ubiquity-dm", line 113, in run
raise XStartupError, "X server failed to start after 60 seconds"
__main__.XStartupError: X server failed to start after 60 seconds [Fail][/B]

ive read quite alot about this problem and read you can put the code "noapic" at the end of the commmand line when u run from the disc but it just seemed to keep flashing at top left for absolutely ages so i turned my computer off, bt im using a Toshiba Satellite A210-11P, i use dual boot.

i am ok with computers but ive never used ubuntu before so id prefer it if you could speak basic if possible thankyou for help in advance.

---

### Post by oldos2er on 2009-01-26
Are you trying the LiveCD? or the alternate? What are your hardware specs?

---

### Post by jamesreece on 2009-01-26
> **oldos2er said:**
> Are you trying the LiveCD? or the alternate? What are your hardware specs?

i think it may of been live CD, i did install it on windows following this.

[http://seogadget.co.uk/the-ubuntu-installation-guide/](http://seogadget.co.uk/the-ubuntu-installation-guide/)

and how do i find my hardware specs thanx for replying

---

### Post by oldos2er on 2009-01-26
Run ```
lshw
``` in a terminal, copy and paste the output here.

---

### Post by jamesreece on 2009-01-26
> **oldos2er said:**
> Run ```
lshw
``` in a terminal, copy and paste the output here.

is the terminal the bit it goes too after it cannot load, the command line

**Did you mean do that on windows or linux i did it on windows and i cannot find it because it says windows cannot find it**

---

### Post by jamesreece on 2009-01-26
ok i did that i recieved this,

        ```
[B]vendor: Advanced Micro Devices [AMD]
        physical id: 103
        bus info: pci@0000 :00 :18.2
        version :00
        width: 32bits
        clock: 33Mhz

*-pci: 4
        description: Host bridge
        product: K8 [Athlon64/Opteron] Miscellaneous Control
        vendor: Advanced Micro Devices [AMD]
        physical id: 104
        bus info: pci@0000 :00 :18.3
        version: 00
        width: 32 bits
        clock: 33Mhz
        configuration: driver=k8temp module=k8temp
*-network DISABLED
         description: Ethernet interface
         physical id: 1
         logical name: pan8
         serial: a2:79:6e:19:12:07
         capabilities: ethernet physical
         configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/a
multicast=yes[/B]
```

thats what i got, any ideas thanx

---

### Post by oldos2er on 2009-01-26
Yes, sorry, I meant run 'lshw' in a terminal while you're booted from the LiveCD or in your wubi install. There should be quite a bit more output than what you posted.

---

### Post by jamesreece on 2009-01-27
> **oldos2er said:**
> Yes, sorry, I meant run 'lshw' in a terminal while you're booted from the LiveCD or in your wubi install. There should be quite a bit more output than what you posted.

haha i know i kept putting "1shw" then later realised it was an "l"
rite maybe it did but im not entirely sure how you scroll up,

in the mean time i have used the openSUSE GNOME Live CD, but i couldnt even install it because it says that something is being mounted and i must unmount whatever is being mounted but i can still use that software, i do think it has something to do with my graphics cared because it said that on openSUSE that i couldnt do desktop effects because of my graphics card or something is that because i have that nvidia card or whatever its called.

---

### Post by oldos2er on 2009-01-27
There should be a scroll bar on the right side of the terminal window.

 All we really need to know is how much RAM, hard disk space, video card make/manufacturer, CPU. If it's easier for you to get this info from Windows, please do.

---

### Post by jamesreece on 2009-01-27
> **oldos2er said:**
> There should be a scroll bar on the right side of the terminal window.

 All we really need to know is how much RAM, hard disk space, video card make/manufacturer, CPU. If it's easier for you to get this info from Windows, please do.

[B]RAM = 2046MB

Processor = AMD Turion(tm) 64 X2 Mobile Technology TL -56 1.80 GHz[/B]

I Have 2 Hardrives

[B]C: Vista = 22.7Gb Free
E: Data = 90.7 Gb Free[/B]

Video Card

[B]ATI Mobility Radeon HD 2600

Manufacturer: ATI Technologies Inc.[/B]

---

### Post by oldos2er on 2009-01-27
[SIZE=2]Someone else posted today about the same problem[/SIZE] "**MP-BIOS bug : 8254 timer not connected to IO-APIC". **After doing some googling and reading, I can't see any easy way to resolve this problem, other than running 'noacpi' at bootup (but you mentioned you'd tried that already).

 Which version of Ubuntu are you trying? If 8.10, maybe give 8.04.2 a try (or vice versa). Thank you for posting your specs--they look fine.

---

### Post by jamesreece on 2009-01-27
thanx for taking time out to help me tho man, really appreciated

---

### Post by oldos2er on 2009-01-27
You're welcome.

---

