---
title: "Ubuntu hangs in boot when DVB PCI card is plugged in"
date: 2010-03-07
forum: Hardware
---

### Post by remilio on 2010-03-07
Hi all,
I'm quite new to Ubuntu and I'll be glad if someone could solve my problem.

On my Windows PC, I installed Ubuntu 9.10 Desktop x86 on a different HD (1st HD Windows and 2nd HD Ubuntu). 

Unfortunately the Ubuntu boot sequence hangs when my PCI DVB Twinhan 1020 card is plugged in the PCI bus. If I remove the card Ubuntu boots successfully.

Since I need this card only when booting in Windows, is it possible to disable such a PCI card (via software), e.g. setting something in the Kernel boot options?

I already tried the following options, but it still hangs :-(

pci=noacpi 
pci=nopper 
pci=nosort 
pci=routeirq 
acpi=noapic 
pci=off 

removing "quite" and "splash" options i see that it hangs when the following is shown (sometime on the 1st one and sometimes on the 2nd one depending on the above boot parameter settings):

[B][I]Running /scripts/init-bottom
Setting preliminary Keymap
[/I][/B]
What is Ubuntu doing on these phases when it hangs?

 /Thanks in advance, Remilio.

---

### Post by remilio on 2010-03-07
Problem solved.

Just to share what I did.

added in 
[/etc/modprobe.d/blacklist.conf]("file:///etc/modprobe.d/blacklist.conf")

the following row:
[COLOR=Blue]blacklist bttv[/COLOR]

So no driver is loaded for Twinhan 1020 PCI card  and boot does not hang anymore :-)

   /Thanks, Remilio.

---

