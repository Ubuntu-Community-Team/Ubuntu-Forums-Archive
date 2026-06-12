---
title: "Delayed graphic card activation at startup"
date: 2019-11-16
forum: Hardware
---

### Post by Clueless Wonder on 2019-11-16
I apologize for the bizarre title...couldn't think of a different way to state the problem.

I installed Lubuntu 18.04 on a Dell XPS Studio.  Startup worked fine...saw the Dell splash screen, then the GRUB menu (it's a dual boot with Windows 10).  I then installed a Radeon x300se graphics card so I could use two monitors.  Everything appears to be great except there is a delay in the graphics card being activated.  Here is what happens....I start the PC, monitor is in Power Save mode....and stays there until about the time the GRUB menu loads.  I am thinking the integrated card might be active until then.  I have used both this card and a NVIDIA card (that has the same issue in another PC) with Lubuntu 16.04 and it didn't have this problem. 

I would be grateful for any thoughts and/or suggestions.

---

### Post by mörgæs on 2019-11-18
Now I have read your post several times and I still don't understand what the problem is. Could you elaborate, please?

---

### Post by Clueless Wonder on 2019-11-18
Hi Morgaes - thanks so much for replying and asking.

I will be more specific...and please ask more questions if it still isn't making sense.

When I turn on the PC with the monitor plugged into the integrated graphic card, the monitor wakes up right away and shows the (in this instance) Dell splash screen, which allows me to choose whether I want to enter set-up, boot sequence, etc.  What I am dealing with right now is...when I plug the monitors into the dedicated graphic card, the monitor takes a bit before it wakes up (in other words...the power light is blinking as if in sleep mode before "waking up" and being a solid green).  By the time it "wakes up", the PC has already gone through the time where the Dell splash screen happens and it is well into the Grub menu.  I am wanting the monitor to wake-up right away, like when it is plugged into the integrated graphic card.  This works great for me on my PC that has 16.04 on it.  Is there a setting I need to change?  Or something else?

Does this help explain the issue better?

---

### Post by CatKiller on 2019-11-18
The period that you're talking about has no operating system handling displays, it's all down to the BIOS/UEFI of the motherboard. If the motherboard is capable of having its display on a dedicated graphics card (some are so tightly integrated as a package with the cpu that they aren't) then it will be an option in the BIOS to specify the primary display. Nothing else is running at that point to be able to do it.

---

### Post by Clueless Wonder on 2019-11-19
Hi Catkiller -

that is similar to what the folks at Nvidia told me about the same issue I was having with one of their cards in a Optiplex 790.  Then, I put the Radeon in that PC and am now getting the splash screen.

I am confused because I would think I would have had the same issue with the Optiplex 790 and the Radeon card if it was a PC issue.

---

### Post by jdcosta283 on 2019-11-20
The problem is not matter for graphic card activation, it is required minimum system for Lubuntu [facebook]("https://www.facebook.com/"). For that system will be minimum required Pentium core-ll or celeron cpu.

---

### Post by Clueless Wonder on 2019-11-24
Not sure what solved it, but the computer isn't having this problem anymore.  I will close it as solved.

---

