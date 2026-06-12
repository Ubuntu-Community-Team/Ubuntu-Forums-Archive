---
title: "Ubuntu hardy kernel recompile missing alsa ? Also why is kernel set to 250Hz?"
date: 2008-08-24
forum: General Help
---

### Post by interzoneuk on 2008-08-24
Hi.

When compiling a kernel from the linux-source package, I used the default config-2.6.24-19-generic as a base.

When looking through the options I noticed that all the Alsa(and oss) modules are not enabled...

Is this because Ubuntu loads them separately? If so how do I load them on a custom kernel ?

Also why is kernel timer not set to 1000Hz ? As the generic kernel is generally used for Desktops wouldn't the default setting of 1000Hz be better ? I ask because it is set to that for Mandriva and Fedora... (Opensuse also set it to 250hz...)

ID software have said that to Play ETQW your kernel should have preemption and be set to 1000 hz for the client AND server....

Any idea why it is at 250Hz?

see :-

[http://www.wolfstuff.org/modules.php?name=Content&pa=showpage&pid=16](http://www.wolfstuff.org/modules.php?name=Content&pa=showpage&pid=16)

---------------------------------------------------------------
Important system requirements:

------------------------------

You need a low latency kernel for optimal performance (this applies to both client and server installations). Make sure your kernel

is configured with CONFIG_HZ_1000=y. You should also enable other low latency settings, such as the various preemption settings.

-------------------------------------------------------

---

