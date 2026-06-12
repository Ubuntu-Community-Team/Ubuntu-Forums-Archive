---
title: "ATI proprietary drivers cause freezing with Radeon XPress 200 and Intel motherboard"
date: 2007-02-11
forum: Hardware &amp; Laptops
---

### Post by CroEragon on 2007-02-11
After 4 month of research and testing i have discovered what caused my Ubuntu to freeze. Best part is that it is not actally Ubuntu's fault, its ATI's fault.

I have met few people in this forum that report  freezing with XPress 200 and some have no problem. Most confusing. I know that in about first 2 weeks of using Ubuntu i had no freezing(after i understood that it was while using opensource drivers). I did a LOT research about it, finding almost nothing or very little. I was stuck with knowing that it is actualy conflict with X.

So, unable to use Ubuntu properly i resorted to Mandriva, workede like charm, no freezing, but i used opensource version without ATI's drivers. I didn't like Mandriva so i installed openSUSE and again, everything worked. In attemot to install beryl, i had to install proprietary drivers to get acceleration. And then freezing appered on openSUSE same as in Ubuntu. Just to test it, i installed Mandriva again and this time installing  proprietary drivers.l Gues what!!!! Freezing.  Obviously , ati's developers are unable to make drivers for their own card.

This is no support thread, just to let you know this happens. You can ask if you want anything, i will keep eye on thread.
I would add it to incompatibillity thread but it is closed and this is uncommon problem
This is just for somebody who may e stuck with same, to share my research.

---

### Post by Toadmund on 2007-03-25
Well, I have a MSI rs480m2 with xpress 200 series graphics, now I am noticing that when I leave my computer for awhile and I come back to log in again, the spinning curser locks up and I am stuck on a plain beige screen. So I have to reset and reboot from scratch.

Next MOBO I get will have NO ATI stuff on it, are you reading that ATI people?
(unless of course AMD changes things, since they just acquired ATI)
If I was shopping for a new board it would certainly be nvidia.

---

### Post by kamstrup on 2007-05-01
I also have an xpress 200g and Feisty just totally freezes up just when it launches X. I am left with a black screen with a few red vertical lines. Only option left is hard reset.

The worst part is that the open source radeon driver is really bad on my card too. It can only give me 800x600 and that is really not acceptable. The card works fine in Dapper and Edgy.

I've been a real tinkerer for quite some time now and have always got any old obscure piece of hardware working, compiling drivers and kernels and whole toolchains, applying patches (and writing them myself).  Well it's 1-0 to ATI now. I'm giving up. This card is simply unusable with the current state of affairs in Feisty.

/me looking for bugs in Launchpad and filing if appropriate

---

