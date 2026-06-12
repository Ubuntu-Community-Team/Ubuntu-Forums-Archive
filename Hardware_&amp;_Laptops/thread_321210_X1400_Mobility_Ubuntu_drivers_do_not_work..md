---
title: "X1400 Mobility Ubuntu drivers do not work."
date: 2006-12-18
forum: Hardware &amp; Laptops
---

### Post by raid517 on 2006-12-18
Hi I reported this bug here:

[https://launchpad.net/distros/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/76338](https://launchpad.net/distros/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/76338)

> Hi I am writing to report that the FGLRX ATI drivers included in the linux-restricted modules package are incompatible with Radeon mobility (laptop) chipsets. This isn't just restricted to the 2.6.20-2 restricted modules - it is also true of all restricted-modules packages to date.

From my own experience the generic drivers for the ATI X series of cards (as in X1500, X1600, X1700 etc) which are applicable to desktop systems, are *not* the same as those for the equivalent ATI mobility series of cards which are intended for laptop use - and are rarely if ever interchangeable. Installing the linux restricted modules package on a laptop appears to cause the generic desktop fglrx modules to be installed - which as I said, simply does not work.

Previously to overcome this I simply used this script from Kanotix.com: [http://www.kanotix.com/files/install-fglrx-debian.sh](http://www.kanotix.com/files/install-fglrx-debian.sh) which pretty much took care of all of the most difficult issues - often also patching for incompatibilities with existing kernel versions. This script has always been excellent for this - and in many senses I would highly recommended it.

However this script is also incompatible with the latest FGLRX drivers and the 2.6.20-2 kernel - and now Kanotix itself as a project looks like it may be in the process of an implosion - so it is not at all clear if this script will be maintained any more. (It was however effective right up until the latest 2.6.19 Kubuntu kernel release).

There should almost certainly be a dialog that allows you to select the appropriate driver type for one's system (i.e.desktop or laptop) and also perhaps a modified/updated version of this script could be run to ensure atomatic configuration of the appropriate driver parameters.

I would very much like to be able to maintain my system directly through the Ubuntu repositories rather than being required to always seem the assistance or advice of third parties.

Please if any of you guys have experienced this bug, could you kindly confirm it?

In the meantime I would be very grateful if anyone could offer some kind of work around.

Has anyone here ever experienced a similar issue?

---

### Post by zybir on 2006-12-21
I am new to linux, and recently installed it on my Dell e1505/6400 laptop which has a x1400 Mobility.  I've been tinkering and searching for a solution and nothing has worked, editing the xorg.conf, installing different driver packages, and after a week of troubleshooting I found you post.  I have yet to get it to work.  I really hope this is resolved soon,  I don't like having to dual boot :(

---

### Post by raid517 on 2006-12-21
As far as I can work out the FGLRX drivers that are included in the repositories are strictly for desktop users only - and do not work for laptop owners.

If you don't mind however, it is possible that you can do more than 'hope', as the only way this will get fixed is if people who have encountered this issue confirm the bug.

In the meantime you can use this script to install the official (and correct) FGLRX drivers:

[http://www.kanotix.com/files/install-fglrx-debian.sh](http://www.kanotix.com/files/install-fglrx-debian.sh)

Make sure you remove these lines:

```
if [ ! -f /etc/kanotix-version ]; then
 echo Error: No KANOTIX found. Do not ask for support!
 exit 100
fi
```
You will probably need all the build essential and module-utils, kernel headers and so on too and make sure you make the script executable and put it in /usr/local/bin/ and then quit X.

Then from the command line just type install-fglrx-kanotix.sh hit enter and everything else should be taken care of.

Again though please don't take this as a 'solution'. It isn't. Its a workaround. The correct drivers should be supplied.

---

### Post by zybir on 2006-12-22
You officially can claim my first born, all the other first born promises are nullified, it's all yours.  Thank you so much, this worked perfectly.

---

### Post by raid517 on 2006-12-22
NP. I'll pass on the offer of your first born child if you don't mind - my own kids are enough of a financial drain on me at the best of times.

Instead as I said, it would be useful if you also confirmed the bug.

This is not a solution provided by Ubuntu. Ubuntu do not at this time provide a viable working solution - and it is not clear at this time how much longer the script I pointed you to will be maintained.

So Ubuntu need to preferably provide their own solution ASAP.

---

### Post by NTolerance on 2006-12-26
I've got an E1505 with the Mobility X1400.  I've been using the fglrx drivers provided by the Ubuntu repositories from the Dapper betas all the way up to Edgy and have never had a problem.  I've been using this guide for installation:

[http://wiki.cchtml.com/index.php/Ubuntu](http://wiki.cchtml.com/index.php/Ubuntu)

Other than "not working", what problem are you experiencing?

---

