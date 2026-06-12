---
title: "Screen flickering issue on MSI U120."
date: 2010-05-02
forum: Hardware
---

### Post by Linuxperiment on 2010-05-02
I tried installing both Ubuntu 10.04 Desktop AND Netbook Edition, and both are the exact same in regards to this issue.

MSI U120 Specs:
Intel Atom 1.6 GHZ (Single Core)
Intel GMA 950 Graphics

#1) The Live CD is fine, there is no flickering.
#2) After installed to the HD on first boot up, the screen starts flickering (the adjustment of brightness goes up and down over and over VERY quickly)

What can I possibly do to resolve this? I don't know if it's a kernel, BIOS, or Ubuntu issue. Any ideas, or should I just switch distros?

---

### Post by acubu on 2010-05-02
As I was very satisfied with the ubuntu versions over the past years in several PCs, I didn't hesitate to upgrade. Now I am i bit disappointed about the change to the 10.04 LTE.  I expected a real progress like in the past years.
My netbook a Dell Inspiron 6400 worked great with 9.10  but with the change to 10.04 after a few minutes the graphics on the left half of the screen begins to flicker and I didn't find a solution, yet  to solve this. The only thing that works is to reboot. after a few minutes the flickering restarts.
This was with the new kernel 2.6.32. 

I started the computer with kernel 2.6.31 and there the flickering does not appear. Everything runs stable there as it ran with 9.10. 
Perhaps you should also get back to 2.6.31 to fix the problem for the moment.
I didn't yet try how the live CD works, this could be another try, but I do not think it will be a solution.
As well I didn't make a clean install I upgraded.

What is the difference in setup of the graphics of the two kernel versions?

---

### Post by Linuxperiment on 2010-05-02
I had a feeling it was the kernel, because Ubuntu 9.04 runs great on it, although its sort of outdated now.....guess it's time to distro hop

---

### Post by SaltAndVinegar on 2011-12-28
Just in case there is still someone with this problem:
There is a small 'work around' because I have the same issue on my MSIU120 with the Ubuntu LiveUSB key and the Ubuntu-based Caine distribution on my USBstick..

1) Open a terminal
2) Switch to the terminal full screen view with ctrl+alt+F1.
3) Now switch back to Ubuntu desktop with ctrl+alt+F7

The flickering should disappear!

Good luck!

(Thanks to my friend who told me that)

:)

---

