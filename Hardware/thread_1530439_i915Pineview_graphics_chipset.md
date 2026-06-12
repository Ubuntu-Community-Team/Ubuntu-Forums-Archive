---
title: "i915/Pineview graphics chipset"
date: 2010-07-13
forum: Hardware
---

### Post by jwdv22 on 2010-07-13
Hi all,

I have 10.04 installed but my laptop runs hot, after much investigating. I see  that my chipset has updated drivers that are not in the repo yet.
Specifically here
[http://intellinuxgraphics.org/2010Q2.html](http://intellinuxgraphics.org/2010Q2.html)
However, I am confused on what I need to do to get this all working. I am guess I was hoping someone could direct me on what I need to do to get the kernel and mesa and XORG, all this is confusing to me.

Appreciate any help.

Thanks

---

### Post by gordintoronto on 2010-07-13
Ubuntu follows a conservative approach with drivers and kernels. They actually test that stuff works, thus avoid having widespread disasters.

If you want to be on the bleeding edge, you might want to try a different distro.

I would be amazed if updated video drivers have anything to do with how hot your laptop runs. If that is your issue, start a different thread, and begin by saying what brand and model of laptop you have.

---

### Post by jwdv22 on 2010-07-14
> **gordintoronto said:**
> Ubuntu follows a conservative approach with drivers and kernels. They actually test that stuff works, thus avoid having widespread disasters.

If you want to be on the bleeding edge, you might want to try a different distro.

I would be amazed if updated video drivers have anything to do with how hot your laptop runs. If that is your issue, start a different thread, and begin by saying what brand and model of laptop you have.

1.) Is it bleeding edge to get drivers for a chipset that maybe Ubuntu hasn't tested with? Is it bleeding edge to want to join the linux community want to learn about it and learn how to install stuff? If I wanted to have decisions and chooses made for me, I guess I would be an Apple lemming.

2.) Consider yourself amazed. Read the link I sent. Intel doesn't supply the drivers for Linux anymore.


Can anyone help with any tips for installing Intel Chipset drivers?

---

### Post by snowpine on 2010-07-14
> **jwdv22 said:**
> 1.) Is it bleeding edge to get drivers for a chipset that maybe Ubuntu hasn't tested with? Is it bleeding edge to want to join the linux community want to learn about it and learn how to install stuff? If I wanted to have decisions and chooses made for me, I guess I would be an Apple lemming.

2.) Consider yourself amazed. Read the link I sent. Intel doesn't supply the drivers for Linux anymore.


Can anyone help with any tips for installing Intel Chipset drivers?

Please try to be more polite to other users. :) Everything Gord said is true and he was just trying to help. To expand a bit, Ubuntu 10.04 was released in April, and the Intel 2010Q2 Graphics Package was released June 27. Therefore, until someone invents time-travel technology, the driver you are looking for will never be a part of Ubuntu 10.04. ;-)

If you are looking for a more "bleeding edge" experience, you might consider testing Ubuntu 10.10. Obviously, this is Alpha software, so you should expect frequent breakage and crashes if you go this route.

Another option is to stick with 10.04 and use the "xorg-edgers ppa". This is a bleeding-edge, 3rd party software repository that is not supported by Ubuntu in any way: [https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

(note: I am not promising that either of the above options will necessarily give you the driver you're looking for, just that they are the 2 most bleeding edge Ubuntu options I am aware of.)

ps I agree with the above hypothesis that bleeding-edge video drivers are likely NOT the best solution to your laptop overheating problem.

---

### Post by jwdv22 on 2010-07-14
Fair enough, I guess trying to figure out installing the drivers has me frustrated. I do realize he was trying to help, but I guess I was more or less looking for someone to help with an answer, not tell me to go look for another distro.


If I move to a move bleeding edge distro would have have my chipset drivers?

---

### Post by snowpine on 2010-07-14
> **jwdv22 said:**
> Fair enough, I guess trying to figure out installing the drivers has me frustrated. I do realize he was trying to help, but I guess I was more or less looking for someone to help with an answer, not tell me to go look for another distro.

If I move to a move bleeding edge distro would have have my chipset drivers?

I don't actually agree with Gord's advice. :) I think you should stick with Ubuntu 10.04 and avoid anything "bleeding edge" until you are more experienced with Linux (and when you are, you might rethink that goal ;)). 

Unless you are having a specific graphics-related problem, I would recommend using the stable and well-tested graphics drivers provided with the distro.

Post a new thread about "my laptop is overheating" with specific hardware information, and I'm sure you will get some good advice. :)

---

### Post by jwdv22 on 2010-07-14
> **snowpine said:**
> I don't actually agree with Gord's advice. :) I think you should stick with Ubuntu 10.04 and avoid anything "bleeding edge" until you are more experienced with Linux (and when you are, you might rethink that goal ;)). 

Unless you are having a specific graphics-related problem, I would recommend using the stable and well-tested graphics drivers provided with the distro.

Post a new thread about "my laptop is overheating" with specific hardware information, and I'm sure you will get some good advice. :)

Here is why I think it is a driver issue.

Powertop says this

Top causes for wakeups:
  48.6% (402.7)   [uhci_hcd:usb3, uhci_hcd:usb4, uhci_hcd:usb5, sky2@pci:0000:01:00.0, ipw2200, yenta, **i915**@pci:0000:00:02.0, ohci1394, mmc0, mmc1, mmc2] <in
And xsensor says temp 1 is 75 degrees C and temp 2 is 54

Here is the new thread you suggested. Thanks
[http://ubuntuforums.org/showthread.php?p=9588420#post9588420](http://ubuntuforums.org/showthread.php?p=9588420#post9588420)

---

