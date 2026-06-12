---
title: "On Touchpad Upgrade &quot;touchpad&quot; tab missing in settings"
date: 2010-11-02
forum: Hardware
---

### Post by crisco552 on 2010-11-02
So a few days ago my Laptop's battery died and I called dell to get a new one. Well, not only was the battery and AC adapter replaced but my touchpad as well. I had my touchpad working how I wanted it to, I could use the right edge to scroll vertically, the bottom edge to scroll horizontally, and there was no tap to click. Well, after the upgrade both of the scrolling was disabled and now it clicks whenever I tap. however, I can no longer change it, I go to System > Preferences > Mouse and there is no "Touchpad" option, I've looked through and the only thing that seems to help is filing a bug report, however I would like to check here before I bug the developers about something like that. 
I am using an Inspiron 1545 by Dell, it has a 2.20 GHz Intel Core 2 Duo processor. and 4GB or RAM (However since I am using Ubuntu 10.04 32bit it only recognizes 3.4GB)

uname -a outputs:
```
Linux [My User Name]-laptop 2.6.32-25-generic #45-Ubuntu SMP Sat Oct 16 19:48:22 UTC 2010 i686 GNU/Linux

```any help would be appreciated.

I've tried installing gsynaptics and modifying the SHMConfig file as well... nothing seems to work

---

### Post by Weidbrewer on 2010-12-03
I have the same laptop with the same issue.  I have tried installing xserver-xorg-input-synaptics, but don't know how to open it, much less use it.  Also, gpointing devices doesn't give me any options for touchpad.  Also, running 10.04 on this system.  Any help would be greatly appreciated.

---

### Post by gpgp on 2010-12-20
I have 2 dell 1545s. Only 1 of them is having this problem. The one that has the problem is a fresh install of 10.04 from cd. I am trying to remember but i think the other was upgraded from 9.10. I am going to try a fresh install of 9.04 or 9.10 on this machine, then upgrade. post back with results. 

gpgp

---

### Post by gpgp on 2010-12-26
I have not tried this solution but it appears to be a known kernel bug.

See [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/554050](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/554050)
it seems to say if you use the kernel here [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33/) it will solve the problem. i have a fresh install and nothing to lose so i will try this tonight or tomorrow and post back.

gpgp

---

### Post by Weidbrewer on 2010-12-28
Any luck?

---

### Post by crisco552 on 2010-12-31
hmm weird, I was pretty sure it was a kernel bug, but according to uname -a I have 

```
Linux Laptop 2.6.35-24-generic #42-Ubuntu SMP Thu Dec 2 01:41:57 UTC 2010 i686 GNU/Linux
```

---

