---
title: "Dell Dimension 9100 dual core &amp; UBUNTU"
date: 2005-09-23
forum: Hardware &amp; Laptops
---

### Post by dqsis on 2005-09-23
Hello UBUNTU friends!  

I recently got a DELL DIMENSION 9100 DUAL CORE computer. It also has a SATA hard drive. 

Before installing anything I would like to ask the following:

= Will UBUNTU recognise the Dual Core Processor? Has anyone previous experience?

= Will UBUNTU work ok with the SATA hard drive?

= If UBUNTU doesn't support the above, which other Linux version do you suggest I should use? Maybe SUSE?

Thank you all in advance!

---

### Post by fordfan753 on 2005-09-23
Ubuntu should be fine with the SATA, I don't know about the dual core, you may have to install an SMP kernel, ie Ubuntu might see the dual core as two parallel processors. I base this on absolutely nothing, feel free to correct me.

---

### Post by dqsis on 2005-09-23
When I insert the CD everything seems to start nicely, but after a while I get the error:

"Cannot read data from the CD. Check's CD's integrity". 

Do you have any idea where the fault lies? It must be an incompatibility somewhere because the CD works perfect! 

Thanks!

---

### Post by fordfan753 on 2005-09-23
Integrity check normally implies a bad burn....

---

### Post by matt h on 2005-09-23
You might want to be cautious. I expected better success with this machine, and i have read threads of successful installs...but...

my 9100 is a single core dual thread machine, but i basically can't get Unbuntu (live) (or pretty much any other Linux distro) to work.

I think it's a combination of the SATA drive and the Radeon X300 card. 

The best i've been able to do is get a command line from Knoppix with a bunch of the HW detection turned off.

I, too would appreciate some suggestions. 

-matt

---

### Post by bob_c_b on 2005-09-23
Intel has released binary drivers for the 945 chipset for Linux, but so far only RedHat RPMs are available for download. I doubt any non-beta distro out right this minute has drivers for the 945 chipset or recognizes a dual core PIV, but I am sure by the end of the year all will be on board. I know the binaries released for RedHat are also working in Fedora Core 4 as well. Good luck.

---

