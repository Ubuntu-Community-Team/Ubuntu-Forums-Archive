---
title: "Suspend to RAM."
date: 2005-12-31
forum: Hardware &amp; Laptops
---

### Post by tbw on 2005-12-31
Hi,
I'm using a HP DV1331SE Centrino based laptop. Most features have worked flawlessly out of the box.

I am however having trouble with suspend to RAM.

I was reading the Linux ACPI howto and learned how to change the value on the proc filsystem to put it to sleep in RAM. When I opened the lid, the machine came up and immediately went through the shutdown process.


Any ideas? Places I can go to learn how to deal with this? Thanks.

TIm

---

### Post by Luzbel on 2005-12-31
Had the same issue on a Toshiba, haven't gone thru a correction yet. Have you managed to suspend it when the lid is closed? Or you need to suspend and the close the lid?

---

### Post by tbw on 2005-12-31
[QUOTE=Luzbel]Had the same issue on a Toshiba, haven't gone thru a correction yet. Have you managed to suspend it when the lid is closed? Or you need to suspend and the close the lid?[/QUOTE]

Apparently what needs to happen ist hat we need to echo mem  to the proc filesystem whent he ACPI event "lid close" happens -- I think. 

When I close the lid currently, it just locks the screen -- if I sleep it and then close the lid I have the shutdown issue.

---

### Post by Luzbel on 2006-01-01
Well, there's a tool ("acpid" AFAIR -remember-) you can use to manage ACPI events. I mean, you can configure it for the computer to sleep when you press X key, or when you press the power button, etc. I think a little configuration on this tool could avoid the shutdown thing. I tested it on my PC and it worked, but haven't tried on my lappy yet ;)

---

