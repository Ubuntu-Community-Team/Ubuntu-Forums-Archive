---
title: "dec530 irq11: nobody cared"
date: 2007-10-31
forum: Hardware &amp; Laptops
---

### Post by dave37 on 2007-10-31
I've been trying to get networking going on an older amd k7-750 ak72 via board and am unable to network in either ubuntu 6.06 server or desktop.  In dmesg I keep getting the irq11: nobody cared.  I suspect it's the network card a dec 530 using the de2104x driver.  The bios doesn't allow irq assignment, i've disabled any unnecessary devices in the bios and no luck.  Short of trying another model nic, is there anything I can try?

---

### Post by Linicks on 2007-10-31
> **dave37 said:**
> In dmesg I keep getting the irq11: nobody cared.

That qualifies for a post to the Linux kernel mailing list... send a full debug (uname -a, lspci, etc. etc.).

Nick

---

### Post by dave37 on 2007-10-31
I've also tried the irqpoll and pci=irqpmask options in grub to no avail.  Unfortunately this is on Server, and I'm not the best with cli, but I'll try!  Who would I direct those files to? How would I create those files from the command line?

---

### Post by Linicks on 2007-10-31
lspci > lspci.txt

will create lspci.txt file

uname -a > uname.txt

will create uname.txt file

etc.

Just send a mail to:

[email]linux-kernel@vger.kernel.org[/email]

and use (or similar):

dec 530 -  irq11: nobody cared

as a subject.  Include what I said, plus what you have tried.  Ask to be CC'ed as you are not subscribed (300 mails a day otherwise).


Be brief, but explain all you have done/what hardware you have.  Hopefully somebody will try to help you.

Nick

---

### Post by dave37 on 2007-10-31
Thanks Nick.  Interestingly, the grub boot options that got rid of it was pci=bios.  I now no longer receive a "network unreachable" error when restarting networking, and I can see it trying to connect to the router.  However it ends with "no dhcp offers received"

---

### Post by Linicks on 2007-10-31
Ummm.  OK, years ago I had an issue with a network card on an old machine.

Have a lookie here:

[http://www.linicks.net/8139too_debug/THE_FIX.txt](http://www.linicks.net/8139too_debug/THE_FIX.txt)

I had an option in my BIOS to set the PCI... see if yours is similar.

Nick

---

### Post by dave37 on 2007-10-31
Thanks for the reference but no similarities.  I set the machine to static ip in /etc/network/interfaces and I can see the light flashing on the router when I issue a ping command from it (also see this with eth0 set to dhcp).  I'm going to borrow a nic tomorrow and see if that changes anything.

Thanks!

---

### Post by dave37 on 2007-10-31
SOLVED!!  Or rather fixed.  Reread your reference again, and got to thinking about pci performance controls on the bios.  Turned off pci wait state and pci dynamic bursting and am now connected.  I'm going to go back tomorrow and turn each on and off to isolate which was the cause and will post back.

Thanks Nick!!!

:KS

---

### Post by dave37 on 2007-11-01
Can now confirm that the solution was to turn off, in the Bios, pci dynamic burst state and the usb controller and add the kernel boot options of pci=bios and noapic.  With those off, all is well

---

