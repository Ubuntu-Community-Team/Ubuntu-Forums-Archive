---
title: "ubuntu-drivers-common update causes system instability"
date: 2017-08-26
forum: Hardware
---

### Post by msobkow@sasktel.net on 2017-08-26
The new release of ubuntu-drivers-common for 17.04 causes system instability problems for my ASUS Prime B350-M/CSM based system with an AMD Ryzen 5 processor.

Downgrading to the original release of the drivers re-stabilized my system; I have the new release blocked from installing.  With the new release, my system spontaneously reboots a couple of times a day.

I suspect it is the driver for the RealTek ALC887 audio chipset that is causing the problem, as that driver has definitely changed.  I get static problems with Flash for the original release of ubuntu-drivers-common, which had gone away with the update.

I'm just concerned that this buggy driver might make its way into the next desktop release in October; I can't reinstall with the LTS release because of the Ryzen processor, and I can't live with the instability of the newer driver.  I need to be able to run my system for *days* at a time for some of my builds.

I wasn't sure where to report this, so I figured the forums might be monitored by the Ubuntu team.

---

### Post by msobkow@sasktel.net on 2017-08-29
Apparently I was wrong.  I looked into the change logs, and there is nothing in this package which has to do with the drivers themselves, only utilities for managing and installing drivers.  So I've re-enabled the update, and will see how things go.  If my system gets unstable again, I'll re-apply my downgrade-and-block script (I'm a sucker for scripts: I'm a lazy bastard.)

I'll post again in a couple of days and let you know one way or the other.

---

### Post by msobkow@sasktel.net on 2017-08-29
So far so good.

[COLOR=#1D2129][FONT=Helvetica]There has been a kernel update since I was having stability problems. Plus I've stopped using Firefox, which was causing the NVidia display driver to complain about illegal arguments and such. As the Nvidia driver runs kernel-level code, I now believe the root of my problems were caused by bad Firefox code.
[/FONT][/COLOR]
[COLOR=#1D2129][FONT=Helvetica]Linux may be secure, but that doesn't mean bad code can't take down a system if it finds a way past the protections normally employed for user-level code.

P.S. No problems with Flash playback, either.[/FONT][/COLOR]

---

### Post by msobkow@sasktel.net on 2017-08-29
*LOL* I just noticed the "First Cup of Ubuntu" tag.  I've been coding for *nix systems since 1983.  I think I might have a little more experience than that...

---

### Post by jeremy31 on 2017-08-29
If you wish to file a bug report see [https://ubuntuforums.org/showthread.php?t=1011078](https://ubuntuforums.org/showthread.php?t=1011078)
The "First Cup of Ubuntu" is based on your bean(post) count

---

### Post by mc4man on 2017-08-30
16.04.3 image has the same kernel as 17.04 so you should have been able to use. 16.04.4 will use 17.10's kernel & 16.04.5 will use 18.04's.
There is also the edge metapackage for 16.04 that gives earlier access to upcoming HWE
(- linux-generic-hwe-16.04-edge

---

### Post by msobkow@sasktel.net on 2017-09-01
No, I was just logging in to report that the system has been stable no matter what I threw at it for the past week.

I wasn't imagining the instability, but it seems to have been sorted out by the normal flow of updates for Ubuntu desktop.

No need to file a bug report for a non-bug. :)

---

