---
title: "[SOLVED] unable to shutdown"
date: 2008-11-25
forum: General Help
---

### Post by sandy8925 on 2008-11-25
Hi,

I'm running Ubuntu 8.10 on a desktop and I'm not able to shut it down properly. When I click shutdown it does all the normal shutdown stuff. I see the splash screen with the bar shrinking and then the numlock,capslock,scrolllock indicators on the keyboard flash and then go off. The splash screen still remains and I know it's not off yet because the power indicator on the CPU is still on. 

I had actually added the options:

pci=noacpi 
acpi=off

to the menu.lst file and I guess that one of these (or both) is the reason that it's not shutting down fully. Reminds me of the time when I used Windows 95 and it would say 'It's safe to turn off your computer now'.

So can anyone help me ?

---

### Post by Bucky Ball on 2008-11-25
Try removing one of those from the menu.lst and see if you can shut down. If not, add it back and omit the other. That way you would know for sure if it was that change causing this problem.

Also, when you boot to the recovery kernel, does it throw any errors and does it shutdown okay from that?

---

### Post by sandy8925 on 2008-11-25
I never booted the recovery kernel. I use it in the normal way.

---

### Post by Bucky Ball on 2008-11-25
You need to pull the commands from the menu.lst to be certain it is that but boot into recovery kernel to do it and see if that makes a difference also. Then boot as normal and try to shut down.

---

### Post by CatKiller on 2008-11-25
Having the computer turn off once it's shut down is a function of [ACPI]("http://en.wikipedia.org/wiki/ACPI"). Since you've turned ACPI off, your computer won't turn off when you shut it down.

If you want your computer to turn itself off, you'll need to re-enable ACPI.

It's not a coincidence that it reminds you of Windows 95; the ACPI spec was first written in 1996.

---

### Post by sandy8925 on 2008-11-28
I removed the acpi=off option and it shuts down properly now.

Thanks a lot!

---

