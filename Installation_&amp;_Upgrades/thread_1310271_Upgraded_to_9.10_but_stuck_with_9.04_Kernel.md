---
title: "Upgraded to 9.10 but stuck with 9.04 Kernel"
date: 2009-11-01
forum: Installation &amp; Upgrades
---

### Post by Zilioum on 2009-11-01
I'm stuck with this weird problem and its really annoying since it makes it impossible to use my notebook.
I just upgraded it from 9.04 to 9.10. The upgrade process worked fine, and my notebook rebooted. Thats when the problems started:
[LIST]
[*]GRUB boots from the latest 9.04 Kernel. No 9.10 kernel anyware to be seen.
[*]I get the 9.04 loading bar, which after a few seconds is half way overlapped by the new 9.10 boot-up screen.
[*]When I finally reach the GNOME desktop I'm beeing asked wether I want to "update standard folders to current language" because supposedly the system language changed (it did not!)
[*]The desktop looks like 9.10, new icons etc.
[*]My touchpad doesnt work (Its a VAIO, I saw a thread with a fix for it). Maybe it helps to figure out the problem...
[*]I also get a box which tells me that I have "incomplete language support".
[*]Keyoard still works, so im able to open a terminal.
[*]I restarted via terminal, and the shutdown screen was the correct 9.10 one.

[/LIST]

I have a feeling that the language thing and the weird 9.04 "Zombie Kernel" are two different issues. 
During the upgrade process I said that I wanted to keep my old menu.lst file. Do I need to add the new 9.10 kernel manually?
I rebooted a few times, and sometimes after I leave my notebook doing nothing, the screen turns black and I get a flashing _ in the top-left corner.
Help would be very appreciated, especially with the kernel problem.

Cheers

---

### Post by renkinjutsu on 2009-11-01
yup, you'll have to update your menu.lst manually

or you can update to GRUB2 if you're not already using it
click [here]("https://wiki.ubuntu.com/Grub2") for a guide

---

### Post by Zilioum on 2009-11-01
That did it. I installed grub2, following the instructions on the link you posted. Everything works fine again now (even the touchpad!)
Thank you very much!

---

