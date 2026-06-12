---
title: "System unstable, segfaults and freezing"
date: 2014-05-09
forum: Hardware
---

### Post by Diskdoc on 2014-05-09
I'm having trouble after upgrading 13.10 -> 14.04. Chromium segfaults, plugins crash, system freezes up. I also upgraded my memory recently but running a thorough Memtest checks out ok. At first I thought it might be due to some Mesa/Radeon bug but now I noticed this in dmesg:

> [ 2070.144085] ACPI : EC: GPE storm detected(12 GPEs), transactions will use polling mode
[ 2124.239879] systemd-hostnamed[21994]: Warning: nss-myhostname is not installed. Changing the local hostname might make it unresolveable. Please install nss-myhostname!
[ 2733.816110] chromium-browse[2976]: segfault at 10ed00300018 ip 00007fca8c11e89a sp 00007fff86afb8a0 error 4 in libv8.so[7fca8bf40000+58c000]
[ 2861.818376] chromium-browse[2908]: segfault at 7f5e9ae6c000 ip 00007f5f4a4e976f sp 00007fff907a6058 error 6 in libskia.so[7f5f4a2bb000+2de000]

A, GPE storm? Didn't see that before, ever. Found this:

[http://askubuntu.com/questions/148726/what-is-an-acpi-gpe-storm]("http://askubuntu.com/questions/148726/what-is-an-acpi-gpe-storm")

and this:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/270017]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/270017")

but how do I find what's causing the trouble? And how do I solve it? Is it a kernel bug or some hardware acting up?

---

### Post by Diskdoc on 2014-05-10
Just wanted to comment (in case anyone else has trouble like mine) that the problem might be Radeon-related after all! My laptop also has Intel graphics and I yesterday I switched to using it. Not as fast or pretty but I haven't had a crash or freeze yet!

---

### Post by Diskdoc on 2014-05-12
This is driving me crazy! I eventually had a freeze using Intel-graphics so I switched back to Radeon. Where I also had program crashes (usually Firefox) and freezes.

I tried using an older kernel (3.11.0-19) - same problem.
I tried switching back to my original memorychips - same problem.

It's worth noting that I rarely get the GPE storm-messages in dmesg - perhaps they aren't related to my problem at all.

But something's wrong. And it doesn't look to be the kernel, not the xorg-graphics driver, not my memory chips...it started after upgrading to Trusty. What the heck is it? And why doesn't anyone else have the same trouble? My only recourse now seems to be to reinstall Trusty and see if the problem remains. But I really hate to do it, seems like a Windows-solution to things and doesn't tell me what is actually wrong.

---

### Post by matt_symes on 2014-05-12
Hi

There were major changes to the ACPI subsystem for the 3.13 kernel.

[http://www.phoronix.com/scan.php?page=news_item&px=MTUwODA](http://www.phoronix.com/scan.php?page=news_item&px=MTUwODA)

These may be the cause of your interrupt storms on 14.04.

In place upgrades can be problematic and you may have been unlucky in the upgrade. 

I take it you disabled and purged all the ppas you may have installed that may upgrade cause problems such as xedgers ?

I would run from a LiveCD/USB for a while and see how you get on with that. You can still save files to your hard drive by mounting it.

Kind regards

---

### Post by xeddog on 2014-05-14
I also have a computer that I upgraded from Ubuntu 13.10 to 14.04, and I have also started having problems with the machine freezing.  It doesn't sound like my problem is quite as bad as yours, but there could be several reasons for that.  Anyway, my machine is lightly used.  It's sole purpose at the present time is to run SABnzbd+, SickBeard, and Couch Potato.  The machine may run anywhere from an hour to several hours, but it will eventually freeze.  I just now finished running memtest for the last 24 hours and according to that I don't have memory problems.  Since that machine is not attended, when it does freeze there are no messages or anything else to diagnose with.  Most of the time when it hangs, the monitor has gone into power-saving mode and is turned off.  OCCASSIONALLY, I am able to at least get the monitor to turn back on, but that is very uncommon.  Much more often than not, the machine is essentially dead.  When it does though, the screen looks completely normal

I see that you have tried using Radeon and Intel graphics, but my machine has an nVidia graphics card.   You also mentioned the xorg-graphics driver, and I did see some Xorg crashes on this machine during boot, but they seem to have stopped as I haven't seen it in a few days now.  I use FireFox instead of Chromium and have not seen Firefox crash at all.

This machine is pretty much barebones.  No ppas have been added.  Software has been added either via the Software Center (SABnzbd+), or git (SickBeard and CouchPotato).

I hope someone can find a resolution for us.

X

---

### Post by Diskdoc on 2014-05-15
Thanks for replying, both of you! I hope I have my problem pinned down now..a couple of more days of running would make me more certain - but it seems one of the two new memory modules is faulty. Odd though, because it passed Memtest several times (although froze it once). I simply started trying different combinations of memory modules and it seemed only to freeze/segfault when I had one of the new 4GiB modules installed.

---

### Post by matt_symes on 2014-05-16
Hi

> Odd though, because it passed Memtest several times (although froze it once)

That's not a pass if it freezes :D

I know someone else who had some new bad memory recently and had random crashes on a Windows box so that may well be the cause of the problem in your case.

Memtest is not a 100% reliable test of memory but it can be a good indicator that there is a problem. If memtest froze while running then i would certainly suspect a memory problem.

I hope that's the issue and fixes it.

Kind regards

---

