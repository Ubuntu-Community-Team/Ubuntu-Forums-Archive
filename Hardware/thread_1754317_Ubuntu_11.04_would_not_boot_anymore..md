---
title: "Ubuntu 11.04 would not boot anymore."
date: 2011-05-09
forum: Hardware
---

### Post by linikz on 2011-05-09
HELP!!! Ubuntu 11.04 64-bit would not boot in my HP G42 laptop anymore. 

I just recently upgraded my OS, from 10.10 64-bit to Natty. It was working fine for about a week; not perfect, but I was definitely enjoying Unity especially the dash.

Last night I noticed that my HP's wifi key was orange lit even though I was connected to the Internet. So I tried to press it repeatedly to see if the light would turn blue. Then suddenly, my screen had blue and white stripes all over it. I had no choice but to hard reboot it.

However, after the splash screen, the screen would just stay blank. No cursor or anything. Just plain blank. It would stay that way forever. I tried hard rebooting it again, and after a few tries I was given the option to repair the system. I couldn't remember all the options, but I thought it would fix the problem. But it did not!

I tried to boot through 11.04 64-bit LiveCD, but it gives me the same result! I tried a 32-bit version, but nothing has changed!!!

And then I tried to pop in my Fedora 14 32-bit LiveCD. It worked!

From countless forums, I got the idea that the problem might be my graphics card/its driver. I tried some of the solutions suggested by some users but none has worked. I don't know what to do! I don't really have important files in my HD. I can just easily install Fedora 14 in my HD and then install Ubuntu again.

But...I want to try to solve this thing. I do want to be a Linux power user someday. I figured this can be a good learning experience for me. I do need your help tho guyyys! Right now I'm using the Fedora 14 32-bit LiveCD with a wired network. I want my Natty back!!!

Please help me guys! I would really appreciate it! :D

P.S. I'm thinking of burning a 10.10 64-bit and/or 32-bit LiveCD and see if it's going to work.

---

### Post by kris07 on 2011-05-10
I'm currently experiencing this same issue.

---

### Post by linikz on 2011-05-23
> **kris07 said:**
> I'm currently experiencing this same issue.
  Have you fixed it yet? More than a week ago I tried to boot 11.04 again while pressing Shift repeatedly. It suddenly worked for some odd reason! I was expecting to see a grub option or something by pressing shift but I was just taken to the login screen. And then when I logged in, a dialog box appeared saying that I don't have the right hardware for Unity. I edited the grub file and added "nomodest" (yes, I mispelled it) and then rebooted and it still worked. I just realized that I should have put "nomodeset" instead a few days ago. Lol. It's working fine now but still, not perfectly.

---

### Post by Rasa1111 on 2011-05-23
I also recently had a little problem after performing a hard reboot..
and after the grub screen would load and id hit enter... it would go all purple then to a black shell screen with blinking cursor. 

Nothing I did would make it work..
Then someone suggested I simply power it down, unplug it from it's power source, and retry, and to my amazement.. it worked! 

I only removed its power supply (in this case, it's battery) for 30-60 seconds,
and when i popped it back in and turned it on.. everything was back to normal. Couldn't believe it.  lol

Glad you got it worked out

---

