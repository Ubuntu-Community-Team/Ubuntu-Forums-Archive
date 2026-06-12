---
title: "Unexplained boot problems"
date: 2008-08-14
forum: General Help
---

### Post by viherpeukalo on 2008-08-14
I'm running Hardy 8.04.1 with 2.6.24-20-generic kernel. About five times out of six boot hangs up (able to reboot by ctrl+alt+del or AltGr+SysRq+B) or the whole thing gets locked. 
Sometimes the system gets locked at bootsplash.
Sometimes the bootsplash disappears and the system seems to hang up at 'starting basic networking'
Sometimes the system hangs up at loading keymap
Sometimes the thing tries to start BusyBox but hangs up
Sometimes it starts looping an error message about some problem with processor not able to do something (can't remember exactly since that hasn't happend in a while)
Sometimes it hangs up at loading usb devices
Sometimes I'm able to boot the system through recovery mode, but sometimes that crashes too at one of the cases above.

I did have some problems earlier on with the new broadcom wireless card drivers, but they were solved.

help? ideas where to look at? thank you

---

### Post by cmnorton on 2008-08-15
First, look in your logs and the output of dmesg. See if there are any indicators there.

Then performing one change at a time, not many at once. For example, try changing things, like booting the kernel without a splash screen. Try booting into recovery mode and changing your graphics driver. Your description sounds like a graphics problem to me.

---

