---
title: "Complete list of compatible hardware"
date: 2018-07-23
forum: Hardware
---

### Post by lynman on 2018-07-23
Hi,

I know there are topics on the top but:
[https://ubuntuforums.org/showthread.php?t=361236](https://ubuntuforums.org/showthread.php?t=361236) - 93 pages
[https://ubuntuforums.org/showthread.php?t=361237](https://ubuntuforums.org/showthread.php?t=361237) - 677 pages
[https://ubuntuforums.org/showthread.php?t=1543006](https://ubuntuforums.org/showthread.php?t=1543006) - 174 pages
[https://ubuntuforums.org/showthread.php?t=1543009](https://ubuntuforums.org/showthread.php?t=1543009) - 419 pages

Over 1300 pages :-s

Is there anything more user friendly? Searchable? Categorised? With filters?

e.g. I would love to see the list of the most powerful (ubuntu friendly) hardware that is currently in stores.

---

### Post by oldfred on 2018-07-23
There is very little that does not work.
But some video cards, Internet chips or other specific hardware may not work or require special drivers.
The more unique and newer the hardware the less likely it is to work.

Also while very new hardware is often supported by Linux, each distribution may not yet have the very new kernel & hardware required to fully support it. So becomes a case of adding ppas or even compiling your own kernel, making install a bit more difficult.

So often best to get system that is not the very newest and uses standard components, if ease of install is a requirement.

Often better to narrow choices down to one or two systems and then ask in chat whether other uses have used it yet. 

Also if you want better system, build it yourself. Not really all that difficult. 

There also is this site among others.
       Intel Core i5 8400 Linux Performance to Ryzen & i7 Oct 2017
[https://www.phoronix.com/scan.php?page=article&item=intel-linux-8400&num=1](https://www.phoronix.com/scan.php?page=article&item=intel-linux-8400&num=1) 
    
And then he provides this test site where users can compare systems. Search for what hardware you are interested in.
[http://openbenchmarking.org/](http://openbenchmarking.org/)

---

### Post by 1clue on 2018-07-23
It's not possible to have a complete list of supported hardware because:

[LIST=1]
[*]The list of actual hardware is changing much too fast for any comprehensive list to be maintained
[*]Some drivers are packaged with the kernel, some commercial or FOSS drivers are supplied by the manufacturer, and others are being written by some guy who wants his hardware to work.
[*]While some hardware will be listed by someone as working with such-and-such driver, how well it works is not always clear. Frequently somebody who only needs basic functionality will mark a driver as working with their hardware, but when you get it it may not do what you need.
[/LIST]

Some rules of thumb:
[LIST=1]
[*]Cheap hardware is less likely to work smoothly than midrange hardware. Manufacturers of cheap hardware cut corners and make up for it on driver software.
[LIST=1]
[*]The prime example of this is the win-modem from the mid 90s. They only worked on Windows, and the reason was the manufacturers built very limited hardware which was not enough to be an actual modem, and then wrote the rest into the driver. Writing the driver for Linux becomes more problematic and often the manufacturer doesn't want people to know how crappy their hardware is.
[*]Realtek network cards are another example. While you can get near wire speed from these cards, the CPU load goes up much faster than if you had an Intel NIC with an 'igb' driver.
[/LIST]

[*]High-end consumer hardware is less likely to work than midrange hardware. Here I'm talking not so much motherboards as peripherals. If you have some sort of special-purpose gadget not found on an every-day computer, you really need to be careful in your driver search before you buy it. Years ago I bought a Canon all-in-one color laser printer. It was one of the first ones aimed at a consumer market. This printer sat on my table for almost 3 years before I could reliably print from it.
[*]Professional special-purpose hardware is likely to be buggy or nonfunctional for a long time. I knew someone who had professional video editing hardware. I don't know if she ever got it working.
[*]Some companies embrace Linux and FOSS. Others do not. Learn which is which and you can predict whether a missing or faulty driver is likely to ever be fixed.
[/LIST]

Motherboards:
[LIST=1]
[*]The quality of components on the board indicate a general overall quality of the motherboard.
[*]Cheap NICs on the motherboard is an indicator that not all will be fantastic. Realtek is a cheap NIC. I didn't care until I tried to build a router with 5x Realtek nics on the board. My i7 was under high load. Later used an atom c2758 board with 7 Intel nics built-in, and the atom routed packets faster than the i7 and with less cpu load.
[*]Sticking with the same example, my Asus p6t with the Realtek nics had a buggy firmware that has still not been fixed. It doesn't interfere with everyday computing but if you want to use it for virtualization you're pretty much screwed.
[*]High quality boards found in server rooms tend to support Linux. Again, check the manufacturer for their Linux reputation, and check for available drivers on ANYTHING you depend on.
[/LIST]

Manufacturers I like, not in any particular order:
[LIST]
[*]IBM
[*]SuperMicro
[*]HP
[/LIST]

---

