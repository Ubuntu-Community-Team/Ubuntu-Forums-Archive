---
title: "problems with 11.04 on Acer 2010 laptop"
date: 2011-05-09
forum: Hardware
---

### Post by VogonZarniwoop on 2011-05-09
I have done a fresh install of 11.04 on my Acer 2010 laptop, which used  to be, gosh.. maybe 9.04 or perhaps even older than that, I forget  exactly.  The older kubuntu was more or less working fine.  11.04 I'm  having a lot of problems though.

* Even the install CD won't boot without acpi=off.  Once the system is  installed, I must also boot with acpi=off, but then a bunch of stuff  doesn't work at all like the battery monitor, suspend, or proper  operation of the power switch.  Anybody know why this might be?

* Wireless, which was working in 9.04, is fubar.  At least 9 boots out  of 10, rather than the wireless adapter showing up as "eth0" as it  usually does, it shows up as "eth1-eth0".  (Yes, exactly like that, with the dash in the name).   When that happens, it doesn't work at all.  The KDE network thing  doesn't even show its usual settings for wireless, and the "Settings"  area for wireless is greyed out.  Strangely, every once in a rare while  if i reboot, it shows up as "eth0" and then everything is fine, and I  can connect with no problems.

Unfortunately, the wireless problem is a showstopper for me.  Does  anyone have ideas about it?  I've been through the Ubuntu wireless faqs,  some of which are kind of complicated, but nothing i have found in  there has helped me.  Even after reading all that stuff, I don't know  why the wireless adapter appears as "eth1-eth0" most of the time.  I've tried rmmod and modprobe of ipw2200, but it doesn't help.

The acpi problems are not fatal, but are rather annoying, so I'd like to figure that out too.

Thanks for any ideas!

On the plus side, sound worked out the box.  Sound *never* works for me  out of the box on Linux.  Now I've got sound, but no networking.  I  guess you can't have everything :D.

---

### Post by VogonZarniwoop on 2011-05-09
Oh, and relatedly is there a way to get the wireless adaptor to be called "wlan0", like it is on my other laptop?  I don't like this "eth1-eth0" name, never mind that it doesn't even work :)  I don't know how to rename them and the only thing I found by googling was a really long hairy page of instructions that looked downright scary.

---

