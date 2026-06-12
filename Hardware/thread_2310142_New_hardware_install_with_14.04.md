---
title: "New hardware install with 14.04"
date: 2016-01-16
forum: Hardware
---

### Post by pmjs1115 on 2016-01-16
I have a new HP notebook [ something like ab100]. Wired Ethernet is OK. Wireless is not; an Intel chip 3165; apparently not supported until kernel 4.1. There is no sound; it uses an Intel chip 9d70. lspci reports "Capabilities: <access denied>", but it reports that for many chips. Sound controls show in the Sound Properties, but test produces nothing.

I would appreciate some clues on how to solve this problem.

Paul

---

### Post by weatherman2 on 2016-01-16
I built the latest iwlwifi driver for Ubuntu 12.04 from backports when I upgraded my wireless card to an Intel 7260.  Backports give you newer drivers for older Ubuntu releases.

Something like this:

[http://askubuntu.com/questions/331667/no-wireless-for-intel-corporation-7260-version-63](http://askubuntu.com/questions/331667/no-wireless-for-intel-corporation-7260-version-63)

(Follow the instructions in the first answer - involves a few terminal commands.  You'll want to be plugged in temporarily with ethernet while doing this.)

but you might want to look for a newer backports version than that - probably this one:

[https://www.kernel.org/pub/linux/kernel/projects/backports/stable/v4.3/backports-4.3-1.tar.gz](https://www.kernel.org/pub/linux/kernel/projects/backports/stable/v4.3/backports-4.3-1.tar.gz)

You might also have an issue with the firmware even after doing that.  Give that a try first, though.

---

### Post by weatherman2 on 2016-01-16
Maybe there's a way to build a driver for the sound card, too - not sure if there is one in the backports.  You might also go ahead and just build the 4.1 kernel outright.

---

### Post by mörgæs on 2016-01-17
> **pmjs1115 said:**
> apparently not supported until kernel 4.1.

Then doing a fresh install (no upgrades) of 15.10 is your best option.

---

### Post by tokyobadger on 2016-01-17
> **mörgæs said:**
> Then doing a fresh install (no upgrades) of 15.10 is your best option.
Genuine question:14.04 + HWE to 15.10's 4.2.x kernel not an option? OP keeps LTS and gets updated hardware support in kernel, no reinstall required.
[URL="https://wiki.ubuntu.com/Kernel/LTSEnablementStack"]
**Trusty**

 The  14.04.2 and newer point release will ship with an updated kernel and X  stack by default. If you have installed with older media you can use the  following to install the newer kernel from 15.04 (Vivid): 
 
**Desktop**

  sudo apt-get install --install-recommends linux-generic-lts-vivid xserver-xorg-core-lts-vivid xserver-xorg-lts-vivid xserver-xorg-video-all-lts-vivid xserver-xorg-input-all-lts-vivid libwayland-egl1-mesa-lts-vivid [/URL]
Replacing vivid (15.04 / 3.19 kernel) with wily of course

---

### Post by mörgæs on 2016-01-17
The hardware enablement stack is an attempt at making 14.04 behave 15.10-ish which I think is a pointless exercise since we have the real thing (the 15.10 ISO) available and since a reinstall only takes twenty minutes. 

How many new packages should be backported from 15.10 to solve a given series of problems? We don't know. Has '14.04 + something' enough backports? We don't know that either. Therefore, the least troublesome approach is using all packages new, that is a standard 15.10.

Well, let's hear from original poster what works best.

---

### Post by pmjs1115 on 2016-01-17
Posting from 15.10 liveCD. There is sound and wireless connects. Thanks for all your answers. 15.10 install must be the answer. I will repost if it is not.

Paul

---

### Post by mörgæs on 2016-01-17
Good, if the install works as the live boot then please mark the thread solved (and spread the word: New software for new hardware).

---

### Post by maxinstuff2 on 2016-01-18
And remember you can jump on to the 16.04 LTS release when it drops in a few months - if you don't like the idea of being on a shorter term release.

---

