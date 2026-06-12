---
title: "Can I have backed up data on my USB start up thumb drive ?"
date: 2014-12-02
forum: Hardware
---

### Post by michael-piziak on 2014-12-02
I only have one thumb drive now.  I "might" use it to try out a 64 bit version of Ubuntu for my computer.  
Can I put data (backed up data like photos) on the same USB thumb drive that I will make a 64 bit USB Startup Up DIsk for Ubuntu (installation) on ?

---

### Post by Mark Phelps on 2014-12-02
Not sure, but my guess would be -- probably not.

All the apps I've used to create Linux startup disks start by reformatting the entire USB drive -- which would erase anything already on there.

You might be able to do what you want if you reverse the process:
1) Create the Linux startup drive using the USB stick
2) Insert the USB stick and open Gparted
3) Shrink down the Linux filesystem partition to leave some room
4) Create another partition in the free space
5) Copy the data you want to save to the new partition.

That said, given the relative cheapness of USB sticks, and the possibility that you might accidentally reformat this stick (forgetting that you had stuff saved on it), my own advice would be to use separate USB sticks.

---

### Post by michael-piziak on 2014-12-02
Thanks so much for your reply.

I will just buy another usb stick when I'm at Walmart.   

Marking this thread as solved.

---

