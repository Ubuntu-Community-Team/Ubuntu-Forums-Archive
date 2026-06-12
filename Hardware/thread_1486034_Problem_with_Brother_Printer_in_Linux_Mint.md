---
title: "Problem with Brother Printer in Linux Mint"
date: 2010-05-17
forum: Hardware
---

### Post by AvataroftheSun on 2010-05-17
I'm having some problems with my printer working correctly in Linux Mint.

My OS is Linux Mint 8 Helena x64.
The model of my printer is Brother DCP-7030.  It connects via USB.

I have already installed the LPR and cupswrapper drivers from the Brother website by following their tutorial: [http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn1a.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn1a.html)

The result of checking the state of the drivers is:
```
corey@corey-desktop ~ $ dpkg -l | grep Brother
ii  brdcp7030lpr                                   2.0.2-1
Brother DCP-7030 LPR driver
ii  brscan3                                        0.2.9-1
Brother Scanner Driver
ii  cupswrapperdcp7030                             2.0.2-1
Brother DCP7030 CUPS wrapper driver

```

One thing I'm already speculating is that the drivers are intended for a 32-bit OS and I'm running a 64-bit.  I'll try to install the 32-bit version to see if that works, but I want someone else's opinion.

---

### Post by AvataroftheSun on 2010-05-18
Update:  I've installed the 32-bit version to a seperate partition and installed the same drivers and they come up with the same problem.  Specifically (forgot to mention this sooner), when a job is sent to the printer, it just prints a bunch of pages with only a dot of ink on them until the job is canceled.  Anyone know what I might be doing wrong?  Help would be most appreciated for the 64-bit version, but I'll take anything anyone knows about.

---

