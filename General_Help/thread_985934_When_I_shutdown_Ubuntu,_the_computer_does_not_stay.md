---
title: "When I shutdown Ubuntu, the computer does not stay off"
date: 2008-11-18
forum: General Help
---

### Post by swinky on 2008-11-18
I have been working on getting Ubuntu 8.10 (64-bit) working on my Toshiba Satellite L305 for a few days and finally got it all working after a few reinstalls. Today I thought I had everything smoothed out until I shutdown my system. Half an hour later I came back and found that it was on, and had been on long enough to turn off the display.

After a few test shutdowns, I have noted that it only seems to turn itself back on after the lid has been closed and that it only happens after shutting down from Ubuntu (which is to say, if I am running Windows and shut it down, is stays off.) Before 8.10 64-bit I was running 8.10 beta 32 and then later I upgraded to 64 bit. I have reinstalled a couple of times from trying to get things to work in the 64 bit version, but before this latest install both versions shut down fine. I am running the same software I was running before.

I am really lost as to how the computer can turn itself on again after I turn it off, specifically in regard to the fact that in only happens after running Ubuntu.

---

### Post by Th3Professor on 2008-11-18
If you were not experiencing these issues in 32-bit but you are now and only in 64-bit, then you might consider asking in the 64-bit forum, most 64-bit users tend to be pretty responsive in that forum (usually). ;)

---

### Post by swinky on 2008-11-18
> **Th3Professor said:**
> If you were not experiencing these issues in 32-bit but you are now and only in 64-bit, then you might consider asking in the 64-bit forum, most 64-bit users tend to be pretty responsive in that forum (usually). ;)

Not a bad idea except that after experiencing all sorts of problems related to running 64-bit I opted to reinstall the 32-bit version. In fact, I reinstalled from the same 8.10 beta CD I was running before. But the problem still persists. I have been using dpkg with --get-selections and --set-selections to automatically reinstall all the packages I have been using because I have been reinstalling left and right. I have also been keeping my same /home partition. I suppose I need to start figuring out what packages might have been installed or some random setting that may have been set in my home directory that might be causing this.

Any ideas where to start?

---

### Post by Th3Professor on 2008-11-18
You could start from the start, erm, from the beginning. Start fresh. Completely. Though be sure to back-up any important data first. ;)

---

### Post by 420shaggy on 2008-11-18
Not sure if this will help, but try messing with the Power Management settings.  Instead of having something happen when you close the lid (eg-> hibernate, shutdown or whatever it might be set to) just turn that setting off and see what happens.  Who knows, it might just be that easy.

---

### Post by swinky on 2008-11-19
I retraced my steps for setting up the original install vs. the latest install and I realized the only major difference was setting up the wireless support. On the first install I set up wireless with madwifi, on the 64 bit I used ndiswrapper, because as I am told, madwifi does not work with the 64 bit version. So I uninstalled ndiswrapper (since it was automatically installed when I reinstalled ALL the packages I had previously installed).

I also realized that in the install process for the madwifi drivers, the tutorial I was following suggested blacklisting the ath_pci module. This was not copied over to any new installs. So I unloaded it and blacklisted ath_pci.

I don't know which action fixed it, but now when my computer is turned off, it STAYS off. :) I don't know WHY this worked (probably something to do with wake on LAN, even though I disabled it in the BIOS, because both modules are pertaining to wireless networking) but it is working 100%

---

### Post by Th3Professor on 2008-11-20
Odd but cool, still... problem solved. Cool beans. Glad to hear. :)

---

