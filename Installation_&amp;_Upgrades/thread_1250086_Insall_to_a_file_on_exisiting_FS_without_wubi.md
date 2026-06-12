---
title: "Insall to a file on exisiting FS without wubi"
date: 2009-08-26
forum: Installation &amp; Upgrades
---

### Post by zespri on 2009-08-26
Hello,

wubi supports only x32 version of ubuntu. I'd like to install the x64 version this way. Where can I find instructions on how to do this (installing to a file within existing filesystem) manually, i.e. without wubi?

Cheers,
Andrew

---

### Post by Mark Phelps on 2009-08-26
> **zespri said:**
> Hello,
wubi supports only x32 version of ubuntu. 
Where'd you get that information? 
> I'd like to install the x64 version this way. Where can I find instructions on how to do this (installing to a file within existing filesystem) manually, i.e. without wubi?
You can't install Ubuntu "within" another OS unless you're using Wubi or you install some kind of virtualization SW (Virtualbox, VMWare, Virtual PC).

---

### Post by zespri on 2009-08-26
> **Mark Phelps said:**
> Where'd you get that information?

Looks like I assumed, and assumed wrongly. I swear I read it somewhere before. Thanks. 

> **Mark Phelps said:**
> 
You can't install Ubuntu "within" another OS unless you're using Wubi or you install some kind of virtualization SW (Virtualbox, VMWare, Virtual PC).
Wubi doesn't use virtualization, so surely you can do the same thing it does, you just need to know how.

Thank you again for your reply!

---

### Post by Mark Phelps on 2009-08-26
> **zespri said:**
> Wubi doesn't use virtualization, so surely you can do the same thing it does, you just need to know how.

Your original post asked where you can find instructions for doing this, not whether or not it can be done.  Since the Wubi project folks figured out how to do it, of course it can be done.

But unless they're willing to release their source code, I have no idea where you can find the instructions needed to replicate their efforts.

---

### Post by zespri on 2009-08-26
Fair enough. Thanks

---

### Post by garvinrick4 on 2009-08-26
Matter of fact Wubi will automatically install 64 bit if machine is capable of
sustaining. It is nice double boot if you use unstable version like 9.10 Alpha 4
and Ubuntu changes GRUB and cannot exit Ubuntu without crashing it is nice
to be able to just uninstall and download 9.04 again then dist-upgrade again then
chrash again and start over again. Good thing I am retired and have time. Ubuntu
had to know it would not work in dual boot with WUBI. Sure they will fix, they always do.
Maybe they do not want Ubuntu installed in DOS partition. My father who is 80 or so
will only use Windows and freaks at the thought of Linux. So I keep dual boot. He has
earned it.   You see sometimes there is a reason for keeping DOS around.

---

