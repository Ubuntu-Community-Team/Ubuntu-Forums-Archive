---
title: "wicd fails to connect on reboot"
date: 2009-04-20
forum: Hardware
---

### Post by jackal242 on 2009-04-20
I'm having this problem that on reboot wicd fails to connect or see my remote basestation.

When I launch wicd is says, no basestations found.

However, when I click REFRESH, it sees the basestation, and I can click it and connect - no problem.

So what would prevent wicd from seeing the basestation on reboot? Why do i have to click REFRESH before it sees the basestation?

Just seems like a wasted step to have to do every time you log in....

This is on Ubuntu 8.04 on a Dell Netbook 12.

---

### Post by kerry_s on 2009-04-20
in the preferences, remove "wired interface" just leave it blank if your not using it. in external programs, pick your dhcp type, i think dhclient is the default in ubuntu. that will speed up the finding.

in the connection window, open the drop down, make sure "use as default" is checked, open scripts and advanced settings, just click okay for both of those, you don't have to put nothing, but if you don't open them it won't be saved.

wicd is pretty slow, most python programs are, give it a minute see if it is even attempting to start, you can hover the mouse over the icon to see what it's doing.

forgot 1, make sure you uncheck the ethernet as default.

---

### Post by jackal242 on 2009-04-20
> **kerry_s said:**
> in the preferences, remove "wired interface" just leave it blank if your not using it. in external programs, pick your dhcp type, i think dhclient is the default in ubuntu. that will speed up the finding.

in the connection window, open the drop down, make sure "use as default" is checked, open scripts and advanced settings, just click okay for both of those, you don't have to put nothing, but if you don't open them it won't be saved.


I've already done all that.   This is a WPA2 connection so I had to fill out the "advanced settings" to make it connect in the first place.

And wired interface is disabled.

So I already have all that set.

Again - the problem is that the computer is not seeing the basestation WITHOUT running wicd manually and clicking REFRESH to see the basestation first.

---

### Post by imdano on 2009-04-21
I think this is caused by bug where wicd doesn't keep rescanning when its initial scan doesn't find any results.  For whatever reason (either the wireless interface wasn't ready yet, or it just didn't find any networks on the first scan attempt), your wireless driver doesn't find any networks on the initial scan wicd triggers, so wicd can't automatically connect to anything.  Now, from there wicd should keep trying to scan periodically until you connect manually or it finds a network to autoconnect to.  Unfortunately I think this doesn't work correctly in v1.5.9.  I also believe it is fixed in the soon-to-be-released 1.6.0.

As a little experiment, you can try disconnecting from all networks, then kill wicd and wicd-client and restart them.  I'd expect it to automatically connect you in that case, since your wireless interface should be able to find networks when wicd triggers a scan.

---

