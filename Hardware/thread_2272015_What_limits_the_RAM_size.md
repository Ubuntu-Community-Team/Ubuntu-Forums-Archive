---
title: "What limits the RAM size?"
date: 2015-04-03
forum: Hardware
---

### Post by Unterseeboot_234 on 2015-04-03
I uninstalled 2GB DDR2-SIMM from a 4GB 'upgrade' because I could never exceed 50% usage of 2GB. This is according to System Administration --> System Monitor. I know you have to have a 64-bit OS to even see 4-GB, but I never seemed to be using one third of the installed 2GB. Instead my AMD64 Athlon-II CPU seems to be the speed bottleneck. Intensive file copying to LAN or video rendering slow down the computer over time with the Athlon constantly being maxed out at 100% usage. 

In another Ubuntu box we have the Hexacore AMD64 which takes a long time to boot the OS but once running the workflow is 4 times faster than a single-core CPU. System monitor shows 6 CPU History graphs and basically 2 cores rarely come online and work. Again, it is rare we exceed 50% usage of 2GB RAM on that box also.

How would I ever use a total of 4GB of RAM?

---

### Post by dino99 on 2015-04-03
which kind of installation is it ? is it a single desktop with real install or a shared installation on a lan/cloud/vm ? have you full control on the machine settings or is there an other admin ?
what you described is either false (64 bits/4gb) or abnormaly strange: all pc on earth are able to use 4 gb if the bios settings are ok

---

### Post by sotiris2 on 2015-04-03
Well I wonder if cp does only use buffers/cache (as you would see in free) which system monitor does not display.

---

### Post by Mark Phelps on 2015-04-03
>  I know you have to have a 64-bit OS to even see 4-GB, Not true.  Recent Linux distros use PAE such that 32-bit installs can see far more than 4GB.  I have Mint installed in 32-bit and it can see all of my 12GB without problems.

---

### Post by mörgæs on 2015-04-03
The drawback of using a 32 bit PAE install is that each application can only use 2 GB, no matter how much is available.

---

### Post by Unterseeboot_234 on 2015-04-03
My hardware is a tower box, dedicated Ubuntu 14.04 64-bit desktop. I can see the physical RAM count in BIOS -- both in startup and set-up. I have never exceeded a gig of RAM in any computer usage. I can recall having to program for 64-K memory on the mainframes. I have frozen the Java plug-in in a browser after exceeding 90MB. But, I've never exceeded a gig of RAM using multi-tasked Ubuntu. My computer did write heavily to Swap when I had just a 1-Gig SIMM installed. I do recall 32-bit OS machines always leave a tiny portion of installed memory as never addressable.

I don't care for virtualization. VM reminds me of why the original Macintosh OS would freeze for no reason and require constant hard reboots.

So, I guess my question is: Is there any situation when 4GB of RAM will enhance my computer usage? What does one do with a 16-gig RAM machine? All I can think of you would have to write your own program to utilize those extra addresses.

---

### Post by ajgreeny on 2015-04-03
> **Unterseeboot_234 said:**
> So, I guess my question is: Is there any situation when 4GB of RAM will enhance my computer usage? What does one do with a 16-gig RAM machine? All I can think of you would have to write your own program to utilize those extra addresses.
What do you use your machine for?  I have 8GB ram on mine but in "normal" use it seldom uses more than 1GB.  However on the odd occasions that I use some video encoding application it can rack up the ram usage enormously.

Try using handbrake or VLC to decode and re-encode a video from one HD format to another HD format; that not only uses ram but also cpu.

Finally, although you obviously don't use it according to your comment, running VMs on your host will eat up its ram, and run two or three VMs simultaneously on the same host and you can easily use 7 or 8GB ram.

So, to answer your question: "How long is a piece of string?" - it all depends!

---

### Post by Unterseeboot_234 on 2015-04-03
Thanks, ajgreeny. I'm going to re-install Cinelerra and the 2nd 2GIG SIMM and see if I do go over 2-gig usage. The single-core AMD will bang the ceiling when I render, I can tell you that. Then I'll do the same thing with my Hexacore AMD. But, seriously I've tried several things trying to see how much RAM is utilized including taking out a PCIe graphics card and using the onboard nVidea chip. My reasoning is if the computer never uses more than 2-GIG then why cook the unused SIMM? My thinking is just keep the extra SIMM for a spare.

---

