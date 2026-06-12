---
title: "tring to install"
date: 2009-04-03
forum: Installation &amp; Upgrades
---

### Post by kadds on 2009-04-03
just got a used ibm t30 laptop. has a 40gig drive that i partitioned to 30 and 10.
want to install ubuntu 8.1 on 10gig
using the same dvd iso disk i installed on desktop.
the laptop will not read disk in windows or boot with it, it works ok in desktop.  haved tried other burnt't dvd in laptop that i have made and it reads ok.

any ideas

---

### Post by leonardo_neo on 2009-04-03
> **kadds said:**
> just got a used ibm t30 laptop. has a 40gig drive that i partitioned to 30 and 10.
want to install ubuntu 8.1 on 10gig
using the same dvd iso disk i installed on desktop.
the laptop will not read disk in windows or boot with it, it works ok in desktop.  haved tried other burnt't dvd in laptop that i have made and it reads ok.

any ideas

What other burnt DVD you tried on the laptop? Is it .iso boot file DVD, or any other media file?

Well, from your description, I can guess that either the boot CD has some errors, or in the laptop's BIOS setting, disk boot is not in the first preference. Check both of these issues.

---

### Post by kadds on 2009-04-03
i have tried 3 movies that all work ok
i have a mandriva 2009 dvd that will not read in the laptop also
i have a win98 "cd" that will boot in the laptop
again both linux dist will boot and read ok in desktop pc
when booting with laptop, i'm selecting to boot with cd-rom first

---

### Post by paradigm2 on 2009-04-03
> **kadds said:**
> i have tried 3 movies that all work ok
i have a mandriva 2009 dvd that will not read in the laptop also
i have a win98 "cd" that will boot in the laptop
again both linux dist will boot and read ok in desktop pc
when booting with laptop, i'm selecting to boot with cd-rom first

I had much the same problem:

[http://ubuntuforums.org/showthread.php?t=1114556](http://ubuntuforums.org/showthread.php?t=1114556)

Is the CD Check utility on the Laptop reporting an error?  It did for me with 11 different disks and burining the ISOs at the lowest setting.

I ended up having to set up a DHCP and tftp server on my desktop and then set the laptop to install using a network boot!  You do that it seems like you need to have an extra switch or router laying around where you can disable DHCP on it and put it downstream from your primary router.  Since Router1 and router2 will be on different subnets, the DHCP Servers won't interfere.  It's a pain to set up, but I can verify that it works.  It would have been easier if I had a usb drive.

One thing you might try is to burn it on a regular CD-R not as a DVD.  Perhaps the format will make a difference?

---

### Post by kadds on 2009-04-03
got it to work
redownloaded .iso file 700meg and burned it to a cdr
the laptop will read this disk ok
I wonder why it will not read a burned dvd data disk?

---

