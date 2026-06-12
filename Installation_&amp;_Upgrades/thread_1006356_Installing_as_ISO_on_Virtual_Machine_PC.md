---
title: "Installing as ISO on Virtual Machine PC"
date: 2008-12-09
forum: Installation &amp; Upgrades
---

### Post by ol_ing on 2008-12-09
I am trying to install Ubuntu 8.10 server on a "Virtual Machine" I created on my PC. I select to run Ubuntu from an ISO image (capture ISO image) and then get the installation display. When I select to run installation, the installation starts (probably by unpacking), but then halts immediately. The last line displayed is:

0.160010] ---[end trace 4eaa2a86a8e2da22]---

The cursor blinks beneath this line and nothing can be done. Any ideas of what is wrong or how to continue?

Thanks,
ol_ing

---

### Post by jenkinbr on 2008-12-09
Have you tried verifying the CD (in your case the ISO) by checking the disk for defects in the VM?

---

### Post by ol_ing on 2008-12-09
Yes I tried to run the "Check CD (ISO) for defects". It stops with the same message as before (when selecting "Installing Ubuntu Server")..

---

### Post by jenkinbr on 2008-12-09
Perhaps you have a bad ISO.

Could you verify the MD5 hash with that which is posted where you downloaded the file to begin with?

---

### Post by caleb.vear on 2009-01-06
I had the same problem.  To get around it I installed Virtual Pc 2007 SP1 and then at the install screen I pressed F6 and added *noreplace-paravirt* to the options.  Give that a go and see if it works.

---

### Post by Bongus on 2009-01-08
Thanks for the Info.  I'm using Virtual PC 2004.  All I did was press F6 and then enter the commands.  The install started up no problem.  Currently installing.....

---

### Post by Bongus on 2009-01-09
Ok, Got in it installed but now it won't run, I get the same error as above.  When I try to add the *roreplace-paravirt[I]*[/I]
into GRUB it either doesn't work or I get a Fatal Processor Error (Depending on where I put it)

Anyone else have any ideas??

---

