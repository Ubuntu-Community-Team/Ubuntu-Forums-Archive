---
title: "Suspend in Edgy not Resuming"
date: 2006-12-23
forum: Hardware &amp; Laptops
---

### Post by joeyjwc on 2006-12-23
Hello.

I've been having this problem for quite a while, but haven't bothered to try fixing it yet.  I run Kubuntu Edgy Eft 6.10 on my computer which has an nVidia GeForce 6800XT graphics card in it with two monitors attached, using TwinView to configure them.  When I try to use standby mode, either through the K Menu or through # hibernate-ram in a console, things seem to go well at first.  The screens shut off and the power button on my computer blinks like it should while in standby.  However, when I start the computer back up, both screens turn on, but remain black.  Then, on my second screen, which is a CRT monitor (my main screen is an LCD monitor), a box comes up (which is an error message displayed internally through the monitor) saying "Frequency out of Range."  I have to hold the power button for 5 seconds to force the computer to power off.  CTRL+ALT+Backspace does not work, so I don't think this is a problem with the X Server.  I have tried adding nvidia to the MODULES="" parameter in /etc/default/acpi-support but when I run hibernate-ram, it spits  back this:
```
Some modules failed to unload: nvidia
hibernate-ram: Aborting suspend due to errors in ModulesUnloadBlacklist (use --force to override).
```


My xorg.conf configuration is located here:
[http://joeyjwc.x3fusion.com/briefcase/xorg.conf](http://joeyjwc.x3fusion.com/briefcase/xorg.conf)

I suspect the issue is with TwinView because the problem occurs directly with restoring the video.  I tried suspend2, but when I tried to use suspend from the K Menu, it didn't do anything at all, so I got fed up and uninstalled it and installed the standard non-suspend2 kernel instead.

---

### Post by joeyjwc on 2006-12-26
My apologies for bumping this topic...

---

### Post by zorglab on 2007-01-01
Have you tried disabling TwinView and see if it works ?

---

### Post by futz on 2007-01-01
I've got 5 or 6 different boxes here (hardware changing pretty regularly as parts or whole machines get sold off and new/different ones come in) running various linux distros. Some of these are multi-booting winxp as well. I've never been able to get standby to work on any of them in linux. The ones with xp will standby in windows just fine, but not ever in linux.

Oh, they'll do the proper power light blinky thing and power down to S3, no problem. But when they wake up again things are very messed up, or you get a blank screen or the problem you're seeing. Very annoying. :(

I hate waiting for a full bootup. Wish this would work reliably. ](*,)

> I suspect the issue is with TwinView because the problem occurs directly with restoring the video. 
Take a look in the power settings in your BIOS. Many have a setting for a video rePOST on wakeup. Test with that toggle switched each way and see if that helps.

---

### Post by joeyjwc on 2007-01-11
Sorry for not replying.  I asked over at the LinuxQuestions.org forum, but I essentially got the same replies: suspend and Linux aren't best friends.

It was suggested to me to try being more specific with the modelines, but that didn't seem to help any.

It works fairly well on my laptop, at least.  20% of the time, I get the blank screen syndrome, but most other times, things work.  My guess is that system services get tied up that 20% of the time.

This is about the only thing that I miss from Windows because sometimes I need to shut off my machine for five or ten minutes to think (I don't have water cooling, so the fans are a little loud) and then will turn it back on.  Oh well.

I had always thought that I was just unlucky with suspend.  I guess it's fairly common then.  :D

---

### Post by futz on 2007-01-14
Here's something I found in [http://www.freesoftwaremagazine.com/articles/hibernate_linux](http://www.freesoftwaremagazine.com/articles/hibernate_linux)
> **swsusp will not work with Symmetric Multi Processing (SMP) enabled in your kernel**

---

### Post by mixonic on 2007-01-15
Hey,

Check this out:

  [http://ubuntuforums.org/showthread.php?t=337687](http://ubuntuforums.org/showthread.php?t=337687)

My issue with suspend is actually only the display not waking up from dpms, the suspend function without all the ubuntu fancy scripts works great.

-Matt

---

### Post by joeyjwc on 2007-01-15
xset dpms force off works without problem for me.  In fact, I invoke it, along with a screen blanking screensaver, every time I need to leave my computer for a while.  My GPU tends to get really hot (it can get up to 76 degrees centigrade with a GL screensaver running on both screens!), so I need a way to keep it somewhat cool when I'm not using it.  This method gets it down to 55 - 60 degrees centigrade.  The normal temperature for it on Linux is about 66 centigrade, but for Windows, it's usually somewhere between 55 and 57 centigrade.  I wonder why...

---

### Post by futz on 2007-02-07
Found this article today. Interesting...
[http://www.advogato.org/article/913.html](http://www.advogato.org/article/913.html)

---

