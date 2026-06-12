---
title: "Core 2 Duo vs Core 2 Quad"
date: 2015-03-15
forum: Hardware
---

### Post by Max_Henderson on 2015-03-15
Hi, 

I am relatively new to Linux and run 14.04. I've recently put together a used machine:

HP dc7900 with an SSD and 8GB.

It runs very well and I'm very happy. 

It's been such a cheap set-up, I've thought of throwing a little more money at it cause I'm still way under-budget of what I expected to pay. 

The CPU is a Core 2 Duo E8500 running at 3.16GHz.
(benchmark 2310 at cpubenchmark.net)

I was thinking of swapping it out w/a used Core 2 Quad Q9550 @ 2.83GHz.
(benchmark 4070)

In terms of use, I'm mostly in Chrome (using very heavy web apps), LibreOffice, GIMP, and Sublime. 

Most of the discussions I've seen on 2 vs 4 cores are a few years old and it's been hard to pin down a conclusion on performance improvement. 

I don't need to experience a vast improvement to justify the upgrade... I just want to know that I'll experience at least something. 

What do you think?

Thanks for any input, in advance.

---

### Post by weatherman2 on 2015-03-15
For those uses, I doubt you will notice any performance difference.

Why do more cores help?  They allow your machine to do multiple things at the same time.  Linux can schedule multiple tasks on a single core to share the CPU.  But unless one task was written in a parallel way so that it can be split over multiple processors, you won't see any speed-up by adding additional processors or cores.

I'm not sure how a Chrome process can split out its tasks in a parallel way.  You can check that out with your current CPU and two cores.  Monitor the CPU use as you work, then stop and look at the CPU load (use the "top" command in a terminal window).  When you are manipulating images in GIMP - say resizing an image or applying a filter - it will probably use only one process running on one core.

I think you'd see more benefits from running Windows with a quad core CPU than a single-user Linux computer would.  Windows needs to run anti-virus scans while you are doing other things at the same time.  Linux does other tasks in parallel too while you are working but generally not a lot.  A multi-user machine or server would also benefit more from a quad core CPU.

I'm glad you are happy with your new setup, but keep in mind it's getting to be old technology now.  The Intel i3/i5/i5 "core" CPUs - starting with 2nd generation (Sandy Bridge) integrate the video onto the CPU, giving you great performance improvements over old generations (unless you have a separate video card).  And they also use less power, so the fan can be smaller/slower/quieter.  The newer motherboard have chipset that can also handle USB 3.0, faster SATA ports, etc.

---

### Post by PhilGil on 2015-03-15
I agree with the previous poster. The only upgrades that I would consider on a computer of that age would be more RAM (go to 4GB if you have less) or more "portable" upgrades such as an SSD, larger hard drive or video card.

---

