---
title: "Madness! Can anyone help me track down these kernel panics?"
date: 2012-08-12
forum: Hardware
---

### Post by buddhaflow on 2012-08-12
I bought a new (used) computer, and have been having problems with it.

About every couple hours or so, it will dump out to text and barf up the kernel panic information on the screen. It also totally freezes sometimes, but more often kernel panic.

Also, frequently Chrome will kill all the tabs that are from one site. This happens sometimes even with no flash. Ditto Opera, just crashes sometimes. Also, flash sometimes crashes and won't restart when reload.

Computer is C2D, 4GB, 500GB. Desktop, HP DC7800. Running Ubuntu 12.04.

Here are the steps I've taken:

Switched out computer (off government lease, no RAM/HDD) for similar computer from same seller. So change motherboard/processor/power supply.

Run memtest for 32 hours, 30 passes, 0 errors (Oh! I had forgotten the warmth of sunshine on my skin!)

Tried another hard drive (both, however from same eBay vendor).

Run OS off of USB.

Disable ACPI.

Reinstalled 12.04.

Upgraded kernel to 3.4.

Dang, still doing it.

I tried to store the kernel panic info by installing and configuring a package to do so, but the steps didn't work and nothing is ever left in /var/log. The kernel panics will be in random programs; sometimes in chrome, sometimes in kworker, sometimes in other processes I've never heard of.

I'm at my wits end. I feel like I've tried to isolate every single point of failure I could think of. Sometimes I won't be doing anything, just leaning back reading a long article, not interacting with computer in any way, and boom it's toast.

Any advice? What could possibly be the problem?

Your help is greatly appreciated!!

dmesg: [http://pastebin.com/DR0yjg5A](http://pastebin.com/DR0yjg5A)
lspci: [http://pastebin.com/jj3kYZF2](http://pastebin.com/jj3kYZF2)

Any other info I should include?

---

### Post by sanderj on 2012-08-12
Good that you already ran memtest. A pity that it not reveal errors. ;-)

Maybe the CPU/system temperature is getting too high? You could set a threshold in your BIOS, and/or you could measure the temperature from within Ubuntu.

Oh, and have you tried another version of Ubuntu, for example 10.04 and 11.04?

---

### Post by buddhaflow on 2012-08-13
Hey, thanks for that. It's a good idea. I thought I had tried unsucessfully to add temperature gauges to AWN when I installed it, but they are working now. I will keep an eye on them. However, I did de-dust the computer when I got it, and it's got plenty of airflow, so I don't see why it should be doing that. 

To answer your second question, yes; when I tested it off USB, that was a Lucid install. However, it was on an old USB that might be failing (had it on my motorcycle keychain for 2+ years), so maybe it wasn't the best testbed! Perhaps I will make a fresh Lucid USB and try again. Or even Fedora or *dread* XP.

Frustrating problem, no?

Thank you for your advice!

---

