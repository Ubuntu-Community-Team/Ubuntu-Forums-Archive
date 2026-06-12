---
title: "Black screen after changing from Intel to Nvidia"
date: 2015-05-28
forum: Hardware
---

### Post by nigro.orlando on 2015-05-28
Hi!
This is probably a well documented issue on the forum but I couldn't find anything right for my case (maybe I haven't searched well).
I have had problem with Kubuntu 14.10 and Nvidia because I couldn't update the driver from 331 otherwise I would have had a black screen at the log in.
Since I updated to 15.04 I finally installed the most recents 346.59 without having "black screen" problems. But that's what I thought because 
when I switched to Intel and then I switched back to Nvidia (to play) I got the black screen. I was forced to "auto-remove" nvidia and install it again, the 346.59 which now is the only one
that works without black screens. The card is a GTX 860M.
Now I'm using Nvidia without problem but I'd like to use Intel too sometime so spare energy.
Does anybody know what I can do?

---

### Post by Keith_Helms on 2015-05-28
My system also has an Nvidia GTX 860M.  With the 331 drivers and the nvidia-prime package I can switch back and forth between using the Nvidia GPU and the Intel GPU.  I'm on the 14.04 LTS releases, so I can't say what works under 14.10 and 15.04.  I use the Nvidia X Server Settings application and the Prime Profiles option under it to switch GPUs.  The only problem I'm aware of is the the Nvidia GPU in an Optimus system (dual GPUs) can't sync to vblank, so some screen tearing is visible on videos.

---

### Post by efflandt on 2015-05-29
I have Intel HD 4600/Nvidia GTX 765m using nvidia-331-updates. If I switch from Nvidia to Intel using NVIDIA X Server Settings in 14.04, I have to log out and log back into X for Intel to take effect. If I switch from Intel to Nvidia, I have to reboot for it to take effect (I forget what happened if I did not reboot, but I know that logging out of X and back in did not work). I have Ubuntu on mSATA SSD though, so rebooting does not take long.

I have not tried newer nvidia drivers on my laptop yet since the GTX 765m has been around for awhile. But just tonight I purged nvidia-349 on my desktop PC and installed nvidia-352 (xorg-edgers ppa) which is only marginally quicker.

---

### Post by Keith_Helms on 2015-05-29
> **efflandt said:**
> I have Intel HD 4600/Nvidia GTX 765m using nvidia-331-updates. If I switch from Nvidia to Intel using NVIDIA X Server Settings in 14.04, I have to log out and log back into X for Intel to take effect. If I switch from Intel to Nvidia, I have to reboot for it to take effect (I forget what happened if I did not reboot, but I know that logging out of X and back in did not work). I have Ubuntu on mSATA SSD though, so rebooting does not take long.

I have not tried newer nvidia drivers on my laptop yet since the GTX 765m has been around for awhile. But just tonight I purged nvidia-349 on my desktop PC and installed nvidia-352 (xorg-edgers ppa) which is only marginally quicker.

Yeah, I've seen that too.  Supposedly you can change GPUs with just a logout, but sometimes when switching to Nvidia I got a black screen and had to actually reboot before the video would work again.  I've also seen some stupid problem where the first time I rebooted I got one of those "an error has occurred, would you like to report it..." prompts.  When I close that error window, the system seemed to work fine and then I didn't get the error on subsequent boots.  Lately, I haven't seen either of those problems, although I don't switch GPUs very often.

---

### Post by nigro.orlando on 2015-07-05
Hi and thank you for answering to my post. I'm very sorry I didn't follow up your answers! 

I also used to have the nvidia 331 when I hade kubuntu 14.10 and It didn't get me any troubles with black screen. I used to switch from Nvidia to Intel with the server setting and it worked pretty well.

Now that I updated to the 15.04 the 331 always gives me the black screen after reboot while the 346.59 doesn't. But the 346.59 is still unstable because (and this is weird) when I reboot after installing it I don't get the black screen and I can login as usual but if I reboot once again I get the black screen and I have to remove the driver in order to get the graphic interface back, isn't it odd? If I switch to Intel is fine but when I switch back to Nvidia I get the black screen after reboot...

---

### Post by nigro.orlando on 2015-07-16
No ideas? 
I'm installing and removing the nvidia-drivers all the time in order to play. It is quite frustrating.

---

