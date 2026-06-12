---
title: "Issues with suspend caused by fglrx driver in 13.10 and 14.04 (HP Probook 4540s)"
date: 2014-05-15
forum: Hardware
---

### Post by Shai Hulud on 2014-05-15
Hello, i have some issues on my laptop (HP Probook 4540s) with Radeon 7650M, that i think are caused by the fglrx driver.

On my 13.10 install with fglrx everything works normal - i can switch between the graphics mode (with restart), through the AMD control GUI, my wifi works. The only thing that is not working is suspend to ram. The weirdest part is that hibernating to the disk works without a hitch (no matter through pm-hibernate or through the gui). But when i try to suspend, in the beginning everything is fine - the computer goes to sleep, but when i try to wake it, i see only black screen.

Following some tips i tried playing some music before suspending so i can hear if the machine is waking up, and there is something wrong with the display waking, but nope, no music.
Also i've tried on the black screen after resuming to switch to another terminal (with Ctrl+Alt+F1), but no luck with that either.
I've found some people that recommend switching to another virtual terminal and then suspending - again no luck with that: i switch with Ctrl+Alt+F1, do pm-suspend and on waking i am again hit with the black screen.

My only option is cold reset.

I've tried fglrx-updates on Ubuntu and Kubuntu 14.04 and still have the same problem - no suspend (hibernate to disk works).
I did one install of Ubuntu 14.04 with disabled discrete videocard (so only intel drivers) and suspend to ram (as well as hibernate do disk) works. That led me to believe, that fglrx is at fault.

Any advice how i can rectify this situation?

tl;dr
Hibernate to disk works, but suspend to ram is not working on 13.10 and 14.04 with the fglrx(-updates) driver.
When i disable the discrete video card and use only the intel driver suspend to ram works.

P.S. One additional question that is not so important - i think i saw somewhere, that in 14.04 switching between videocards should be possible without restart, but when i try to switch i have to restart. So is there some option to switch without restart, or this article is just a figment of my wishful thinking? :)

---

### Post by Graeme_Pietersz on 2014-08-23
I think with 14.04 it is supposed to use both card dynamically (rendering on the Radeon) - Google radoen muxless.

Suspend works for me with the radeon driver, but freezes on resume with fglrx.

I do have a problem with the graphics chips overheating though (even with the radeon turned off in the BIOS)

---

