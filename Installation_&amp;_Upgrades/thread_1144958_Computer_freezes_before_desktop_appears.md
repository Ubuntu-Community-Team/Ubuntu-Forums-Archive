---
title: "Computer freezes before desktop appears"
date: 2009-05-01
forum: Installation &amp; Upgrades
---

### Post by mafaldaspeaks on 2009-05-01
My desktop just finished installing and asked to be restarted. I did so and it went through the usual initial stages until just before the desktop screen appeared--I mean, the screen froze with all these horizontal bar lines. Nothing's working.

So I did a forced shutdown and then restarted. At the grub loading, i clicked ESC and chose the recovery mode. It went on to say that errors were corrected, restarted by itself, and then exactly the same thing happened: the screen froze with all these horizontal bar lines. Nothing's working.

Please help. This is my family's computer so I'm going to delay their work if i don't get to fix this today.

---

### Post by zeex on 2009-05-01
> **mafaldaspeaks said:**
> My desktop just finished installing and asked to be restarted. I did so and it went through the usual initial stages until just before the desktop screen appeared--I mean, the screen froze with all these horizontal bar lines. Nothing's working.

So I did a forced shutdown and then restarted. At the grub loading, i clicked ESC and chose the recovery mode. It went on to say that errors were corrected, restarted by itself, and then exactly the same thing happened: the screen froze with all these horizontal bar lines. Nothing's working.

Please help. This is my family's computer so I'm going to delay their work if i don't get to fix this today.

Hi, 

I'm guessing you installed ubuntu 9.04. It has a log of bugs. If you'll give more info about what you were doin' / installed before this it'd be helpful. 

If your work is critical. spend half an hour and install 8.04 or 8.10. It'll take less time than getting the bug fixed by asking on forum, waiting for an answer and then trying it.

---

### Post by mafaldaspeaks on 2009-05-01
> **zeex said:**
> Hi, 

I'm guessing you installed ubuntu 9.04. It has a log of bugs. If you'll give more info about what you were doin' / installed before this it'd be helpful. 

If your work is critical. spend half an hour and install 8.04 or 8.10. It'll take less time than getting the bug fixed by asking on forum, waiting for an answer and then trying it.

Yes, I upgraded from 8.10 to 9.04. As it instructed under documentation, I used the update manager to install all the updates for 8.04 then clicked on the update to the new distribution release. It went through all the steps until the part when it asked for the computer to be restarted. I restarted and as I've tried to explain, the whole computer freezes even before the desktop screen is launched so i can't use anything.

---

### Post by mafaldaspeaks on 2009-05-01
Ok, so I put the CD installer of 8.04.1 from Canonical and still the same thing--the computer reaches exactly that same point and freezes. The cd drive sounds as if it's starting to run, but nothing really happens. Oh my, and I've been "promoting" this upgrade to my family.

---

### Post by mafaldaspeaks on 2009-05-03
Good news. After the nightmare of spending a whole day upgrading my family's desktop from 8.10 to 9.04 and having to see the display freeze without any response at all, I tried rebooting on a live CD (I originally had 8.04 only and then was able to download 9.04 on the laptop) as user ZEEX very helpfully suggested to me.

First I went to BIOS so as to change the boot settings, making the CD drive the first one. Then I simply restarted with the live CD inside the drive and jaunty installed as smooth as anything--and finished within one hour! It's working quite well now.

Thanks to zeex and emarkay for all the help!

---

