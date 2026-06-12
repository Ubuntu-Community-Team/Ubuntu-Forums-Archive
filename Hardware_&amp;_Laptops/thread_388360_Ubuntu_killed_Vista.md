---
title: "Ubuntu killed Vista?"
date: 2007-03-19
forum: Hardware &amp; Laptops
---

### Post by IceBergEB on 2007-03-19
All of a sudden Vista is not booting up past the logo screen (with the green
animated progress bar). Actually, it goes into blank screen mode after 1-2
minutes and nothing happens ever after that.

Worst yet, even the Vista Ultimate CD (which I used originally to install,
twice before) is NOT loading past the same screen (logo)! it first goes
through the 'loading windows files...' then boots to the logo screen and
nothing happens for several minutes!


Originally before all this I simply booted (not installed) from Ubuntu CD to
test it out. I attempted to install and was stuck on step 5/6 where it asks
for partition. I made it 40GB (120GB total drive) and nothing was happening,
I successfully canceled and then all broke loose after that.

What should I do? I'm really stuck, can't boot of Vista CD nor drive. I have
critical data on my hard drive.


Yes, the machine, a Toshiba P105-S9339, came with Vista Ultimate installed.

---

### Post by milton1 on 2007-03-19
Did you actually choose "write partitions to disk"? If not, sounds like a hardware issue. Since your machine has vista, I will assume it is fairly new. Make use of your warranty.

Can you boot the live cd? You could use that to retrieve data just in case.

Even if you did start the partitioning process, that should not interfere with booting from the CD. This really sounds like a hardware issue.

---

### Post by IceBergEB on 2007-03-19
Thanks.  I think my MBR was hosed. I will try to recover my data with the livecd, but would still like to hear from others.

To be more specific, I did write the partitions to disk, but then got a message that I had to set up a swap file.  I tried to go back and do this, wasn't allowed to, cancelled the install and removed the partition.  I have tried to recreate the new partition using gparted, but it will not allow me to create a partition of any size.  I am considering wiping the whole drive, but see this as a last resort.

---

### Post by dptxp on 2007-03-19
Ubuntu has not killed Vista (yet). It may one day.
No, not on your PC of course:) .

---

### Post by equability on 2007-03-19
Ciao mi amici.

There is no need for it !

Vista will kill itself ):P

---

### Post by milton1 on 2007-03-22
MBR should not be affected until grub is installed, and agian, even a hosed MBR should not interfere with booting from CD unless bios is set to boot from hd first. Maybe check bios settings?

---

