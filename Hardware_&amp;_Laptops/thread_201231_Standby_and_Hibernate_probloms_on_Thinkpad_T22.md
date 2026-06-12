---
title: "Standby and Hibernate probloms on Thinkpad T22"
date: 2006-06-21
forum: Hardware &amp; Laptops
---

### Post by WBuik on 2006-06-21
I recently installed Xubuntu 6.06 onto a IBM Thinkpad T22.  Unfortunatly, I can't get the standby and hibernate functions to work correctly.  I have tried a few things but I'm not really sure of what I'm doing.  I have tried every combination of apm=on/off acpi=on/off and that has had no effect, though it did make it fail in different ways.

When only apm is enabled the hibernate function does literaly nothing, and sleep just turns off the screen, I can still here the processor fan.
When acpi is enabled, the sleep function puts the computer to sleep, but then nothing wakes it up.  Even after forcing it to shut off by holding the power butten the computer will not turn back on until AC and battery power are removed and replaced.  Hibernate causes it to hang at a blank screen.

I checked if it had the ibm-acpi module running and it did, but it still doesn't respond to the IBM hot keys either.

It is running kernel 2.6.15-25, and is a fresh install, so I assume I just haven't configured something.  Does anyone know how to get this running?

I don't know if this is useful, but I also had similar probloms with the Breezy Badger beta awhile ago.

Thanks in advanced.
-WBuik

---

### Post by alanphil on 2006-06-21
In Gnome, suspend is not working on my Thinkpad x30 either. This was broken during the last week after applying updates. The odd thing is that I can get suspend to work if I run XFCE (another window manager) instead of Gnome. 

I've read posts that blame the suspend issue on the latest kernel, but I'm running the previous kernel and have the suspend problem. It seems like it is more likely a problem with Gnome (which had a number of updates over the last week). :roll:

---

### Post by WBuik on 2006-06-21
Interesting, Xubuntu runs XFCE, but then again I never was able to get it working with the regular Gnome version either when Daper was in beta.

---

### Post by Kimmo_S on 2006-07-05
Thinkpad T22 here, with BIOS upgraded to newest version, that is 1.12 and Ubuntu 5.10 upgraded to 6.06 - that means regular Gnome. When pressing Fn+F12, there is some HD activity for a while.  Then the screen goes blank and the moon symbol at the base of the display starts blinking.  HD does not spin down, and CPU fan keeps running.  There is no way to wake up the system.  The machine must be switched off using the power button and then back on.

One must be logged in to have something happen with Fn+F12.  If on the login screen, the keypress is ignored.  Undocking the machine (from a simple port replicator), Fn+F12 made it sleep (screen went black but HD kept spinning and CPU fan running) but after a couple of seconds (about 5) the backlight turns on and after some more seconds, the machine asks for a password.  On wakeup there is "stopping tasks failed (1 tasks remaining)" on the logging virtual console (VT12).

Fn+F4 does the exact same thing, except that there is no HD activity before the screen goes blank.

The BIOS upgrade is a "just in case" measure, meaning it did not help with anything. ThinkWiki has some instructions for doing it, but one should also be aware of the real danger of making the machine totally unusable if something fails while doing it.

---

### Post by veebis on 2006-09-12
Same exact scenario as WBuik's initial post...

With acpi, Suspend initiates just fine, but will not wake. Hard crash, won't even restart until AC & battery removed/reset.

With apm ("acpi=off apm=on noacpi"), Suspend blanks screen briefly, kicks on screensaver for a second, then asks for password to reenter. Doing so gets me back to a desktop that soon crashes (unresponsive to clicks).

Thinkpad T22, latest Dapper 6.06.1

I'd REALLY like to be able to suspend this puppy... Any fresh insights would be much appreciated!

Thanks,
-Vb

PS: Also, any wisdom to help my MadWIfi-empowered Atheros AR5212 mini-PCI 802.11abg connection frickin' STAY UP once it connects (it does, but drops out) would be great, too (ndiswrapper doesn't help; driver that works in Win2K doesn't work in Ubuntu)...

---

### Post by trubblemaker on 2006-09-22
don't have a think pad but I'm working on this issue for my machine, there is two area's that I've come across so I hope this helps, Google suspend2 their is a project that might help you out.  Also check your synaptic for hibernate, a package that you need to download to enable hibernate, so it says in the description.  I haven't gotten any farther, installing it but it might help ya'll 


Cheers

---

### Post by xyz on 2006-09-23
[Suspend/Hibernate for any Computer]("http://www.linux.com/article.pl?sid=06/05/24/1716222")
This here did it for me (Toshiba Satellite A 40) and the explanation says it ought to wor on any computer. Hopefully it does the trick for you.
Let us know.

---

### Post by trubblemaker on 2006-09-25
Great website for those that are starting out, or haven't done any leg work yet to get suspend or hibernate going.  It's really basic but will be helpful for others.  It doesn't help me at all.

---

### Post by alarichall on 2006-09-27
I've only had Ubuntu (or any sort of Linux) for a few days. Having got to the login screen on my T22, I unwisely went to options and thought 'hmm, I wonder what happens if I click "suspend"?' Now I can't get my computer to wake up at all: it just sits doing nothing. Any hints as to how I can get it to wake up again?

---

### Post by trubblemaker on 2006-09-27
did you try the power button?  Some computer's need you to punch the power button.  

Alternatively if it wasn't plugged in, the battery may have died so plug the computer in first.

---

### Post by alarichall on 2006-09-27
Thanks, Trubblemaker. Yeah, I'd tried the power button and had power.

Actually, I have now fixed the problem by unplugging and taking the battery out. I left the machine for an hour, put everything back, and then it started okay--I'm using it now.

Guess I just won't try going on standby again...

---

