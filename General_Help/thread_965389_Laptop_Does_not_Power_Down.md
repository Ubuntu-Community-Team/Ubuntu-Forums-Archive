---
title: "Laptop Does not Power Down"
date: 2008-10-31
forum: General Help
---

### Post by lch503 on 2008-10-31
Hello
I am dual booting xp and ubuntu 8.04 and I have a problem at shutdown. The laptop starts to shutdown, gets to the ubuntu screen then the bar turns from orange to black as usual. The problem is that the bar turns completely black then nothing happens and i have to hold the power button to shutdown.
When i press ctrl-alt-f1 the output given is something like
Unable to free already free device (IRQ 20)
Can someone tell me how to fix this problem or find out the device that is causing it?
Thank you in advanced for the help.
If you need any more details please reply.

Leon

---

### Post by lch503 on 2008-11-01
Have upgraded to ubuntu 8.1.0
Same problem, but with no error like the IRQ as before
Shutdown bar goes orange to black and when the bar is completely black you can hear and see that the laptop tries to power off, (the hard drive stops) but the screen and cpu fan remain on and have to use power button to turn off.

Have tried the following at boot time:
acpi=force
acpi=force lapic

and

apm poweroff=1
in /etc/modules

I am a newbie to ubuntu so any help would be greatly appreciated.

Leon

---

### Post by lch503 on 2008-11-01
Just tried nolapic in the grub boot but doesn't work.

---

### Post by Rodney9 on 2008-11-01
I am having the same shutdown problem with my new desktop.

---

