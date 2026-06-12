---
title: "WD spamware"
date: 2015-02-24
forum: Hardware
---

### Post by swisswilson on 2015-02-24
I was given a WD external hard drive from a friend and it has the crap WD smartware on it.  I have tried using Gparted, shred command from terminal and neither were able to remove the damn hidden VCD, does anyone have any suggestions?  ive read that on windows machines people have had luck using HP usb disk format thingy, maybe theres an alternative for ubuntu that will detect and remove the bloatware.

regards

---

### Post by papibe on 2015-02-24
Hi swisswilson. Welcome to the forum ):P

Unfortunately, you need to remove the VCD from Windows. Here's a [tutorial]("http://www.dedoimedo.com/computers/passport-vcd.html").

Come here often, and have fun.
Regards.

---

### Post by swisswilson on 2015-02-24
papide,

thanks for the speedy and pleasant response.  i unfortunately dont have acces to a windows computer, i did read that tutorial and am disappointed theres no way to remove it on a linux machine, i assume using startup disk creator will not work? there must be a solution other that the HP USB disk that i can use on linux

---

### Post by weatherman2 on 2015-02-24
What about the U3 tool?  Might be worth a try:

[http://u3-tool.sourceforge.net/](http://u3-tool.sourceforge.net/)

---

### Post by Bucky Ball on 2015-02-25
> **swisswilson said:**
> i unfortunately dont have acces to a windows computer ...

Any chance the friend who gave you the drive has one you can use for 1/2 and hour?

> **weatherman2 said:**
> What about the U3 tool?  Might be worth a try:

[http://u3-tool.sourceforge.net/](http://u3-tool.sourceforge.net/)

From the previous [link]("http://www.dedoimedo.com/computers/passport-vcd.html") provided by papibe:

>  What about U3?

Ah yes, another nonsense. Well, there's the U3 utility that truly kills it off, available for Windows and Mac users. In Linux, you may want to try u3-tool, which does the same thing. Thanks to Ocky for this discovery.

So yes, worth a try.

---

