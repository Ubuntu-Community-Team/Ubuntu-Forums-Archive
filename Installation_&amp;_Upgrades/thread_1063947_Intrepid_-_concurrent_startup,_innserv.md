---
title: "Intrepid - concurrent startup, innserv?"
date: 2009-02-08
forum: Installation &amp; Upgrades
---

### Post by Dusenberg on 2009-02-08
Hi

Any experience out there on concurrent startup on Intrepid / innserv?

I just moved to Intrepid 8.10 from Gutsy (clean install) on my dual-core laptop and things going real well.  I had concurrent startup setup on Gutsy (concurrency=shell in init.d/rc along with some fixes for 7.10) and it worked. Now I want to do on 8.10 and i read the following in the std rc script - basically warning that init scripts need to be in correct sequence and pointing you to innserv package

> 
# Specify method used to enable concurrent init.d scripts.
# Valid options are 'none', 'shell' and 'startpar'.  To enable the
# concurrent boot option, the init.d script order must allow for
# concurrency.  This is not the case with the default boot sequence in
# Debian as of 2008-01-20.  Before enabling concurrency, one need to
# check the sequence values of all boot scripts, and make sure only
# scripts that can be started in parallel have the same sequence
# number, and that a scripts dependencies have a earlier sequence
# number. See the insserv package for a away to reorder the boot
# automatically to allow this.
CONCURRENCY=none
 

I do not know id the std 8.10 rc scripts are correctly sequenced - do you?

Checking the inserv website [http://packages.debian.org/unstable/misc/insserv](http://packages.debian.org/unstable/misc/insserv) warns as follows:
> 
This utility reorders the init.d boot scripts based on dependencies given in scripts' LSB comment headers, or in override files included in this package or added in /etc/insserv.

This package should be used with care, as incorrect or missing dependencies can lead to an unbootable system. 


Anybody used innserv or know how to setup concurrency??

Cheers

---

### Post by duanedesign on 2009-09-14
I am also curious about this issue.

I am using Jaunty and when looking changing the concurrency in /etc/init.d/rc i came across the paragraph mentioned in the previous post. Is it necessary to run insserv? Is it recommended? Any insight using insserv or changing concurrency in /rc would be appreciated.

---

### Post by wyrless2002 on 2009-10-14
I took the chance and changed concurrency=shell with no ill effects. It does speed up the boot process, but I don't know if I just got lucky and everything was satisfiable. I'll be watching this post to see if someone can shed some light on using or installing insserv.

---

