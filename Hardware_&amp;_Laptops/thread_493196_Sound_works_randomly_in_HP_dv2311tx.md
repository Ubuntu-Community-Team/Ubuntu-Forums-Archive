---
title: "Sound works randomly in HP dv2311tx"
date: 2007-07-05
forum: Hardware &amp; Laptops
---

### Post by khawk on 2007-07-05
Hello everyone

I couldnt find this topic in the forum so I apologize if its being repeated.

I have HP Pavilion 2311tx laptop with the following specs:

Card: HDA Intel
Chip: Conexant CX20549 (Venice)

I am running Ubuntu 7.04 and here is the output of system tools
>cat /proc/asound/cards
      0 [Intel          ]: HDA-Intel - HDA Intel
                            HDA Intel at 0xd6400000 irq 23
>tail -2 /proc/asound/oss/sndstat
     Mixers:
     0: Conexant CX20549 (Venice)
>asoundconf list
     Names of available sound cards:
     Intel

The problem is that sound works randomly i.e. sometime sound works on switching on the laptop and sometimes it does not. I have checked whether everything in mixer to make sure things are unmuted.

I am not sure whats wrong and why I get sound randomly?

Ciao
khawk

---

### Post by khawk on 2007-07-06
Could someone please help?

Thanks
khawk

---

### Post by khawk on 2007-07-09
This [http://ubuntuforums.org/showthread.php?t=455147](http://ubuntuforums.org/showthread.php?t=455147)
seems to have resolved the problem but will make sure thoroughly. But surely it has solved other problem in which sound was coming of from both speakers and headphones.

Ciao
khawk
[www.i-flux.net](www.i-flux.net)

---

### Post by khawk on 2007-07-11
ok I have figured out why the sound card works occassionaly. I have dual boot system with Windows XP and Ubuntu 7.04. Whenever I switch to XP and then boot to Ubuntu, sound does not work even if you restart the system.
The trick is to reboot the system in Ubuntu, while your power cord is disconnect and laptop is running on battery. Seems something like ACPI bug.

Ciao
khawk
[www.i-flux.net](www.i-flux.net)

---

