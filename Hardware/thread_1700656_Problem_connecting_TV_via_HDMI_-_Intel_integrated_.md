---
title: "Problem connecting TV via HDMI - Intel integrated graphics - 10.10"
date: 2011-03-05
forum: Hardware
---

### Post by thaDM on 2011-03-05
Hi,

I have done a lot of searching and cannot seem to find a conclusive solution to this problem.

I am trying to use my TV as a second monitor by connecting with HDMI. Under Windows it worked fine and I managed to connect to my friend's tele fine (with Ubuntu) but *my* tv won't allow for a resolution higher than 720x480 (even though it can do 1024x768 ) and has a thick black line down the left-hand side.

I am running 10.10 with Intel Integrated Graphics (rev 12).

Has anybody else experienced this and managed to fix it? I've been reading about changing a file called xorg.conf but it is not in 10.10. I am fairly new to the linux scene so please be gentle with descriptions/instructions.

Thanks in advance.

---

### Post by Antarctica32 on 2011-03-05
To be honest I do not know too much about TV screens as monitors and have only done it a few times, but I too have the thick black stripe on the left side on some of my monitors but it only lasts for a few seconds during boot. I have never really looked into it before as it was never a problem. I did however used to have an old tube screen that had a stripe on the side but it was because it was so old and somewhat broken. Sorry I couldn't help.

---

### Post by thaDM on 2011-03-20
Bump, any ideas?

---

### Post by Hello! on 2011-07-04
Go to System-Preferences-Monitors and switch off your laptop monitor. What happens is the two monitors are trying to take a common resolution, so switching one of them off will make the other monitor take the highest resolution by default (If it doesnt take so, manually change the resolution and then log out and log in again). Hope this helps.

---

