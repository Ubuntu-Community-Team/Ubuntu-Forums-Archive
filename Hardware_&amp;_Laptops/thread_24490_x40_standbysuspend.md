---
title: "x40 standby/suspend"
date: 2005-04-07
forum: Hardware &amp; Laptops
---

### Post by kabanta on 2005-04-07
I'm having trouble with suspend/resume on an IBM Thinkpad x40 with Hoary.

Hitting FN-F4 will put it into suspend mode (as will closing the lid for more than a few seconds), but hitting FN alone (and various other key-combinations I tried) will not get it to resume. Rather, I get some on-screen text that begins with something of the form "Welcome back to C".

So, if my laptop goes into suspend mode, I basically have to reboot.

I do have the thinkpad-x49-support utility loaded ("suspend/resume should just work with no configuration"). And otherwise, most of the other laptop features work just fine.

I've seen lots of discussion/debates about this issue of suspend/resume for laptops using linux, but nothing conclusive.

Any suggestions?

thanks.

---

### Post by Manuel Siggen on 2005-04-07
[QUOTE=kabanta]I'm having trouble with suspend/resume on an IBM Thinkpad x40 with Hoary.

Hitting FN-F4 will put it into suspend mode (as will closing the lid for more than a few seconds), but hitting FN alone (and various other key-combinations I tried) will not get it to resume. Rather, I get some on-screen text that begins with something of the form "Welcome back to C".

So, if my laptop goes into suspend mode, I basically have to reboot.

I do have the thinkpad-x49-support utility loaded ("suspend/resume should just work with no configuration"). And otherwise, most of the other laptop features work just fine.

I've seen lots of discussion/debates about this issue of suspend/resume for laptops using linux, but nothing conclusive.

Any suggestions?

thanks.[/QUOTE]
 I'm using Hoarx Preview Release (fresh install, upgrade from Warty didn't work so good), and I have now suspend-to-ram working nicely. 

Note that I had to uncomment the ACPI_SLEEP=true line in /etc/default/acpi-support to allow it. In same file, I also had to add modules e1000 and ipw2100 to the MODULES line in order to get network interfaces working on resume.

Hope it helps.

---

### Post by closure on 2005-04-07
i am using an old gateway solo 9300 and i have similar problem i have set it up to where it does not suspend at all as i can not get it back up. though i still do not know how to make it not suspend when i close the lid. is the line above stating how to do that?

---

### Post by kabanta on 2005-04-07
[QUOTE=Manuel Siggen]I had to uncomment the ACPI_SLEEP=true line in /etc/default/acpi-support to allow it. In same file, I also had to add modules e1000 and ipw2100 to the MODULES line in order to get network interfaces working on resume.[/QUOTE]
Hi Manuel,

Thanks for the tip. The /etc/default/acp-support file looks promising. Unfortunately, the solution you describe did not work for me. Same behavior as before. (This is really a problem as it means I cannot close the lid on the laptop when running on battery only.)

How do you get your laptop to resume? Do you just hit the FN key once? or?

thanks.

---

### Post by hyperboloid on 2005-05-31
> Originally Posted by **kabanta**:
[I]I'm having trouble with suspend/resume on an IBM Thinkpad x40 with Hoary.

Hitting FN-F4 will put it into suspend mode (as will closing the lid for more than a few seconds), but hitting FN alone (and various other key-combinations I tried) will not get it to resume. Rather, I get some on-screen text that begins with something of the form "Welcome back to C".

So, if my laptop goes into suspend mode, I basically have to reboot.

I do have the thinkpad-x49-support utility loaded ("suspend/resume should just work with no configuration"). And otherwise, most of the other laptop features work just fine.

I've seen lots of discussion/debates about this issue of suspend/resume for laptops using linux, but nothing conclusive.[/I]


I'm having exactly the same problem with a newly installed Hoary on an IBM Thinkpad T41. Suspend works just fine (after being enabled by turning it on in /etc/default/acpi-support) but the resume freezes the system and I have to power off and on again. Sigh...

---

