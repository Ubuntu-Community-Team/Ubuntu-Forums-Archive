---
title: "Slow Startup"
date: 2008-08-02
forum: Hardware
---

### Post by kentcb on 2008-08-02
Hi all,

I have an 8.04 installation on a new laptop. Everything works fine, but startup takes a lot longer than I'd expect. I have an old laptop also with 8.04 installed, and it boots faster!

One thing I've noticed is that there are a whole heap of startup messages, most of which are repeated. Does this mean that everything is being done twice?

I'm new to Ubuntu and linux in general, so I don't really have any ideas about where to start looking. I did enable concurrent booting since I have a dual core machine, but that didn't seem to improve anything.

Any ideas?

Thanks,
Kent

---

### Post by ajgreeny on 2008-08-02
Try booting without the usplash if you haven't already done so and it should tell you exactly where the hold-up is.  At the grub menu hit **e**  on the chosen line and then go to the kernel line that appears and hit **e** again.  Now delete the words **quiet** and **splash** to remove the usplash for that boot, hit return to use the edited line, then **b** to boot it.  Let us then know exactly where the stop occurs.

---

### Post by kentcb on 2008-08-03
Thanks for the reply ajgreeny. I removed the 'quiet' from the boot command but there was no 'splash' to remove. After that, the boot proceeded as normal - nothing appeared to be any different.

---

### Post by ajgreeny on 2008-08-03
You mean it was still slower than you expect?

---

### Post by kentcb on 2008-08-04
Yeah, that's what I mean. Startup was still exactly the same (slow) speed as previously.

---

### Post by gjoellee on 2008-08-04
check out the tweaks and stuff here at my home page [www.polishubuntu.co.nr](www.polishubuntu.co.nr)
here is the direct link: [http://www.polishubuntu.piczo.com/optimizeubuntu8.04forspeed/?cr=2#](http://www.polishubuntu.piczo.com/optimizeubuntu8.04forspeed/?cr=2#)
it helps for most people

---

### Post by her15t on 2008-08-04
I have same problem, mine booting time about 2 minutes
and from dmesg I got this error messages (hundred line)

[11204.779679] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.GFX0.DD03._BCM] (Node f7c51558), AE_NOT_FOUND
[11204.798318] ACPI Error (psargs-0355): [BRTW] Namespace lookup failure, AE_NOT_FOUND
[11204.798332] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.GFX0.DD03._BCM] (Node f7c51558), AE_NOT_FOUND
[11204.817005] ACPI Error (psargs-0355): [BRTW] Namespace lookup failure, AE_NOT_FOUND
[11204.817019] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.GFX0.DD03._BCM] (Node f7c51558), AE_NOT_FOUND

I think that error make my comp. slow at start up but don't know to fix.

---

### Post by kentcb on 2008-08-17
> **gjoellee said:**
> check out the tweaks and stuff here at my home page 

Thanks gjoellee. I applied all suggestions apart from auto login and swappiness and it is definitely faster. Strangely, I get a Kubuntu splash screen on boot even though I'm running Ubunutu :confused: Other than that, works perfectly!

---

### Post by Crafty Kisses on 2008-08-17
Try booting into verbose mode so you can see what part is taking so long.

---

