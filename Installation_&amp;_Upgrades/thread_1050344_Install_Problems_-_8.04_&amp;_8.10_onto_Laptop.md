---
title: "Install Problems - 8.04 &amp; 8.10 onto Laptop"
date: 2009-01-25
forum: Installation &amp; Upgrades
---

### Post by skinumb2 on 2009-01-25
I'm having problems installing both 8.04 and 8.10 on my laptop and on my desktop. My first thought is memory issues and wonder if there is a minimum memory requirement (I can't find any references to answer that).

Both Ubuntu versions were downloaded as desktop ISO's and burned to CDr. I've tried various CDr brands and have burned at 1x, 10x and 48x using two burning programmes on my laptop burner.

The laptop is an EI Systems T1400 1.73ghz Celeron Dual Core, 1gb ram, Vista Home Premium SP1, SiS Mirage Graphics. I've carried out the various recommended pre-install routines, such as defrag. I set aside 15gb on the hd for ubuntu install.

Booting from CDr, the splash screen appears, the orange bar  clears the first three 'lozenges' and hangs variously on the dividing line or just beyond it. The orange bar gets to the same place when I try to check the disk for integrity (the disks pass integrity on the desktop).

Installing inside Windows works, but when I then try to boot Ubuntu I get to the same place as described above with the orange bar on the splash screen.

The desktop pc problem is described in another thread.

Any suggestions?

rich

---

### Post by Lesouteneur on 2009-01-25
This seems to be a big problem on HP computers. On my Compaq (manufactured by HP) laptop i set acpi=noirq as a boot option. Try it as livecd and post your results

---

### Post by skinumb2 on 2009-01-25
UPDATE:

Okay, I just got 8.10 installed and working on the desktop. It had installed okay until reboot when it would freeze on 'checking instalation'. I resolved this by enabling the safe display mode (or whatever it's called, the first option after normal start-up mode) and that did the trick. Installed, opening and seemigly fine. Looks nice too. My first Linux experience and surprisingly user friendly,intuitive and featured.

I'll see if I can find that option on the laptop.

rich.

---

### Post by skinumb2 on 2009-01-25
Okay, I tried installing from boot disc again, but it freezes before it is possible to enter any menu.

So I tried installing again inside windows, first in safe display mode. It froze at the following point:

[3684693] Processor Supports 8 Throttling States
ACPI Exception (processor core-0816) AE Not Found. Processor Devices not present [20070126]...
...then a further 5 similar lines.

So I next tried installing with 'ignore ACPI' mode, which worked.

Now I can boot into Ubuntu, but unlike on my desktop pc cannot see files inside the windows partition. That's a bummer.

Now to find out how to connect my wireless internet.

---

