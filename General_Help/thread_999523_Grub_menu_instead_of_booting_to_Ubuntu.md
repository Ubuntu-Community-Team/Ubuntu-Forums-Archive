---
title: "Grub menu instead of booting to Ubuntu"
date: 2008-12-01
forum: General Help
---

### Post by awesome nick on 2008-12-01
Hi 2 all)) Need help

I've got kinda problem with my Ubuntu 8.10/
After having done some work in Windows XP I tried to boot into my Ubuntu, but instead of booting the OS I was shown a grub menu.

What just has gone wrong and what to do now?

upd: and now under Windows i see no partition where my Ubuntu (wubi-installed) is 0_o I used to have 4 partiotions but now there are only 2 ov them((

---

### Post by bapoumba on 2008-12-02
Moved to Wubi, and bump :)

---

### Post by Jammanuser on 2008-12-02
> **awesome nick said:**
> Hi 2 all)) Need help

I've got kinda problem with my Ubuntu 8.10/
After having done some work in Windows XP I tried to boot into my Ubuntu, but instead of booting the OS I was shown a grub menu.

What just has gone wrong and what to do now?

upd: and now under Windows i see no partition where my Ubuntu (wubi-installed) is 0_o I used to have 4 partiotions but now there are only 2 ov them((

could u please be more specific? what did the grub menu say? was it by any chance a "crc error" and then on next line "system halted" message?

if so, then i think that i have some advice to give... ;)

---

### Post by ago on 2008-12-03
> **awesome nick said:**
> 
What just has gone wrong and what to do now?
It could be that the drive where you installed to is not accessible at boot time.
If you press the insert key rapidly at boot you will have more info. Post here what you see.

> upd: and now under Windows i see no partition where my Ubuntu (wubi-installed) is 0_o I used to have 4 partiotions but now there are only 2 ov them((
Wubi does not create or install in a partition, but inside a file. The partition table is untouched.

---

### Post by Gillette on 2008-12-06
I've had the same experience. Any solutions?

---

### Post by Jammanuser on 2008-12-06
> **Gillette said:**
> I've had the same experience. Any solutions?

As i said to the original poster...what did ur Grub menu say when it stopped? ;)

Cheers! :)

-jammanuser

:D

---

### Post by Gillette on 2008-12-06
Here is what the screen says:

GRUB4DOS 0.4.4 2008-10-27, MEMORY: 639K / 478M, CodeEnd: 0x42910
[Minimal BASH-like line editing is supported. For the first word, TAB
lists possible command completions. Anywhere else TAB lists the possible
completions of a device/filename. ESC at any time exits.]

grub>

---

### Post by Jammanuser on 2008-12-06
> **Gillette said:**
> Here is what the screen says:

GRUB4DOS 0.4.4 2008-10-27, MEMORY: 639K / 478M, CodeEnd: 0x42910
[Minimal BASH-like line editing is supported. For the first word, TAB
lists possible command completions. Anywhere else TAB lists the possible
completions of a device/filename. ESC at any time exits.]

grub>

Same answer that i posted in ur own thread! ;)

Cheers! :)

-jammanuser

:D

---

### Post by ago on 2008-12-06
> **Gillette said:**
> Here is what the screen says:

GRUB4DOS 0.4.4 2008-10-27, MEMORY: 639K / 478M, CodeEnd: 0x42910
[Minimal BASH-like line editing is supported. For the first word, TAB
lists possible command completions. Anywhere else TAB lists the possible
completions of a device/filename. ESC at any time exits.]

grub>

[https://wiki.ubuntu.com/WubiGuide#Cannot%20boot%20into%20Ubuntu](https://wiki.ubuntu.com/WubiGuide#Cannot%20boot%20into%20Ubuntu)

---

