---
title: "How can a PCI card cause my monitor to crash?"
date: 2008-05-27
forum: Hardware
---

### Post by ncosens on 2008-05-27
I've been trying to get my EVDO card working in Linux on an old computer but have been having some trouble.  PupplyLinux doesn't seem to be capable of installing it (haven't tried real hard atm) and Damn Small Linux seems to have too many pre-installed devices.  The card is supposed to appear as a USB based device and install as ttyACM0 but DSL comes with ttyACM0 through ttyACM15 (or ttyACM16) already existing).

So I thought I'd try it in my main machine.  I added the PCMCIA to PCI adapter card and booted the computer.  I'm using Ubuntu 8.04 with the latest kernel (2.6.24-17 I think).  It appears to boot normally until the screen with the Ubuntu logo and the loading bar complete, then a bunch of text appears about loading Timidiy and it hangs for a few moments then my screen blinks and displays:

"Out of Range"

And it just sits there.  Trying the other kernel options from GRUB didn't seem to affect it.  Trying with Windows XP does work though.  After removing the PCMCIA to PCI adapter my system runs normally.

How in the world does it effect my ability to boot into Ubuntu and is there a way to remedy this?  Or the installation of the EVDO card in the other computer.

---

