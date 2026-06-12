---
title: "sound not working on new Ryzen install - odd pattern forming"
date: 2017-06-21
forum: Hardware
---

### Post by bartt2 on 2017-06-21
Just built a new Ryzen system. Using Ubuntu 17.04 for a host OS (with many virtual machines running on top). Everything works nicely except for the sound (Realtek ALC892 built in on the MB). 
I have update the kernel 3 times and each time on the first boot the sound works. If I run the alsa-info script it shows that it found the sound system and loaded the drivers.
On subsequent boots/restarts the sound system is not found, no drivers are loaded and alsa won't behave. 
I have loaded kernels 4.10, 4.11.3 and 4.11.6. In each case the newly started kernel finds the sound system and uses it. And in each case rebooting the system into the same kernel yeilds no sound.

So, the question I have is what is different between a new kernel install/startup and subsequent loading of the kernel?

TIA 
bart

---

### Post by QIII on 2017-06-21
Virtually all boards that accept the Ryzen are displaying this behavior with the current mainline kernels prior to 4.11.  Obviously, there are still some problems with some systems even still.  That's why I held off on doing a build.

---

### Post by bartt2 on 2017-06-21
Hmmm..
That's some good info. Since misery loves company.
But I still wonder what happens to the sound system information that is discovered when the new kernel is installed vs. when the system boots for the second time. There has to be some difference.

---

### Post by gsahli on 2017-06-22
I don't have 17.04...
Have you tried pulseaudio volume control (pavucontrol)? It gives you GUI displays of which output is working.

---

### Post by bartt2 on 2017-06-22
Thanks for the reply..
Yes, pulse audio controller shows the correct info and works on the first startup of a new kernel, but shows dummy output on subsequent boots.
I've done some research in the weeks that I have been experimenting. I think I have narrowed it down to alsa not loading the drivers (or something else not discovering the sound system) after the first boot.
The pattern that I pointed out above could perhaps be a clue for those that know more than I. 
I'd still like to know how first startup and later startups differ in hardware discovery and dirver loading.

---

### Post by bartt2 on 2017-06-25
Just installed the 4.11.7 kernel last night. 
On restart I had sound for exactly one session. After the second and subsequent restart I have no sound. So the pattern is holding
There has to be some discovery mechanism that is getting confused. 
What is different from the first restart to the second? 
More-over, what can I do to cause a complete hardware discovery and perhaps get sound back?
TIA..

---

