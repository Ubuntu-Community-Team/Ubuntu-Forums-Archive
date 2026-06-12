---
title: "Bios downgrade"
date: 2008-11-19
forum: General Help
---

### Post by dr_cerebro on 2008-11-19
I have an Acer Aspire 5050-4872.

The only version have ever worked in this machine is 7.10, and the only operative system I have in this computer is Linux.

I will like to try newer versions, these versions only work with the options acpi=off doapm.  I need ACPI to make wireless work.

Does any of you know how to make a BIOS downgrade strictly from Linux?

I hope it could be possible.

Does any of you know how to do it?

---

### Post by ciscosurfer on 2008-11-19
I wouldn't recommend *downgrading* your BIOS, but if you *really* want to you can follow the instructions in my [HOWTO guide]("http://ubuntuforums.org/showthread.php?t=318789").

---

### Post by dr_cerebro on 2008-11-19
> **ciscosurfer said:**
> I wouldn't recommend *downgrading* your BIOS, but if you *really* want to you can follow the instructions in my [HOWTO guide]("http://ubuntuforums.org/showthread.php?t=318789").

Thank you for your reply.  What would you recommend to fix that problem?

---

### Post by ciscosurfer on 2008-11-19
Searching the Forums I found many posts related to your issue.  I would first suggest looking on [Launchpad for bugs and potential workarounds]("http://www.google.com/search?hl=en&q=acpi+wireless+Acer+Aspire+site%3Alaunchpad.net&btnG=Search") regarding these issues; then [search the Forums]("http://www.google.com/search?hl=en&q=acpi+wireless+Acer+Aspire+site%3Aubuntuforums.org&btnG=Search") for more info; a [google search]("http://www.google.com/search?hl=en&q=acpi+wireless+Acer+Aspire+5050-4872+ubuntu&btnG=Search") should provide some feedback as well. I will get back to you with more info in a little bit.

---

### Post by ciscosurfer on 2008-11-19
Any luck with those links?

---

### Post by dr_cerebro on 2008-11-20
> **ciscosurfer said:**
> Any luck with those links?

Maybe this one:

[HTML]https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/151859[/HTML]

but still can't find how to make linux run in this machine without acpi=off

Ubuntu 7.10 runs out of the box in this machine, but is the only one, and Sabayon 3.4 f too.

acer_acpi is used to make wireless "appear" in the system, I installed myself in this machine, but there is a bug report where they mention acer_acpi is included in the kernel in version 8.04 and later.  But still I have the same problem.  I cannot run Linux without acpi=off

I read the downgrade howto you wrote and it looks pretty dangerous specially this:

WARNING: Some motherboards have what are called "CMOS Jumpers" which in effect may prevent you from properly flashing your BIOS. If you believe you fall into this category, it is then necessary to read your BIOS flashing instructions from either your BIOS or hardware manufacturer for proper instructions on how to physically remove this jumper to allow for BIOS flashing. These instructions will be unique to each BIOS/hardware manufacturer. To get you started in finding out this information, here is a link to Google. You should modify this search query with your specific BIOS/hardware manufacturer's name to get unique hits/results.

