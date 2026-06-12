---
title: "lshw segmentation fault"
date: 2017-08-14
forum: Hardware
---

### Post by herveb on 2017-08-14
Hello

i'm a newish user, and downloaded today lubuntu 17.04 on a acer aspire 4740G with a atheros ar5b93. I was able to connect to the internet previously on the same pc using puppy linux.
when trying to connect to the internet, no wifi network is appearing on the list.

i have typed ```
sudo lshw -C network
``` and got
segmentation fault (core dumped)

what's wrong?

---

### Post by user_of_gnomes on 2017-08-14
Did you check the disc for defects before installing Ubuntu?

---

### Post by herveb on 2017-08-14
nope - not sure how to do this. Actually that would make sense, as the previous windows install was corrupt beyond repair and the mothercard is complaining at the bootup (i got a rapid succession of several beeps before the OS takes over).

any suggestions on how to take it from there?

---

### Post by user_of_gnomes on 2017-08-14
You can easily check the status of the hard drive (or SSD) from within Ubuntu by typing "disks' in Dash and then clicking on the three bars on the right hand side after selecting the hard drive in question.
From there you go to S.M.A.R.T data & self tests and click on start self test. A quick test is often enough to bring serious problems to light. You can also post the S.M.A.R.T data here for review.

You can also try your hand at the command line version if you're up for it: [https://help.ubuntu.com/community/Smartmontools](https://help.ubuntu.com/community/Smartmontools)

The installation media itself can be tested by selecting "Check disc integrity" when booting from it. Not sure if this applies to usb-media as well.
See this article for mor [https://help.ubuntu.com/community/Installation/CDIntegrityCheck](https://help.ubuntu.com/community/Installation/CDIntegrityCheck)

Might want to test your RAM while you're at it, any way: [https://help.ubuntu.com/community/MemoryTest](https://help.ubuntu.com/community/MemoryTest)

> This page explains how to perform a memory test on Ubuntu Live CD and Installed system.

    Turn On or Restart the system

    Hold down Shift to bring up the GRUB menu.

    Use the arrow keys to move to the entry labeled Ubuntu, memtest86+

    Press Enter. The test will run automatically, and continue until you end it by pressing the Escape key
    Allow the test to run for at least one full pass 

It also sounds to me like your mainboard is trying to tell you something. Did you check your mainboard for bad capacitors and poor CMOS battery voltage?

---

