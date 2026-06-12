---
title: "ATI GFX issues."
date: 2012-01-15
forum: Hardware
---

### Post by pingaan on 2012-01-15
When digging through some old boxes I found my Acer Travelmate 7520 and decided to make use of it, once again! 
I installed Ubuntu 11.10 and I had issues with both the wireless and the GFX card.
I've gotten the network sorted but I can't really figure out the GFX. I've installed the latest driver pack (11.12), after doing that the gui reacts better but I still can't run aticonfig in the terminal, it says that there's no present ati card and when checking system info the GFX spot is empty.
I'm sure I can get the laptop to run faster and smoother if I get the GFX card properly installed!

Any ideas?

Regarsa.

---

### Post by Mark Phelps on 2012-01-16
According to Google, that ACER has an ATI X1250 video chipset -- for which AMD/ATI stopped writing Linux drivers years ago.

The drivers available today are the open-source drivers -- which are installed by default.

---

### Post by pingaan on 2012-01-16
Correct, ATI Radeon X1250.. 
Been coming across many pages/forum threads about ATI/AMD giving up on the old GFX cards.
I found this [https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver) , is this something that I should follow blindly? I'm talking about "Problem: Need to fully remove -fglrx and reinstall -ati from scratch".
I tried doing it actually, I'm still far away from an advanced Debian user, so I might have failed at some point.
After installing this should everything about the GFX card sort itself out? I mean, identifying the card to begin with and choosing the right drivers for it? 
Maybe you know of some better guide than this one? 

Cheers for taking the time to answer..

---

### Post by pingaan on 2012-01-16
Just to try it out to see where it goes wrong I followed the guide again;
It all goes well up till the last step: sudo apt-get install fglrx-modaliases , I get the message 'E: Package 'fglrx-modaliases' has no installation candidate' and I don't really know if it's necessary or not.
Also when checking what's installed;
[COPIED FROM THE SOURCE]
[I]libgl1-mesa-dri                                 install 
libgl1-mesa-dri:i386 install 
libgl1-mesa-glx                                 install 
libgl1-mesa-glx:i386 install

[/I]It only shows the none i386 ones, is that an issue?

Regards.

---

### Post by Mark Phelps on 2012-01-17
That's the right page, but you should be following the instructions in the step below the one you read -- the one dealing with removing fglrx and reinstalling ATI from scratch.  That one should work.

---

### Post by pingaan on 2012-01-17
Deleted the post, an edited one is below.

---

### Post by pingaan on 2012-01-17
That is the one guide I've been following, please take a look at post no. 3 in this thread;

> **pingaan said:**
> Correct, ATI Radeon X1250.. 
Been coming across many pages/forum threads about ATI/AMD giving up on the old GFX cards.
I found this [https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver) , is this something that I should follow blindly? I'm talking about "Problem: Need to fully remove -fglrx and reinstall -ati from scratch".
I tried doing it actually, I'm still far away from an advanced Debian user, so I might have failed at some point.
After installing this should everything about the GFX card sort itself out? I mean, identifying the card to begin with and choosing the right drivers for it? 
Maybe you know of some better guide than this one? 

Cheers for taking the time to answer..

---

### Post by MoreOrLess on 2012-01-17
Once you have the Catalyst driver removed, you can try the xorg-edgers PPA: [https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

That has the latest (and probably best) drivers for your GPU.

---

### Post by pingaan on 2012-01-21
Correct me if I'm wrong but shouldn't the final line be "sudo apt-get install cairo"?
Doesn't work for me.. Added the PPA and did an apt-get update..

---

