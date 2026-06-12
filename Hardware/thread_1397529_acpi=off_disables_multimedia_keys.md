---
title: "acpi=off disables multimedia keys?"
date: 2010-02-03
forum: Hardware
---

### Post by agnes on 2010-02-03
Hi everyone,

when I upgraded the default 9.10 kernel to the 2.6.31-17 kernel,
I had issues with the suggested FGLRX graphics driver (ATI Mob. Radeon HD 3650),
so I added to that kernel in GRUB: "**noacpi acpi=off**" because then it works.

But now my multimedia keys don't work anymore, and they ALWAYS did with all ubuntu versions.
The keys are volume up, volume down, play, pause, stop.

The key **bindings** in System->Preferences->Keyboard Shortcuts are correct, but the keys just aren't **recognized** at all (no output in xev etc.).

So... I was wondering, has this to do with acpi being turned off?
Or is it a kernel bug?
[I]
$ acpi -V[/I] also does not give any output, is that normal?

(AFAIK I do have the necessary packages for multimedia keys to work.)

---

### Post by agnes on 2010-02-04
Well, just to answer myself: turns out I was correct in my assumption, because I managed to install the ATI driver this time (kudos to 9.10, in 9.04 it "just didn't work") and therefore removed "noacpi acpi=off" from the kernel boot, now:
- my multimedia keys work
- "acpi -V" outpouts info

---

