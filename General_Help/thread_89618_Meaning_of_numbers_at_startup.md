---
title: "Meaning of numbers at startup?"
date: 2005-11-13
forum: General Help
---

### Post by grendel_khan on 2005-11-13
In dmesg (seen at bootup), there are lots of numbers. (Bolded below.) What do they mean? The last Linux setup I had before this one didn't have them. It also says something about "audit" starting up. What's that?

The numbers I'm talking about are the bolded ones below:

```
**[4294667.296000]** Linux version 2.6.12-9-386 (buildd@rothera) (gcc version 3.4.5 20050809 (prerelease) (Ubuntu 3.4.4-6ubuntu8)) #1 Mon Oct 10 13:14:36 BST 2005
**[4294667.296000]** BIOS-provided physical RAM map:
**[4294667.296000]**  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
**[4294667.296000]**  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserve
```

Thanks!

---

### Post by mrcbrown on 2005-11-13
[QUOTE=grendel_khan]In dmesg (seen at bootup), there are lots of numbers. (Bolded below.) What do they mean? The last Linux setup I had before this one didn't have them. It also says something about "audit" starting up. What's that?

The numbers I'm talking about are the bolded ones below:

```
**[4294667.296000]** Linux version 2.6.12-9-386 (buildd@rothera) (gcc version 3.4.5 20050809 (prerelease) (Ubuntu 3.4.4-6ubuntu8)) #1 Mon Oct 10 13:14:36 BST 2005
**[4294667.296000]** BIOS-provided physical RAM map:
**[4294667.296000]**  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
**[4294667.296000]**  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserve
```

Thanks![/QUOTE]


That's just the address space your bios has, it's a range of the ram sections - more really technical response I could Google I'd imagine, but I have had the same info with installs of Gentoo, Fedora, and Ubuntu - nothing to worry about.

---

### Post by grendel_khan on 2005-11-13
No, I meant the ones on the left; the [4294667.296000] and such. They're present through at least most of the dmesg output. (As far as I scrolled down while looking for hardware information, that is.)

---

### Post by Zwack on 2005-11-13
Well, I've done some poking around, and they're not coming from dmesg which means that they are probably being put into the kernel log buffer by the kernel itself.

This is the point at which I start thinking that reading the kernel source isn't what I want to be doing this Sunday.  They do look like some form of address information though.

I hope that this helps a bit.

Z.

---

### Post by az on 2005-11-13
That is the system clock.

---

