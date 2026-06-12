---
title: "Weird &quot;Exception&quot; Dialog While Booting"
date: 2010-01-20
forum: Hardware
---

### Post by Greenbean209 on 2010-01-20
So here is what happened. This was on my mom's computer that runs Windows XP, its a Dell with a Pentium processor. It crashed on her while she was working on some word file. We rebooted and the computer began to make a beeps about a quarter of a second apart and a clicking noise started (FYI pretty sure its not the fan). It ran past the dell logo and at some point before booting windows it displayed a dialog the had the title Exception. Im not sure if that was the only word... It displayed a couple of things with different labels like fs or cy or flags. Mostly there were number values attached to them, there werent any words I recognized. The noises were going on the whole time. We rebooted and everything was fine.

Since the malfunction dialog occured after the initial "hardware" boot up and before the Windows boot, I suspect it might have been a dialog about the harddrive.

Can any body tell me what this dialog might have been or what it may have meant?
Is my mom's harddrive on the brink?

Much thanks for any help.

---

### Post by AlexZaim on 2010-01-21
It MAY be (i'm making a huge guess) an XP error, or some other software that executed some bad instructions, making your pc to reboot and with invalid code segments/data segments.

You've mentioned about flags, yes there are such things in the processor. They are tiny bits of memory that carry information of the result of the last instruction executed.

A little bi of assembly:
```

cmp ax,3         ; means: compare the ax regester with the value 3 
jz next_label    ; means: jump if zero (the zero flag is set to 1) to "next_label"

;...

next_label:      ; continue executing

```

My recomandation is to swich from Xp. It's old. I'm not to sure about it's security measures. Maybe ubuntu instead?

---

