---
title: "ThinkPad T43p: Breezy locks up battery power, Suspend issues, Hibernate issue."
date: 2006-02-19
forum: Hardware &amp; Laptops
---

### Post by JELaVallee on 2006-02-19
Hello all,

I've been using Ubuntu on this ThinkPad T43p since the last Hoary RC... Just recently did a full re-install with Breezy and ran into a few issues seemingly related to power management, but I'm having issues narrowing it down.

I'm running kernel version 2.6.12-10-686

I have acpi=off in my grub kernel boot params.  Not sure why... I didn't set it up that way myself.

Here are the issues I'm having:
1) Battery Power Crash - If I boot into the machine while it's on battery power the system works fine.  If I boot into the machine while it's on the AC adapter and then unplug the power cord, battery power works fine but within <30 seconds the system locks up.  I can Ctrl-Alt-Fx to other consoles but I can't login.  There is occasionally a kernel message burped to the console, but I' need to reproduce it and long-hand the message.  I'll post the results of such here.

2) Suspend Lockup - I can make the machine go to suspend from the System->Logout panel or from the Fn-F4 notebook key-combo.  It appears to suspend and the notebook begins flashing the "moon-hibernate" case light.  But I'm totally unable to get the machine to resume.  This is a total headache because closing the cover of the laptop has the same effect and then I need to hard reset to get the machine back.

3) Hibernate Not Recovering - I *just* resolved this one... Removing "splash" from my grub kernel params fixed this... I can live without the pretty splash screen if it means I can recover from hibernation.  Prior to this I'd get be able to restart from hibernate, but during the restore process, the system would just become unresponsive.

I'll post more as I find such here and at [http://www.thinkwiki.org](http://www.thinkwiki.org)

If anyone knows of solutions to any of these problems, please let me know.  I can also provide any logs or cat dumps that may help.

thanks,
cheers,
Etienne

---

### Post by mjg59 on 2006-02-20
Please remove acpi=off. APM support doesn't tend to work too well these days. Getting that message would be helpful, though.

---

### Post by JELaVallee on 2006-02-20
[QUOTE=mjg59]Please remove acpi=off. APM support doesn't tend to work too well these days. Getting that message would be helpful, though.[/QUOTE]

Thanks!  This and setting ACPI_SLEEP=true in /etc/default/acpi-support (as you recommended in a similar thread for at T30 user) did the trick.

Any idea why this install would have set the kernel param 'acpi=off' in my boot list (it was that way for all kernels 386 and 686 alike)?  Just wondering...

cheers,
Etienne

---

