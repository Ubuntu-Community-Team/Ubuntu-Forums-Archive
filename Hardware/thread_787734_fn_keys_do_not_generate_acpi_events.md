---
title: "fn keys do not generate acpi events"
date: 2008-05-09
forum: Hardware
---

### Post by eidam655 on 2008-05-09
hello,

i have a problem with my notebook, ASUS F2Hf. in windows, the Fn+F5 and Fn+F6 key combinations successfully turn the display brightness down / up.

the thing is, that they do not work under my Ubuntu (currently 8.04). they do not even generate ACPI events; they stay unrecognized (we could say?).

but, when running

```
sudo /etc/acpi/video_brightnessdown.sh
```

and

```
sudo /etc/acpi/video_brightnessup.sh
```

the display brightness turns down / up.

however, when doing only 'sudo acpi_fakekey $KEY_BRIGHNTESSDOWN', no reaction. the same with $KEY_BRIGHNTESSUP.

does anyone have a clue where the problem can be?

thank you for replies.

EDIT: just to be complete - windows and Ubuntu behave inversely, which means that in Ubuntu, i can use the Fn+F10 to F12 keys (which correspond to volume mute, volume up & volume down) and i cannot use them in windows. however, on WIN i can turn down/up the display brightness, but i am unable to do so in Ubuntu.

and one last thing to mention: when i am at the GRUB loading screen, the brightness keys work. i haven't tried the volume keys, but as there are no sounds playing at the booting time, i do not really have an option to do so.

again, thanks for replies.

---

### Post by sdennie on 2008-05-09
When you press the Fn keys that don't work, have you checked the output of "dmesg" from a terminal afterwards?  It usually tells you information about keys you've pressed that the system doesn't recognize.  Unfortunately, all the keys on my laptop are recognized so I can't say if feeding the key codes from dmesg into acpi-fakekey will help but, it might be worth trying.

---

### Post by eidam655 on 2008-05-09
unfortunately,

i do not know what to search for in the 'dmesg' output. however, there isn't even much said; only bunch of

```
[12480.500274] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.SBRG.EC0_._Q0E] (Node de820e88), AE_NOT_FOUND
[12480.647062] ACPI Error (psargs-0355): [\_SB_.PCI0.P0P2.VGA_.LCDD] Namespace lookup failure, AE_NOT_FOUND
[12480.647073] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.SBRG.EC0_._Q0E] (Node de820e88), AE_NOT_FOUND
[12480.774289] ACPI Error (psargs-0355): [\_SB_.PCI0.P0P2.VGA_.LCDD] Namespace lookup failure, AE_NOT_FOUND
[12480.774301] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.SBRG.EC0_._Q0E] (Node de820e88), AE_NOT_FOUND
[12480.970034] ACPI Error (psargs-0355): [\_SB_.PCI0.P0P2.VGA_.LCDD] Namespace lookup failure, AE_NOT_FOUND
[12480.970045] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.SBRG.EC0_._Q0F] (Node de820ea0), AE_NOT_FOUND
[12481.121796] ACPI Error (psargs-0355): [\_SB_.PCI0.P0P2.VGA_.LCDD] Namespace lookup failure, AE_NOT_FOUND
[12481.121807] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.SBRG.EC0_._Q0F] (Node de820ea0), AE_NOT_FOUND
[12481.273426] ACPI Error (psargs-0355): [\_SB_.PCI0.P0P2.VGA_.LCDD] Namespace lookup failure, AE_NOT_FOUND
[12481.273437] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.SBRG.EC0_._Q0F] (Node de820ea0), AE_NOT_FOUND

```

things...

then the last message is about the disconnection of my mouse. after perssing several times the keys that do not work and seeing the dmesg ouput again, i do not see any changes; the last line still informs about the mouse disconnection.

any other ideas, what could be wrong?

EDIT:
hah... i just found that only the upper 5 keys does not output anything. after a sequence of Fn+F5 presses i again get these messages.

Fn+F5, and Fn+F6 outputs these line-pairs respectively:

```
[19545.402548] ACPI Error (psargs-0355): [\_SB_.PCI0.P0P2.VGA_.LCDD] Namespace lookup failure, AE_NOT_FOUND
[19545.402559] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.SBRG.EC0_._Q0E] (Node de820e88), AE_NOT_FOUND
[19545.729236] ACPI Error (psargs-0355): [\_SB_.PCI0.P0P2.VGA_.LCDD] Namespace lookup failure, AE_NOT_FOUND
[19545.729247] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.SBRG.EC0_._Q0F] (Node de820ea0), AE_NOT_FOUND

```

---

### Post by sdennie on 2008-05-09
It looks like the keys are registering but your DSDT is buggy and so it's generating ACPI errors instead of adjusting the brightness.  You could see if there is a BIOS update for your machine or, alternatively, try to fix your DSDT.  It's not trivial to do but, it might fix your problem.  [This]("http://gentoo-wiki.com/HOWTO_Fix_Common_ACPI_Problems") looks like a decent guide.

---

### Post by eidam655 on 2008-05-09
wow :)

hmm.. i do not understand the second article / i find it too difficult :D

do you think that the BIOS flash would really solve the problems? because, to tell the truth, i have experience with flashing bios only on desktop computers, and only with user-friendly interface through Windows :D

is there any easy and relatively safe way to do this also on the laptop?

thank you.

---

### Post by sdennie on 2008-05-09
It might help but, there is no way for me to be positive.  You'd have to look to see if any updates are available and if they list that your problem is fixed.

---

