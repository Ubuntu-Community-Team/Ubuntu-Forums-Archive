---
title: "Screen Resolution app Fails to Detect monitors"
date: 2008-11-28
forum: Hardware
---

### Post by gcbzzzz on 2008-11-28
case 1: works partially fine :)
1. plug in external monitor to notebook
2. turn notebook on.
3. open System > preferences > Screen Resolution
4. i can set external monitor to Full Wide Screen resolution. But refresh rate is 60hz (manual recomends using 70hz)

Case 2: Fail. :confused:
1. turn on notebook
2. plug in external monitor
3. open System > preferences > Screen Resolution
4. External monitor only goes to 1024x768. and even so, the screen first appear as cloned, even though the Clone Screens is unchecked. Here i have the option to use 70hz.

if I keep changing resolution then eventually the screen stops getting cloned, but I never get the full display resolution available.

The question is:
**What is the method used at boot time that correctly identifies the monitor capabilities? And how do i use it after boot time?**

Thank you

---

### Post by gcbzzzz on 2009-01-04
bump. this is also happening to my desktop. using a nvidia card with dvi and vga output.

at boot time, detection is perfect.

later on it SUCKS.

works alright on windows.

so,**[COLOR="DarkRed"] What is the method used at boot time that correctly identifies the monitor capabilities? And how do i use it after boot time?[/COLOR]**

---

### Post by Altay_H on 2009-06-15
I'm having the same problem. The gnome-display-properties fails to detect the television I have plugged in via S-video when I click the "Detect Monitors" button. I have managed to get the television to display a clone of my monitor in a lower resolution using xrandr, so I know it works. Display Preferences just won't detect external monitors. It stinks.

---

### Post by CatKiller on 2009-06-15
I think you'll find that it's your monitor that doesn't identify itself. The mechanism to do this is [EDID]("http://en.wikipedia.org/wiki/EDID"). It's only been around for 15 years. You can't expect monitor manufacturers to have got the hang of it yet...

How is X supposed to know what monitor you're using if the manufacturer won't say what it is?

---

### Post by Altay_H on 2009-06-15
> **CatKiller said:**
> How is X supposed to know what monitor you're using if the manufacturer won't say what it is?
I'm not sure, but I know that Windows has no problem doing it. How does Windows identify anonymous monitors? Is there a reason Linux can't do it the same way?

---

### Post by CatKiller on 2009-06-15
> **Altay_H said:**
> I'm not sure, but I know that Windows has no problem doing it. How does Windows identify anonymous monitors? Is there a reason Linux can't do it the same way?

Windows can't do it either. You're in Generic VGA until you install a "monitor driver" that contains the information that the monitor should have given through EDID already.

Ubuntu had a tool for a couple of releases that was able to take the Windows "monitor driver" and do what Windows does; strip the important information out and put it in the appropriate place for configuration. That was quite neat. Unfortunately, the recent changes to X meant that it didn't work any more and, since Ubuntu was the only distribution that used it, the work's been proceeding quite slowly to get it re-written. I understand that it will be back when that work's been done, though.

---

### Post by planetLars on 2009-06-15
You might have luck with xrandr.

See [http://ubuntuforums.org/showpost.php?p=7404056&postcount=5]("http://ubuntuforums.org/showpost.php?p=7404056&postcount=5").

Note that xrandr got updated last week I think. It now exhibits the same bug as mentioned in above post for the display preference which is if you start with a lower res it doesn't show higher res. You have to add a --newmode to xrandr.

Best

Lars

---

### Post by Altay_H on 2009-06-15
> **CatKiller said:**
> Windows can't do it either. You're in Generic VGA until you install a "monitor driver" that contains the information that the monitor should have given through EDID already.
Actually, when I connect my computer to the television via S-video using Windows I don't have to install any drivers. It automatically detects the television and messes up my screen resolution to fit that of the television. Maybe the drivers are already installed or something, but Vista has no trouble detecting the television.

I also have another computer running the same version Ubuntu that *does* detect the television when it's plugged in. It uses the nVidia driver tools to do so. Since I'm running a non-proprietary graphics card driver for ATI on this computer, I don't have the same tools. I have considered switching to a proprietary driver solely to be able to detect external monitors though. Any thoughts?

I tried using xrandr as well, as [this post]("http://ubuntuforums.org/showthread.php?t=1149711") suggested. However I couldn't set the screen resolution to be anything other than 800x600 and I could only get it to clone my display. Also the output had static in some places that should have been white.

If gnome-display-properties is so bad at detecting S-video connections, why doesn't it allow the user to inform it that there is something plugged in?

---

### Post by CatKiller on 2009-06-15
> **Altay_H said:**
> I also have another computer running the same version Ubuntu that *does* detect the television when it's plugged in. It uses the nVidia driver tools to do so. Since I'm running a non-proprietary graphics card driver for ATI on this computer, I don't have the same tools. I have considered switching to a proprietary driver solely to be able to detect external monitors though. Any thoughts?

That's interesting. I was aware that the NVidia driver did some dual screen voodoo because it meant that the driver never reported the correct refresh rate but I never actually found out what it did. Now I know; it makes your TV work :)

I haven't ever used the proprietary Ati driver, so I have no idea whether it will be able to do the same trickery.

> If gnome-display-properties is so bad at detecting S-video connections, why doesn't it allow the user to inform it that there is something plugged in?

Do you want to code it? I'm sure they'd be grateful for the patch :)

Seriously, I'd imagine that it's a case of limited resources. X is in a state of flux at the moment to make all these things like display hotplugging work, and there's only so much developer time to go around.

I've never tried connecting an S-Video output to my computer, but is there a reason why it's 800×600? PAL is 625 lines, NTSC is 525. I would have though that specifying a native mode for the TV would be more sensible.

---

### Post by gcbzzzz on 2010-10-26
Since my problem was detecting the second monitor (a TV) *after* boot time (it's is detected alright if plugged *before* turning the computer on) i solved it hardcoding the detected entry to xorg.conf.

The downside is that my desktop has a huge unused area on the bottom (where's the TV is supposed to use) even when i'm not with the TV plugged in... sometimes an alert dialog get lost in there... sucks.

---

### Post by gcbzzzz on 2011-02-05
[COLOR="DarkRed"]Any one can point me to the methods ubuntu or X uses to detect a monitor at boot time?[/COLOR]

at boot time everything is detected normally. but i do not want to reboot my computer everytime i attach a monitor

---

### Post by richiva on 2012-02-10
In Oneric Ocelot i'm having same issue. Xrandr does not detect monitors fine unless at boot time. 
 
As pointed before, in earlier versions of Ubuntu, it worked fine with the windows driver trick. So this hack is espected to be available again?

This problem really sucks when trying to talk about the benefits of Ubuntu.

---

### Post by gcbzzzz on 2012-02-10
this thread is old.

well, i've started using debian and gentoo as it's more other-wm friendly since ubuntu forced us to use alpha work on gnome-3...

but back on topic, i recently learned that calling `sudo udevadm trigger` sometimes does the trick of activating hardware that was available after boot.

in my case i use that on the gentoo livedvd, after i downloaded the wifi card firmwares.

keep in mind that this command will probably mess something up. in my case, it redetected my switchable video card and my X session restarted. other than that it worked ok.

---

