---
title: "Netgear GA511 NIC crash"
date: 2007-02-17
forum: Hardware &amp; Laptops
---

### Post by madoka on 2007-02-17
I have a Netgear GA511 network card, which I'm pretty sure is causing my ThinkPad T23 to crash on a weekly basis, since this is what I see in /var/log/messages once I rebooted:

```
Feb 17 02:44:49 skuld kernel: [43699361.990000] eth1: Rx ERROR!!!
Feb 17 02:44:49 skuld last message repeated 2 times
Feb 17 02:44:49 skuld kernel: [43699362.120000] eth1: Rx ERROR!!!
Feb 17 02:44:49 skuld last message repeated 2 times
Feb 17 02:44:51 skuld kernel: [43699364.450000] eth1: Rx ERROR!!!
Feb 17 02:44:51 skuld last message repeated 2 times
...
Feb 17 02:52:09 skuld syslogd 1.4.1#18ubuntu6: restart.
Feb 17 02:52:09 skuld kernel: Inspecting /boot/System.map-2.6.17-11-server
...
```

I don't think the card's faulty, since the identical system ran fine for at least a month under Windows XP.  I'm using the r1000 driver, instead of the r8169 driver, since the latter will not put the card in Gigabit mode for some reason, even when I turn off auto-negotiation.

Perhaps I should trying using ndiswrapper?

---

### Post by tgalati4 on 2007-02-20
Network cards do fail and Linux does not handle hardware failure gracefully (depending on your point of view).  What looks like a freeze is really the operating system waiting for data.  Data never comes.  System can't continue until it gets data!  Since networking is vital to the kernel, any problems with networking cause the kernel to act strange.

Try this:

Remove the card, run memtest over night.  (It's listed in the grub boot up menu or the Live CD).  Make sure your memory is OK.  Sometimes you need to reseat it.  Especially on tankish T-Series machines.  Run at least 10 passes (that should take some time).

Does the card get unusually hot in gigabit mode?  Try running it in 100 mode for testing purposes.  A T-23 is an older machine.  I can't think of anything it can do that would require gigabit performance.  Perhaps you are plugged directly into the Internet Pipe?  "I need gigabit speeds so I can:"

Watch high def movies?  No (I don't think the T-23 can play decent video)
Play high-quality audio streams?  No
Send birthday pictures to Grandma?  No
Predicting ice storms using a super computer to prevent the stranding of a 1000 passengers?  Yes

If you answered more than one yes, they by all means use gigabit.

Just because you can do something doesn't mean it's a good idea.  I have 10-base and 100-base cards that get toasty and sometimes freak out.  I can't imagine a cardbus card running at microwave speeds.

ndiswrapper will probably work.  Were you getting gigabit speeds in Windows?  Does the card work now in Windows?

Find another computer to test the card on, or purchase another card.

My gut feel is that the card is getting hot causing timing errors on the bus which causes freeze ups.  Run it at 100 megabits per second and be happy--unless you were one of those stranded passengers.

---

### Post by madoka on 2007-02-23
> **tgalati4 said:**
> Network cards do fail and Linux does not handle hardware failure gracefully (depending on your point of view).  What looks like a freeze is really the operating system waiting for data.  Data never comes.  System can't continue until it gets data!  Since networking is vital to the kernel, any problems with networking cause the kernel to act strange.

Try this:

Remove the card, run memtest over night.  (It's listed in the grub boot up menu or the Live CD).  Make sure your memory is OK.  Sometimes you need to reseat it.  Especially on tankish T-Series machines.  Run at least 10 passes (that should take some time).
It's really unlikely that the memory's faulty.  I've ran memtest overnight before, and I haven't really moved the laptop around much since then, because its LCD's busted.  And I also ran memtest a few days ago (only 1 pass) for an unrelated reason.

> Does the card get unusually hot in gigabit mode?  Try running it in 100 mode for testing purposes.  A T-23 is an older machine.  I can't think of anything it can do that would require gigabit performance.  Perhaps you are plugged directly into the Internet Pipe?  "I need gigabit speeds so I can:"

...

ndiswrapper will probably work.  Were you getting gigabit speeds in Windows?  Does the card work now in Windows?
I'm using the T23 as a firewall / file server (since the screen's broken); the Gigabit NIC is LAN-facing.  I've not considered the heat issue, and I guess the closet where it's sitting in can get quite hot.  I'll keep the closet door open, and run the card at lower speeds to see if that helps.

Nevertheless, the same setup (in the closet) ran fine in Windows.  As a Gigabit NIC, GA511 is not very good: I'm getting between 100Mbps ~ 150Mbps.  However, I already knew that before I bought the card.  Also, since the T23 is quite old, there are other bottlenecks anyway.

ndiswrapper indeed work, but the driver doesn't support promiscuous mode!  So VMware doesn't work, and I didn't find out if ndiswrapper is more stable.  Maybe I can work around the issue (host-only adapter + bridge mode?), but I've already zapped the install.  I'm not ready to completely give up yet, so it's running OpenBSD at the moment.

> Find another computer to test the card on, or purchase another card.

My gut feel is that the card is getting hot causing timing errors on the bus which causes freeze ups.  Run it at 100 megabits per second and be happy--unless you were one of those stranded passengers.

Temperature may indeed play a role here.  However, a possibly related problem occurs on OpenBSD (see [http://www.bsdforums.org/forums/showthread.php?t=46424](http://www.bsdforums.org/forums/showthread.php?t=46424)), and the error shows up immediately, so presumably the card shouldn't be very hot yet.

It's funny that you should mention that I buy another card.  My original plan was to run OpenBSD, and I bought the GA511 because it's in the supported hardware list ([http://www.openbsd.org/i386.html](http://www.openbsd.org/i386.html)).  When that didn't work out, I got a different NIC (DUB-E100), but only the older revision was supported ](*,)--it doesn't work in edgy either, but newer version of the kernel appears to support it, so it'll probably work in feisty fawn.

I'm not sure I'll have better luck the 3rd time around. :(

---

### Post by tgalati4 on 2007-02-23
Cracked LCD screen?  Sounds like the machine has taken some abuse.  Just because it works doesn't mean it's 100%.  There could be an intermittent motherboard trace that is acting up.  Laptops don't take kindly to impact and perhaps hidden damage is starting to appear.  Try changing the orientation, horizontal to vertical for instance.  This will change the gravity load on the board and may change it's behavior.

---

