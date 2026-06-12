---
title: "Server install for 7 year old laptop"
date: 2013-02-14
forum: Hardware
---

### Post by TheKoolAidGuy on 2013-02-14
Okay, so my friend has a 7 year old laptop that she is trying to install Ubuntu Server 12.04 LTS onto but when she clicks install it is telling her that the CPU is not supported by the kernel.

Is there a version that will support it that is available?

Here are the specs of the CPU.

1.8Ghz Pentium M/2MB L2 Cache/400Mhz FSB

If you need more please let me know!

Thanks!

---

### Post by cjhabs on 2013-02-14
Maybe you are trying to install a 64-bit OS onto a 32-bit processor?

---

### Post by TheKoolAidGuy on 2013-02-14
I asked and she say's she assumed when she went to download that with the age of the PC that the 32-bit version is what she would need so that isn't the problem here.

---

### Post by papibe on 2013-02-14
Hi TheKoolAidGuy.

How much RAM does her machine have?
(related to PAE and non PAE kernels).

Regards.

---

### Post by Bashing-om on 2013-02-14
TheKoolAidGuy;

I have it on authority of others that 12.04 is too heavy. System requirements:
[http://desktoplinuxreviews.com/2012/05/09/ubuntu-12-04/](http://desktoplinuxreviews.com/2012/05/09/ubuntu-12-04/)

google search for others too.

Will also require that the cpu support pae, and sse2
to see, from liveCD terminal command:
```
 cat /proc/cpuinfo
```look for those items in the flag's field of the output.

There are other alternatives to ubuntu 12.04 server for your needs.


[INDENT][INDENT][INDENT]hth

[/INDENT][/INDENT][/INDENT]

---

### Post by Yellow Pasque on 2013-02-14
Pentium M = non-PAE CPU
You can make life easy and use Lubuntu 12.04 (then install ubuntu-desktop package if you want Unity), or do something more complicated like: [http://www.webupd8.org/2012/11/how-to-install-ubuntu-1210-on-non-pae.html](http://www.webupd8.org/2012/11/how-to-install-ubuntu-1210-on-non-pae.html)

---

### Post by papibe on 2013-02-14
> **Temüjin said:**
> Pentium M = non-PAE CPU
Just to be precise...

There are 2 Pentium M generations. Firt one, called Banias, did not support PAE. However, the next generation, called Dothan, indeed do support PAE.

It seems that TheKoolAidGuy's friend do not support it, but may be there is a slim chance (guessing here) that could be enabled by entering the BIOS.

Temüjin's suggestion about the mini ISO could be your best bet. Chose [command line install]("http://www.psychocats.net/ubuntu/minimal"), then install [tasksel]("https://help.ubuntu.com/community/Tasksel") and select the server meta packages you want.

Regards.

---

### Post by Yellow Pasque on 2013-02-14
@papibe: thanks for correction

EDIT: papibe's not completely correct either :P Some 2nd-gen/Dothan Pentium M's still didn't support PAE.
[https://en.wikipedia.org/wiki/List_of_Intel_Pentium_M_microprocessors](https://en.wikipedia.org/wiki/List_of_Intel_Pentium_M_microprocessors)

---

### Post by tgalati4 on 2013-02-14
There's a thread on the forums (you'll have to search for it) that provides a work-around to provide a "fake-PAE" flag that will allow installation.  Your alternative is to use an older distro without PAE.  At 1.8GHz, my guess is that it is one of the newer processors in the M family and even though the PAE flag is not shown in /proc/cpuinfo, it really can handle PAE fine.

If you want a graphical desktop, give Linux Mint Mate 14 32-bit a try.  It runs well on my older Dell 600m with a Pentium M processor and of the same time period.

---

### Post by papibe on 2013-02-14
> **Temüjin said:**
> papibe's not completely correct either :P Some 2nd-gen/Dothan Pentium M's still didn't support PAE.
Oopsy :oops:

Good catch Temüjin!

---

### Post by Yellow Pasque on 2013-02-14
> **papibe said:**
> Oopsy :oops:

I don't think either one of use needs to be red in the face when there's seemingly no rhyme/reason (even from looking at the marketing/model numbers) for the PAE/non-PAE support throughout the Pentium M line-up. :KS

---

### Post by Redalien0304 on 2013-02-14
also you can Download 12.04 Non from here. I have tested the one From canonical
[http://people.canonical.com/~diwic/12.04-nonpae/](http://people.canonical.com/~diwic/12.04-nonpae/)

[http://www.wilderssecurity.com/showthread.php?t=323210](http://www.wilderssecurity.com/showthread.php?t=323210)

---

### Post by papibe on 2013-02-14
That's very interesting, alien0304, thanks.

Do you have a link for a the server version?

Regards

---

### Post by TheKoolAidGuy on 2013-02-15
I appreciate all of your input here I am sorry I haven't replied :P also alien is that ubuntu still?

---

