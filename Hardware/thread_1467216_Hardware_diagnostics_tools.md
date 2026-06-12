---
title: "Hardware diagnostics tools"
date: 2010-04-30
forum: Hardware
---

### Post by zeroti on 2010-04-30
Are there any hardware diagnostic tools for ubuntu? Something that checks memory, graphics cards, hard drive r/w, etc. I would prefer something that doesn't require booting to a cd, but if that's my only option, I'll consider trying it.

Thanks! :)

---

### Post by Julita on 2010-04-30
You can look at [http://smartmontools.sourceforge.net/](http://smartmontools.sourceforge.net/)

---

### Post by robert.matear on 2010-04-30
There is a package called HardInfo that gives you detailed information about your computer hardware, but its not really a diagnostic tool unless you compare what CPU speed and memory you should have with the information that it returns?

I know you said you didn't want something that required a disk boot. However, I seem to remember that there was a memory diagnostic tool built in with the Ubuntu live CD.

---

### Post by Julita on 2010-04-30
> **robert.matear said:**
> However, I seem to remember that there was a memory diagnostic tool built in with the Ubuntu live CD.

There is a memory test. By the way, exists [http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/) with a whole bunch of tools, but the OP does not want CDs, so...

---

### Post by zeroti on 2010-04-30
> **Julita said:**
> There is a memory test. By the way, exists [http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/) with a whole bunch of tools, but the OP does not want CDs, so...

If I were to use a boot cd, it would have to support ppc/openfirmware, but I'm sure your suggestion is helpful for people with more standard architectures. :)

---

### Post by robert.matear on 2010-04-30
May i ask what architecture your using? Sorry for being nosey. I still have a lot to learn, hence the curiosity. :-)

---

### Post by conradin on 2010-04-30
inside the grub boot sceen, there is a memtest option. PPC has many of the same tools to check its hardware, search the synaptic package manager for more specific types. GUIs, There might be some, but mostly, its terminal programs.

---

### Post by zeroti on 2010-05-01
> **robert.matear said:**
> May i ask what architecture your using? Sorry for being nosey. I still have a lot to learn, hence the curiosity. :-)

I have a powerbook G4. So it has Open Firmware instead of BIOS, and uses a PPC chip instead of an x86 one.

---

