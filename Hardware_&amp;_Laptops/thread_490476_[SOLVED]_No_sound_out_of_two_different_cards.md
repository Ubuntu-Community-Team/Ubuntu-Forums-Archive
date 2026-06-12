---
title: "[SOLVED] No sound out of two different cards"
date: 2007-07-02
forum: Hardware &amp; Laptops
---

### Post by azraelck on 2007-07-02
I just installed Feisty Fawn last night, and this morning got to trying to get my sound to work. Back when I had winXP, my on-board intel chip worked fine. However, I installed openSuSE; and nothing would work. I switched to Ubuntu because of the hassle and headache of openSuSE not working. While Ubuntu has been far better, I still do not have sound whatsoever. I have two sound cards, both the Intel integrated and a old SB Live! 24bit I had in another computer. Again, both worked fine under windows xp, so I know they are not messed up. ALSA does not work, nor does the OSS drivers. 

This is the most aggravating thing I've come across thus far since going to Linux. At least Ubuntu wasn't as bad as openSuSE though. It took two weeks and 4 installs to get my video card working. Thank you for your time.

---

### Post by avik on 2007-07-02
This one worked for me in Edgy (I had sound in Feisty without any workarounds required): [https://help.ubuntu.com/community/HdaIntelSoundHowto]("https://help.ubuntu.com/community/HdaIntelSoundHowto").  Give it a shot.

---

### Post by azraelck on 2007-07-02
*sigh* Didn't work. Apparently, even though I'm looking straight at them, the downloaded files for ALSA don't exist. They're a myth while at the command line. Might as well be a myth anyway; since I already have ALSA installed and it doesn't work. I'm beginning to think working sound in any Linux distro is impossible without sacrificing a goat. 5 months of trying with openSuSE failed to get anything more than errors and the occasional re-install; and two days with Ubuntu has me just short of that.

---

### Post by azraelck on 2007-07-02
Is there any other drivers available for Linux, outside of ALSA or OSS? Or is that it?

---

### Post by azraelck on 2007-07-03
Ok, digging further I have Ubuntu saying I have a nVidia sound card. Which is odd because nVidia has no drivers, support, or any mention of sound cards or chips on their website. So I think the problem is ALSA is not able to figure out what my card is. That, or it's the product of a thousand monkeys at a thousand computers. Much like Windows. 

I have PC Speaker, which surprised me (I didn't even know new computers still had an integral speaker), so Ubuntu is working correctly as far as sound goes. The volume controls on my keyboard even work. Just ALSA does not.  

Now, if it's just ALSA not able to properly detect my card; I have two questions. How do I manually set what my sound card is? Also, my Soundblaster is a SB Live! 24 bit, but it's detecting it as a Audigy LS. I can't tell if it's trying to use that card or not, nor do I know if that is how the ALSA driver reads the old Live! 24bit card or not. 

Thank you for your time.

---

### Post by azraelck on 2007-07-03
I shut down the nVidia/Intel whatever the bloody heck it is integrated POS, so now I'm on the SB Live... which doesn't work either. It still says I have an Audigy, which I do not. There is literally nothing I can find to do to change anything, like what sound card I actually have instead of what ALSA thinks I have. 

Is there no setup tool for this thing?

---

### Post by azraelck on 2007-07-03
Man, this is a busy forum... 4th page in only 10 hours.

---

### Post by azraelck on 2007-07-03
Ok, apparently I was wrong. It is showing my SB Live! 24 bit, as the OEM product in the PCI tab. It's showing the SB Audigy LS as the product in the same tab. Which makes no sense, but then if it did I wouldn't be making repeated failed attempts to find some help in resolving this issue. 

So then ALSA simply does not work. So I go back to the question of if there is a working Linux sound driver or not. Or, another forum for either general Linux help or another Ubuntu-specific forum so I can see if anyone there knows anything. Thank you.

---

### Post by azraelck on 2007-07-03
I got it working, finally. I'll probably be back when something else doesn't work, but thanks for the help.

---

### Post by avik on 2007-07-04
Wow, that's great that you got it working!  What was the problem and what was the fix?

Sorry I couldn't be of more help, but looking at your posts... wow!

---

