---
title: "SMART hard drive Data irregulatories"
date: 2019-08-23
forum: Hardware
---

### Post by rsteinmetz70112 on 2019-08-23
I have a machine with 4 hard drives in 2 arrays. A while a go I began getting SMART  errors indicating an eminent failure. I got another drive installed it in the array and rebuilt. 

Today I had a power supply failure and after replacing the hard drive when rebooting that one I began to get SMART failures on boot and an error message from the Motherboard. It was identifying two different drives as failed. I had some issues getting the machine back up, still getting SMART errors whenever I tried. Once I got it to boot I found the arrays were not assembling properly. I re-added the hard drives and the array began rebuilding. Using Disk Gnome Disk Utility I checked the SMART status and all disks reported that they were OK, I'm no longer getting teh boot errors.

Can anyone offer a theory of what is happening and how I might check further?

---

### Post by TheFu on 2019-08-23
Please post the raw SMART data for each drive so we can see some facts.

---

### Post by rsteinmetz70112 on 2019-08-25
Unless there is some way to restore the previous readings I can't. The current SMART data shows everything within acceptable parameters. 
I did not have smartctl installed and relied on Gnome Disks to periodically check the drive status. I was getting SMART errors from the motherboard, it would halt during startup and reporting 2 of the drives had SMART errors and needed to be replaced.

---

