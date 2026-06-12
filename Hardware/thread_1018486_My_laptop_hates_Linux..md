---
title: "My laptop hates Linux."
date: 2008-12-22
forum: Hardware
---

### Post by Slicx on 2008-12-22
I've been trying to install Ubuntu on my laptop, though it will never load the installation past the initial stages (the orange bar bit).

I have tried a few other Distros and they all freeze at roughly the same stage/place on their loading bar. 

I have heard that some laptops are 'locked' to prevent certain things happening to them. I'm not sure if it is possibly to lock out an operating system though. Sounds a bit far-fetched though I may be wrong. 

It will not load the live version either, with similar symptoms.

All the installation sources are fine, I've used multiple ones and am confident in them not being corrupt or damaged in some way. 

Any suggestions?

Thanks.

---

### Post by SlidingHorn on 2008-12-22
make sure the image's md5 checksum checks out.

I gave this advice to someone else this morning, and it may sound stupid, but it can't hurt to try, and it worked for me and a few others:

When it freezes up @ the orange bar, immediately and repeatedly press the right arrow key.

---

### Post by Yellow Pasque on 2008-12-22
"Freezing on the orange bar" doesn't tell you a whole lot. Boot without the splash option (use the LiveCD and remove the "splash" keyword from the boot line) so you can see where it's actually getting hung up.

---

### Post by Captain_tux on 2008-12-22
Are you attempting to dual boot with Windows? 

If so, make sure you defrag your disk at least a couple of times...

---

### Post by Slicx on 2008-12-22
> **Temüjin said:**
> "Freezing on the orange bar" doesn't tell you a whole lot. Boot without the splash option (use the LiveCD and remove the "splash" keyword from the boot line) so you can see where it's actually getting hung up.

From what I can tell, it thinks I don't have a processor.

*Taken from roughly the start of the error:*

```
[76.920041] ACPI: CPU1 (Power states: C1[C1] C2[C2] C3[C3])

[76.920204] ACPI: Processor [CPU1] (Supports 8 throttling states)

[76.920331] ACPI exception (PROCESSOR_CORE-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
```

It then repeats the last paragraph about 4 or 5 times, mostly the same, though with a few number differences.

Thanks for everything so far.

---

### Post by Yellow Pasque on 2008-12-22
There you go. ACPI error. What kernel version (or Ubuntu version) are you using?
Your system will probably boot with adding "acpi=off" to the kernel line, though this might cripple power management features.
[http://bugzilla.kernel.org/show_bug.cgi?id=11166](http://bugzilla.kernel.org/show_bug.cgi?id=11166)

---

### Post by Kevbert on 2008-12-22
What are your laptop system specs ? RAM memory ?

---

### Post by Slicx on 2008-12-22
> **Kevbert said:**
> What are your laptop system specs ? RAM memory ?

It's a E-System machine, quite a low-spec one.

Intel Celeron Dual-Core T1400 1.73GHz
Motherboard by [http://www.phoenix.com]("http://www.phoenix.com")
1GB RAM
120GB HDD
SIS Mirage 3 672-Series 128MB
Vista Home Premium

> **Temüjin said:**
> What kernel version (or Ubuntu version) are you using?
It's Ubuntu 8.4, though I've tried 8.10 using wubi and that didn't work either.

I'm not into Linux enough to know kernel versions off the top off my head, sorry.

I will try your suggestion. 

Thanks all.

---

### Post by Kevbert on 2008-12-22
Specs are fine. As Temüjin suggests you may need to add acpi=off  to the boot line (here's a [COLOR="Red"][link]("https://help.ubuntu.com/community/BootOptions")[/COLOR] on how to do this). 
You may also want to take a look at [[COLOR="Red"]this[/COLOR]]("http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm").

---

### Post by Slicx on 2008-12-22
"acpi=off" gives me:

```
[52.226036] ExtINT not setup in hardware but reported by MP table

[52.226145] ENABLING IO-APIC IRQs

[52.226356] .. TIMER:vector=0x31 apic1=0 pin1=2 apic2=0 pin2=0
```

At which point it will not go any further.

**Update:** I added in "noapic" and it got further than it has before, though stalled while initialising bluetooth, which I though was strange, that's not a very technical thing, right?

---

### Post by Yellow Pasque on 2008-12-22
The Bluetooth module may depend on ACPI. That's the problem with disabling it (especially on laptops, which depend on ACPI for critical functions like CPU throttling and fan control).

See if there's a BIOS update for your system, and if that doesn't fix things, complain to the manufacturer that they don't have ACPI implemented correctly.

---

### Post by Slicx on 2008-12-25
I'm not sure this is the best place to carry this on, considering where I am, but I got SUSE 11.0 to install with the *noapic* and *acpi=off* parameters. 

Is there any way to undo those now the system is installed?

Hope you don't mind me asking you about SUSE :)

Thanks for everything so far, you've all been great.

---

