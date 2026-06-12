---
title: "HP Pavillion dv6000 serious boot issues"
date: 2008-10-28
forum: Hardware
---

### Post by foilboy on 2008-10-28
Hey all, I was wondering if anyone here had any ideas on how to solve my laptop issues.  I've had my dv6000 for a little over a year now (i.e. the warrenty expired a few months ago), and two weeks ago I started having some serious issues.  

Ever since updating the kernel and wireless drivers that came out 2 weeks ago, my laptop has had some serious problems turning on.  I hit the power button, some of the keyboard lights come on, I hear fans/HD spinning, but the screen stays black.  It stays like that for about 30 seconds, beeps faintly, and I hear the fans go off and the lights go out.  Then tries again: fan whirring, lights on, black screen.  It never gets to the BIOS splash screen.  It does this a random number of times before actually turning on, between 0 (boots up right away), and way too many to count (it took over an hour yesterday for it to come on).

This is what happened 2 weeks ago when the problem first started:
Everything was working normally up until then.  Update manager informed me that morning that there were new updates available, so I glanced at them and downloaded/installed them.  One of them was a new kernel update, so it needed to restart, but I didn't right away - I just turned the laptop off about an hour later to bring to class.  When I got to class, it turned on fine initally, and I was informed there were new wireless drivers available.  I turned them on, and was prompted to restart.  I did, and that's when I first started to not boot right away.  So I'm not sure if it was the wireless driver exactly, or the kernel update, and I just got lucky turning it on that first time.

I had been dual booting XPsp3 and Hardy 8.04, but yesterday after the nail-biting hour I spent trying to get this dumb thing to turn on, I backed everything up and formatted everything, going back to XP (what I'm posting from now).  It did **not** solve the issue, neither did these other things I've tried:

Reseat RAM
Try all possible configurations of RAM (2x1GB sticks)
Boot without HD
Boot with friend's HD plugged in
Boot without CDROM drive
Booth without wireless card
Reflash BIOS to latest version (was already at latest before hand)
Reset all BIOS settings to default and playing with them
Boot on AC power with/without battery
Boot on just battery
Boot with ethernet cable plugged in/not plugged in.
Ran smartmontools, a HD integrity checker (no errors found)
Ran memtest86+ through one complete cycle of tests (no errors found)

The only option along those lines that I can think of but haven't yet tried is with a completely different set of RAM sticks, because I don't have any handy.  I know someone with the same laptop as mine though, so I could probably get hers temporarily if you guys think it's worthwhile.

Other than that, though, I'm out of ideas.  I feel like it has to be either some sort of hardware issue, or a BIOS issue, but I reflashed the BIOS and it didn't help.  And it started after updating the kernel, though it may just be some weird coincidence.

Does anyone else have ideas to try?  Currently Ubuntu isn't installed, but I can try putting it back on to run other diagnostic tests I can't get to under Windows.

---

### Post by foilboy on 2008-10-29
I spoke with an HP rep today and even though the laptop is no longer under warranty, they're going to fix it free.  I don't know why, but I'm not complaining!

---

### Post by teaker1s on 2008-10-30
yes me too, it's graphics/motherboard/wireless failure- known issue fixed free once

---

### Post by Kobalt on 2008-10-30
I can confirm : common and known issue on the dv6000 series ... Mine broke 3 months after buying, wireless/graphics card out. It came back from repair a while ago but the wireless died again. I've given up on this laptop as far as I'm concerned.

---

### Post by sergiom99 on 2008-10-30
could you guys post your system's specs, just to know which DV6000 series are defective and maybe enforce my warranty claims if there's need.
Thanks!

---

### Post by Kobalt on 2008-10-30
Mine is a dv6120eu precisely.

---

### Post by sergiom99 on 2008-10-30
> **Kobalt said:**
> Mine is a dv6120eu precisely.

AMD/Intel? Nvidia? 
please post more hardware details.

Thanks a lot!

---

### Post by Kobalt on 2008-10-30
AMD cpu, Nvidia chipset, Broadcom 94311 wireless.

---

### Post by putnam on 2008-11-07
I have the same laptop, mine started doing that to, but after trying to install ubuntu. It does the same as in ur description, and shutsoff, retries etc.  I just shut it off (holding power key for 5 seconds) and unplugged it, waited 5 minutes, and then it worked fine after it asked if i wanted to use startup repair.


about 5 months ago, my vista totally crashed, the update to SP1 is defective for HP dv6000's precisely, and my warranty had expired 3 fricken days before... I called the dude and he told me they couldnt do sumthing cus it mustve been a hardware issue and it was my fault after it forced me to install a defective SP. I called again, diff guy and he sent me a new vista CD and told me to tell no1 he did this. lol

---

