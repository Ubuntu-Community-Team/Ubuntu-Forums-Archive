---
title: "Radeon ATI x600 driver problems in 9.10"
date: 2010-01-16
forum: Hardware
---

### Post by EmersonA on 2010-01-16
Linux noob here,

I've recently switched from linux to windows. I'm not incredibly savvy with computers, but I'm familiar enough that I'm willing to commit to switching to linux.

That said, I'm not too familiar with the terminal commands and things of that nature, so any help is CERTAINLY appreciated, but elaboration on what are probably fairly simple operations would be even more appreciated.

I'm running Ubuntu 9.10 on my desktop computer (via wubi), and I'm trying to install drivers for my Radeon x600 card. I've downloaded the installation .run file from ATI's website, and I follow the instructions given, but I run into a problem in the terminal. Everything goes fine (after entering "sh ati-driver-installer-9-3-x86.x86_64.run") until it finishes uncompressing, which I receive a message saying:
"Error: ./default_policy.sh does not support version default:v2:i686:lib::none:2.6.31-17-generic; make sure that the version is being correctly set by --iscurrentdistro"

I don't understand precisely what the problem is, and I don't understand exactly what it is telling me to do to remedy the problem, so if anyone could clear this up, that would be much appreciated

Thank you very much!
Also, I'm very sorry if this is in the wrong forum; like I said, pretty big noob!

---

### Post by Yellow Pasque on 2010-01-16
Your card is no longer supported by the proprietary driver. Just use the pre-installed open-source driver.

---

