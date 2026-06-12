---
title: "I can't run Ubuntu 7.10 in my LT HP Pavilion dv6220BR."
date: 2007-10-18
forum: Hardware &amp; Laptops
---

### Post by themeron on 2007-10-18
I make the dowload today about Ubuntu 7.10 and the cd is OK (I check in prompt of instalation).
But the program stop in all options of the boots.
It stop in the bar (left<=>right) and I don't know what's happen.
I need help!
Thanks folks!

Themeron

---

### Post by the_darkside_986 on 2007-10-18
How long did you wait? It may simply be taking a long time to do a specific task so you might want to just let it sit and wait even though it looks frozen. Sometimes when I have trouble booting an OS on a burnt CD, I have to shutdown the PC's power, wait a few seconds, and then try again.

Also it might be helpful to post your hardware specs, such as CPU, amount of main memory, graphics card, etc.

Good luck.

---

### Post by Ayuthia on 2007-10-18
You might try booting with noapic.  In order to access this, you will need to press F6 on the options screen and add noapic to the end of the line.

---

### Post by phr0ze on 2007-10-18
Try alt-f1 or alt-f2 (can't remember) when you choose to start/install ubuntu. This should show you what is happening when you boot. See where it is stopping and let us know.

---

### Post by thinkjones on 2007-10-22
I have the same problem with my HP Pavillion 6040Us machine.

Adding noapic solves this, it did with version 7.04 anyhow.

Thanks
Gene

---

### Post by themeron on 2007-11-14
Thank you all for the help!!
I will try with this option.
I installed in my desktop (intel p4 - 2,40Gz - 512 RAM) and was OK!
Now I want to install in my notebook HP Pavilion 6220br.
Good luck for all and see you soon.

hugs from Brazil

Themeron

---

### Post by dlfollmann on 2007-12-06
I have success using this on the kernel line: noapic nolapic nosmp pnpbios=off

After installing, because i have many system freezes, i have installed de -386 kernel, and now is the system good.

Good Luck

(sorry, my english is bad, i'm brazilian)

---

