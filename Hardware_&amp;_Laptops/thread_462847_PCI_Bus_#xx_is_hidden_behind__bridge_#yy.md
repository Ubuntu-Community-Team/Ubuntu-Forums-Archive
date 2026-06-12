---
title: "PCI: Bus #xx is hidden behind  bridge #yy"
date: 2007-06-03
forum: Hardware &amp; Laptops
---

### Post by masterthor on 2007-06-03
I get a strange message in the DMESG like this:

[   16.620292] PCI: Bus #03 (-#06) is hidden behind  bridge #02 (-#02) (try 'pci=assign-busses')
[   16.620295] Please report the result to linux-kernel to fix this permanently

Anyone have a clue as what it is and what i might do? It seems to ask me something :P

---

### Post by Ken_Lewis81 on 2007-06-03
The 'try pci=assign-buses' is a request that you edit the GRUB boot line that starts "kernel..." to include the option that tells the Linux kernel to assign all PCI bus numbers.  It will report some stuff in 'dmesg' which you can then post to the Linux Kernel Mailing List, see [http://vger.kernel.org/](http://vger.kernel.org/).  The kernel developers wil then be able to fix up the way that Linux accesses your PCI busses and this problem will go away.

Take care.
Ken.

---

### Post by masterthor on 2007-06-03
can i send a message to linux-kernel without subscribing to the list? if so, how can i see the responses i get? I've seen that subscribing gives me A LOT of mails daily, and i'm not sure i'm that advanced just yet to see all that ;)

---

### Post by Ken_Lewis81 on 2007-06-05
Yes, you don't need to be a subscriber, but you might miss requests for more details.  You could get the 100kiB summary or the daily summary editions mailed to you if you want.  The instructions are at [http://vger.kernel.org/vger-lists.html#linux-kernel](http://vger.kernel.org/vger-lists.html#linux-kernel), and there's a FAQ you should read ([http://www.tux.org/lkml/](http://www.tux.org/lkml/)) as well as directions for best formatting your mail and a list of words that are automatically filtered to the killfile.

Take care.
Ken.

---

