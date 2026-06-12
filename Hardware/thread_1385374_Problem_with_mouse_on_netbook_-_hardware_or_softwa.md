---
title: "Problem with mouse on netbook - hardware or software?"
date: 2010-01-19
forum: Hardware
---

### Post by Objekt on 2010-01-19
I have an Acer Aspire One netbook that went in for repairs recently, after it died abrutply for no apparent reason.
Now that I have it back, there is a very odd mouse problem that only happens under Linux.  I'm trying to determine whether it's a hardware problem, or a previously unknown bug which is peculiar to Ubuntu-based Linuxes.

The problem is that after a variable amount of time, the left mouse button stops working.  That is, no matter what mouse I use, I can't do a left-click.  The problem occurs with the built-in touchpad as well as a USB mouse, and only affects the left button.  I can still right-click, but having no left-click makes it impossible to do anything but drop to the command line & reboot from there.

I've tried 3 different mice, all wireless, plus the built-in touchpad.  Same problem in all cases.  All 3 wireless mice work fine on other machines, even other Acer Aspire One netbooks, regardless of OS.  The mice are two different models of Logitech wireless (one is a V450 Nano) and one Acer-branded wireless mouse, which came with an Acer netbook accessory kit.  They work fine on other desktops and other Acer netbooks running various Ubuntu-based distros.

This problem is only reproducible when running a non-Windows OS.  It doesn't happen under either Windows XP Home, or Windows 7 RC.  I've left both running for hours and hours, without the problem recurring.  When running Linux, the left mouse button goes dead after anywhere from a few minutes after getting to the desktop, to an hour later.

All the Linux distros I have tried so far have been Ubuntu- or Debian-based:

Mint Linux 8 (Helena)
Ubuntu Netbook Remix 9.10
Kuki Linux 2.8
Ubuntu 9.10

Problem was first observed when running the above Linuxes in Live mode off a USB stick.  I have managed to get Kuki Linux and Ubuntu Netbook Remix installed on the HDD as well, although it was hard to get it done before the left button stopped working.  The problem also occurs when running Linuxes that have been installed on the HDD.

FWIW, the netbook in question is a red Acer Aspire One D150-1920.  Atom N270 CPU, 1 GB RAM, no Bluetooth, 160 GB SATA HDD, etc.  It seems to have received a new mainboard as part of the repair process, because it has a slightly different set of networking hardware than before (probably a new motherboard revision, or whatever spares they had around the shop).  

WTF is going on here?  I am reluctant to call the repair shop for another warranty repair, and am not sure the netbook is really broken.  They don't officially support anything but Windows XP, and I don't want to pay return shipping yet again, just to have the same problem when I get it back or be told nothing's wrong with it.

---

### Post by t4thfavor on 2010-01-21
I always thought I was nuts, and that my Asus was broken or something, but now that at least one other person experiences this, I guess I can stop taking the pills.

I have an Asus eeepc 900a with 2GB ram, and 4GB flash. This is my second one as the first was stolen. When I got it (used) I thought that the button was broken, or somebody spilled something in it. I guess this is not the case, as I had 9.04 on the stolen one, and started out with 9.10 on this one.

I should also add that mine is sporatic as in it will work sometimes.

Keep a terminal open, and when it happens check the last few lines in dmesg.

---

### Post by Objekt on 2010-01-21
I tried another Linux distro & did not have the mouse button problem.  While I only had it running for a couple of hours, Puppy Linux did not exhibit the left-mouse-button-stops-working bug.  I am going to install Puppy later today for some longer-term testing.  Booting off the HDD vs. USB stick really shouldn't make any difference, but who knows?

Puppy Linux is an offshoot of Slackware, so maybe it's only Debian-based Linuxes that have this mouse problem on some netbooks.

The strangest thing is that my other two netbooks have no problems at all, despite one of them being exactly the same model.

I also posted about this problem on a forum just for Acer Aspire One users, but no one's responded yet.

---

### Post by t4thfavor on 2010-01-21
Kind of questionable that two of the same model have different outcomes. But with all the hardware jockeying that goes on in all of the major system producers factories, I am not suprised.

