---
title: "[SOLVED] Ethernet monitoring program"
date: 2008-11-08
forum: General Help
---

### Post by Bruce M. on 2008-11-08
Hi Folks,

I've been getting "disconnected" from the net at various times throughout that day for about a month now.  So I was wondering if there is a program in the repos that can "monitor and log" activity on my ethernet card.

It's built into my MSI motherboard, I'm NOT running a server, no network in the house, just a simple desktop running Ubuntu 8.04 64bit connected to the Net via a cable modem (only 4 days old, my ISP gave me a new one.)

Is there anything that can create logs for me to know when I've been disconnected for how long (and a plus would be why)?

Thanks for your time.

Have a nice day.
Bruce

---

### Post by uljanow on 2008-11-08
Try wireshark or tcpdump. Both are packet sniffers.

---

### Post by Bruce M. on 2008-11-08
> **uljanow said:**
> Try wireshark or tcpdump. Both are packet sniffers.

Thank you, I'll keep you posted.

Chimo!
Bruce

---

### Post by cariboo on 2008-11-08
Iptraf and vnstat are another two programs that monitor throughput. Vnstat will even estimate you up and down loads.

Vnstat is command line program, and Iptraf has an ncurses interface.

Jim

---

### Post by Bruce M. on 2008-11-09
> **cariboo907 said:**
> Iptraf and vnstat are another two programs that monitor throughput. Vnstat will even estimate you up and down loads.

Vnstat is command line program, and Iptraf has an ncurses interface.

Jim

Thanks for the reply, I'll check those out too.

When it comes to this stuff I'm a real green newbie and it will take me a while to read through the man pages.  :)

Have a nice day.
Bruce

---

### Post by dburnett77 on 2008-11-09
Do you run a firewall and av.

I use firestarter and clamav (plus the daemon).  It might help if someone is intensionally disrupting your connection.

---

