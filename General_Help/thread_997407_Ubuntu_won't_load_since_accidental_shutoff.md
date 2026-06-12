---
title: "Ubuntu won't load since accidental shutoff"
date: 2008-11-29
forum: General Help
---

### Post by musicaly on 2008-11-29
Plz help,

Since my laptop accidentally got unplugged just after it booted up into Ubuntu, it hasn't been able to boot since.  I'm new to linux and I don't know what information someone would need in order to help my ordeal.  So, please respond so I can get this figured out.

Thanks.

---

### Post by steveydoteu on 2008-11-29
What actually happens when it "won't load".

What errors if any are you getting?

Have you tried using recovery mode?

---

### Post by musicaly on 2008-11-29
Well, it commences with the bootup.  I see the screen that has the progress bar and labeled ubuntu above it.  Then it goes to a black screen and has written the following:
```

 * Starting anac(h)ronistic cron anacron                      [OK]
 * Starting deferred execution scheduler adt                  [OK]
 * Starting periodic command scheduler crond                  [OK]
 * Enabling additional executable binary formats binfmt-support
                                                              [OK]
 * Checking battery state...                                  [OK]
 * Running local boot scripts (/etc/rc.local)                 [OK]

```
After this, my computer doesn't go any further into the boot.  I was able to login from this point by pressing alt+F1 and just using the terminal to navigate around.  Also, I checked /etc/rc.local, it is empty.

I did try to use the recovery mode, but only for the computer to not find anything wrong with the computer.

I hope that's what you need.

Thanks for replying.

---

### Post by bodhi.zazen on 2008-11-29
At that screen, try just hitting the enter key.

It sounds as if X has failed.

Boot to recovery mode and select the "xfix" option.

If that fails we need to know what video card it is (guessing Nvidia or ATI),

---

### Post by musicaly on 2008-11-30
From that screen I have tried pressing enter and typing other things.  Everything that I type is displayed to the screen, but nothing happens.

From the recovery mode, I have selected the xfix option.  It informs me that it succeeded, yet no change when it comes to the problem at hand.

My video card is: "ATI Radeon Xpress 1250 Hypermemory (Up to 896 MB)".

---

### Post by musicaly on 2008-12-29
Well, thanks for your attempts to help me.  Since I never got it solved, I just installed Ubuntu 8.10 and restored everything from scratch.  It was a pain, but I like version 8.10.  Too bad that it never got solved. oh well

---

### Post by physeetcosmo on 2009-01-19
> **bodhi.zazen said:**
> At that screen, try just hitting the enter key.

It sounds as if X has failed.

Boot to recovery mode and select the "xfix" option.

If that fails we need to know what video card it is (guessing Nvidia or ATI),

I had this issue as well after last night. I was uninstalling some packages and the system hung, so I forced shutoff. I rebooted into eeePC-kernel (recovery mode) but didn't select the X Server Fix option.

I'll try this and get back to you, thanks!:)

---

### Post by riteandritual on 2009-01-23
This is a stupid question - and believe me I've looked for the answer and only got myself confused - how do I boot into recovery mode? 

I have the Ubuntu Intrepid (live?) disk, and it doesn't give an option like that.

---

### Post by riteandritual on 2009-01-26
Well, I had this problem in Ubuntu 8.10, and I tried this to no avail. What worked for me - I don't know why but it did - was installing Sabayo linux, which booted fine, then installing ubuntu again. Weird, but it worked.

---

