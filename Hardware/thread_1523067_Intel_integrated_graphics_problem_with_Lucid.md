---
title: "Intel integrated graphics problem with Lucid"
date: 2010-07-03
forum: Hardware
---

### Post by sambarluc on 2010-07-03
Hi,
the integrated graphics of an Intel Core i5 540 does not work on Ubuntu 10.04. I could upgrade from 9.10, but the monitor is black. I can hear the sound of the login screen, but the screen is just black. If I boot with the older kernel 2.6.31.22 (instead of 2.6.32.23) it works with no problem. The live CD does not work either. On Launchpad somebody reported similar things, but I couldn't find a clean solution.
Any idea?
Thanks.

---

### Post by Yarui on 2010-07-03
If it works with the old kernel and not the newest one it would probably be best to just use the older one for now.  It is only a month or so older than the current one, it was released after 10.04, so it's not like it is some outdated piece of junk.  This is the reason why old kernels are saved on your system, because sometimes new kernels can cause hardware issues.  If you are lucky the next kernel, which will probably be released in just over a month, won't have the same issue.  There is, however, nothing wrong with trying to figure out what's causing the problem, of course.

---

### Post by sambarluc on 2010-07-04
The point is that other things do not work with this kernel, like the speakers (work on newer kernel), the brightness control (can't say) or wireless (can't say either).

---

### Post by davidmohammed on 2010-07-04
have you tried booting with i915.modeset=1 or nomodeset as your grub setting? (Press shift on boot to display the list of kernels - press e and add one of the options immediately before quiet splash)

---

### Post by sambarluc on 2010-07-04
Yes, I tried that, but doesn't work (I think that's meant for nvidia cards). The system blocks, with black screen.

---

### Post by davidmohammed on 2010-07-04
some intel graphics you need to turn off kms - boot with i915.modeset=0.  Does that work?

---

### Post by sambarluc on 2010-07-22
I tried that, but it doesn't work...
I really hope a new kernel comes out soon, because it's disappointing having to choose between sound and video (not) working...

---

### Post by Fiery Spirited on 2010-08-17
I have a newly purchased Dell Latitude E5510 and did a clean install on it with 10.04. I did not encounter any problem with the graphics. The kernel I am using is 2.6.32-24-generic.

---

### Post by unratedexter on 2010-09-07
> **Fiery Spirited said:**
> I have a newly purchased Dell Latitude E5510 and did a clean install on it with 10.04. I did not encounter any problem with the graphics. The kernel I am using is 2.6.32-24-generic.

Hi Guys,
 We are experiencing the same *****, and we use ubuntu as dev laptops (as I'm pushing ubuntu more than windows 7 for our company :). Has anyone tried to get the latest 10.10 working on the e5510?

I think I might try it out - I'll report back if there is some hope.

---

### Post by sambarluc on 2010-09-07
Using kernel 2.6.35, the (stable) kernel from Ubuntu 10.10, inside 10.04 works 100% on my HP 8440p. And, incidentally, it also solves some problems I had with my wireless.

---

### Post by eclectica on 2010-09-10
does it need to be 64 bit Ubuntu? maybe that is the problem.

---

### Post by eclectica on 2010-09-11
I just ran a test.  Ubuntu 10.04.1 64 bit also doesn't install on the Dell Latitude E5510.  But 10.10 alpha-3 32 bit desktop does.

---

