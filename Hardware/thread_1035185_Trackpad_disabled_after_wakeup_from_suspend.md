---
title: "Trackpad disabled after wakeup from suspend"
date: 2009-01-09
forum: Hardware
---

### Post by kneecarrot on 2009-01-09
Hi,

First time Ubuntu user.  Running 8.10 on a Gateway 6020GZ laptop. 

After wakeup from suspend, the trackpad does not work (surface plus buttons).  I have to plug in an external mouse and reboot.

I have seen a fix for Apple laptops for this issue but nothing for non-Jobsian machines. :)

I really hope I can solve this one as this is the last thing keeping me from moving entirely to Ubuntu from XP.

Thank you kindly,
Jeff

---

### Post by kneecarrot on 2009-01-14
This is a real shame as this will force me to abandon Ubuntu to go back to the world of Windows.  Literally everything else I needed worked.  Darn.

---

### Post by kneecarrot on 2009-01-19
Sad sad sad.  The traditionally helpful Linux community has completely lost.  I will now make it my life's mission to discourage anyone from installing Linux.

---

### Post by kneecarrot on 2009-01-20
This is going from bad to worse.  My trackpad continues to not function after a hibernate.  I have taken all measures and nothing will remedy this problem.  I can't eat.  I can't sleep.  I spend most of my days looking wistfully out the window, hoping for spring but knowing that there is far too much winter to come.

---

### Post by kneecarrot on 2009-01-21
Due to my ongoing trackpad problems, my wife has now left me.  Due to extreme depression, my employer had no choice but to let me go.  Thank you, Linux community.  

This will likely be my last post, as I will be joining a group of nomadic Mongolian herders.  After the setting up/tearing down of camp and daily chores, there will be little time for Linux troubleshooting.  Also, there is no electricity or Internet access.

---

### Post by sbenson on 2009-01-21
My understanding is Linux IS available in Mongolian, Thanks for using Linux.

---

### Post by icepenguin on 2009-01-21
I would recommend continuing to use the external mouse as a workaround until you can determine the cause of the problem.  As an added bonus, the mouse cable can be used to tie your new mongolian yaks to their hitching posts at night.

Also, have you tried installing gsynaptics?  That may help as well.

See [https://help.ubuntu.com/community/SynapticsTouchpad#shmconfig](https://help.ubuntu.com/community/SynapticsTouchpad#shmconfig)

---

### Post by last1 on 2009-01-21
Via Reddit:> 
He doesn't need to plug in a mouse to reboot. Ctrl-Alt-F1 will land him in a console and he can do "sudo shutdown -r now" from there. Or perhaps restart whatever daemon is causing the problem.

---

### Post by aldenhg on 2009-01-21
Try restarting X with Ctrl+Alt+Del. If that doesn't work, it's the drivers for the trackpad. I know that it doesn't solve the problem, but it might help categorize it.

---

### Post by 10wattmindtrip on 2009-01-21
Instead of trying Ctrl+Alt+Del. Try Ctrl+Alt+Backspace. This should restart X.

---

### Post by gldblade on 2009-01-22
These workarounds seem to defeat the whole point of standby.  You might as well stop using standby if you're forced to reboot every time anyway.

Not that that's an amazing solution, but I guess Linux isn't perfect.

---

### Post by monkeyp on 2009-01-22
Have you tried changing the suspend to unload the module for your touchpad and to reload it in the wakeup script?

---

### Post by kneecarrot on 2009-01-22
> **monkeyp said:**
> Have you tried changing the suspend to unload the module for your touchpad and to reload it in the wakeup script?

What is this?  Now I am getting replies?  But but... my wife... my job... I am now on a course to forge a new life!

---

### Post by xavster on 2009-01-22
google: dell trackpack not working after suspend

---

### Post by kneecarrot on 2009-01-22
Update: My possessions have all been sold and I stand here with only the clothes on my back, my walking stick, and my trusty Gateway 6020GZ.  My boat for Mongolia leaves in hours.  I decided to check back in this thread before I started my new life and low and behold the saga posted here made it to some website called Reddit.  And now I sit awash in suggestions on how to get my trackpad working after suspend.  Perhaps I will try a few of these ideas before I leave.  It is too late for me (thanks again, Linux "community"), but the homeless man whom I will entrust my Gateway will surely appreciate a working trackpad after suspend.  He looks like he could also use some beans or perhaps a shirt.

---

### Post by overdrank on 2009-01-22
Please stay on topic and without all the drama. :)

---