If you buy a Dell Vostro XXX in May, and then another of the same EXACT order in Aug they will most definately have different pieces inside them. 

I literally ordered one, and then called my sales rep and said another one like the last please, and they had different parts in them.

one had a pciE slot the other did not, one had 2 slots for RAM the other had 4, one had IDE the other had all sata. It's like they were playing a joke on me.

I could go on all day!

---

### Post by Objekt on 2010-01-21
I'll have to check it at home later, but I'm reasonably sure that the problem netbook is even the exact same SKU (D150-1920) as one of my other netbooks.

That said, I strongly suspect the repair shop changed out a major component or two.  I sent the system in because it died abruptly, in a manner that usually indicates mainboard replacement.  Apparently, I received a new mainboard that does not get along with Debian-based Linuxes, or perhaps some component of the Ubuntu GUI software.

I definitely received a different network adapter.  I now have an Atheros something or other for wired networking instead of what it had before (Marvell if I recall).  NICs usually being integrated into the mainboard today, that again suggests a different hardware revision.

Additionally, the Windows 7 RC install I had saved in a hard disk image before repairs suddenly thinks it is "not genuine" and demands to phone home.  Win 7 (including RC, it seems) is reported to do that after certain hardware changes.  A different mainboard may well have done it.

When I was running Puppy Linux, I used an alternate windowing system, something called Xvesa, instead of the Xorg server.  Puppy can also run with Xorg server, at the cost of more memory use.  I'm going to try Xorg next, to see whether the mouse problem recurs with Puppy.  I may have stumbled upon a bug in the Xorg windowing system on certain hardware.

---

### Post by llawwehttam on 2010-01-21
Personally I have seen a lot of bugs in Karmic. Lucid is coming out in April though and as it is a long term support release it should be very stable. There have also been several wireless bugs in the latest kernel.

---

### Post by pi/roman on 2010-01-21
You could try:
xinput list

to get a list of your input devices then use the id number to check it by:
xinput get-button-map "id#"

then make sure the first mapped number is 1. If not then use
xinput set-button-map "id#" 1 2 3

or maybe try other numbers if that doesn't work like:
xinput set-button-map "id#" 4 2 3

---

### Post by Objekt on 2010-01-21
> **t4thfavor said:**
> 
Keep a terminal open, and when it happens check the last few lines in dmesg.

Just tried that.  Nothing.  I opened a terminal and ran dmesg while the mouse was still working.  At that time, the last message was 
```
[  59.812042] eth0: no IPv6 routers present
```

After the left mouse button stopped working, I ran dmesg again and got the same result.

Is there some other command I could run to find out what the heck is going on?

---

### Post by Objekt on 2010-01-21
> **pi/roman said:**
> You could try:
xinput list

to get a list of your input devices then use the id number to check it by:
xinput get-button-map "id#"

then make sure the first mapped number is 1. If not then use
xinput set-button-map "id#" 1 2 3

or maybe try other numbers if that doesn't work like:
xinput set-button-map "id#" 4 2 3

Here's the weird thing about the xinput list:  There are a few entries that identify as "Chicony 2.4G Multimedia Wireless Kit."  That makes some sense, as the Acer wireless mouse is supplied by Chicony (a random Chinese mfg.).  However, each entry says it is a "KEYBOARD" instead of a mouse.

I ran get-button-map on each device that might have been the mouse, but all of them had buttons 1-to-whatever.  The number of buttons didn't necessarily make sense.

I'm really not sure what the deal is here.

---

### Post by Objekt on 2010-02-01
Problem solved by hardware breakage.  Left touchpad button stopped working completely, so I returned the netbook for a refund.  I won't have any more problems with that particular netbook.

---

### Post by macabro22 on 2010-02-01
My eee pc touchpad left button also stopped working in karmic.

---

### Post by JlyGrnMigt on 2010-03-04
I really don't think this thread should be marked solved.  This problem still affects a fair number of users, and no actual fix has been found.  Returning my computer is not an option.

---

