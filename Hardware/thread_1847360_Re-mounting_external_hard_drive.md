---
title: "Re-mounting external hard drive"
date: 2011-09-20
forum: Hardware
---

### Post by mgt2000 on 2011-09-20
Hi,
I have a problem with my external had drive in Ubuntu (11.04). When I click on "safely remove", after (about) 5 seconds it mounts again automatically!!! Could you please let me know what is the problem.  of course I use Ubuntu on my laptop and also in my desktop computer in the office but I have the same problem in both.

Thanks

---

### Post by coffeecat on 2011-09-20
There is a bug in Maverick (10.10) and Natty (11.04) which causes this and which I originally thought was confined to nvidia USB controller motherboard chipsets. Certainly when I investigated this on a number of machines, the ones with nvidia USB controllers exhibited this phenomenon but not with AMD or Intel USB controllers. However, since then I've been involved in a couple of threads where the OP reports this behaviour but said they had USB controllers other than nvidia ones. This is all a bit theoretical, but out of interest post the terminal output from both machines of:

```
lspci | grep USB
```

You'll need to highlight that with the mouse, right-click -> copy to paste it into your post. This will tell us what your USB controller is.

Bugs here:

[https://bugs.launchpad.net/ubuntu/+source/udev/+bug/624755](https://bugs.launchpad.net/ubuntu/+source/udev/+bug/624755)

[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/792085](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/792085)

As far as I can see, all you can do is to be aware of this problem, wait until it is remounted and safely remove a second time, after which it will remain unmounted.

---

### Post by KBD47 on 2011-09-20
Just out of curiousity--I have Ubuntu 11.04 installed on an external hard drive. When I boot up it says something about Ubuntu not being mounted yet and I have to type "S" for "skip" to get it to work. Is this related?
KBD47

---

### Post by coffeecat on 2011-09-20
> **KBD47 said:**
> Is this related?
KBD47

No. mgt2000's problem is an issue with udev or perhaps the kernel USB driver. Yours sounds as though it might be a misconfiguration in /etc/fstab. If you need help with that, do please start your own thread. :)

---

### Post by mgt2000 on 2011-09-21
> **coffeecat said:**
> There is a bug in Maverick (10.10) and Natty (11.04) which causes this and which I originally thought was confined to nvidia USB controller motherboard chipsets. Certainly when I investigated this on a number of machines, the ones with nvidia USB controllers exhibited this phenomenon but not with AMD or Intel USB controllers. However, since then I've been involved in a couple of threads where the OP reports this behaviour but said they had USB controllers other than nvidia ones. This is all a bit theoretical, but out of interest post the terminal output from both machines of:

```
lspci | grep USB
```You'll need to highlight that with the mouse, right-click -> copy to paste it into your post. This will tell us what your USB controller is.

Bugs here:

[https://bugs.launchpad.net/ubuntu/+source/udev/+bug/624755](https://bugs.launchpad.net/ubuntu/+source/udev/+bug/624755)

[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/792085](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/792085)

As far as I can see, all you can do is to be aware of this problem, wait until it is remounted and safely remove a second time, after which it will remain unmounted.

Thank you very much for your reply.
Here is the information of the desktop (Dell-Vostro-410):
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)

And here is the information of my laptop:
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)

---

### Post by coffeecat on 2011-09-21
Thanks for that. More Intel, I see. My earlier impression that this was a nvidia-only problem was wrong. It seems you're unlucky with two different machines affected. Sorry I can't offer more than my previous comment and perhaps a suggestion that you add a comment and/or a me-to to the bug reports.

---

### Post by mgt2000 on 2011-09-21
Thank you. I will await for fixing the bug:D

---

### Post by mgt2000 on 2011-10-13
It seems this problems hasn't been solved in Ubuntu 11.10 because I have the same problem with this version :(

---

### Post by mgt2000 on 2011-12-25
This problem is still exist even in Kernel 3.1.4 (Ubuntu 11.10)! Does any one have a solution?

---

### Post by mgt2000 on 2012-06-14
I still have this problem in Ubuntu 12.04 ans its last kernel :(
I have the same problem in a new laptop Acer aspire 7750G. Isn't there any solution?

---