Maybe is time for me to buy a new laptop, but I feel like (the opposite of succesful, I don't remember the word in english).  I have waited two years using Linux with the hope to get this machine work out of the box, with any distro I like, and their updates or upgrades, and it looks like Linux is not the problem (but these two distributions worked fine), maybe the BIOS is the real problem.

---

### Post by ciscosurfer on 2008-11-20
*Derrotado (defeated?).*  Don't give up hope just yet.  You can also check the Acer website to see if there is a *newer* BIOS upgrade that you can use to flash/run that may solve this problem.  Did the Launchpad discussion look promising, in other words, could you post your question there and perhaps have one of the "bug watchers" investigate for you?  Just some thoughts.  You might also look into apm instead of acpi as some people have had better luck with that power daemon/manager. Me mantienen al corriente de su progreso :-D.

---

### Post by dr_cerebro on 2008-11-20
> **ciscosurfer said:**
> *Derrotado (defeated?).*  Don't give up hope just yet.  You can also check the Acer website to see if there is a *newer* BIOS upgrade that you can use to flash/run that may solve this problem.  Did the Launchpad discussion look promising, in other words, could you post your question there and perhaps have one of the "bug watchers" investigate for you?  Just some thoughts.  You might also look into apm instead of acpi as some people have had better luck with that power daemon/manager. Me mantienen al corriente de su progreso :-D.

Thank you very much for your support.  You're right.  I bought this acer laptop because I wanted to learn linux.  Now, I'm pretty comfortable with GNU/Linux and is the OS I use 95% (or more) of the time.  I'm not going to give up, I have made a lot of progress, and the customized Ubuntu I have in this laptop is proof of that.  I will send my bug to the launchpad.  I was thinking why this machine could install normally; without that ACPI problem, in one distro (Ubuntu 7.10), could it be a kernel problem?, or maybe that time the developers had the time to go that "extra mile" to deal with compatibility issues?  In Sabayon-Linux 3.4F, I had to install with "acpi=off", but weeks later, I learned to make a kernel downgrade, and ACPI worked fine.  I think it could be a kernel problem more than a BIOS problem.

I like to fix (or try to fix things) in this system.  I feel proud when that happen.  I fixed the DSDT, I fixed the wireless, and some minor other things (with a lot of help from other users), I have also post my experiences and hints and have helped other people, so is not a waste of time.  Some of these fixes I "translated" from other distros (like Gentoo, or Fedora) and made it work in Ubuntu and viceversa.

I wanted BIOS downgrade, because there is a post in OpenSuse forums where a guy says it is the only way than Acer Aspire 5050 series can act "normal".

I will have vacations (and plenty of time) in few weeks and I will send my bug to Launchpad, maybe there is an easiest way.  But I still think, meanwhile, I need another laptop (not an Acer, never more) to try the advances in this OS.

Thank you for your support amigo.

I will post my progress.

Gracias de nuevo.

---

### Post by dr_cerebro on 2008-11-20
I think I found the problem.

Launchpad did not provide a lot of help with this issue.

I started looking in the Kernel bugs, and it looks than it is a kernel bug in the 2.6 series, and sometimes they get lucky, and gets fixed in the one release, and some other times they have a "regression" and acpi fails in some machines.

I will send my bug report in Linux kernel bugs and see what happen.

---

### Post by ciscosurfer on 2008-11-21
Did you find that it is a known bug in all of the 2.6 kernels?  In other words, are you able to downgrade or revert the kernel to an earlier 2.6.xx-x release?  From what I gather, this could be a possibility as you've stated.

---

### Post by dr_cerebro on 2008-11-21
> **ciscosurfer said:**
> Did you find that it is a known bug in all of the 2.6 kernels?  In other words, are you able to downgrade or revert the kernel to an earlier 2.6.xx-x release?  From what I gather, this could be a possibility as you've stated.

Yes, by the way, the kernel bugtrackers recoginze this is a problem in most of the 2.6.X.X kernels, not in the 2.4.X.X kernels, and they are trying to fix that, but mentioned it is not possible (yet) to load all ACPI modules in a single kernel, unless they just load the basic ACPI config, and have support to the basic config.  There is a patch with some lines of code from the 2.4.X.X kernels than can be used to patch the kernel.  I will try that, but I'm still looking how to the that (they posted the solution, but there is lack of information about how to do that).  Some bugtrackers think that problem was already solved in some kernels, and there was a "regression" in the kernel development, and again they release a new kernel with the same bug.

In one of the posts, one person suggested it could be a BIOS problem, the same BIOS I have.  But the bugtrackers discarded that possibility, and suggested to patch the kernel and it worked.

That is why, when I did a kernel downgrade, I was lucky to downgrade to a kernel without that problem.  And the original kernel in Ubuntu 7.10 does not have that problem either.

The thing is I have updated the original kernel in Gutsy twice via Update manager, I don't know what version of kernel was the original, but now is 2.6.22.15 generic, I don't know if those were kernel updates or kernel upgrades, but my laptop is still working (maybe those were just updates).

What do you think?

---

### Post by ciscosurfer on 2008-11-21
Looks like 2.6.22.14 was the original so my guess is that .15 is just an update.  If the patch they provide works then I'd say use it but only if you don't suffer loss of other functionality.  I would definitely not recommed downgrading to any 2.4 kernel (that's ancient history!  People still use it, but you'll likely lose some functionality and speed if you downgrade to it).  That's just my opinion, though.

---

### Post by dr_cerebro on 2008-11-21
> **ciscosurfer said:**
> Looks like 2.6.22.14 was the original so my guess is that .15 is just an update.  If the patch they provide works then I'd say use it but only if you don't suffer loss of other functionality.  I would definitely not recommed downgrading to any 2.4 kernel (that's ancient history!  People still use it, but you'll likely lose some functionality and speed if you downgrade to it).  That's just my opinion, though.

The patch just add to the kernel some lines of code missing in 2.6.X.X series.  Those lines were took from kernel 2.4.X.X.  The kernel still is the one installed, with some lines more than make ACPI work normal (I guess).

[http://bugzilla.kernel.org/show_bug.cgi?id=1558]("http://bugzilla.kernel.org/show_bug.cgi?id=1558")

This is one of the posts.  Please check it out.

I'm in a hurry, I'm almost late for work.

See you later.

Thanks.

---

