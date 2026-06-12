---
title: "Changing CMOS battery?"
date: 2013-11-10
forum: Hardware
---

### Post by Niemil on 2013-11-10
My girlfriends dad have problem with his old stationary computer (about 6 years old or so).
We been trying reinstalling Windows 7 completely, which didn't work really, time changed on the computer etc, about 50% of times it wont boot up, and if it's on for an half hour or so, it's possible to freeze etc.

I then installed Ubuntu lucid lynx or something like that, version 10.04 or something. As I thought it was Windows 7  that were wrong.
But after asking on a forum I got up the idea that it may be this CMOS battery that are running out in the computer, that explains quite a lot why the time in Windows had changed etc.


Now I wonder how can I change this battery? It probably looks very simple task, but me, my gf or my gf's dad have none of us ever opened a stationary computer.
Also is the CR2032 battery (which I believe it is?) need to be something special?

Also first of all I think it may be good idea to figure out what kind of computer this is and search via internet.
I wonder, with Ubuntu 10.04 (or something like that, I know it's named lucid something), can I via terminal or something else, find out what the computer hardware is named? I am quite sure it's not a self-built computer or so.

Because then I might find some manual of the computer.

Any tips?

---

### Post by deadflowr on 2013-11-10
What do you mean by stationary computer?
Do you mean a tower(a box with lots of cords connecting to a power source, monitor, keyboard, mouse)?

If so, then one of the sides should be removal.
Before removing any side panels, best practice is to unplug the machine.

If the machine hasn't been opened before, go get a can of compressed air first. 
When you open it, it will probably be coated in dust. Use the compressed air to blow the dust away.

The battery should be easy to remove and replace, it looks like a big watch battery.

---

### Post by Dennis N on 2013-11-10
CR2032 very common in electronic devices - calculators, computers, watches. Buy at any store that sells batteries. Wal Mart, Target, drugstores, if you are in the U.S. Usually just snaps out. Sometimes there is a release catch.

---

### Post by Dennis N on 2013-11-10
Cautionary note: Ground yourself when touching parts inside the computer. Static electricity can cause damage.

---

### Post by Niemil on 2013-11-10
> **deadflowr said:**
> What do you mean by stationary computer?
Do you mean a tower(a box with lots of cords connecting to a power source, monitor, keyboard, mouse)?

If so, then one of the sides should be removal.
Before removing any side panels, best practice is to unplug the machine.

If the machine hasn't been opened before, go get a can of compressed air first. 
When you open it, it will probably be coated in dust. Use the compressed air to blow the dust away.

The battery should be easy to remove and replace, it looks like a big watch battery.
Yeah, that's what I mean with stationary computer.

I know it's to move the side panels, but still unsure how to do or so, don't wanna damage anything.
But, I think it will be alright, I may just try that out next time I'm there.

> **Dennis N said:**
> CR2032 very common in electronic devices - calculators, computers, watches. Buy at any store that sells batteries. Wal Mart, Target, drugstores, if you are in the U.S. Usually just snaps out. Sometimes there is a release catch.
Alright. The battery I think wont be hard to get, I am sure they being sold in my city, if not I would just order from eBay or somewhere else.
I just wonder if the battery has to be something special, I know there are different types of CR2032, I read on some forum about lithum or something like that. If it even matters?
Also I read missplacing the battery can occur explosion?




Oh well, I think I may fix it anyway, just unplug all cables and t hen open the computer at first and look for the battery, then try bring it out and look what battery it is, then I can go to a store and ask for same type of battery, and then just go back and plug it in to the computer and then place computer away from me while plugging in, in case of explosion or somethin :p

[EDIT]
> **Dennis N said:**
> Cautionary note: Ground yourself when touching parts inside the computer. Static electricity can cause damage.
Yeah, it was this type of thing I also were wondering aobut.
I heard my dad saying about it, that it can damage the parts. That when I open it first and touching computer, I shall hold with one of the hand on a heating element? to avoid static electricity.

---

### Post by deadflowr on 2013-11-10
The side panel that can be removed is usually held with screws.
Get the correct screw driver and loosen and remove them.
The panel should come off without any problems.

That panel is normally metal and a practice normally used is to place a hand or body part on the metal to discharge any static you have.

---

### Post by Dennis N on 2013-11-10
All CR2032 are the same size and voltage - no difference between brands. The vast majority are Lithium - it should say that on the package. Lithium is what you want. Eveready and Rayovac (common U.S. Brands) both make them.


Grounding yourself:
[http://www.tomshardware.com/forum/322660-30-ground-yourself](http://www.tomshardware.com/forum/322660-30-ground-yourself)
[http://www.wikihow.com/Ground-Yourself-to-Avoid-Destroying-a-Computer-with-Electrostatic-Discharge](http://www.wikihow.com/Ground-Yourself-to-Avoid-Destroying-a-Computer-with-Electrostatic-Discharge)

---

### Post by Petro Dawg on 2013-11-10
Just be careful about asking someone at a big box store about what battery you need, most of their employees will likely know less than you about computers and just sell you what ever looks right, its better to do your research online first.  

On current Ubuntu systems you can find your system hardware info by running...

```
sudo lshw
```

It can have a really long input and take a while to execute, but what you are looking for in order to do your research is probably at the top of the output.  For example the top portion of the output for my machine is as follows...

```
    description: Desktop Computer
    product: Dimension C521 ()
    vendor: Winbond Electronics
    serial: BWP4FC1
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=1 uuid=44454C4C-5700-1050-8034-C2C04F464331
  *-core
       description: Motherboard
       product: 0HY175
       vendor: Winbond Electronics
       physical id: 0
       version: A03
       serial: ..CN708216B1K0KM.
     *-firmware
          description: BIOS
          vendor: Winbond Electronics
          physical id: 1
          version: 1.1.4
          date: 12/09/2006
          size: 128KiB
          capacity: 448KiB
          capabilities: isa pci pnp apm upgrade shadowing cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb
     *-cpu
          description: CPU
          product: AMD Athlon(tm) 64 Processor 3200+
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 8
          bus info: cpu@0
          version: 15.15.2
          slot: Socket M2
          size: 1GHz
          capacity: 3GHz
          width: 64 bits
          clock: 1GHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt rdtscp x86-64 3dnowext 3dnow up extd_apicid pni cx16 lahf_lm svm extapic cr8_legacy cpufreq

...


```

Most likely a Google search of your computer model, given by the "product:" output (e.g. Dimension C521 in the example above) will lead you to the correct BIOS battery as well as the manual showing you how to correctly install it.

---

### Post by Dennis N on 2013-11-10
If you haven't yet removed the battery, do so and the battery number is marked on the battery itself. For a one time job, attach a bare wire from your wrist to the computer case to ground yourself. Be sure the power is off, and don't work on a carpet. Cost of battery: bought a two pack a few weeks ago, for around $4. These batteries will last several years, and they have to be replaced just like any battery.

---

### Post by deadflowr on 2013-11-10
Another thing would be if the battery has any wires sprawled over them,  and it seems hard to get to, don't be afraid to simply nudge the wires out of the way.

---

### Post by ppjdee on 2013-11-10
you sure its the cmos battery? the time changing and not updating and a few other things sounds like that but the comp freezing after running for a while sounds like hardware issues.
not saying dont try the battery thing, cause meh its only a dollar :D but anyways goodluck hope it fixes it.

---

