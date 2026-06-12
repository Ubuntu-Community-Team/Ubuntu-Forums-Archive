---
title: "Promise SATA300 TX4302 controller"
date: 2008-07-30
forum: Hardware
---

### Post by ZioNemo on 2008-07-30
Hi,
I've been going crazy with the Sata controller I installed.

I have a very recent ubuntu version (Linux heimdall 2.6.24-20-generic #1 SMP Mon Jul 28 13:49:52 UTC 2008 i686 GNU/Linux).

I installed the Controller (Promise SATA300 TX4302 using a PDC40718 chip) and everything went (apparently) well.
I started using the new disks and used them mainly to backup my (huge) files.
After a while my new disks began malfunctioning.
I was terrified since they were brand new and some of the content was not backed-up.
To make a long story short:
The drives are Ok.
The controller, after some hours, just decides to "forget" the existence of the drives.
Next boot everything is back to normal... for a while.

I searched for answers and found some (old) thread detailing kernel recompilation with Promise source drivers, but I didn't see anything matching my behavior.

Before I embark in some lengthy (and possibly useless) recompilation:
This chipset seems to be supported (see: [http://linuxmafia.com/faq/Hardware/sata.html#promise-40718](http://linuxmafia.com/faq/Hardware/sata.html#promise-40718)).
Is support built into the standard ubuntu kernel?

Can someone help me debugging this? (I'm obviously ready to send all the logs needed, I just didn't want to flood You :) ).

Thanks in Advance
ZioNemo

---

### Post by evets25 on 2008-07-30
Whether or not you decide to compile your own kernel, you should probably file a bug report first.

---

### Post by ZioNemo on 2008-07-30
> **evets25 said:**
> Whether or not you decide to compile your own kernel, you should probably file a bug report first.
Thanks for the fast answer,
but, before filing any complaint I would like to know if such a problem is confirmed.

Regards
ZioNemo

---

### Post by evets25 on 2008-07-30
Well, I say "before" because if file a bug report and say that you are running a custom kernel, then the bug report will simply be closed without warning. Make sure you specify on the bug report that this behavior occurs with the stock ubuntu kernel, and not just the custom kernel you built to try and fix the problem. Also, filing a bug report can be a way of getting to the root of a problem, as they will also troubleshoot and help you figure out exactly what the problem is and how to fix it. 

Note that for everyone else reading this, filing a bug report is not normally a recommended way to get simple tech support, but in this case, that may be what is needed.

---

