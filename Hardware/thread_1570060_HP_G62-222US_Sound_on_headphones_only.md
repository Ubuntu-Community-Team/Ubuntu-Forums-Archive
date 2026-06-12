---
title: "HP G62-222US Sound on headphones only"
date: 2010-09-07
forum: Hardware
---

### Post by DrJohn999 on 2010-09-07
Installed 10.04 Netbook Remix, but sound only on headphones; alsamixer shows only master and pcm, no mics, speakers, or anything else

Enabled backports in Synaptic Package Manager then ran:
```
~$ sudo aptitude update
~$ sudo aptitude install linux-backports-modules-alsa-lucid-generic
```
After reboot sound plays through speakers and phones, and internal mic is working too. 

No other problems except that the fn keys are not active for volume, brightness, etc. Did not test HDMI audio out.

---

### Post by cdkayak on 2010-12-01
Thanks, that was  big help.  I was working with an alsa update script in another thread and this worked out much cleaner.

CD

---

### Post by bilkay on 2011-01-28
I installed the package some time ago and it worked fine! (Thanks, by the way) But apparently, the last upgrade broke it and I'm back to where I was - no speaker, no mic.

I tried reinstalling it and got the following:

```
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  linux-backports-modules-alsa-lucid-generic: Depends: linux-backports-modules-alsa-2.6.32-28-generic but it is not installable
E: Broken packages
```

---

### Post by bilkay on 2011-01-29
Fortunately, I was able to restore the system to prior to the update. Interestingly, when I run Update Manager now, it lists an update for linux-backports-modules-alsa-lucid-generic, but it is unchecked and can't be checked for installation.

---

### Post by bilkay on 2011-01-29
The sound goes away when booted into the latest 2.6.32-28 kernel. It works when booted into 2.6.32-27.

---

### Post by dantheperson on 2011-01-29
The latest kernel upgrade in lucid is broken, they haven't built the alsa module so stay on -27 if you want sound.

---

### Post by bilkay on 2011-02-02
I see that update manager now has two new updates for alsa. I'd sure like to know if it's safe to install them.

---

### Post by dantheperson on 2011-02-02
> **bilkay said:**
> I see that update manager now has two new updates for alsa. I'd sure like to know if it's safe to install them.

I've installed them and rebooted to the new -28 ABI kernel and sound is all good.

---

### Post by bilkay on 2011-02-02
> **dantheperson said:**
> I've installed them and rebooted to the new -28 ABI kernel and sound is all good.
You're braver than I.

 I'm giving it a shot - after doing a full back-up.

---

### Post by dantheperson on 2011-02-02
> **bilkay said:**
> You're braver than I.

 I'm giving it a shot - after doing a full back-up.

I don't see why you're so hesitant... you can always boot back using the old -27 kernel from the grub menu.

I think boot menu doesn't display on a default install..
edit /etc/default/grub and a # to this line 

#GRUB_HIDDEN_TIMEOUT=0

then run sudo update-grub

then when the PC boots you'll have 2 secs to choose which kernel to boot.

---

### Post by piymon on 2011-02-07
thanks for everything guys. this thread was real helpful to me

---

### Post by Walpy on 2011-02-28
> **DrJohn999 said:**
> Installed 10.04 Netbook Remix, but sound only on headphones; alsamixer shows only master and pcm, no mics, speakers, or anything else

Enabled backports in Synaptic Package Manager then ran:
```
~$ sudo aptitude update
~$ sudo aptitude install linux-backports-modules-alsa-lucid-generic
```After reboot sound plays through speakers and phones, and internal mic is working too. 

No other problems except that the fn keys are not active for volume, brightness, etc. Did not test HDMI audio out.

Thanks DrJohn999 !

I installed Ubuntu 10.04 LTS on my HP G62 (don't know what exact model) and had the same problem and now it is working fine! :)

Everything is working like it should.

---

