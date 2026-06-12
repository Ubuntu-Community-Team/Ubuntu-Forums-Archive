---
title: "Won't Load: Not starting K Display Manager"
date: 2008-10-29
forum: General Help
---

### Post by Matt86 on 2008-10-29
OK,

I'm running Kubuntu 8.10 on a HP compaq nx7010 laptop.

When booting I now get the message:

grep: /user/lib/kde4/etc/kde4/kdm/kdmrc: no such file or directory
Not starting K Display Manager (kdm-kde4); it is not the default display manager

I can only guess that this is attributed to me installing an ATI driver in the previous session. I was having issues with Kubuntu not shuting down, restarting, or logging off (just a black screen with the cursor showing) and found some information suggesting it might be attributed to ATI graphic cards.

I have an ATI mobility radeon 9200 so I installed an ATI driver from adept (as there was no ATI folder in /etc and hardware drivers didn't detect any driver).

Following this, I got the afore mentioned error - so I cannot enter Kubuntu.

I tried entering recovery mode and using:
sudo dpkg-reconfigure xserver-xorg

However, after setting up the keyboard for configuration I get a prompt from xserver saying that it may override existing configuration and it is making a backup, and then nothing happens.

If anyone knows anything that might help me resolve the situation I'd be greatly appreciative - I really don't want to have to reinstall merely because of my incompetency without a GUI.

Thanks,
Matt

---

### Post by richardcarter on 2009-01-06
I doubt you'll notice my post, as I see so many unanswered posts on here.

I'm experiencing the exact thing you did this past October.  Hopefully you've resolved your issue by now.  I tried to install ATI graphics drivers for an ATI-All-In-Wonder 9000 graphics card using the official driver for my model of card from the ATI website.  After rebooting I can't load kdm, but instead get a rundown of system processes, starting cupsd, starting sama, starting bluetooth, etc.  But then it says "FATAL: Error inserting speedstep_centrino (/lib/modules/2.6.24-19-generic/kernel/arch/x86/kernel/cpu/cpufreq/speedstep-centrino.ko) : No such device.


And then it gets to "running local boot scripts" and stops.

I am so so so sick of setting up my entire system, loading a linux distribution, configuring the desktop and themes to my preferences, getting rid of crap programs I don't want, installing the ones I do want, setting up all of my e-mail preferences and filters and then trying to fix the graphics card (because no graphics card ever seems to work properly by itself on Ubuntu/kubuntu/linuxmint/any other distro, and then having it crash and having to restart the process with the hope that it'll work next time.

I hate windows, I hate MAC, linux is dependable, but is a NIGHTMARE to set up.

Can someone help me?

I'm currently running linuxmint KDE Community Edition 5 on a Dell 4600 Desktop with the following specs:

[http://reviews.cnet.com/desktops/dell-dimension-4600-pentium/4507-3118_7-30529709.html?tag=mncol;rnav]("http://reviews.cnet.com/desktops/dell-dimension-4600-pentium/4507-3118_7-30529709.html?tag=mncol;rnav") except that I opted for an upgraded Radeon All-In-Wonder 9000 graphics card. 

Help....Please...

---

### Post by sayakb on 2009-01-07
@Matt
Seems like a malformed path. Try reinstalling kdm instead first:
```
sudo apt-get install --reinstall kdm
```

---

