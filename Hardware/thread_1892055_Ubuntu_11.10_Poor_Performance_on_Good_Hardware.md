---
title: "Ubuntu 11.10 Poor Performance on Good Hardware"
date: 2011-12-07
forum: Hardware
---

### Post by mellow_fellow on 2011-12-07
Hello everyone, been searching these forums for a while, but just registered because I couldn't find a solution to my problem, I have been running ubuntu 10 on my old far weaker laptop when it comes to hardware and it was running very good compared to now. 

Now the config. on my Lenovo Y560 is i7 740QM @ 1.73GHz 4 cores 
ATI Mobility Radeon HD 5730 1gb DDR3 and 4GB of RAM

Ubuntu 11.10 is installed on a separate 20GB partition. 

Now I know that this hardware is more than enough to run Ubuntu smooth, but it runs everything else than that. First the graphics aren't running at 20 % of their potential I think, Unity is very slow and laggy, I installed the additional drivers and tried the ones from AMD's website with no improvement. I just found out that a new version of the drivers came out recently so I'll give it a try again.

Second the system itself is acting very weird, sometimes it will just boot into the desktop with only the top bar visible and nothing else, so basically giving me no control whatsoever.

Also the battery monitor icon is acting weird too. When its plugged in it will display the full white battery icon, however when I plug it out from power it turns into the battery with thunderbolt and showing the time to charge, isn't it supposed to be the other way around?

Please help, I consider it to be a very good OS and I would really like to use it to its full potential, so if you guys know any solution(s) to these problems I will be very thankful.

---

### Post by tartalo on 2011-12-07
> **mellow_fellow said:**
> I have been running ubuntu 10 on my old far weaker laptop when it comes to hardware and it was running very good compared to now. (11.10)

Ubuntu 10.04 and 1.10 use Gnome 2 as the Desktop environment. 11.10 uses Ubuntu Unity. Enough said?

---

### Post by LinuxFan999 on 2011-12-07
(Removed post)

---

### Post by thaelim on 2011-12-07
Your problem is the ATI graphics. I have been strugging with this problem on my work PC (which has a very similar config to yours). I run dual monitors (1920x1200 each) and the performance was just always sluggish no matter what I did. Open drivers, binary drivers, tweaking Compiz, nothing really helped very much.

The thing that cured all my problems in the end was throwing the ATI POS in the bin and getting an nVidia GTX550Ti. Installed the nVidia binary drivers and now I'm cruising at warp speed. Seriously, it's not worth the aggravation - just ditch the ATI card.

Edit: I just realised it's a laptop... bummer! If you are really stuck with the ATI graphics, the best performance on Unity is achieved as follows:
- Install compizconfig-settings-manager (to tweak advanced graphics settings)
- Remove the ATI 'additional' drivers to switch back to the open source drivers - the open drivers ALWAYS outperform the binary ones.
- In compizconfig-settings-manager, under OpenGL ensure vsync is not enabled. Under Composite ensure 'detect refresh rate' is disabled, and manually adjust the refresh rate slider to 60.  

This is really just making the best of a poor situation, but until the open drivers mature even further there's not much we can do.

---

