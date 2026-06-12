---
title: "Smart Battery Support"
date: 2005-12-22
forum: Hardware &amp; Laptops
---

### Post by daschl on 2005-12-22
Does anyone know a tutorial how to install the smart battery support?

Is there a kernel-patch already out or do i have to patch the kernel with this freaky dsdt patches? (they dont work for my notebook-model :()

i really hope that someone has useful answers or informations for me

kind regards and thanks in advance
daschl

---

### Post by bb002 on 2005-12-23
Smart battery??

I can do "cat /proc/acpi/battery/BAT1/state" and "cat /proc/acpi/battery/BAT1/info" to get the battery's current state and lots of info about it. Is that what you mean??

---

### Post by elemental666 on 2005-12-23
little more info is needed to form a good answer, what kind of laptop do you have? and what do you mean by smart battery?

I'm running 5.10 on a IBM TP A31 and I have a little widget up by the clock in gnome that displays my battery info:

When on battery power is shows a battery with a colored power bar to indicate the charge left.

When on AC is shows a plug and hovering your pointer over it will tell you the charge state including how long left until its fully charged.

You can enter the configuration for the widget by right clicking on it and choosing preferences, in there you can change the appearance, enable disable time/percent displays, set notifications for low battery charge and full battery charge.  

It works right out of the box and is installed by default.

---

### Post by daschl on 2005-12-23
[QUOTE=bb002]Smart battery??

I can do "cat /proc/acpi/battery/BAT1/state" and "cat /proc/acpi/battery/BAT1/info" to get the battery's current state and lots of info about it. Is that what you mean??[/QUOTE]


smart battery is a battery type :)

i have a acer travelmate 4000, but all other notebooks which were equipped with the smart-battery have the same problems

so if i look in /proc/acpi/battery/ there is nothing ;)

i mean this for example:

[https://sourceforge.net/projects/sbs-linux/](https://sourceforge.net/projects/sbs-linux/)

but it doesnt work for me (maybe im to dumb but i dont think so)

---

### Post by KEMitchell on 2005-12-23
I, too, own a SBS  laptop... an Acer model 3200. It's a great machine, but as described, it accesses the "smart" circuit on the battery via a rather inconvenient BUS.

As of this writing, i currently have the system to the point where ACPI is running fine - the battery is detected and /proc/acpi works as expected and the processor is scaling with powernowd. This was accomplished by using the DSDT patches and the Intel IASL compiler to fix the DSDT, which was slightly bad. With the ubuntu kernel, you don't actually have to recompile the kernel to alter the DSDT: one of the ubuntu patches allows the kernel to get the DSDT from the ramdisk on boot. This is far more convenient than the alternative - statically compiling the DSDT into the kernel via the config option for dsdt.hex. 1 point for the ubuntu project's choice of patches.

Just dpkg-reinstall your kernels to apply the new DSDT. The directory to stick the patched dsdt file varies b/t hoary and breezy. Google it. 

If you haven't run across this thread yet, it will undoubtedly prove useful:
[http://forums.gentoo.org/viewtopic.php?t=122145]("http://forums.gentoo.org/viewtopic.php?t=122145")

Mostly following these directions, I appended the DSDT to (a copy of!) the default ramdisk and now have a working /proc/acpi/battery... device.

Unfortunately, the issue isn't entirely resolved. Apparently a spinlock issue in /linux/drivers/acpi/ec.c causes the checking of the battery to result in lost interrupts (e.g. keystrokes - what a pain!). This was briefly addressed by an option in the main kernel branch which can be set from the kernel command line by ec_nospinlock=1 or somesuch, but this resulted in rediculously long delays when polling the battery to the point of near uselessness. The SBS SourceForge project ships with a acpi-ec-nospinlock pactch for the 2.6.12 and 14 (and other) kernels which provides a workaround. Unfortunately, these patches don't seem to apply cleanly to the ubuntu linux source packages, so compiling a good ubuntu kernel from the ubuntu sources with patches has proved challenging. I can only assume that the ubuntu patches make some changes to ec.c which prevent the patch from working cleanly (some blocks don't fail, most do). -1 point for the ubuntu kernel patches.

These patches, as intended, DO work for the pristine kernel sources for the linux versions they were written for. As of today i am working on compiling a kernel with the spinlock patch and the external DSDT patch from a pristine archive of the 2.6.14 sources, but i haven't got it working yet. I will probably take a look at ec.c from the ubuntu sources again before it's all said and done, as without the ubuntu patches pre-applied i'm having to worry about autodetection for my wireless card and other issues. I'd like to stick as close to the ubuntu images as i can.

Yes, this is a major pain in the neck, but apparently it's the way to get things done. Even if i do get the nospinlock patch applied to a useful kernel, that patch still amounts to little more than a workaround, not a solution, and its a non-official patch. I'm going to end up recompiling my own kernels until support is added to the main kernel branch (or at least to the ubuntu patches), but it seems unlikely that we'll see that in the near future if ever.

Believe me, you have my empathy in trying to resolve this situation. Apparently it is possible to get this working ship-shape using the SBS dsdt patches and kernel ec-nospinlock patch, but it will inevitably require (at least in my case, i'm not intimately familiar with the 4000s) both patching the dsdt and recompiling the kernel (hint: use the make-kpkg command from the "kernel-package" package to build the kernels... you'll thank yourself for it later).

I will probably post my solution, assuming i find one, once i get it working. Until then, i'll probably continue my attempts at building a kernel from the kernel.org sources, maybe tinkering with finding a way to patch the ubuntu ec.c for nospinlock, and maybe take a look at some other laptop-oriented distros to see if anyone has a prepared kernel image with the patches i require. If i get one working, i'll make a post here, probably provide it as a kernel-image package too.

Best of luck

(PS: Feel free to drop me an email, especially if you have any good news ;) )
[email]kyle.mitchell@mail.utexas.edu[/email]

---

### Post by KEMitchell on 2005-12-23
Update: It has occurred to me that working up from a pristine kernel probably isn't going to end up being worth my while. At the current point (after some helpul runs of xxdiff on various versions of /drivers/acpi/ec.c) it appears that the stituation is the following (**please correct any errors here if you know otherwise**):
[LIST=1]
[*]The ubuntu kernel includes a patched version of ec.c which varies from the pristine version
[*]This difference prevents the clean application of acpi-ec-nospinlock-2.6.12.diff from the SBS project
[/LIST]

My current plan of action follows thus:
[LIST]
[*]Find all ubuntu patches against the 2.6.12 tree which alter ec.c
[*]Apply the nospinlock patch to a pristine 2.6.12 version of ec.c
[*]apply any subsequent ubuntu patches which affect ec.c
[*]Transplant ec.c from the patched pristine version to the published patched ubuntu tree
[*]Compile and test
[/LIST]

If anyone knows for a fact that the ubuntu patches make these alterations fatal, please let me know before i burn too much time compiling and testing kamikaze kernels ;)

---

