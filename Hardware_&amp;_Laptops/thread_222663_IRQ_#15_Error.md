---
title: "IRQ #15 Error"
date: 2006-07-25
forum: Hardware &amp; Laptops
---

### Post by rivera82falcon on 2006-07-25
Hey everyone! I'm pretty darn new to Linux and so far, I'm enjoying it very much. My school gave us Ubuntu to practice with and right now I am trying to install it onto my laptop.

Laptop Specs
IBM Thinkpad R30
Pentium III 700mhz
386MB RAM
40GB HDD
DVD-Rom

I recently updated the bios because I kept getting this error, and after reading around, this was the solution proposed. After updating, I ran the live cd again so I could install it but the same issue keeps coming up:

[xxxxxxx.xxxxxx] IRQ 15: nobody cared (try booting with the "irqpoll" option)
[xxxxxxx.xxxxxx] handlers
[xxxxxxx.xxxxxx] [<c0252040>] (ide_intr+0x0.0x200)
[xxxxxxx.xxxxxx] Disabling IRQ #15

After about a minute or so, the same thing pops up where the [xxxxxxx.xxxxxx] is a different number. How do I get around this so I can get Ubuntu installed on my laptop? I appreciate any help!

---

### Post by kaamos on 2006-07-25
Hello!

In the live cd boot screen there is an option "expert" or something like the in the bottom right corner. You can insert additional boot parameters there, so try typing "irqpoll" to the end of the line (without the quotes) and press enter.

Hope this helps.

---

### Post by rivera82falcon on 2006-07-25
F6: other options

I added it to the end line like you said and it booted up! Thank you VERY much for the help! 8) 

I'll definitely be back if I have other issues.

---

### Post by Funkey Monkey on 2007-08-21
Had the same prob and IRQPOLL fixed it for me. 
Thanks

---

