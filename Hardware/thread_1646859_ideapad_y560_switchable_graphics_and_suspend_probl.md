---
title: "ideapad y560 switchable graphics and suspend problem"
date: 2010-12-16
forum: Hardware
---

### Post by thebinaryblob on 2010-12-16
So I've gotten myself a Lenovo Ideapad Y560 06465AU. It has a core i5 and an ATI Radeon Mobility HD 5730. It also supports switchable graphics; I, however, have disabled the Radeon as it reduces battery life from 4 hours to 1.5 hours. I disabled it using the timelinex_acpi module (I lost the link, its somewhere on the forums, but I have also attached it). Doing this unleashed a new issue. I cannot suspend or resume, or even hibernate the system when it is running on the intel gpu inside the cpu. I do not have these problems when the ati card is turned on but, as previously stated, this quadruples power consumption.

I have tried running the test on this page: [https://wiki.ubuntu.com/KernelTeam/SuspendResumeTesting](https://wiki.ubuntu.com/KernelTeam/SuspendResumeTesting), but the system freezes before it even suspends.

I have also tried the old uswsusp, but it just appears to freeze and then boots me back, leaving the system in a usable but non-suspended state.

I don't really have any experience dealing with these kinds of problems so any help or information would be incredibly useful, my Google searches haven't really given any good information yet.

---------------------

News:
So after a while I tried to fix another issue by compiling a kernel from the latest stable sources, this had the side-effect of curing my suspend problem. For anyone who googles this, I used these instructions [http://www.webupd8.org/2010/12/how-to-compile-kernel-in-ubuntu-easy.html]("http://www.webupd8.org/2010/12/how-to-compile-kernel-in-ubuntu-easy.html") .

---

### Post by shinepuppy on 2011-02-02
I have the same suspend problem with my y560 (core i7 though)

Wicked find with KernelCheck!! I'm playing with it now :) The only problem with that tutorial is there's no sound... or text/screencaps. Maybe I'll record one with voice.

thanks!

---

### Post by nikkbelov on 2011-02-26
Can you put here steb by step instruction for beginers?
I am owner of Lenovo Y560.
What i have to do with files you are attached.

---

### Post by Angelontu22 on 2011-03-04
Were you able to install the proprietary amd/ati fglrx drivers? 


I tried installing them doing the System > Administration > Additional Drivers method which appeared to install correctly once I click the "Active" button. By the time the system rebooted, I was presented with a black terminal screen asking for login information. Also tried installing them manually from the amd site. Again, appears to install but after restarting doing this method there is a black screen and all I hear is the sound from startup. I removed the drivers using recovery mode and currently using the default opensource. The fan seems to be running all time making the cpu a little hot. 


I just installed Ubuntu less than 24 hours prior to this post so please, bare with me. Any help would be very appreciated! 



Specs; 

Lenovo Ideapad Y560 
Intel core i5-450m
ATI Mobility Radeon HD 5730 / Intel HD switchable graphics
4GB RAM
Dual-booting Ubuntu 10.10 with Win 7 Home Premium 64-bit

---

### Post by ibalog on 2011-03-21
How did you even get the i5 graphics working? I could not 
even manage to do that! I believe that there exists a problem 
with the i5 graphics:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/590504](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/590504)

I tried to switch by using UCC but it did not work on my laptop -
after switching to i5 graphics Mobility Radeon 5730 remained 
working.

[http://www.omgubuntu.co.uk/2010/08/ubuntu-control-centre-0-5-brings-gpu-switching-to-linux/](http://www.omgubuntu.co.uk/2010/08/ubuntu-control-centre-0-5-brings-gpu-switching-to-linux/)

If anyone could give any insight I would be grateful.

---

### Post by infomissing123 on 2011-04-12
Alright, I own an ideapad y560p, model 4397.  I7 Sandy.  Not switchable graphics, just the ATI ones.  The suspend/resume has mostly been working but crashes on resume every once in a while.  No meaningful errors other than PM: resume failed.  

I guess I don't really have a question other than why is this thread marked as "SOLVED"?

---

