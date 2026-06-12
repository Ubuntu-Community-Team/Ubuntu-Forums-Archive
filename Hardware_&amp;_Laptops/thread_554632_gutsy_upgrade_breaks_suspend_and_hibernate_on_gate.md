---
title: "gutsy upgrade breaks suspend and hibernate on gateway laptop"
date: 2007-09-19
forum: Hardware &amp; Laptops
---

### Post by ewand on 2007-09-19
no problem with suspend on feisty (though as I recall return from hibernate had some issues with either my sound or video) - however, since I tried Gutsy Tribe 5...

- both suspend and hibernate get almost all the way there. the screen shuts off, the dvd drive spins down - but not the hdd. then it just sits there.

- have tried both fglrx and radeon drivers to see if it had something to do with video (doubt it since the screen shuts off) - no luck

- add print statements to all the scripts in /etc/acpi/suspend.d/ - it gets all the way to the very end of the last one - something is going wrong after this.

... any pointers?

cheers
ewan

---

### Post by ptelder on 2007-10-20
I'm having similar issues.on a Solo 450SX4. Both hibernate and suspend worked on Feisty using µswsusp. Under Gutsy, suspend is working, but hibernate is a no go. Using the standard pmi, all I get is a blank screen for a few seconds, then I get the HAL failed to hibernate error.

Using µswsusp via  ```
sudo s2disk
```, it gets as far as building the snapshot and then hangs.

---

### Post by greg.hagen on 2007-10-23
Gutsy breaks suspend on any machine that has the fglrx kernel module loaded. It would have been nice if they warned people about that one, since they knew about the bug in fglrx since about a month before the release.

---

### Post by ptelder on 2007-11-20
fglrx is not the issue in this case.

For the past few weeks, I've downgraded to Feisty to get functionality back, but I saw enough people complaining about SMP and Network Manager to think I'd have a chance if I upgraded again.

I'm also interested in aquiring a bridge if anyone's selling.

Okay, so I'm now attempting to hibernate in Gutsy after booting in "Recovery Mode"

Still not working via µswsusp or pmi. Just so we're clear, I've checked my dmesg output and lsmod - fglrx is *not* loaded. My chipset is old enough for decent performance under the open source driver. I've also disable smp with the "nosmp" boot option.

Any ideas out there?

---

### Post by ptelder on 2007-12-02
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/acpi/+bug/75174](https://bugs.launchpad.net/ubuntu/+source/acpi/+bug/75174) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Eureka!

Ove the past week or so, I've been poking around trying to fix this issue. I'd been able to get a successful hibernate once or twice, but could not replicate it.

Until tonight.

I had to do a clean reinstall after a hard drive failure and burned a shiny new Gutsy CD to do it (Previously, I'd installed Feisty and upgraded from there).

After my first system update, I tried Hibernate just to see if the Gutsy install media made a difference.

It didn't. But the machine did sort-of Hibernate. It went to a blank screen, had lots of disk access, and then just sat there. Imagine my surprise when I power-cycled it and it resumed back my desktop.

Imagine my choice of words when I couldn't get it to do so again after a reboot...

Encouraged by the one success, I began tweaking setting in /etc/default/acpi-support - with no real differences.

And then I noticed something.

With each attempt, the cpu fan on my laptop kicked into high gear. This is something that also happens when kacpi_notify and acpid go runaway on my system (see the launchpad bug link above).

Usually, when I'm using my laptop for any period of time I renice both kacpi_notify and acpid to 19 to keep things usable. When I was testing my ability to hibernate, I was doing as little as possible and attempting to hibernate right after booting, without renicing the offending proccesses.

With those troublemakers reniced, my laptop successfully writes out the image, but fails to power itself off. A quck edit of /etc/default/acpi-support to change HIBERNATE_MODE to "platform" fixed that, and uncommenting the DOUBLE_CONSOLE_SWITCH option fixes the random video issues I sometimes got under feisty.

In short, it **finally** works.

Now I'm off to learn enough awk to write a script to automaticly renice kacpi_notify and acpid on boot..

---

