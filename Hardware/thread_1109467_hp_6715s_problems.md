---
title: "hp 6715s problems"
date: 2009-03-28
forum: Hardware
---

### Post by david.wahlstedt on 2009-03-28
I want to report some experience with ubuntu on my laptop:
 hp 6715s, AMD Sempron 3800+, 1G Ram, 80G SATA.
It is a 64 bit machine, although it is sometimes claimed to be 32 bit.

I want to run 32 bit ubuntu on it, by various reasons. (and it should work)
I have had no success installing or running 32 bit ubuntu on this machine.
The failed attempts cover all versions so far of 32 bit ubuntu (including 9.04 beta).

There are several problems, the most severe seems to be that the hard disk 
becomes extremely slow.
See [http://ubuntuforums.org/showthread.php?t=499060&page=2](http://ubuntuforums.org/showthread.php?t=499060&page=2)

However, it works with the 64-bit version of ubuntu 7.10, following Gefa's guide in post #13 in the thread above.
(when 8.04 came I tried the 64 bit version, but there the APIC support was worse than in 7.10, so I abandoned it)

For wlan I use ndiswrapper, and it works very well (b43 driver doesnt work).
For getting graphics to work I download the binary from ATI. Works fine.

Two quite annoying problems remain:

1: I get the error message
 [  812.277920] APIC error on CPU0: 40(40)
at a high rate. Sometimes, but not often, the display freezes (maybe because of this, I dont know). Then I almost manage to shut down--but--this error msg is the last thing I see before I press the power button in five seconds to get rid of it.

2: The sound is quite bad. It sounds like the cpu is working very hard although it isnt. It sounds "chopped". There are no error messages from the sound driver.

---

