---
title: "revalidation failed (errno=-5)"
date: 2009-05-12
forum: Installation &amp; Upgrades
---

### Post by imbrian on 2009-05-12
I have a fairly vanilla Xubuntu 64-bit 9.04 installed.  I've removed Bootsplash.

Original install worked flawlessly and was up and running for about 2 weeks.  On Friday, my computer would get past BIOS / Boot loader and sit at a perfectly black screen, indefinitely.  I tried booting into the safe-mode grub menu item and got a ton of errors regarding ATA items (I have two SATA hard drives and one SATA DVD drive).  Toward the end of the errors, I got an error "revalidation failed (errno=-5)".  I then tried booting the install CD to inspect for hardware failure - the install CD would no longer boot (same errors as above).  I booted up the live CD for the previous 64-bit Xubuntu version and it worked flawlessly (phew - not a hardware problem!).

I was able to investigate the error a bit - and it seems to be semi-random, but specific to particular kernels.  An official bug is already filed here: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/206635](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/206635)

The remedy that seems to be the prevailing wisdom is to add "irqpoll all_generic_ide" to the grub kernel boot parameter.  I edited my inline boot options (directly from grub, pre-boot) to include these parameters and it indeed did boot.  I then edited my grub menu.lst to make these changes permanent.

Here's where things get weird.  Upon reboot, the problem persisted.  I then viewed my kernel params directly from grub (again, pre-boot) and they are indeed there.  There seems to be a problem with grub chewing up my inputs via keyboard as well - if I simply remove the kernel params and re-type them verbatim, it will boot without fail.  If I do not edit my boot parameters upon *every* boot, it will fail consistently.  When I re-type the parameters, I must use the <shift> key to type an underscore (_).  When I even click <shift>, it then seemingly alters my keyboard mapping.  I must type "irqpoll allgenericide" - then arrow back and add in "<shift>_" twice - then "<shift><esc>" (as <shift> is now required for some strange reason).  Playing this game will bring me to a functional and nearly pleasant experience - if I'm not trying to do anything "crazy" with my SATA drives (like, say, burn a DVD - which will fail consistently for unspecified and catastrophic reasons).

I presume these failures with my DVD burning as well as my strange disc behavior are directly related to a mis-configuration or bug in the kernel on the new 9.04 release.  Does anyone have any tips?  My patience has been tried to the point where I think I'll be better off spending the time down-grading to the previous release and skipping 9.04 entirely, as it doesn't seem to be friendly with my setup.  Thoughts?  Has anyone seen something familiar?  Is there any rumors of an upcoming kernel release that will relieve my pains?  Are there any details I can clarify?

---

