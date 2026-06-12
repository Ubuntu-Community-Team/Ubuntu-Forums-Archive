---
title: "Disabling integrated on a laptop"
date: 2010-12-29
forum: Hardware
---

### Post by Townley89 on 2010-12-29
Hey guys,

I've got a new Asus U30J laptop with an Nvidia graphics card. When I install the OS it works fine, but when I enable the Nvidia driver, the computer asks to restart to complete the update and then doesn't boot back up (gets stuck on "checking battery state: ok") When I rerun ubuntu in low graphics mode and switch the nvidia driver off, it fixes the problem and I can boot up, but then I'm not using the nvidia card, and not getting the most out of the comp. 

I've been told this might be due to a conflict between my onboard graphics and the nvidia. I'd like to disable the onboard, since I'd like to use the nvidia because its better, but my BIOS does not have an option to do so. Alternatively, if there would somehow be a way to run both for different displays, that would suit my purposes fine. 

Any suggestions on this would be most appreciated!

---

### Post by thinkingtubelite on 2011-01-24
Hey
I have the same/ similar problem. Any solution?

---

### Post by cascade9 on 2011-01-25
> **Townley89 said:**
> I've been told this might be due to a conflict between my onboard graphics and the nvidia. I'd like to disable the onboard, since I'd like to use the nvidia because its better, but my BIOS does not have an option to do so. 

At the moment if there is no BIOS switch to force the nVidia GPU (or to disable the intel video chip) then you have no way to get the nVidia GPU going at all. Sorry. Blame nVidia for not making optimus drivers for linux....

---

### Post by Townley89 on 2011-04-10
Hey, sorting through old threads. Never did find an ubuntu fix for this. However, the problem isn't a problem in Mint (enabling nVidia driver seems to work swimmingly.) So if you're desperate to get something more than your onboard graphics, I guess there's always that option.

---

### Post by beew on 2011-04-10
> **Townley89 said:**
> Hey, sorting through old threads. Never did find an ubuntu fix for this. However, the problem isn't a problem in Mint (enabling nVidia driver seems to work swimmingly.) So if you're desperate to get something more than your onboard graphics, I guess there's always that option.


Are you sure? Your laptop is Optimus enabled there is just no way for the Nvidia card to work in Linux unless there is a switch in the BIOS to choose the discrete card. For one model of ASUS there is a some hack to do that (can find it in the Forum) but it is not your model and it would involve a lot of work so I doubt it very much that it would work in MINT without any heavy duty hacking (if possible at all)

I think you'd  better double check that you are actually using the Nvidia card.

---

