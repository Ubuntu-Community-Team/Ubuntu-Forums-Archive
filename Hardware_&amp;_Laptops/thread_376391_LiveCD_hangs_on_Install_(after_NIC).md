---
title: "LiveCD hangs on Install (after NIC)"
date: 2007-03-04
forum: Hardware &amp; Laptops
---

### Post by ppan76 on 2007-03-04
I have been trying to install Ubuntu on my laptop for days.  I had so many problems, well it seem snow I am getting a little bit closer.

When I try to run the Ubuntu LiveCD (6.10) My laptop now hangs after this:

9136cp: Try the "8139too" driver instead;
9139too Fast EtherNet driver 0.9.27
ACPI: PCI Interrupt 0000:03:04:0[A] --> GSI 16 (level, low) --> IRQ 177

That's the last message I get. Nothing happends afterwards.

Thanks

I have tried: pci=noacpi. noapic nolapic and many others.

---

### Post by seldenthuis on 2007-03-04
There are known problems with the 8139too driver (see last post [here]("https://launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/71212")).

You could try using the 'brokenmodules=8139too' option (see: [http://www.suseforums.net/lofiversion/index.php/t28813.html]("http://www.suseforums.net/lofiversion/index.php/t28813.html")).

---

### Post by ppan76 on 2007-03-27
After more than 1 month trying to get linux installed I have finally given up. Yes it's the same problem with the Phillips X53 series laptop.  

It's ironic, I have worked in technology for over 10 years and used many variants of Unix. 
It's extremely annoying, as I dont want to spend 50 hours trying to install the OS.

---

### Post by tgalati4 on 2007-03-27
Try a Dapper 6.06.1 Live CD and see how far you get.   I'm sure there are others that could use that information.

---

### Post by Gina on 2007-03-27
I tried to use 6.10 and had problems - also with laptop - tried 6.06 and that worked OK.  Except I had to fiddle to get wireless working on my Linksys WPC54G v1.2 card.

---

### Post by tgalati4 on 2007-03-27
Wireless networking under Linux is fiddly.  For sure.  I'm glad Dapper works for you, you get 95% of the Ubuntu experience with 10% of the configuration hassles.  We need to hear from ppan76 to see if Dapper works any better on a Phillips X53.

---

### Post by ppan76 on 2007-03-30
Well installing Linux on my laptop become a challenge. And I think I did spend like 500 hours getting it to work (tried a lot of distros!!!)

The one that worked was the newest version of PCLinuxOS, which I liked a lot. I would have kept it if I could get any network to work. Trying to start the NIC would hang the machine. Spend many hours trying to get the WIFI to work.  I cant live without network..

I managed to install Kubuntu by blacklisting, forcing and text installing.  Then I spend a few more hours trying to get the WIFI to work...and suddenly it started working.

So now I have a working kubuntu 6.10 working.  A lot of time spent...

Thanks

---

