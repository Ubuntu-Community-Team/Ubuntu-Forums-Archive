---
title: "Dual monitors worked under Natty, not working under Oneiric"
date: 2011-10-19
forum: Hardware
---

### Post by Enigma6 on 2011-10-19
I have a Dell Latitude D820. According to notebookreview.com, that means I have a NVIDIA Quadro NVS 120 graphics solution with 512MB TurboCache. I have two external monitors that I use, depending on where I am. Using either of these monitors worked fine with Natty; however, now neither of them work.

[LIST]
[*]I have run all software updates.
[*]I have tried switching driver version under "Additional Drivers" to version 173, and back to "Version Current".
[*]I have searched for previous issues with this, but didn't see too much that helped me.
[/LIST]

The "Displays" dialog shows my laptop screen as "unknown" and does not detect any additional monitors. 

The "Detect Monitors" button is able to be clicked (not grayed out), but it doesn't do anything. 

I'd really appreciate any tips on getting this issue resolved.

Thanks!

---

### Post by kwildman on 2011-10-19
Are you using a docking station?  I have similar issues with Dell Laptop and NVIDIA via docking station and just submitted a help request.   Try without docking station and see if the detect displays works...

---

### Post by Smithie on 2011-10-19
Have you tried nvidia-settings?  Albeit I'm using a PC, the only way I am able to get 11-series Ubuntu to recognize my dual monitor set-up is through changing the display settings directly in the nvidia-settings utility.  If it is not already installed, it should be in the software manager. Install it, open it (in terminal if necessary with "gksudo nvidia-settings") Switch your display settings to "twinview" instead of "seperate x-screens," make sure only one screen is marked as "absolute," click "apply" and then "okay".

I sometimes need to log out and log back in for the system to begin using both screens after this process, but fiddling with nvidia-settings has always allowed me to get the dual screens working again if they fail for some reason.

---

### Post by mankygitt on 2011-10-19
I have the same issue on my Dell XPS L502
I am not using the NVIDIA graphics card as this particular hardware uses the Intel Sandy Bridge, and then attempts a software implementation to decide which apps should run on which video card - a terrible design, and poorly supported on ubuntu/linux in general.

So - under Natty, my mini-display port was active on the intel card and able to use extended desktop / dual screens.
I've installed oneiric (64bit) and have the same issue reported above - Main monitor detected as "unknown" and no additional monitors detected.

This seems like a regression.:confused:

---

### Post by Enigma6 on 2011-10-21
Ok,  Smithie's solution wound up working. The NVIDIA X Server Display Configuration panel (run 'gksudo nvidia-settings') did detect the second monitor, and I was able to change that second monitor's status from disabled to twinview. Interestingly, the built in Ubuntu display settings still fail to recognize that the second monitor exists at all, which is in my opinion, and as mankygitt noted, quite a regression, as it worked fine last version. 

Regardless, thanks so much for your help, all!

---

