---
title: "Thinkpad does not suspend"
date: 2006-06-17
forum: Hardware &amp; Laptops
---

### Post by eferrari on 2006-06-17
Has anyone else had suspend problems after the latest software update?

I am running 6.06 on a thinkpad T42 - everything was working fine until I did a software update Friday (June 16th).

The thinkpad no longer suspends entirely. I have never seen anything like this. The screen blanks and the half moon led lights up, but the machine is still half on -- The cooling fan still runs and I can do things like turn on/off the keyboard light

I have waited for hours for the suspend to complete - it doesn't. The only way out of this half-asleep state is to kill power to the machine and reboot.

Has anyone else seen this?
Does anyone know how I can start to debug this problem?

---

### Post by eferrari on 2006-06-17
It appears that someone posted a nearly identical thread at the same moment I was posting this thread. 

See this thread:
[http://ubuntuforums.org/showthread.php?t=198327](http://ubuntuforums.org/showthread.php?t=198327)

---

### Post by yzord on 2006-06-17
Here's the launchpad entry for the problem:
[https://launchpad.net/distros/ubuntu/+bug/50031](https://launchpad.net/distros/ubuntu/+bug/50031)

Looks like a Thinkpad problem. I have an X31 which unfortunately cannot either suspend or hibernate, although suspend works with the older 2.6.15-23 kernel.

Yz

---

### Post by mpvano on 2006-06-18
I think it's wider than that. My old Sony VAIO PCG-F540 reports "suspend failure" after resuming (even though it appears to suspend/resume properly) with the latest kernel, but not the earlier ones.

I've tried to add this information to the bug thread, but Malone never works right for me. It always acts like I'm not logged in, even after accepting my password (I even tried resetting it). I also see a lot of similar threads being started by owners of other brands.

I use a T30 myself, but have decided to stick with breezy for a few more weeks until things settle down a little more - so far it looks like about half of the Dapper update gets automatically replaced immediately after an install due to serious problems! (I've got it running on three other machines now.)

Mario

---

