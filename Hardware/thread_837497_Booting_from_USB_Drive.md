---
title: "Booting from USB Drive"
date: 2008-06-22
forum: Hardware
---

### Post by leftfootleashed on 2008-06-22
Hi,
Anyone know whether the following would work:
Take my hard drive, with my Ubuntu install and all my data, put it in a USB hard drive enclosure and boot from it with another computer, to avoid using the Windows install on that computer.
Any comments regarding potential problems, performance, etc. would be appreciated.
Thanks,
Dave

---

### Post by Fzang on 2008-06-22
If USB sticks work then I don't see why this wouldn't

---

### Post by Ng Oon-Ee on 2008-06-23
Should work, if GRUB is installed on the external hard disc.

---

### Post by paulderol on 2008-06-23
the only concern i can come up with would be the relatively slow speed of USB compared to even IDE, which drops to a trickle compared with SATA drives. So your issue, as i would see it, would be with slow rates of return and longer load times since all of your system would have to pass through the USB to get to the actual computer.

it should work though.

you might use WUBI instead with a shared folder, but that may not meet your needs.

---

### Post by AndyCee on 2008-06-23
It's worth mentioning that grub may play up if it doesn't detect a partition/drive that it's expecting. (eg. is the portable HD sda1 or is the local HD sda1 ?).

---

### Post by leftfootleashed on 2008-06-23
Thanks for all your advice - I think all that remains now is to give it a try and see what happens.
Cheers,
Dave

---

### Post by AndyCee on 2008-07-22
> ...see what happens.

So what happened?

---

### Post by leftfootleashed on 2008-07-23
I decided not to do it in then lol.

---

