---
title: "IBM 300PL Powerleap"
date: 2009-04-28
forum: Hardware
---

### Post by RealG187 on 2009-04-28
I have my IBM 300PL and I got a Powerleap CPU upgrade (I think it's a socket Pentium III 1.4 GHz on an adapter/riser card/cartridge that fits into slot 1 CPU).

When I boot the PC I get the error "A processor BIOS update cannot be found" and the BIOS says I have a 877 MHz processor installed. The XP system properties reports a 1400 MHz CPU as does CPU-Z (well 1390, but close enough).

Does this mean that Windows can bypass the BIOS limitation, even though the BIOS can't use all the MHz of the CPU, Windows can? (Cuz it's never than the BIOS, well actualy this BIOS is dated 2002 and XP is 2001, funny even the oldest Ubuntu is newer than XP).

How do I know if Ubuntu is utilizing the full potential of this CPU? I have a newer BIOS than the one on the Powerleap site, but the message won't go away.

---

### Post by RealG187 on 2009-04-28
bump

---

### Post by RealG187 on 2009-04-28
>      *-cpu
          description: CPU
          product: Intel(R) Pentium(R) III CPU family      1400MHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.11.1
          slot: CPU
          size: 866MHz
          capacity: 1GHz
          width: 32 bits
          clock: 133MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 mmx fxsr sse up
        *-cache:0

That's what sudo lshw gives me

---

