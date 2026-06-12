---
title: "Need help getting Wubi to start over. (vista)"
date: 2009-01-01
forum: Installation &amp; Upgrades
---

### Post by jrounds on 2009-01-01
I am on vista. So 3 months ago I was goofing around with Wubi.  What I did was create two partitions on an external harddrive.  One was for the wubi install and one was for the ubuntu OS.  I was trying to get the ubuntu OS to boot via wubi change to the Vista booting.

That failed.  It left an option at start up on my laptop to boot from vista or ubuntu.  I ignored it till now.

I went to uninstall wubi/ubuntu via vista control panel and it did notta.  Nothing.

So still interested in ubuntu I thought maybe just running a Wubi install on a new partition this time on my laptop harddrive (the correct way) will get it to fix the boot options.  I did that and restarted and Ubuntu booted.  Set apt failed on install and I think only minimal hardware was installed.  And to make it wierder it turns out this ubuntu install depends on the external harddrive connection to boot.

And to make matters even worse a freshly downloaded copy of wubi installer does nothing when executed.  Just nothing...  While the old wubi on the external harddrive still works.

Here is what I want to do now.  I want to clean this vista installation and booting and start over right.

But I can't figure out how to proceed.  I have a minimally working copy of Ubuntu if there are commands there that can do it.  And I have a working copy of visa but it seems to ignore the wubi uninstall/new wubi.

Help?  Thanks

---

### Post by jrounds on 2009-01-01
EasyBCD solved this in about 15 seconds in a completely intuitive manner (I still have remaints of an uninstalled "program" in windows, but booting is cleaned which is the big issue.)

It was indeed set to boot from the external drive in some sort of haphazard manner. 

Now for round 2.

---

