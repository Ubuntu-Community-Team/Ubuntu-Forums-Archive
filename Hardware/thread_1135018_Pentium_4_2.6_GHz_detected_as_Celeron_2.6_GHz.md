---
title: "Pentium 4 2.6 GHz detected as Celeron 2.6 GHz"
date: 2009-04-24
forum: Hardware
---

### Post by inzpektor on 2009-04-24
Hi there.

Got an old (2004) laptop from my sister with a Pentium 4 2.6 GHz processor.  However, the processor is detected as a Celeron processor in Ubuntu.  How come?

The reason why I "know" that it's a Pentium 4 is because when I got it, it had a certain operating system from Microsoft installed, and when booting into that the fan powered down pretty quickly.  However, it doesn't do that in Ubuntu - in fact it just gets worse - with the CPU reaching about 70 degrees C, and the fan sounding like an A380 about to take-off.  And this is in idle.

From my googling, I've learned that one of the differences between the Pentium 4 and the Pentium 4-based Celerons is that the SpeedStep-interface has been disabled, making it impossible to throttle the CPU.  But since the Microsoft-system seems to be doing that, it must be a Pentium 4 and not a Celeron, right?

Also, my googling has shown that it is indeed a Pentium 4 and not a Celeron; [Clevo D430S products (German)]("http://www.ipc-computer.de/it-index-n-Clevo_D430S-cP-7898_17746-catPos-2269.html") (look at the processors listed there - 1.7 is Celeron, but 2.4 and 2.6 are Pentium 4)

Here's an lshw excerpt (It also detects the notebook as a D400S when in fact it's a D430S because that's what it says on the back, and because of other HW-related things):

```
    description: Notebook
    product: D400S
    vendor: Clevo
    version: 0106
    serial: 12345678901234567
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: boot=oem-specific chassis=notebook uuid=FFFFFFFF-FFFF-0000-0000-000000000000
  *-core
       description: Motherboard
       product: D400S
       vendor: Clevo
       physical id: 0
       version: Rev.A
       serial: None
       slot: &#65533;&#65533;&#65533;
     *-firmware
          description: BIOS
          vendor: Phoenix
          physical id: 0
          version: 4.06 (02/23/2004)
          size: 107KiB
          capacity: 192KiB
          capabilities: pci pcmcia pnp apm upgrade shadowing cdboot bootselect edd int13floppynec int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video usb
     *-cpu
          description: CPU
          product: Intel(R) Celeron(R) CPU 2.60GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 15.2.9
          slot: U23
          size: 2600MHz
          capacity: 3GHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe up pebs bts cid xtpr
          configuration: id=0
        *-cache
             description: L2 cache
             physical id: 5
             slot: L2 Cache
             size: 8KiB
             capacity: 1MiB
             capabilities: burst internal write-back

```

---

### Post by 00b00nt00 on 2009-04-24
Just a suggestion, but are there any BIOS updates available for your computer?

---

### Post by SpyroViper on 2009-04-24
Linux detects some strange things.  Apparently, my Atom is a dual core atom, even though N270's are only single core lol!

---

### Post by inzpektor on 2009-04-24
> **SpyroViper said:**
> Linux detects some strange things.  Apparently, my Atom is a dual core atom, even though N270's are only single core lol!

Yeah, ok.  But is it then possible to tell the kernel what CPU it is - overriding the default detection?  Again, this is so that I can get frequency scaling.

Right now, it's just downloading upgrade-packages for 9.04 and I swear I can boil eggs on the keyboard!

00b00nt00, thx for your suggestion.  I've been looking around for BIOS upgrades, but it doesn't seem like there's anything out there.  I'll give it another shot.

---

### Post by SpyroViper on 2009-04-24
I am going to try looking for upgrades tonight, but I had the same issue with SUSE so either it's a common problem or every distro needs to be 'told' what hardware it's on manually.

---

### Post by inzpektor on 2009-04-24
> **SpyroViper said:**
> I am going to try looking for upgrades tonight, but I had the same issue with SUSE so either it's a common problem or every distro needs to be 'told' what hardware it's on manually.

Ok, so do you know how to "tell" the kernel what the hardware is?

I mean, can you f.ex. echo `get_the_processor_id` > /sys/somewhere or do you have to compile stuff?

---

### Post by inzpektor on 2009-04-24
OK, I think I found a BIOS upgrade for a D430S (It's aimed at a DELL laptop, but since it's the same specs I guess it doesn't matter).  It's called "WinPhlash 1.5 build 55_STD.exe", so I'm installing WINE now so I can run it.

---

### Post by SpyroViper on 2009-04-24
I was thinking I'd have to compile it myself (hopefully not) but now you found this, I'm waiting on baited breath.

---

### Post by inzpektor on 2009-04-24
Well, just as I thought - Error 5, whatever that means.  I'll try and see if I can get rid of that error.

It's kind of scary when it says that it's a driver-related problem.  You should think that the BIOS-guys knew what they were doing when it comes to drivers.  Oh well...

---

### Post by inzpektor on 2009-04-24
Just in case other people with a D430S have stumbled upon this thread, [here's the BIOS upgrade package]("http://www.pinteq.co.za/live/index.php?option=com_docman&task=doc_details&gid=311&&Itemid=26").

Perhaps if someone is using systems from Microsoft on their laptops they could run it there, and if that works, then boot back into Linux and see what lshw says.

---

### Post by inzpektor on 2009-04-24
Ok, this baby is about to do a China syndrome on me, so I'll shut it down before I'm held solely responsible for global warming!

Please let me know if there's a way to force-feed the kernel the processor-name.

---

### Post by 00b00nt00 on 2009-04-26
You won't be able to do a bios update through a virtual machine, because, well, it's a virtual machine!

If you can find a Windows PC with a floppy drive / CD writer, maybe you can make a bootable image of the bios and install on boot.

---

### Post by inzpektor on 2009-04-30
> **00b00nt00 said:**
> If you can find a Windows PC with a floppy drive / CD writer, maybe you can make a bootable image of the bios and install on boot.

I found a [guide]("http://www.nenie.org/misc/flashbootcd.html") on how to make a bootable CD with an operating system that can execute .exe files natively.  After a lot of woes I succeeded in flashing the BIOS, but unfortunately to no avail.

I noticed in the BIOS, which looks **awfully** (in the true meaning of the word) identical to the old BIOS, that it also reports the CPU to be a Celeron 2.60GHz.  So maybe it really IS a Celeron processor after all?  Still doesn't explain why the Microsoft OS can do throttling.

Oh well, I think I'll just put it away for now.  I guess it can come in handy as a heater if I'm to go camping in Norway or something.

---

### Post by 00b00nt00 on 2009-05-03
I read the manual for the Clevo on the Taiwan web-site.

They describe yours as model 'D', and indeed a 2.6GHz Celeron is listed as one of the processors available. Celerons don't have speedstep, and can get damn hot (I'm typing on a Celeron laptop now - toasty).

Do a fresh install of the latest 32bit Ubuntu, and don't type with the computer on you lap if you are planning to have children. If the computer is not shutting itself down, I wouldn't worry too much about it.

---

