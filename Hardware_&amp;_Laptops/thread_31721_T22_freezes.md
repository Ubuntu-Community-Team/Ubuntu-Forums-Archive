---
title: "T22 freezes"
date: 2005-05-04
forum: Hardware &amp; Laptops
---

### Post by MKelly on 2005-05-04
My Thinkpad T22 freezes.  I checked before buying this laptop and it's reported to be Linux and Ubuntu friendly. I installed Ubuntu (Warty, from the CD, then updated) and happily used for a while, then I started getting random freezes, couldn't reboot, had to power machine down.  Then it didn't want to start again- IBM screen w/ F1 BIOS options or F12 for boot options didn't come up.  It was under warranty, so I called and was told I'd have to send it in.  I did, they kept it for a month and "fixed" it by reinstalling Windows.  I finally talked to a tech guy who told me he got it to start again by removing everything and discharging the battery- so I could do this if it happened again.

So I finally got it back, reinstalled Warty, downloaded the updates- on dialup.  Worked for a while, now it's hanging again.  Same issues w/getting it to restart.  This last time it abruptly closed Firefox.  I logged out, and then tried it again. Worked briefly, then hung- the screen turned into different colored blocks with gibberish behind them.  This is the first time it's done this- before it just froze on whatever was on the screen-mail, webpage, whatever.  So is this likely a hardware issue, or something in Ubuntu?  If it is a hardware problem I'd like to get it fixed before the warranty runs out, but I don't have much time left.    Any ideas what it could be, what to check?  I'm a bit handicapped by being new to Linux, as far as troubleshooting.  Any help would be greatly appreciated.

---

### Post by WayneLeutwyler on 2005-05-04
Hello,

I am thinking it could be a problem with ACPI. Maybe your laptop is over heating. Do you notice the laptop be extra hot? Maybe the fan not running or running all the time. 

In your menu.lst under /boot/grub/ edit the kernel line and add acpi=off. Then reboot and see if the problem continues. 

example of a kernel line:

kernel /boot/vmlinuz-2.6.8.1-3-386 root=/dev/hda1 ro quiet splash

example of a kernel line with acpi=off added.

kernel /boot/vmlinuz-2.6.8.1-3-386 root=/dev/hda1 ro acpi=off quiet splash

Hope it helps.

Wayne

---

### Post by derdewey on 2005-05-04
Mayhaps it's bad ram? If there are addon sticks, maybe try taking them out and seeing how the system runs.  Slower, probably, but maybe one of the sticks was busted.

---

### Post by MKelly on 2005-06-30
Just a followup, so anyone searching with a similar problem will know how this turned out.  It was the laptop-it finally died completely.  I had it replaced under warranty.  The new one is running Ubuntu and completely trouble free.

---

