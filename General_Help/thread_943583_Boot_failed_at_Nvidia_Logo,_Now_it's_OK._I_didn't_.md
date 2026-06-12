---
title: "Boot failed at Nvidia Logo, Now it's OK. I didn't do anything to fix it"
date: 2008-10-10
forum: General Help
---

### Post by dhughes on 2008-10-10
My system was on for quite a while, uptime was since the end of July when I built a new system. 

 A few days ago I had to shut it off to move some stuff and when I turned it back on it froze at the Nvidia logo, the one after the Ubuntu logo shows the progress bar loading, the Nvidia logo had noise and white flecks on the screen around it. I thought the video card had fried, so I tried a LiveCD and everything was fine but a reboot would still result in the failure to boot past the Nvidia logo with the noise and garbage showing around it. 

 To be honest I'm not really sure what drivers I have installed, the Nvidia X-Server Settigns utility shows NVIDIA Driver Version: 169.2  Synaptic shows I have installed nividia-glx-new, xserver-xorg-video-nv, nvidia-kernel-common

 That was three days ago, no finally I had some time to look at it and it dawned on my I didn't try any other sessions ctrl+alt+F1 etc. So here I go again booting but this time it booted perfectly! I didn't do anything and I didn't see any messages other than a fsck since it hadn't been able to check the disk becuase I never rebooted for so long.

 Anyway, I'll have to find out what happened, look at some log files but I don't know what to look at. Any suggestions on tracking down this mysterious failure to boot and then the sudden healed system? Oh and this seems to have happened after a recent update, it was three library files that were updated during the last update sent out via the Update Manager.

---

### Post by cariboo on 2008-10-10
I've actually seen a few people on the forums say that some times this is the only way to get /etc/X11/xorg.conf configured properly. It seems to have worked for you.

Jim

---

### Post by dhughes on 2008-10-10
> **cariboo907 said:**
> I've actually seen a few people on the forums say that some times this is the only way to get /etc/X11/xorg.conf configured properly. It seems to have worked for you.

Jim

  But I didn't do anything to xorg.conf, nothing has changed since before or after my problem, other than the three days of it not booting. Do you know where those posts are? I searched but couldn't find much or didn't phrase it right when searching I tried "nvidia logo boot frozen" etc.


 Obviously, or at least it seems so, it's something to do with the video driver when it would hang at the Nvidia logo, although the white bits/noise floating like you'd see after a very bad system bad crash are a mystery, but that's just a guess.

 I looked at dmesg but couldn't see much there,  System>Admin>System Logs none of them show much useful info either.

 About xorg.conf actually I have disabled the Nvidia boot logo with: ```
sudo nvidia-xconfig --no-logo
``` but that was today after my system booted normally. It's my attempt to prevent the Nvidia logo from coming up but I can't see that as being the only reason for a failure to boot.

---

### Post by dhughes on 2008-10-13
This must be a driver problem, it happened again when I rebooted just a few moments ago (the video using a LiveCD works fine) but this time I tried ctrl+alt+F1 and I was able to go there to tty1. If this works again I should, after using this LivedCD, be able to log in normally, then reinstall or change my video driver.

**edit:** Yup, after using a LiveCD and then rebooting normally (not using a LiveCD) my system will boot normally, no errors. Very odd.

 **edit #2:** Went to Synaptic and reinstalled nvidia-glx-new, rebooted, my system rebooted twice on its own and then came up normally to the GDM log in screen.

 FYI this is what I saw (the Ubuntu splash screen was also garbled):

---

### Post by dhughes on 2008-10-15
Here we go again, Update Manger had some fairly big system updates which required a reboot and wouldn't you know it my system failed to start after the reboot or at least it started but all I could see was "snow" (white specks on a black background, the specks falling from the top to the bottom).

 Rebooting with a LiveCD and then immediately exiting then rebooting again without the LiveCD, normal boot, and everything looks fine it's all normal and I can log in.

 Grrrrrrrrr!

 Maybe I'll shut off Compiz or at least dial down the effects (although it works perfectly) or uninstall the Nvidia driver...but what's the alternative?

 ](*,)

edit: I fogrgot to mention it, again, did the double reboot; when the system rebooted it came to the point where Linux would load but then the system rebooted again and when it came up it had the "snow" as I mentioned.

 Just for kicks I rebooted after I last wrote that above and this is what I got (see image) but after a second reboot it was OK.

 My brain is really feeling fuzzy these days!

---

