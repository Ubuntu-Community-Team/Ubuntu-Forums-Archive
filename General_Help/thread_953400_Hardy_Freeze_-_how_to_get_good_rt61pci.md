---
title: "Hardy Freeze - how to get good rt61pci?"
date: 2008-10-20
forum: General Help
---

### Post by 2CV67 on 2008-10-20
Hi Guys!

I may use some big words here, but don't be fooled - I am a dummy & need dummy-level help.

I have an Edimax 7128g PCI card with RT2561 chipset.

In Hardy, this causes freezes (with Caps Lock & Scroll Lock flashing - needing hard reboot) every few minutes, so that Ubuntu is totally useless, no - TOTALLY USELESS!

Bashar, from the French Ubuntu Forum, pointed me at a way of getting a later version of rt61pci (going from 2.0.10 to 2.1.4) via backports and that worked 100% for me, from 6 September to 16 October with zero freeze.
That was with kernel 2.6.24-19.

On 16 October, the kernel got updated to 2.6.24-21 and the freezes came back immediately. (along with 2.0.10)

I was not very happy with the backports fix, partly because I did not know what I was doing and partly because I felt I might be opening the door to heaven-knows-what unproven bits & pieces.
I want to be a user, not a tester.
Maybe those doubts are unfounded?

Fortunately I can still select the old kernel 2.6.24-19 at boot, so I can live a little longer with that.

The question now is - is there any clean, simple, safe, understandable way of getting the right rt61pci (whatever that is, I have no idea) into the new kernel & any later kernels (Intrepid...) that come along before this unacceptable bug ([https://bugs.launchpad.net/ubuntu/+source/linux/+bug/200142](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/200142)) is fixed - if indeed it ever does get fixed.

The numerous Hardy/Freeze threads which have been running for many months with no apparent result, do not suggest that solutions are close, or even probable, but that is another subject!

So - any clean way to get a decent rt61pci into new kernels?

Thanks for any help!

---

### Post by 2CV67 on 2008-10-28
Nobody?

---

