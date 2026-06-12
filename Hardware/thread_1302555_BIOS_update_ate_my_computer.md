---
title: "BIOS update ate my computer"
date: 2009-10-27
forum: Hardware
---

### Post by mikeym on 2009-10-27
Hi,

The title is a little misleading because I had issues before the BIOS update it's just exacerbated them.

My computer was running fine (well occasional dumps into busybox during boot but typing reboot would get things going again) but I realised recently that my menu.lst hadn't been updated for quite a while and that I was running an old kernel (2.6.27-11) so I set the new one to boot (2.6.28-16). Once I booted the new kernel a new (I think) message appeared:

```
MP-BIOS bug: 8254 timer not connected to IO-APIC
```

It also started having vague unpredictable errors.

So to try and fix this I tried updating my BIOS to (ASUS 1205 for M2N4-SLI board). The message hasn't gone and now ubuntu wont boot. 

It loads slowly as far as the end of the splash progress bar and then drops into a low display with text saying 

loading acpi lodules [ok]
some other stuff.... [ok]
some of which fail for no apparent reason...like...
distcc error 102...
and it gets as far as....
bluetooth

and then hangs. 

Now if I follow the advice I found about the MP-BIOS message and dissable apic at boot with *apic=off* then it gives me a load of irq errors and tells me to try again with *irqpoll* boot flag. 

Once I've done that everything boots nicely except I no longer have any usb devices; mouse - dead, external harddrive - dead, scanner - dead.

Any help would be appreciated.

**[COLOR="Red"](edit)[/COLOR]** Not so nicely after all. Most things work well enough but for some reason my keyboard (ps2) wont register a keypress properly while moving my mouse (usb attachment to ps2).

seeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeityyyyyyyyyyyppppppedthwhilllllemmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmovingmymmmmmmmmmmmmmmmmmouse

:)

---

### Post by mikeym on 2009-10-27
I'm probably as well at this stage waiting a couple of days and seeing if karmic does any better on my system.

---

### Post by Iowan on 2009-10-27
I found [this]("http://www.linuxquestions.org/questions/linux-hardware-18/mp-bios-bug-8254-timer-not-connected-use-noapic-option-to-boot-591891/?") page - but it didn't sound too promising...

---

