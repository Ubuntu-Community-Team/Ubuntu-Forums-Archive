---
title: "Intel 3945 Support Gone in SMP Kernel?"
date: 2006-06-04
forum: Hardware &amp; Laptops
---

### Post by jonwatson on 2006-06-04
Hello,

I've been running Flight 7 for a few weeks now under the SMP kernel on my Dell Inspiron 9400. I've been doing the daily updates, but I've been having some problem recently and someone suggested that I actually download and install the 6.06 release which I did.

Now, for some reason, my Intel 3945 wifi card isn't recognized when I boot into the  686 SMP kernel . It worked flawlessly in Flight 7.

I'm not really looking for links to the various threads around here discussing the ipw3945 drivers. I've seen 'em all and I'll go that route if I have to, but since my card worked under the SMP kernel yesterday, I figure there's likely some other explanation as to why it doesn't work now.

Thanks!

J

---

### Post by jonwatson on 2006-06-05
*bump*

Nobody knows why this is borked now?

---

### Post by ariel on 2006-06-05
Hi, I think you are runnning into the same problem that I did. I posted the below in [https://wiki.ubuntu.com/LaptopTestingTeam/ThinkpadX60s](https://wiki.ubuntu.com/LaptopTestingTeam/ThinkpadX60s)

Wireless (ipw3945): works with the default 386 non-smp kernel, and if you change to the smp (which you probably want) please note that you need to install the following metapackage: "linux-686-smp"; if instead you install "linux-686-2.6.x-y-686" etc., you will need to manually install the associated "linux-restricted-modules-2.6.x-y-686" for wireless to work.


Hope this explains and fixes your problem.

---

### Post by rama3i on 2006-06-05
I also had same probelem with you. but it thought that u r more luckily than me. On my first instalation, my network card (e1000) also did'nt works. Thought that i was from my kernel so most forum say that i should recompile my kernel.
But i found on net that i just have recompile my network driver from scratch. So i recompile my network driver and my wireless driver. For my wireless driver, i got it from [http://ipw3945.sourceforge.net/]("http://ipw3945.sourceforge.net/") and latest IEE 80211 driver [http://ieee80211.sourceforge.net/]("http://ieee80211.sourceforge.net/")
I compile it and install it for network my driver. And it's works well till now. hope this can help u

---

### Post by jonwatson on 2006-06-06
[QUOTE=ariel]Hi, I think you are runnning into the same problem that I did. I posted the below in [https://wiki.ubuntu.com/LaptopTestingTeam/ThinkpadX60s](https://wiki.ubuntu.com/LaptopTestingTeam/ThinkpadX60s)

Wireless (ipw3945): works with the default 386 non-smp kernel, and if you change to the smp (which you probably want) please note that you need to install the following metapackage: "linux-686-smp"; if instead you install "linux-686-2.6.x-y-686" etc., you will need to manually install the associated "linux-restricted-modules-2.6.x-y-686" for wireless to work.


Hope this explains and fixes your problem.[/QUOTE]

Worked like a charm. I installed the linux-686-smp package, rebooted into the SMP kernel and my card came up. Thanks so much for the help. I hated having to choose between my two processors and my wifi :)

J

---

### Post by brandym on 2006-06-13
Hi!

I have a Toshiba A100-153 (Core Duo, Intel 3945abg, ...) and installed Xubuntu with single-core kernel which worked fine (though just one cpu). And the 3945-card worked fine too. But, as I am looking forward to use the smp kernel, I installed the linux-686-smp package. But it does not what I wanted to do. After starting up, the CPU(s) runs constantly at 50 % (top->ipw3945/0 uses one core completely) and the 3945-card is not recognized. What can I do?
Thx for replies.

---

### Post by Attila on 2006-06-18
[QUOTE=brandym]Hi!

I have a Toshiba A100-153 (Core Duo, Intel 3945abg, ...) and installed Xubuntu with single-core kernel which worked fine (though just one cpu). And the 3945-card worked fine too. But, as I am looking forward to use the smp kernel, I installed the linux-686-smp package. But it does not what I wanted to do. After starting up, the CPU(s) runs constantly at 50 % (top->ipw3945/0 uses one core completely) and the 3945-card is not recognized. What can I do?
Thx for replies.[/QUOTE]
I have the same problem, identical, on a Compal laptop

---

### Post by parityb on 2006-10-07
MANY MAN THANKS 2 jonwatson who giving me the hint with the linux-686-smp package!!!

Laptop: Toshiba-M100 dual core + ipw3945

after installing the package and rebooting everything goes well!!
no problems like the ones from brandym.

---

### Post by quistive on 2006-10-17
I've had the same exact problem with BrandyM.  I tried it with the 386 kernel, too.  It worked at first, but after a while it had the same problem as the 686-smp

---

