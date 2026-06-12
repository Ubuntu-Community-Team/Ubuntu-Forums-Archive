---
title: "Dell XPS L502X - Battery drain and heating"
date: 2014-07-17
forum: Hardware
---

### Post by sanjay4 on 2014-07-17
I own a Dell XPS L502X and i don't observe any issue (over-heat or quick-drain of battery) if booted under "Windows  7". When booted under Ubuntu 14.04(Dual boot with  Windows), the laptop gets heated up and battery drains up quickly. This is my first installation of Ubuntu and hence i might have missed to installed any other required application . Please help me on resolving this  issue
 

Processor Intel(R) Core(TM) i5-2450M CPU@2.50GHz

Thanks.

---

### Post by Mark Phelps on 2014-07-17
Sorry, but Windows generally does better processor management, and thus lower battery use.

What you can try is the following using tlp:

> sudo add-apt-repository ppa:linrunner/tlp
sudo apt-get update
sudo apt-get install tlp tlp-rdw

> sudo tlp start

---

### Post by Yellow Pasque on 2014-07-17
I really doubt the CPU is the major problem in this case. This is an Optimus system, so it is probably the nvidia GPU that's sucking the battery and generating heat.

On older versions of Ubuntu, the solution would be to install bumblebee to power off the nvidia GPU when it's not in use. On Ubuntu 14.04, there's nvidia-prime to deal with, so maybe that's set to use the nvidia GPU for everything (I think you can change it in the nvidia control panel).

---

### Post by sanjay4 on 2014-07-18
Thanks. Generation of excessive heat is reduced after installation and configuration of "nvidia-prime" (Changing to Intel power saving mode) . The rapid discharge of battery is also reduced but still it doesnt last long. Is there any other application that needs to be installed for power savings.

---

