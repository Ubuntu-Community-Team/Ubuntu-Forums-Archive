---
title: "[SOLVED] Cannot Install 8.04.1 LTS (I've tried everything)"
date: 2009-01-02
forum: Installation &amp; Upgrades
---

### Post by zaveloff on 2009-01-02
I cannot install Ubuntu 8.04.1 LTS no matter what I do. I have a Dell Inspiron 530 with an Intel Core 2 Quad processor, 3 GB of RAM, 1 TR on two internal SATA hard drives (500 GB each), and two DVD RW drives. When I try to either run Ubuntu from the CD or to install it, it gets past the sliding bar and then the screen changes to what appears to be a command prompt. The next thing is a series of error messages that seem to go on forever (the longest I've let it run before manually rebooting up to this point is about an hour). The error messages are all the same with a revalidating/failure repetition.

I first downloaded the CD iso an burned a disk. When this did not work, I ordered a disk thinking there might be something wrong with my download or the burning of the CD. However, I get the same thing with the disk that was sent me (as well as with the Kubuntu disk that was sent also). I tried installing in Windows (I am running Vista Business) but this did not help either and I get the same error messages. As a last resort, I downloaded the DVD iso but it did not make any difference. I have not tried the alternative CD since the explanation for this says that it is for those who have problems with a graphic installation--that does not seem to be my problem.

BTW, I was able to use the CD to install Ubuntu in a virtual machine on a MacBook using VMWare so I know the problem is not the CD.

Can someone please help?

---

### Post by dstew on 2009-01-02
For some reason the Linux kernel on the CD is not able to run on your system. Usually this is because of some characteristic of your system that was not anticipated by the kernel-makers.

You might try another version, like 8.10, or even an older version, like 7.10, and upgrade from there. Often an older kernel will work better.

You can also try kernel parameters. You enter these on the kernel line that you get by (I think) pressing F6 at startup. Kernel parameters temporarily disable or change kernel modules (device drivers) that might not be working well with your hardware. Often tried, with variable success, are the parameters noapic, nolapic, acpi=off, all_generic_ide, irqpoll. You can try these alone, or in combination.

If you can see the very first errors that appear, this might give you a clue as to which kernel parameters to try. To see the kernel errors early, change the kernel line parameters "quiet splash" to "nosplash". That lets you see the text better.

---

### Post by Pumalite on 2009-01-02
Try the Alternate CD amd64

---

### Post by zaveloff on 2009-01-02
I downloaded 8.10 and it installed fine. Thanks for your help

---

