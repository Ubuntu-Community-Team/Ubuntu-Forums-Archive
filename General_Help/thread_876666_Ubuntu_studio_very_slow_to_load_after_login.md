---
title: "Ubuntu studio very slow to load after login"
date: 2008-08-01
forum: General Help
---

### Post by Psimon on 2008-08-01
I recently added the packages for Ubuntu Studio by checking the Ubuntu Studio Desktop package in Synaptic.

It seems to work OK eventually, but it takes an age to load after login. The menu icons don't show up initially, and some panel applets fail. I had no problems like this with the standard Hardy installation.

Is it normal to take so long (3-4 minutes) to load. I have 1GB of RAM and a 3Ghz processor so I don't imagine I have a shortfall in hardware.

Any responses much appreciated.

---

### Post by caljohnsmith on 2008-08-01
If you run "dmesg | more" at the command line, you might find some useful info about any errors/warnings that could be the source of your slow-loading problems.

---

### Post by Psimon on 2008-08-01
I ran the command and scrolled right down to the end to find a couple of error messages.

> 
[   56.746564] Bluetooth: RFCOMM ver 1.8
[   58.185420] tg3: eth0: Link is up at 100 Mbps, full duplex.
[   58.185426] tg3: eth0: Flow control is off for TX and off for RX.
[   58.189067] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   60.888320] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
[   60.888338] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[   60.888377] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
[   61.227680] NET: Registered protocol family 17
[   66.627002] Netfilter messages via NETLINK v0.30.
[121299.739482] gdl_indexer[7679]: segfault at 6f6f6742 eip b7f7cea2 esp 08059f9
0 error 4
[121961.821042] gdl_indexer[23101]: segfault at 6f6f6742 eip b7f55ea2 esp 08059f
90 error 4


Do these error messages offer any clues?

Thanks for your help.

---

### Post by caljohnsmith on 2008-08-01
That "gdl_indexer" seems to be a problem, and I would assume it is probably part of the libgdl* libraries. I would go into Synaptic and make sure those libraries are up-to-date. 

So there were no other errors in dmesg? How about doing "dmesg | grep error" just to be sure.

---

### Post by Psimon on 2008-08-02
Here's the results from the "dmesg | grep error" command:


> 
[   14.278456] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[121299.739482] gdl_indexer[7679]: segfault at 6f6f6742 eip b7f7cea2 esp 08059f90 error 4
[121961.821042] gdl_indexer[23101]: segfault at 6f6f6742 eip b7f55ea2 esp 08059f90 error 4
[124962.283848] gdl_indexer[17323]: segfault at 0000000c eip b7718386 esp b753b590 error 4
[125144.189414] gdl_indexer[22243]: segfault at fbad800d eip b7f2f625 esp b74a8378 error 4
[125206.310520] gdl_indexer[22265]: segfault at 6f6f6742 eip b7f5cea2 esp 08059f90 error 4
[125327.896594] gdl_indexer[27070]: segfault at b81381b9 eip b7fa5e96 esp b751f364 error 4
[126769.959703] gdl_indexer[31323]: segfault at b81aa1b9 eip b7fd7e96 esp b7551364 error 4
[126833.078942] gdl_indexer[31326]: segfault at 6f6f6742 eip b7f96ea2 esp 08059f90 error 4
[126955.655072] gdl_indexer[3730]: segfault at b81991b9 eip b7fe6e96 esp b7560364 error 4
[127020.605210] gdl_indexer[3731]: segfault at 6f6f6742 eip b7fb2ea2 esp 08059f90 error 4
[127082.834953] gdl_indexer[4809]: segfault at 00000004 eip b76e0405 esp b7503d28 error 4
[127146.242067] gdl_indexer[5477]: segfault at fbad800d eip b7f9c625 esp b7515378 error 4


I looked up libgdl in synaptic and the packages are upto date, except the dev & dbg ones aren't installed.

Anything else I should look at?

---

### Post by caljohnsmith on 2008-08-02
I don't know Psimon what might be causing those segfault errors, but it would seem justified to file a bug report at bugs.launchpad.net at this point. There's a pretty good chance they can help you resolve it.

---

### Post by Psimon on 2008-08-02
Thanks again. I'll do as you suggest.

---

### Post by Hudy on 2008-11-28
Sorry, the crash you are seeing is Google Desktop Indexer...I'm having crashes too.

Nov 28 11:31:10 chubby kernel: [ 1417.824439] gdl_indexer[32295]: segfault at 32332f77 eip b7f6ee92 esp 08059fa0 error 4
Nov 28 11:41:14 chubby kernel: [ 2021.288359] gdl_indexer[17692]: segfault at 37312f77 eip b7f7fe92 esp 08059fa0 error 4
Nov 28 11:42:21 chubby kernel: [ 2088.303332] gdl_indexer[6949]: segfault at 39362f77 eip b7f0ee92 esp 08059fa0 error 4
Nov 28 11:43:23 chubby kernel: [ 2118.297998] gdl_indexer[2645]: segfault at 36322f77 eip b7ef2e92 esp 08059fa0 error 4
Nov 28 11:44:27 chubby kernel: [ 2143.475202] gdl_indexer[3033]: segfault at 30332f77 eip b7fade92 esp 08059fa0 error 4
Nov 28 11:46:29 chubby kernel: [ 2184.517496] gdl_indexer[3314]: segfault at 33332f77 eip b7f0de92 esp 08059fa0 error 4
Nov 28 11:48:32 chubby kernel: [ 2223.334722] gdl_indexer[3996]: segfault at 39332f77 eip b7fd9e92 esp 08059fa0 error 4
Nov 28 11:49:35 chubby kernel: [ 2243.217771] gdl_indexer[4704]: segfault at 37342f77 eip b7f9ee92 esp 08059fa0 error 4
Nov 28 11:50:36 chubby kernel: [ 2264.110895] gdl_indexer[4965]: segfault at 39342f77 eip b7f26e92 esp 08059fa0 error 4
Nov 28 11:51:38 chubby kernel: [ 2293.494091] gdl_indexer[5230]: segfault at 32352f77 eip b7f53e92 esp 08059fa0 error 4
Nov 28 11:52:40 chubby kernel: [ 2325.225863] gdl_indexer[5508]: segfault at 35352f77 eip b7f21e92 esp 08059fa0 error 4

I don't know if it's crashing on the same input file, at the same place in the index(es), or what.  I'll have to strace() it & see what's happening...

N.B. As it would most of a week of full-time 24x7 work to rebuild the index, I'm trying to find out what else I can do about it - and not having much luck.  There's just very little info out there about what to do when this software goes belly-up!

I'm rather unhappy at the prospect of blowing away all my indexes, and rebuilding, only to have it start to crash at the same point a week from now :mad:

I'll post here again if strace shows anything interesting.  If anyone else has seen this and knows what must be done, please speak up...thanks.

/Bill

---

### Post by mattdee on 2010-04-12
I am having the same issues with gdl_indexer.

My wireless would drop when gdl_indexer would spit out an error message

I'm assuming its Google Desktop...so I kill Google Desktop and I'm back in business

---

