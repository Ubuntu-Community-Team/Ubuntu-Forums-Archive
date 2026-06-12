---
title: "Brazilian keyboard 'forward slash' and 'question mark'"
date: 2010-01-28
forum: Hardware
---

### Post by Afrobrazil on 2010-01-28
Hey people,

I recently installed Ubuntu 9.10 on my Sony Vaio VGN-FZ25AE (A Brazil only model) and encountered the following issue:

My keyboard requires me to use Ctrl+Alt+Q for a forward slash and Ctrl+Alt+W for a question mark - these do not work at all on my current Ubuntu installation - works fine on Win 7.

Has anyone encountered this and if so - come across any solutions.

Tx.

---

### Post by drdanielfc on 2010-01-28
> **Afrobrazil said:**
> Hey people,

I recently installed Ubuntu 9.10 on my Sony Vaio VGN-FZ25AE (A Brazil only model) and encountered the following issue:

My keyboard requires me to use Ctrl+Alt+Q for a forward slash and Ctrl+Alt+W for a question mark - these do not work at all on my current Ubuntu installation - works fine on Win 7.

Has anyone encountered this and if so - come across any solutions.

Tx.

system>preferences>keyboard>layout
or you may want to create a key-shortcut that runs a script to type those letters? that would be a simple workaround

---

### Post by gnomeuser on 2011-03-25
This sounds like:

[https://bugs.launchpad.net/bugs/66774](https://bugs.launchpad.net/bugs/66774)

I have the exact same issue on Natty presently, I suspect the evdev driver might not be correctly setup for this.

I don't have the rights to reopen the bug though.

---

### Post by rmasoni on 2011-06-05
I also have the exact same problem. I installed Ubuntu 11.04 in my girlfriend's Sony Vaio today and she can't type ? or /. It uses the ctrl+alt modifiers in Windows, but that doesn't work in Ubuntu. All other Fn and NumLock secondary characters work. This is REALLY frustrating because these are very important characters.

Yeah, this keyboard design is absolutely moronic, but it's regrettable to have this issue in Ubuntu&#8230; I'll probably have to install Windows for her again and that sucks :mad:

[COLOR=Red]**IMPORTANT UPDATE (ISSUE SOLVED):**[/COLOR]

A friend figured this out: use **AltGr+Q** and **AltGr+W**. It is the right side Alt.

---

### Post by alicetc on 2011-07-17
OMG, thank you!!! This was driving me crazy! The AltGr+W here worked pretty well for "?" !

Cheers!

---

