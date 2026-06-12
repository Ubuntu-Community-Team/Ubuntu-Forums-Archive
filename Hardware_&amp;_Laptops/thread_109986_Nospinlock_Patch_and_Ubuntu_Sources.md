---
title: "Nospinlock Patch and Ubuntu Sources"
date: 2005-12-29
forum: Hardware &amp; Laptops
---

### Post by KEMitchell on 2005-12-29
Having debugged the DSDT for my Acer laptop, i am now capable of checking my battery status as would be expected for a normal laptop battery.

However, as predicted in the README for the SBS project, the spinlocking of the reading of the battery through the SMBus causes lost interrupts... lost keystrokes in particular. The keyboard still works, but the problem is just persistent enough to make it a major usability issue.

Fortunately, the SBS project provides patches for the 2.6 branch kernel to implement a semaphore in place of a spinlock in the ACPI driver, alleviating the lost interrupt problem (I'm told).

The problem lies in the application of the patch against the ubuntu 2.6.12 tree, which involves a number of patches to the laptop and acpi-related files already. Simply put, the patch does not apply cleanly to the already patched ubuntu .../linux/drivers/acpi/ec.c, with numerous blocks failing.

I am attempting to reconcile the patches for use in a single ec.c which i can use to build a kernel package which overcomes the spinlock issue. My concerns lie in the fact that while i've had a great deal of practice diff'ing and patch <'ing, i'm not all that familiar with the kernel driver code or the ubuntu patches themselves.

My first ideas were along the lines of the following:
[LIST=1]
[*]Just patch a pristine version of ec.c and transplant it into the ubuntu tree... this turned out to be very wishful thinking
[*]Start with a pristine copy, apply the nospinlock patch, and follow with the rest of the ubuntu patches affecting ec.c
[*]Reconcile the two versions by hand
[/LIST]

[COLOR="Red"]
UPDATE:
I am currently testing a 18 megs of kernel based on the 686 package configuration for the 2.6.12 kernel with a patched pristine /drivers/acpi/ec.c "transplanted" into the standard ubuntu kernel source tree for 2.6.12 (hey, why not give it a shot, right?). So far, so good (hooray!).

I have loaded the modules for the other hardware and am now running without problems. Transplanting the patched pristine ec.c seems to have passed without conflict. I'll post again if i have any problems.

Alas, this thread ended up being more like a fix blog than a help thread ;-(
[/LIST]
Time for a google run...
[/COLOR]

One observation: The ubuntu kernel includes patches for IBM and Toshiba laptop extras, neither of which is pertinent to the machines requiring the nospinlock fix

I'd be more than willing to go through and simply hunt down all the lines affected by the nospinlock patch in the ubuntu version, but i'm not entirely sure that wouldn't cause problems with the other patches.

So, in the name of good communication, my questions enumerated:
[LIST=1]
[*]Has anybody already solved this problem and patched the ubuntu kernel (I am as thrilled about educational opportunities as the next guy, but i'm not looking forward to doing this)?

[*]Is there anything to prevent me from just tearing up the big ubuntu kernel patch in the patches package and applying them (and the debian patches) AFTER applying the nospinlock patch to a pristine kernel tree?

[*]Do the ubuntu patches as a whole conflict with the changes the nospinlock patch makes (ie change the waiting behavior for the driver)?
[/LIST]

As always, gracious help is most heartily appreciated :D

---

### Post by Luzbel on 2005-12-30
Perhaps it is a stupid question, but sometimes we like to do things more complicated that they really are. Have you tried to check your battery adding the fixed DSDT table to your initrd this way: [http://gaugusch.at/kernel.shtml](http://gaugusch.at/kernel.shtml) ? Don't know much about the SBS proj (that's why my question is probably stupid), but that way I can check my battery status (percentage and time remaining, which is enough for me) and got no errors. Or perhaps my question is stupid because it's just an Acer laptops problem, when mine is Toshiba (well, not Toshiba really, Phoenix BIOS... >.<).

Sorry if this post is useless for you, I'm just trying to help.

---

### Post by KEMitchell on 2005-12-30
[QUOTE=Luzbel]Have you tried to check your battery adding the fixed DSDT table to your initrd this way: [http://gaugusch.at/kernel.shtml](http://gaugusch.at/kernel.shtml) ?
Sorry if this post is useless for you, I'm just trying to help.[/QUOTE]

No, i appreciate all help.

The patch you refer to is actually incorporated into the ubuntu kernels by default. Just move your DSDT.aml to the correct directory (it varies  b/t hoary and breezy) and run dkpkg-reconfigure on your kernel of choice.... voila

My issue is not the DSDT... that is working fine now thanks to that very patch. The problem is that the method used to check the status of the battery (via the SMBus) causes the kernel to miss interrupts (ie keystrokes) while its checking the battery status... which is every few seconds, naturally. There is a spinlock there that is causing the "problem" in the peculiar case of the Acer laptops. The patch i am currently testing is to resolve that lost interrupt issue. The problem is that the patch is designed against a "pristine" (ie unpatched) kernel, while the ubuntu kernel sources (with all the pre-selected kernel patch gooness) is far from pristine. The patch simply doesn't apply cleanly. Therein lies the problem with fixing the problem... per se :rolleyes:

---

### Post by Luzbel on 2005-12-30
Allright! Didn't know Ubuntu has it already applied, I always try to use the official release so I can't really help. I wish you good luck! ;)

---

### Post by nuclearwasted on 2006-01-09
Hi.
I've also got an Acer laptop that uses the smart battery system. I've gotten my dsdt fixed and patched with the sbs patch but the nospinlock patch won't apply to the ubuntu 2.6.12 kernel sources. 

The thread here says your patching the vanilla linux sources with the nospinlock patch and merely copying the ec.c file over to the ubuntu 2.6.12 sources. Am I right, or is there more involved?

Also I was wondering where I can find more information on incorporating my new dsdt and recompiling the kernel "the ubuntu way". I've gotten the sbs stuff to work using Gentoo linux, but I've seen references to different ways of doing these things under ubuntu. 

Many thanks.

---

### Post by KEMitchell on 2006-01-09
[QUOTE=nuclearwasted]The thread here says your patching the vanilla linux sources with the nospinlock patch and merely copying the ec.c file over to the ubuntu 2.6.12 sources. Am I right, or is there more involved?
[/QUOTE]
That's right - I simply downloaded a tar from kernel.org, patched, and copied the file. I had some serious apprehensions about doing such a thing, but apparently it works... at least so far as i can see. Keep in mind that this is by no stretch of the imagination a "fix." In addition, other patches which affect ec.c (Acer Hotkey support for instance, which i decided to do without), will be nullified by this crude "transplant". It may be possible to apply this patch manually to the pristine version as well, but i haven't attempted it.

> Also I was wondering where I can find more information on incorporating my new dsdt and recompiling the kernel "the ubuntu way". I've gotten the sbs stuff to work using Gentoo linux, but I've seen references to different ways of doing these things under ubuntu. 

The kernel patch that the Gentoo thread refers to is a patch which allows the kernel to read the DSDT from the initrd image rather than from the system or a statically-compiled version. It basically externalizes the process of incorporating the DSDT from the source of the kernel, which is beneficial for numberous reasons.

The great thing about u-/ku- buntu is that this patch is applied and active in the pre-compiled kernels, which means you've just go to tell the kernel where to look and make sure that the DSDT is appended to the initrd image. No "recompilation" of the kernel sources is necessary in this case, which means tons of saved time. If you change the DSDT in the future, just change the initrd... big time saver

The link you are looking for is:
[https://wiki.ubuntu.com/ACPIBattery?highlight=%28DSDT%29]("https://wiki.ubuntu.com/ACPIBattery?highlight=%28DSDT%29")

Check the section "Putting your DSDT into initrd". You can go the manual way by appending the "magic header" and then your DSDT file into the initrd you currently have, but i heartily recomend you just let dpkg do it for you...

Advice from experience: keep in mind that there are situations (such as when patching your kernel to prevent lost keystrokes!) when you may not want a kernel with the correct DSDT and all its problems. Try backing up your current initrd and keeping it in /boot (maybe even make a grub entry for it with the same kernel, so you can choose at boot time - i haven't tried this), or do what i did and keep an old kernel around without the edited DSDT so you can boot up without the keystroke issues. If you don't dkpkg-reconfigure a kernel, it won't be affected by the patched DSDT (each kernel gets its own initrd), so this is possible.



Post here if you have any other concerns... mine isn't a clean solution, but it is a *working * solution at the least...

Best of luck...

---

