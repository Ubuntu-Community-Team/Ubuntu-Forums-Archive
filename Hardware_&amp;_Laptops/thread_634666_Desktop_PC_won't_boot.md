---
title: "Desktop PC won't boot"
date: 2007-12-07
forum: Hardware &amp; Laptops
---

### Post by Gold257 on 2007-12-07
Alright, I started out on XP, then attempted to install 7.10 Desktop via the CD obtained from a .iso image. Used WUBI, worked smoothly. Booted from Live CD, again, worked smoothly. After about an hour toying around on the Live session, I attempted to install fully on the HDD. This might be where I messed up... I think I partitioned incorrectly. I intended to completely format the HDD and install Ubuntu cleanly, but I think I made a separate partition for Ubuntu. Regardless, I booted, and after the BIOS shadowed I recieved an "Error loading OS" message. After several unsuccessful reboots/cold boots, I booted again from the CD several times, but could only get so far as Terminal, and due to my limited knowledge, was unable to get farther than this.

Here's where things really went south. After I shut down from Terminal, I attempted to boot again. This time, I didn't even recieve a BIOS message; I just got a black monitor feed. This leads me to believe it is a motherboard-related problem. I was about to hook up the bad HDD to my working PC, wipe it, reinstall Ubuntu, and try to boot again. Did I completely destroy my computer? Please tell me what I can do, it's a beast of a machine, I'd like to be able to salvage what I can.

Hardware:
>HDD: Maxtor HD, 250 GB, SATA (Run through motherboard)
>Not sure about motherboard type
>Processors: Dual AMD-Athlon 64 (Not sure of anything else)
>3 GB RAM

Hopefully, the information I've provided will help somewhat in the diagnosis.

---

### Post by Chainz on 2007-12-08
If you're saying that you can't normally start with live CD and can only get to terminal it seems that your CD might get corrupted. I'd run a check on it...

But you sad that later on, that you just got blank screen... No panic man!
I got the same when I put my first SATA into my machine. I had to clear CMOS several times + changing configuration (physical connection) of disks to make it work finally.

Try resetting BIOS.

---

