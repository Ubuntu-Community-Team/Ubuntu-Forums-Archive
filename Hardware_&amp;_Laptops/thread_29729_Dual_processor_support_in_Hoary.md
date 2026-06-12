---
title: "Dual processor support in Hoary?"
date: 2005-04-25
forum: Hardware &amp; Laptops
---

### Post by shane101 on 2005-04-25
Hi all

I'm a Linux newbie and I managed to get an old Dell PowerEdge 2300 server from work. I've installed Ubuntu Hoary Hedgehog on it. It has two P2 350MHz processors in it but Ubuntu only seems to recognise the one. Could anyone tell me how to get Ubuntu to detect the second processor and make use of it?

Thanks,
Shane101

---

### Post by PaRRoT.it on 2005-04-25
[QUOTE=shane101]Hi all

I'm a Linux newbie and I managed to get an old Dell PowerEdge 2300 server from work. I've installed Ubuntu Hoary Hedgehog on it. It has two P2 350MHz processors in it but Ubuntu only seems to recognise the one. Could anyone tell me how to get Ubuntu to detect the second processor and make use of it?

Thanks,
Shane101[/QUOTE]
 I think you had to install kernel-image-2.6.10-686-smp and use it.

---

### Post by shane101 on 2005-04-25
[QUOTE=PaRRoT.it]I think you had to install kernel-image-2.6.10-686-smp and use it.[/QUOTE]
 Thanks. Does that mean I have to download the OS again?

---

### Post by kmyram on 2005-04-25
No, just install... At the prompt (Applications > System Tools > Terminal) type:

sudo apt-get install linux-image-2.6.10-686-smp<enter>

And reboot after the new kernel is installed.

---

### Post by ZiZe on 2005-04-25
no, you should only have to do:
sudo apt-get install linux-image-2.6.10-5-686-smp

and both your processors should be registred.
when you have installed the smp kernel you can
cat /proc/cpuinfo
and check that you have 2 cpu's registred there (processor 0 and 1)

---

### Post by shane101 on 2005-04-26
Thanks very much for your help guys. I'll try it out this evening and post the results.  :-P 

Cheers!

---

### Post by rurp on 2005-04-26
I tride to install a SMP-kernel (apt-get install linux-image-2.6.10.....smp) but after the instalation a can't start X. Any ideas wath to do?

---

### Post by shane101 on 2005-04-26
Alright, here are a few lines from my terminal:

sudo apt-get install linux-image-2.6.10-686-smp
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package linux-image-2.6.10-686-smp

What am I doing wrong? Do I need to enable the Universe and if so how do I go about it?

Thanks,
Shane101

---

### Post by aulin on 2005-04-26
I had to install the SMP kernel myself as I have a P4 with HT this is what you want:

sudo apt-get install linux-image-686-smp

---

### Post by shane101 on 2005-04-26
Excellent, thanks aulin. Sorry about this but I'm really stumbling round in the dark  :roll: 

This is what's coming up when I type that in my terminal and hit Enter:

W: Couldn't stat source package list [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) hoary/main Packages (/var/lib/apt/lists/za.archive.ubuntu.com_ubuntu_dists_hoary_main_binary-i386_Packages) - stat (2 No such file or directory)


Did you have the same thing?

---

### Post by shane101 on 2005-04-26
This comes up at the end of the message in my terminal:

W: You may want to run apt-get update to correct these problems
E: Couldn't find package linux-image-686-smp

I try to run apt-get update but then I get the error you see below.

shane@SHADRACK00:~$ apt-get update
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory

Any suggestions?

---

### Post by compmodder26 on 2005-04-26
use "sudo apt-get update"

---

### Post by ZiZe on 2005-04-26
shane101:
i dont know if you already looked at this page
[www.ubuntuguide.org](www.ubuntuguide.org)
It is an unofficial starter guide for ubuntu.
Very helpfull for beginners :)

---

### Post by shane101 on 2005-04-26
Thanks Zize I've been looking at it, so far isn't solving my problem  :) 
No sweat I'll keep trying things.

---

### Post by shane101 on 2005-04-26
Fixed up! Thanks for all the help guys, I found the problem, my proxy in FireFox was set up but for my normal LAN connection that connects to my proxy/gateway it wasn't so everytime I tried to apt-get it wasn't able to get out to the servers on the web.

Anyway my machine is running on both processors now and performance has definitely improved!   \\:D/ 

Thanks for the help

Cheers,
Shane101

---

### Post by aulin on 2005-04-27
Nice one.

Normally something simple :).

---

