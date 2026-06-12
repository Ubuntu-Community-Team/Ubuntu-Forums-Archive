---
title: "openprinting-ppds-postscript-hp cannot be authenticated!"
date: 2009-05-15
forum: Installation &amp; Upgrades
---

### Post by aberrios on 2009-05-15
While doing upgrades this morning found this error:

The following packages will be upgraded:
  openprinting-ppds-postscript-hp
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 1217kB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? 
WARNING: The following packages cannot be authenticated!
  openprinting-ppds-postscript-hp
Install these packages without verification [y/N]? n
E: Some packages could not be authenticated

Is this a package from the Intrepid repository, can not find any reference, just one called hp-pppd. Verifying third party apt sources can not find either.

I am puzzled.

---

### Post by BrainwreckedTech on 2009-05-16
I had to do a little digging on this too.  Here's what's going on.

If you run sudo apt-get update in a terminal window and then scroll back up the output, you'll notice lines like these:

```
Ign [http://www.openprinting.org](http://www.openprinting.org) lsb3.2 Release.gpg
Ign [http://www.openprinting.org](http://www.openprinting.org) lsb3.2/postscript-hp Translation-en_US
Get:10 [http://www.openprinting.org](http://www.openprinting.org) lsb3.2 Release [30.2kB]
Ign [http://www.openprinting.org](http://www.openprinting.org) lsb3.2/postscript-hp Packages
```

Hitting openprinting.org, even though openprinting.org is NOT in /etc/apt/sources.list?  This, coupled with the fact that these are open-source drivers, leads me to belive that the package list for the main repository is pointing this package over to openprinting.org instead of us.archive.ubuntu.org.  By default, the apt system in Ubuntu only has keys for ubuntu.com servers.

If you check out [The Linux Foundation's OpenPrinting Driver List]("http://openprinting.org/driver_list.cgi"), you'll see a whole slew of drivers, including Postscript-HP.  If you read [this Linux Foundation forum thread](http://ldn.linuxfoundation.org/forum/key-signing-downloadable-printer-driver-packages) you'll get the gist of what's going on.

I completely get that users will be able to get the most up-to-date drivers as soon as possible with this method.  But by taking this shortcut (which I don't think was taken in previous versions), the Ubuntu devs have tripped their own security system.

---

### Post by aberrios on 2009-05-19
thanks!

Now there is reasonable doubt!

---

