---
title: "Network printer problem with new Dapper"
date: 2006-07-14
forum: Hardware &amp; Laptops
---

### Post by ramblur on 2006-07-14
I have installed the new Dapper 6.06 but cannot get my network printer to work. This printer worked with Breezy on this machine and currently works with another machine I have just upgraded from Breezy.

It is a networked HP PSC-1600 that I added as a Samba printer.  The printer was detected and seems to be there and when I try to print a test page or from any other program the job appears to go through.  However it does not and this error appears in my CUPS error log for each job (this is the only error):

**E [14/Jul/2006:13:03:11 -0400] [Job 11] No %%BoundingBox: comment in header!**

An error also pops up on the Windows machine that hosts the printer basically stating there was an error found in the "Remote Downlevel Document".

Anyone have any idea what is happening (or not happening)?  Have I discovered a new bug?  I see a few other posts about this error but no resolution yet.

Everything else works perfectly but this one item!

---

### Post by ramblur on 2006-07-15
Apparently a reboot of the Windoze machine was all that was needed???  

I am now seeing authorization errors in the cups error log but these do not seem to be affecting printer operations.

At least everything is now working correctly!  Very kewl indeed.

---

