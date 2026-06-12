---
title: "[SOLVED] WinXP in virtual machine - 32 bit or 64 bit, which one?"
date: 2008-06-06
forum: Hardware
---

### Post by DeadlyOats on 2008-06-06
Hello, everyone!

I have a new question about laptops, vitual machines, and now - the new question - WinXP Pro 32 bit or WinXP Pro 64 bit.

Here's the link from my last series of questions on the matter, and how it was resolved:

[http://ubuntuforums.org/showthread.php?t=787429](http://ubuntuforums.org/showthread.php?t=787429)

I have the laptop now, I'm ready to install the Virtual Machine (I still haven't made up my mind which one), and I'm definately gonna install WinXP Pro (or Home?) edition.

However, I don't know if I *_have_* to get WinXP 64 bit version, or if WinXP 32 bit version is O.K. to use.  Ubuntu Hardy Heron 64 bit version is installed on my new laptop, and that makes me wonder if Windows will have to be the 64 bit version, or if I can get away with the 32 bit version.

So, what's everyone's opinion?  What should I get, WinXP 32 bit or WinXP 64 bit?

---

### Post by Rocket2DMn on 2008-06-06
Since you have the 64 bit version of Ubuntu installed, you can use either version of XP.  You may not see a lot of advantage to using the 64 bit version of XP since it has to run through the VM, and it will most likely require more RAM, too.

I would say use the 32 bit version of XP since it will be smaller and better supported, but the 64 bit may work just fine.

---

### Post by wdaniels on 2008-06-06
No, you don't have to use a 64bit guest OS, and in many cases you can't - Virtualbox I hear doesn't support 64bit guest OS and VMWare will only do so with [certain 64bit processors and BIOS support]("http://kb.vmware.com/selfservice/viewContent.do?externalId=1901"). The way I see it, the only reason to run a Windows VM on Linux is for compatibility with stuff, and 64-bit Windows is not fully compatible with everything Windows-related, so I would definitely use the 32-bit one.

---

### Post by DeadlyOats on 2008-06-06
Ah!  I learned something new!  Thank you for your replies.  So, WinXP Pro (or Home?) 32 bit version it is!

---

### Post by Rocket2DMn on 2008-06-06
I say Pro if you already have it.  There isn't much point to using Home if you have Pro at your disposal.  Realistically, either will probably work fine, but why not use the better of the two options?  I wouldn't go out and buy Pro, though, if you already have Home (and no Pro).

---

