---
title: "Ubuntu shuts down - suddenly and randomly!"
date: 2010-08-04
forum: Hardware
---

### Post by jedimattk on 2010-08-04
This morning, I installed Ubuntu 10.04, wiping my hard drive completely clean of all things Windows. This afternoon, while enjoying my lovely new Linux laptop, I had an unexpected shutdown forced upon me twice. No warning or anything! One moment I was playing around, setting up Ubuntu to my liking; the next I was staring at a black screen on a rapidly-cooling laptop, all power buttons and indicator lights off.

My first thought was overheating, but while my computer does run rather hot, there's nothing to indicate that it overheated. I went into var/log/messages to see if there were any telling errors around that time, and this is what was happening both times it shut down:

Clocksource tsc unstable (delta = 65876015 ns)

I haven't messed around with overclocking my processor or anything like that, so I don't have any clue what this means. All I know is that it's seriously disturbing my Ubuntu mojo! ;)

---

### Post by jedimattk on 2010-08-04
Bump. It's done the random shut-down thing twice more since the original post, and "Clocksource tsc unstable" is invariably the cause. I've been googling around and found a common suggestion to add something to the boot parametres, but I don't know how to do this!

---

### Post by JBAlaska on 2010-08-05
"Clocksource tsc unstable" usually happens on laptops with cpu frequencing scaling, you should be able to turn that off in your BIOS.

If Ubuntu runs fine after that, you know that's the problem.

You can either leave it off or use a kernel option to fix it, to do this highlight the kernel you want to modify in grub and hit the e key, add your option to the string and continue to boot.
There seem to be several options that may work including,
clocksource=hpet or clocksource=acpi_pm.

---

