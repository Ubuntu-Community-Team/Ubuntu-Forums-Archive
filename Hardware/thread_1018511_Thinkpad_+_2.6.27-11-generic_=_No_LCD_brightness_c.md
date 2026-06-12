---
title: "Thinkpad + 2.6.27-11-generic = No LCD brightness control?"
date: 2008-12-22
forum: Hardware
---

### Post by yangwooko on 2008-12-22
I have been using ubuntu Intrepid successfully on my Thinkpad X61. It is not 100% sure but after installing 2.6.27-11 a few days ago, I cannot control the brightness of LCD any more.

I can change the brightness before ubuntu is up. For example, I can control the brightness at CMOS setup screen.

I tried most of combinations suggested in Documentation / laptops / thinkpad-acpi.txt but no success.

Any idea?

---

### Post by mariner09 on 2008-12-22
You're right.  I see the same thing with this kernel on my T61.  Power mgmt can control the brightness, but the Fn keys do not do anything other than bring up the applet gui.

---

### Post by mariner09 on 2008-12-22
If it helps, 2.6.27-10-generic works fine.

Something ACPI related must've changed in the newer kernel.

---

### Post by yangwooko on 2008-12-23
Thanks to your proposal.

I also reverted to -10 and it works correctly.

---

### Post by fosberry on 2008-12-30
I have observed the same problem with a Thinkpad X61s: 
when running 2.6.27-11, the brightness keys (Fn+Home up, Fn+End down) cause the brightness meter to be shown and move, but the screen brightness does not change.

When I go back to using 2.6.27-10, the keys work normally, both showing the brightness meter and changing the screen brightness. Did anyone file a bug at launchpad for this?

---

### Post by pmanski on 2009-01-04
The same in my case. Just upgrade to 2.6.27-11 and the brigtness control stoped working.

---

### Post by plaxx on 2009-01-05
Bug [#314119]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/314119/") has been filed. The source of this bug seems related to bug [#257827]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/257827") and there seems to be a workaround (that I haven't tested).

---

### Post by piemaster89 on 2009-01-06
confirmed on my T61 running 8.10 64-bit on linux 2.6.27-11-generic

---

### Post by plaxx on 2009-01-07
There is a fix in [bug 311716 at comment #5]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/311716/comments/5"). Its updated kernel packages that you can install using dpkg.

It worked for me.

---

### Post by andres403 on 2009-02-28
Hi, I'm sort of a newbie at this but am experiencing the exact same problem with my Thinkpad R61 in Intrepid. I was wondering what exactly 2.6.27-11 was and how I could either revert it to 2.6.27-10 or install the patch. I'm guessing it's the kernel version but I don't even really know how to get at or change the kernal. Can anyone give step by step instructions how to do this? I really appreciate the help.

Thanks,
Andy

---

### Post by ecoxmit on 2009-02-28
I am having the same problem with 2.6.27-12-generic (64bit)

---

### Post by ecoxmit on 2009-02-28
I fixed the problem by adding 
acpi_backlight=vendor 
to the boot options!

(see discussion in [bug 257827]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/257827"))

---

### Post by ecoxmit on 2009-02-28
my suggestion above seems buggy (it stops working).

---

### Post by fishes on 2009-03-19
Hi, I'm running an X61s with the -11 kernel, which broke the brightness controls after I upgraded from -10. Same problem as many others.

Could someone provide instructions or a link to instructions on how to download and install the -10 kernel? I am new.

Thanks.

---

