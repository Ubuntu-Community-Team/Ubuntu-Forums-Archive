---
title: "HOWTO: € and $ on Acer Aspire 5610 (etc)"
date: 2007-10-10
forum: Hardware &amp; Laptops
---

### Post by klange on 2007-10-10
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/hotkey-setup/+bug/30562](https://bugs.launchpad.net/ubuntu/+source/hotkey-setup/+bug/30562) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I just finished writing up my tutorial on how to get the € and $ keys working on the Aspire 5610.
Combined with the inclusion of the acerhk module and the ENE SD drivers in Gutsy, the Aspire 5610 and related models are now completely working.
Anyway, the tutorial is on the LaptopTestingTeam's [Aspire 5610 page](https://wiki.ubuntu.com/LaptopTestingTeam/AcerAspire5610#head-c32b7f7a26c28c9c6d0106485f8c4d6b2433e390)
The keys are read by the kernel without anything extra, so acerhk is not needed for them.
**Also note:** If you're not using a 5610, your scancodes for the keys *may* be different! You need to change them to suit. You can find them in your kernel, messages, and system logs by just pressing they keys (they'll spew out two errors a piece with the number included)

Regardless, it's great to have two more useful keys on my keyboard.

Maybe next I'll work on a tool to get Evolution to work with the email LED...
Anyway, enjoy.

---

### Post by joris1977 on 2007-10-22
Hi

Thanks! You're howto works really nice to enable the € and $ on my acer aspire 5610.

But it disabled the super key aka windows key That's a pity because this key is really useful with all the new nice compiz additions i started using. Any ideas how to get this key working again?

:confused:

---

