---
title: "Ubuntu 64bit on Samsung R560 Aura Madril does not work - kernel crash"
date: 2008-08-25
forum: Hardware
---

### Post by TorstenS on 2008-08-25
Hi all!

I have a new laptop, Samsung R560 Aura Madril. It works fine with Ubuntu 32bit (8.04 as well as 8.10 Alpha 4) but the kernel crashes and the laptop reboots with any 64bit version.

I have followed several threads that suggest any kind of settings regarding the video mode or acpi=off and the like, but no success at all.

Is there anyone who has the same machine?
Is this a known problem on Intel P8400 machines?
How can I produce any kind of dump that might be useful for anyone to find the problem?

Regards,
Torsten

---

### Post by DasI on 2008-12-10
Have the same machine, tried another x86_64 distro - same problems. You can boot Linux with acpi=off, but I wouldn't call this normal work, any activity like power plug-in/out, closing lid leads to immediate crash-restart...
Tried reporting kernel bug, also asked how I could help debugging this problem - no results yet :(
Still have to work with my old machine...

---

### Post by TorstenS on 2008-12-10
Hi!

Indeed, using the now final 8.10 (amd64) and acpi=off, it works pretty well for me. (As well as a system without ACPI can work, as you properly describe.)

So this seems to be an upstream kernel issue.

What did you do to report a kernel bug? There is a but report on Launchpad that people ideed cared about, thus without too much of a result yet:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/272530](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/272530)

IMO the question regaring the kernel bug is: Is this specific to the chipset, so *any* laptop using that chipset would be affected or is this a problem with some other component that Samsung uses in the R560?

Regards,
Torsten

---

### Post by DasI on 2008-12-10
Yeah, mem=4096 option helps a lot. Thank you for this such valuable link.
Actually I've red somewhere, that it might be Montevina problem, but I'm not a kernel developer, so lets hope real Kernel developer will hear us soon.
In general I'm a Fedora user, so I did report it to the Fedora/kernel bugs.

---

### Post by i_ata89 on 2008-12-28
Hi

Had this same problem myself. Could only run the live cd with acpi off. I tried several other distributions and all had same problem.

I have know got it sorted by installing the newest bios version (09LA) from the samsung download center. Hope this works for you.

---

### Post by noavatar on 2009-02-03
I've settled for the 32bit 8.10 after upgrading the bios as advised in the above post, but am having trouble with the webcam. any advise?

edit:

never mind, i found my answer here:
[http://www.bleepingcomputer.com/forums/topic169248.html](http://www.bleepingcomputer.com/forums/topic169248.html)
although i had to change the aspect ratio for the feed

---

### Post by bilif on 2009-11-03
I updated the bios and now everything works fine.

---

