---
title: "Advice with new system: Ubuntu hardware compatibility"
date: 2005-02-22
forum: Hardware &amp; Laptops
---

### Post by bungopolis on 2005-02-22
I'm building a brand new system with which I will be running Ubuntu.

I am planning to run a system with an AMD64 CPU, an NForce4 Ultra chipset mainboard, a GeForce 6600GT video card, and an EMU10K1 based Creative sound card (I doubt the onboard NForce4 audio will work).

Can anybody confirm that all of this should work? I plan to run the AMD64 in 32 bit mode becuase I want to run Cedega and play Windows games. Will I run into any difficulty running in 32 rather than 64 bit mode?

What sound card is suggested? I've heard lots of horror stories about buying the wrong card, so I want to make sure I get one supported.

Thanks for any advice.

---

### Post by kassetra on 2005-02-22
[QUOTE=bungopolis]I'm building a brand new system with which I will be running Ubuntu.

I am planning to run a system with an AMD64 CPU, an NForce4 Ultra chipset mainboard, a GeForce 6600GT video card, and an EMU10K1 based Creative sound card (I doubt the onboard NForce4 audio will work).

Can anybody confirm that all of this should work? I plan to run the AMD64 in 32 bit mode becuase I want to run Cedega and play Windows games. Will I run into any difficulty running in 32 rather than 64 bit mode?

What sound card is suggested? I've heard lots of horror stories about buying the wrong card, so I want to make sure I get one supported.

Thanks for any advice.[/QUOTE]

Here is the huge list of [supported hardware for ubuntu]("http://www.ubuntulinux.org/wiki/HardwareSupport").
(p.s. running an AMD64 in 32 bit mode to run games through a windows emulator is something *I* wouldn't touch with a ten-foot-pole)

---

### Post by bungopolis on 2005-02-22
[QUOTE=kassetra]running an AMD64 in 32 bit mode to run games through a windows emulator is something *I* wouldn't touch with a ten-foot-pole[/QUOTE]

Erm... why? Firstly, Cedega (a fork of Wine) is *not* an emulator (hence WINE Is Not An Emulator). Secondly, why would running an AMD64 in 32 bit mode create any difficulties whatsoever running 32 bit Windows binaries? The AMD64 was designed to be 100% backwards compatible with 32 bit binaries...

---

### Post by bungopolis on 2005-02-22
I will also point out that the Ubuntu hardware database is hardly complete and hardly useful for my purpose. It doesn't list compatible mainboard chipsets, which was my primary compatibility concern.

---

### Post by kassetra on 2005-02-22
[QUOTE=bungopolis]Erm... why? Firstly, Cedega (a fork of Wine) is *not* an emulator (hence WINE Is Not An Emulator). Secondly, why would running an AMD64 in 32 bit mode create any difficulties whatsoever running 32 bit Windows binaries? The AMD64 was designed to be 100% backwards compatible with 32 bit binaries...[/QUOTE]

I know wine says it's not an emulator, but it is. I run cedega myself. It *is* an emulator.  I've been using wine for years now.

Second, designed to be compatible with 32 bit binaries is one thing... designed to be compatible with 32 bit binaries running through an incomplete emulator is a whole different story. 

Also, bear in mind that designed to be compatible means that they tested the compatibility on a vanilla 32bit system. In fact, I can tell you with a very high degree of certainty that it was only tested on real windows systems that were only installed with microsoft applications. (Helps to know people in the chip business)

You can try it, and who knows it might just work wonders for you. But I tend to follow murphy's law on these kinds of things, and it just looks like you're heading straight for a pain.

If you want to run 32bit apps through an emulator, I would stick with a 32bit CPU.

---

### Post by kassetra on 2005-02-22
[QUOTE=bungopolis]I will also point out that the Ubuntu hardware database is hardly complete and hardly useful for my purpose. It doesn't list compatible mainboard chipsets, which was my primary compatibility concern.[/QUOTE]

You might be better off searching through the [linux compatible forums]("http://www.linuxcompatible.org/index.html").

---

### Post by bungopolis on 2005-02-22
Thanks for your help, that link is useful and I've found that all of my hardware should be compatible (someone on this forum has exactly that setup). But I have to insist that WINE and Cedega are most definitely *not* emulators. An emulator in this context refers to the emulation of hardware architecture. If WINE were an emulator, you would be able to run Windows x86 binaries on the PPC or other architecture, but you can't. VirtualPC is an emulator, QEMU is an emulator, MAME is an emulator. WINE is a compatibility layer which is why it is able to run Windows binaries at completely native speed (becuase they are running natively). It's all semantics and, but it matters in this case because there is absolutely no reason why an AMD64 chip should not be able to run x86 binaries running natively (as is the case with a WINE application) just because it also supports x86-64.

---

### Post by kassetra on 2005-02-22
[QUOTE=bungopolis]Thanks for your help, that link is useful and I've found that all of my hardware should be compatible (someone on this forum has exactly that setup). But I have to insist that WINE and Cedega are most definitely *not* emulators. An emulator in this context refers to the emulation of hardware architecture. If WINE were an emulator, you would be able to run Windows x86 binaries on the PPC or other architecture, but you can't. VirtualPC is an emulator, QEMU is an emulator, MAME is an emulator. WINE is a compatibility layer which is why it is able to run Windows binaries at completely native speed (becuase they are running natively). It's all semantics and, but it matters in this case because there is absolutely no reason why an AMD64 chip should not be able to run x86 binaries running natively (as is the case with a WINE application) just because it also supports x86-64.[/QUOTE]

Hey, whatever makes you happy.

---

### Post by fackamato on 2005-03-14
[QUOTE=kassetra]I know wine says it's not an emulator, but it is. I run cedega myself. It *is* an emulator.  I've been using wine for years now.

Second, designed to be compatible with 32 bit binaries is one thing... designed to be compatible with 32 bit binaries running through an incomplete emulator is a whole different story. 

Also, bear in mind that designed to be compatible means that they tested the compatibility on a vanilla 32bit system. In fact, I can tell you with a very high degree of certainty that it was only tested on real windows systems that were only installed with microsoft applications. (Helps to know people in the chip business)

You can try it, and who knows it might just work wonders for you. But I tend to follow murphy's law on these kinds of things, and it just looks like you're heading straight for a pain.

If you want to run 32bit apps through an emulator, I would stick with a 32bit CPU.[/QUOTE]


Redicilous. Athlon64 is as compatible with ANY 32bit x86 software as any Intel P4 or such. Or AMD K7.

**Edit**: I don't mean to sound disrespectful. ;)

---

### Post by Boomstickz on 2005-03-14
Yeah.... I run a AMD 64 3200+ with a Nforce 3 motherboard, and it works perfect in 32-bit mode, but I run 64-bit for the speed the speed gain. However its still awesome in 32-bit mode as well. Whoever this guy is that said it, he doesn't know much about the AMD 64 processor being the first 32 bit/64 bit compatible processor ;) I suggest you read up on the processor, its quite impressive

---

