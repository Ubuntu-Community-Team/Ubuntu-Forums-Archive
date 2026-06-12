---
title: "Laughable suspend"
date: 2008-09-11
forum: General Help
---

### Post by SeanTater on 2008-09-11
I've tried all the ways I can think of to suspend or hibernate my computer.

This is what I got:


Normal suspend -> Works fine -> Suspend again -> Never gets into S3 sleep, unresponsive black screen

Normal hibernate -> Never turns off, looks like the second suspend


Uswsusp Suspend (sudo s2both) -> Never enters S3 sleep, unresponsive -> Restart takes a long time and stops at a blinky underscore. -> Restart again takes no time and resumes right where it left off

Uswsusp Hibernate (sudo s2disk), exactly the same as suspend.

For normal suspend, I:

[LIST]
[*]Blacklisted agpgart (but it's still in lsmod)
[*]Disabled POST_VIDEO
[*]Disabled SAVE_VBE_STATE
[*]Enabled NvAGP (to "1")
[/LIST]
For uswsusp I followed this tutorial: [http://ubuntuforums.org/showthread.php?t=750216](http://ubuntuforums.org/showthread.php?t=750216)

Is there a way to get any of these to work smoothly (particularly suspend?)

If you need a file or command output or something like that, just ask..

---

### Post by Sycron on 2008-09-11
> Normal suspend -> Works fine -> Suspend again -> ..
[I]
Suspend again[/I] means that you turn on from suspend mode ?

---

### Post by SeanTater on 2008-09-11
> **Sycron said:**
> [I]
Suspend again[/I] means that you turn on from suspend mode ?

Exactly. It works perfect the first time. (Not to mention it's speedy)

---

### Post by cdtech on 2008-09-11
I just did a work around on my laptop. The trick is to get gnome-power-manage to use "/etc/acpi/sleep.sh force" instead of whatever it uses. I did this by editing "/usr/lib/hal/scripts/linux/hal-system-power-suspend-linux" and replacing "/usr/sbin/pm-suspend $QUIRKS" with "/etc/acpi/sleep.sh force" around line 74.

Now my laptop suspends properly when I close the lid. I could never get the hibernate to work properly so what I did was to create two aliases within my .bash_aliases file.
```
alias sleep='sudo /etc/acpi/sleep.sh force'
alias hibernate='sudo /etc/acpi/hibernate.sh force'
```
I use the command line to hibernate now.

Hope this helps.......

---

### Post by SeanTater on 2008-09-11
> **cdtech said:**
> I just did a work around on my laptop. The trick is to get gnome-power-manage to use "/etc/acpi/sleep.sh force" instead of whatever it uses. I did this by editing "/usr/lib/hal/scripts/linux/hal-system-power-suspend-linux" and replacing "/usr/sbin/pm-suspend $QUIRKS" with "/etc/acpi/sleep.sh force" around line 74.

Now my laptop suspends properly when I close the lid. I could never get the hibernate to work properly so what I did was to create two aliases within my .bash_aliases file.
```
alias sleep='sudo /etc/acpi/sleep.sh force'
alias hibernate='sudo /etc/acpi/hibernate.sh force'
```
I use the command line to hibernate now.

Hope this helps.......


I don't use Gnome Power Manager (I use kpowersave) but I actually have not done that part yet.
I've tested uswsusp with sudo s2disk and sudo s2both. I didn't want to change all the commands until I knew they worked. Is there more that those scripts need to do than sudo s2disk and similar?

I can change it if necessary, I just did not know..

---

### Post by SeanTater on 2008-09-11
I finished up the tutorial and now it took four reboots before I got it to resume. Not fun.

---

### Post by Sycron on 2008-09-11
You may try the latest Intrepid Ibex, but it's unstable. You may try the Live CD and see if it suspend corectly.

---

### Post by tgalati4 on 2008-09-11
The process trackerd bit me.  My pc would suspend the first time but then wouldn't the second time.  Trackerd (and beagle) are file indexing daemons that run in the background periodically.  When one of these pesky daemons is running, suspend doesn't happen because of a policy exception.  Sometimes a pop-up notice happens.

Try running from the terminal and look for error messages:

>sudo pmi action suspend

---

