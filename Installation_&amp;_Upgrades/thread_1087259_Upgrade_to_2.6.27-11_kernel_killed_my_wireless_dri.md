---
title: "Upgrade to 2.6.27-11 kernel killed my wireless driver!"
date: 2009-03-04
forum: Installation &amp; Upgrades
---

### Post by wacky_keyboards on 2009-03-04
I'm hoping there is a simple solution to this issue.  I've
seen similar posts in other forums, but nothing quite
addresses this problem.

About a month ago, I pulled down upgrades through the Update
Manager which "upgraded" my kernel from 2.6.27-9 to 2.6.27-11.
When I rebooted into the new kernel, however, I discovered
that I had lost access to my wireless drivers.  For example:

     % sudo ifconfig wlan0 up
     wlan0: ERROR while getting interface flags: No such device

My wired access is unaffected.  Also, if I boot back into the
2.6.27-9 kernel, then I have complete network access again.

In other posts which describe similar issues, the suggested
solution was to "reinstall the drivers."  However, I had not
installed any drivers explicitly -- whatever was installed
when I installed Intrepid Ibex from the CD, and subsequently
through the Update Manager, is what I have/had.

Can someone provide help?

Thanks!

---

### Post by ptn107 on 2009-03-04
Make sure that during the kernel update that 'linux-restricted-modules-common' and 'linux-restricted-modules-2.6.27-11-generic' were installed and both are version 2.6.27-11.16.

'linux-restricted-modules-2.6.27-11-generic' in particular is what contained the wireless drivers (ath_pci) for my desktop.

*FYI, originally intrepid installs version 2.6.27-7.12.

---

### Post by wacky_keyboards on 2009-06-18
(Trying to close out threads that I opened.)

I was not able to verify that these modules were installed, so I gave up and went back to using the 2.6.27-9 kernel.  Toward the end of May, I pulled down a bunch of updates which included an upgrade to the 2.6.27-14 kernel, and magickally my wireless was running again.  So I presume the issue was resolved in between!

---

### Post by wacky_keyboards on 2009-06-18
Er, so how does one go about closing one's old threads?

---

