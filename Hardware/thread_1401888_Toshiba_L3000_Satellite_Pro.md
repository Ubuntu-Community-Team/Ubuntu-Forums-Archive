---
title: "Toshiba L3000 Satellite Pro"
date: 2010-02-08
forum: Hardware
---

### Post by Pirada on 2010-02-08
Hello, I have just installed Ubuntu on my laptop (L3000) however I am having some issues with the fan.

I am aware this is a common problem and have been trying to figure out how to fix it but most forum threads on the topic are quite old and remain unsolved not to mention the fact that I just installed Ubuntu yesterday and I am having some trouble figuring out the instructions some threads give.

Anyway, the issue is as follows:


The laptop fan will not turn on no matter what the temperature is causing the laptop to overheat and shut off.

I have tried using  toshutils to turn on the fan but am told that toshiba_acpi is not present and I do not think my laptop model is supported by toshutils (However the website mentions the Phoenix Bios).

I have also found a state file in the /proc/acpi/fan/FAN folder but I am unable to change it to enable the fan and am unable to through the terminal.

However the fan _will_ turn on if I type in aciptool -s (can't remember the command right now, but it does put the laptop into a sleep mode however I can't awaken it.)

The Bios on the laptop is the InsydeH20 variant.

If anyone is able to help me or point me towards a website with a fix I would be grateful.

Also if you could try and simplify any explanations I would appreciate it as I am still learning how to do pretty much everything!

Thanks again.

---

### Post by Pirada on 2010-02-08
*Yes it is the acpitool -s command that activates the fan but still can't wake from sleep mode.

---

