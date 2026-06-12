---
title: "A kubuntu laptop - power management &amp; hdd life"
date: 2007-07-23
forum: Hardware &amp; Laptops
---

### Post by schultz on 2007-07-23
Hello, I am new to the Ubuntu community.

I have just installed Kubuntu Feisty Fawn in my HP ze4950. It works very nicely.

Previous to that, I was having a hard time making Gentoo hibernate or suspend, or even using lm_sensors. ](*,)

Then I used kubuntu. I must say I am impressed.

There are some downsides in kubuntu that I hope to fix, though.

The one that make me the most preocupated is turn on/off, hibernate and suspend. When I do any of them the screen gets some garbage in some points and in shutdown the laptop makes a hell of a noise! Also, the console is not what I can call pretty (as it was in Gentoo).

This noise is really making me feel worried (about hardware damage). It says "power down" in the console and then do a noise like "Phiuuuuu"!!!

Windows (yes, the laptop came with windows) did not do that noise.

Also, the suspend/hibernate/boot time is too large. It takes more than 20 seconds to suspend and additional 20 to resume. Hibernation takes some 25 secs in suspend and other 30 in resume. Boot is as bad.

Except for acpi, there has been some problems. I told the loggers to stop and never be turned on at boot, but someone keep writting to the disk.

I heard an article in which someone says using laptop-mode incorrectly may damage the hdd.

I want to maximise the lifetime of the PC. How is it I can tune the laptop so that it lasts the most?

I do not know how to debug hdd usage / life time / status.

I installed superkaramba and downloaded Norakai system monitor. I found it ugly and want to remove it, but then uninstall button does not show up (like a virus!).

Is it ok to put XGL in this machine or is it too heavy?

Please answer, I need help, otherwise I cannot feel confortable in using kubuntu.

I liked the system very much, it is nice, nice indeed. I thank all the community for such a nice system. Thanks very much.

(I also liked the Goku simley: :lolflag:, what does LOL mean?)

---

### Post by fredj on 2007-07-25
Apparently there is a problem with disk shutdown and that is responsible for the noise you hear from the HDD.
Some people have suggested that this will shorten the life of l HDDs. It is a kernel problem and is in
other distributions as well. It has been reported as a bug and will be fixed in the next kernel release. 
I don't know if it will shorten the life of a HDD or not but at present the last few kernels do not unload the disk 
heads properly before cutting the power so the noise you hear is the disk unloading the head itself and then spinning down.

---

### Post by viking777 on 2007-07-30
I too suffer from shutdown problems with my laptop - I have to hold down the power button every time to get it to switch off - and although I am now using kernel kernel 2.6.22-8 it has still not been fixed, so when you say it will be fixed "in the next kernel release", which kernel do you mean?

Make that the 2.6.22-9 kernel now and it still doesn't work!!

---

