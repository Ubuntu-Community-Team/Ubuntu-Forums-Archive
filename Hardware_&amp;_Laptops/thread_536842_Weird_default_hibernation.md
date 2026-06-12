---
title: "Weird default hibernation"
date: 2007-08-28
forum: Hardware &amp; Laptops
---

### Post by Vadi on 2007-08-28
This really isn't a problem for me yet, but I just wanted to post since it might help some developers or somesuch.

I have my HD patritioned for Edubuntu and Ubuntu, Edubuntu was installed first. Each os has it's own uuid, but I've never tried yet fixing hibernation on my laptop. Last night I decided to try it out just to see if it'll work from my Ubuntu.

I've set it to hibernate, the laptop does a nice-looking fadeout shutdown. So that's good. Then I power it up, and... see the usual IBM logo on my ThinkPad T40 and then Grub. I thought that it didn't work, and since it was late, didn't want to wait for ubuntu to boot up, so I chose the memtest on my ubuntu patrition, and left it for the night.

Coming back morning today, the laptop it seems the laptop "fell asleep" - the screen was off. I press a key, memtest is still running, only 28% done. Wall time for some reason was at all zero's and started counting from there. I decide not to wait for it to finish, reboot, choose ubuntu. I get the usual ubuntu logo with an orange line, it starts loading... then I get a white fat horizontal line across my screen. Uh oh. I wait for it to continue, the screen gets a couple of weird video glitches, then suddenly, poof, my ubuntu desktop shows up, just like it was before. So apparently it looks like hibernation -did- work without me tinkering.

The only problem though is that the network manager took quite a long time to connect to the network and internet wasn't working even after it did. I rebooted and it was working fine after.

---

