---
title: "wont boot"
date: 2010-04-14
forum: Hardware
---

### Post by slgtheindividual on 2010-04-14
I'm dual booting ubuntu and windows 7, booted ubuntu lots of times before it worked fine, for some reason it wont boot today, it says something like 'vga=799 has deprecated' I cant quite catch it, it flashes on then the screen goes blank and wont load, any help would be useful =]

---

### Post by quixote on 2010-04-15
This sounds like somehow the graphics driver or xorg's details for it have become corrupted.

What computer do you have?  What graphics card?  Which version of Ubuntu are you running?  And do you use the old grub or grub2?

---

### Post by slgtheindividual on 2010-04-21
I'm running ubuntu 9.1 with AMD Athlon X2 Dual-Core QL-64 grub 2 on a packard bell laptop (no idea what model), ATI radeon graphics card? 

sorry for the late reply

---

### Post by quixote on 2010-04-22
I'm not much of an expert on configuring xorg and graphics cards, but somewhere on the forums is going to be a thread with the answer to your question.  Search for "ATI Radeon *Model#* 9.10 64-bit Packard Bell" (without quotes) and see what comes up.

There's also a help page: [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

Check that first because there may be the actual answer out there.  The steps to try to fix a broken system are:

Have an ethernet cable attached before you start.  Boot into recovery mode at the grub menu on bootup.  Select "root with network access" option.

Once you're at the # prompt: ```

dpkg --configure -a
apt-get -f install     [alternatively, you can use aptitude -f install]
apt-get update       [alternatively, you can use aptitude update]
```(A lot of people I respect prefer the "aptitude" variant of "apt-get")

The following is the command to get xorg behaving again in a wide variety of situations.  I don't think it hurts anything in any case, so you can run that after you fix broken packages.  As I say, read up on the help page and forums first.
```
dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by duke.tim on 2010-04-22
This may be redundant but do you get to the boot screen (grub or windows bootloader)?

---

