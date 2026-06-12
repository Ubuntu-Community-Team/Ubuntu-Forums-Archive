---
title: "HP DV2320 compatability and iso question"
date: 2007-06-10
forum: Hardware &amp; Laptops
---

### Post by hotstovejer on 2007-06-10
Hi all,

I scoured the forums looking for this model of laptop and any incompatability issues it might have, and I have found nothing. Also looked for the wiki on HP laptop testing, and found nill. Anyone used the dv2300 series? Or even the dv2000 series? I tried a DV 6000 series laptop, and couldn't even get it to use the liveCD.

Also, what version of 7.04 should I use for a Turion 64 X2? The AMD 64 one, or the 386 one? I know the 64 bit version had some bugs, but don't know if those have been ironed out.

Thanks all for the help!

Jeremy

---

### Post by Kobalt on 2007-06-10
Hello,

First off, if you didn't find any specific thread related to your laptop then maybe there aren't any problems with this one :) 
For your HP dv6000, as I own one, you should know you need to use the noapic nolapic options to boot properly. When you boot your computer with the LiveCD, at boot screen press F6 to access the boot options. At the end of the line, and after a space, enter > noapic nolapicThen press Enter to boot, and it should be ok.
For a Turion64, you should use a 64bit version of Ubuntu. The remaining bugs in Ubuntu 7.04 64bit are very minor things. If you want to learn the advantages/disadvantages of Ubuntu 64bit, please [read this]("http://ubuntuforums.org/showthread.php?t=368607").

---

### Post by hotstovejer on 2007-06-11
Thanks for your help! I took the 6000 back, cause I couldn't get any options to work, so I figured I would just return it and try again on another machine. Kinda diggin on the 14 inch screen. If it doesn't work after some trying, that is why there are return policies! ;)

Jeremy

---

