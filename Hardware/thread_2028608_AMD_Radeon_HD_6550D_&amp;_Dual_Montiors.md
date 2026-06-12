---
title: "AMD Radeon HD 6550D &amp; Dual Montiors"
date: 2012-07-18
forum: Hardware
---

### Post by Big Dan on 2012-07-18
Hi All, 

  I'm wondering if you can help me out. I did a fresh install of 12.04 yesterday along with the AMD ATI/AMD Proprietary FGLRX graphics driver. I have two monitors. A 23" with a native resolution of 1920x1080 and a 19" with a 1440x900 resolution. 

   Yesterday, I was able to get both monitors running in their native resolution through the ATI Catalyst manager. This morning I booted and noticed my main display (23") was scaled to the resolution of the my secondary monitor. Trying to edit the display properties via Catalyst either results in Catalyst crashing or nothing. By nothing I mean the changes appear to take effect but when rebooting it reverts to both monitors being ran at 1440x900. 

  I should note that I'm unable to install the ATI/AMD post release updates from Additional Drivers it just errors out. 

  Any ideas? 

Thanks, 
Dan

---

### Post by QIII on 2012-07-18
The post-release version causes problems for some users.

The "Additional Drivers" method of installation causes problems for some users.

Before exploring that, could you tell me if you are running the CCC in administrator mode?  How did you install the driver?

---

### Post by Big Dan on 2012-07-18
> **QIII said:**
> The post-release version causes problems for some users.

The "Additional Drivers" method of installation causes problems for some users.

Before exploring that, could you tell me if you are running the CCC in administrator mode?  How did you install the driver?

Thanks QIII. Yes, I'm running Catalyst in admin mode. I installed the driver via the additional drivers dialog.

---

### Post by QIII on 2012-07-18
Goofy things sometimes happen with APUs and hybrid ATI/ATI graphics.

Could you paste the contents of /etc/X11/xorg.conf between code flags(click the # sign above)?

---

### Post by Big Dan on 2012-07-18
> **QIII said:**
> Goofy things sometimes happen with APUs and hybrid ATI/ATI graphics.

Could you paste the contents of /etc/X11/xorg.conf between code flags(click the # sign above)?

I'll post as soon I get Ubuntu back up and running. I hosed GRUB and had to use my Windows recovery disc to boot into Windows. :popcorn:

I appreciate you taking the time to help me.

---

### Post by QIII on 2012-07-18
No problem.  After you posted it I was going to tell you I'd have to look at it when I get home so I can take a look at my own and make some notes.  Only Windows at work (and the cell phone I'm typing on right now while I wait for a test to finish running!)

---

### Post by Big Dan on 2012-07-19
> **QIII said:**
> No problem.  After you posted it I was going to tell you I'd have to look at it when I get home so I can take a look at my own and make some notes.  Only Windows at work (and the cell phone I'm typing on right now while I wait for a test to finish running!)

I wound up reinstalling Ubuntu and both monitors are working normally now. :confused:

Thanks anyway. :)

---

