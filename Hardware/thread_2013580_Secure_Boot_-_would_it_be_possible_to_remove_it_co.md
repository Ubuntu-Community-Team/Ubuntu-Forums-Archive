---
title: "Secure Boot - would it be possible to remove it completely?"
date: 2012-07-01
forum: Hardware
---

### Post by Louigi Verona on 2012-07-01
Hey fellas!

Read this from FSF: [http://www.fsf.org/campaigns/secure-boot-vs-restricted-boot/whitepaper-web](http://www.fsf.org/campaigns/secure-boot-vs-restricted-boot/whitepaper-web)

And this from Ubuntu: [https://lists.ubuntu.com/archives/ubuntu-devel/2012-June/035445.html](https://lists.ubuntu.com/archives/ubuntu-devel/2012-June/035445.html)

Question goes as follows - when I buy a laptop with this Secure Boot, would I be able to simply wipe it out fully, without the need for any keys, be it Microsoft or Ubuntu?

Or are the days when you can just buy a laptop and install Linux without any keys are about to be gone?

---

### Post by ahallubuntu on 2012-07-01
Yes, any X86 PC will have the ability to remove secure boot completely.  Microsoft's original proposal did not include this, but it was later modified so every one will have the option for the user to disable it.

This requirement only applies to X86-compliant PCs, not to Android devices etc.

It's likely your favorite distro will have a signed kernel/boot sector anyway, so you may not  Red Hat's solution for Fedora is to pay a one-time $99 fee (TOTAL paid by them once - not by each user) to sign theirs, so every user can install and boot Fedora without needing to disable secure boot.  Most big distros will probably follow suit.  $99 isn't a big barrier for someone distributing an operating system.

The bigger question is, how easy will it be for the average user to disable secure boot?  Some people can't even figure out how to enter their BIOS Setup now to, say, change the boot order or something.  There is no standard way to do anything in today's BIOSes.  Not sure there will be a standard way to disable secure boot, either.  Experts will not have a problem doing it but novice users may have trouble.  It does add a small barrier to mass acceptance of Linux as an alternative to Windows.

---

### Post by Louigi Verona on 2012-07-01
But let's say at some point in time Microsoft will say - okay, we are locking out even x86 devices. Is it possible to hack UEFI in question? Or is it fully hardware based?

---

### Post by ahallubuntu on 2012-07-01
Microsoft can't lock your future X86 UEFI secure boot hardware any more than they can stop you from changing the BIOS settings in your old computer.  It's not in Microsoft's control.

At worst, they (or is it Verisign?) could stop charging only $99 to sign the boot sector - maybe they start charging $10,000, to make it harder for other operating systems to be installed easily.  But you would still be able to disable secure boot yourself.  Microsoft can't block that.

---

### Post by Louigi Verona on 2012-07-01
That I understand. But some vendors have went as far as to say that some models they will not allow the user to switch Secure Boot off even on x86. So question is - you get a laptop with no option to switch off Secure Boot. Can you do something or is this hardware built-in?
In other words - will we see standard laptops without option to switch Secure Boot off (at least in theory) be jail-broken?

---

### Post by Louigi Verona on 2012-07-03
bump

---

