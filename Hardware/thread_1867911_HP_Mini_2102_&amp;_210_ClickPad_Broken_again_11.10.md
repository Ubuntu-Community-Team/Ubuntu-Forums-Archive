---
title: "HP Mini 2102 &amp; 210 ClickPad Broken again 11.10"
date: 2011-10-23
forum: Hardware
---

### Post by VideoRoy on 2011-10-23
Well I decided to upgrade to 11.10 from 11.04 and the clickpad is broken again.  I am really regretting the upgrade since it took me weeks to get it working in 11.04 and all previous patches do not work except for the PSMOUSE addition to modprobe.

Many other things seem to be fixed in 11.10 but is seems this basic feature is still broken almost 2 years later for me.  The Fedora and SUSE distros seem to have solved this and SUSE is in fact where the patches came from for the 11.04 fix but I am not skilled enough to go and add them back into the 11.10 default Synaptics driver.

So I added the old "options psmouse proto=exps" line to the /etc/modprobe.d/psmouse.modprobe config file but of course that disables the Synaptics driver and cripples the clickpad to basic functionality.

This might seem like a minor thing to many, but not being able to use the basic input features on my main computer is enough of a headache that I am going to have to explore the other distros until this can get fixed.

I dual boot into Win7 since it came with Mini and will have to use that for my work until I can find a better Linux solution.  I have invested a lot into Ubuntu and will continue to use it on my server and another computer but it is just not worth the reduced functionality on something I depend on 100% of the time.

If you have an HP Mini 2102 or 210 I would recommend not doing the upgrade at this time.

---

### Post by VideoRoy on 2011-10-23
Just when I had given up hope, began downloading SUSE and wasted 6 hours on this, I found a patch the Sergio Faria created.

His PPA and patch are here:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/582809/comments/275]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/582809/comments/275")

This puts me back to the original functionality I had with 11.04.  One word of warning for those that have been using the PSMOUSE fix.  When you load that fix it disables the Synaptics driver and you do not get the benefits of the patch.  I think that was a mistake that many made previously.  I had never used the PSMOUSE hack before but now it makes sense why people did not see the same benefits I did previously.

I have faith again that this may get fixed in the future.

---

### Post by kvichare on 2011-12-12
Thanks VideoRoy. This worked on my HP Pavilion dv5 2134us. I was trying to get reasonable clickpad functionality when I lost it after upgrading to Ubuntu 11.10 Oneiric Ocelot.
K.

---

