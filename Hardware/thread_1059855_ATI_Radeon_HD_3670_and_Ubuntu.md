---
title: "ATI Radeon HD 3670 and Ubuntu"
date: 2009-02-04
forum: Hardware
---

### Post by gumbeto on 2009-02-04
Hello,

I can't find it in the hardware support page, so has anyone tried ATI Radeon HD 3670 with ubuntu? Can you share your experience?

Thank you

---

### Post by Mizzou_Engineer on 2009-02-04
> **gumbeto said:**
> Hello,

I can't find it in the hardware support page, so has anyone tried ATI Radeon HD 3670 with ubuntu? Can you share your experience?

Thank you

The Radeon HD 3670 will work in Linux as it is fully supported by AMD's fglrx driver (the "restricted" one that Ubuntu prompts you to install) and has 2D support with the standard free "ati" driver. I have a Radeon HD 3850 running nicely under Linux with the fglrx driver, and the 3850 is very similar to your 3670 in terms of hardware.

Links: 
[AMD proprietary driver]("http://ati.amd.com/support/drivers/linux64/linux64-radeon.html")
[Xorg ATi Radeon hardware support page]("http://dri.freedesktop.org/wiki/ATIRadeon")
[Xorg ATi driver feature support page]("http://www.x.org/wiki/RadeonFeature")

---

### Post by Bablefish on 2009-02-04
I tried once and it crashed my OS...NEVER AGAIN!!!

---

### Post by gumbeto on 2009-02-04
thank you Mizzou_Engineer. i think i will go with it.

what do you mean Bablefish? you tried it once? What did you do then, you threw it away??

---

### Post by khelben1979 on 2009-02-04
> **Bablefish said:**
> I tried once and it crashed my OS...NEVER AGAIN!!!

I believe that he tried one version of that driver and it failed. Trying different versions can sometime solve problems like these.

---

### Post by krippa on 2009-04-26
How do you install different versions of this driver? 

I have just installed Jaunty on my brand new Dell Studio XPS 16 with an ATI Radeon HD 3670 graphics card and am experiencing some problems with the proprietary driver which I have described in the following bug report: [https://bugs.launchpad.net/ubuntu/+bug/363533]("https://bugs.launchpad.net/ubuntu/+bug/363533")

In short the proprietary driver which I need for 3D support makes most graphics operations unstable when used with an external screen and resume from sleep also does not work.

---

### Post by khelben1979 on 2009-04-26
> **krippa said:**
> How do you install different versions of this driver?

[Check this out!]("http://support.amd.com/us/gpudownload/linux/previous/Pages/radeon_linux.aspx")

---

### Post by StuartN on 2009-04-26
> **krippa said:**
> How do you install different versions of this driver?

Only version 9.4 is compatible with Ubuntu 9.04. The list of supported cards is in the release notes at [http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.37](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.37)

Installing an earlier driver will crash your Ubuntu 9.04 (but not your Debian Lenny).

Unsupported cards, listed in the Catalyst 9.3 notes as "legacy" [http://support.amd.com/us/gpudownload/linux/legacy/Pages/radeon_linux.aspx?type=2.4.2&product=2.4.2.3.11&lang=English](http://support.amd.com/us/gpudownload/linux/legacy/Pages/radeon_linux.aspx?type=2.4.2&product=2.4.2.3.11&lang=English) will use the open source drivers, with some loss of performance.

---

### Post by Josef_A on 2009-04-26
> **StuartN said:**
> 
Unsupported cards, listed in the Catalyst 9.3 notes as "legacy" [http://support.amd.com/us/gpudownload/linux/legacy/Pages/radeon_linux.aspx?type=2.4.2&product=2.4.2.3.11&lang=English](http://support.amd.com/us/gpudownload/linux/legacy/Pages/radeon_linux.aspx?type=2.4.2&product=2.4.2.3.11&lang=English) will use the open source drivers, with some loss of performance.

I have one of those, a Radeon Express 1250.

If Im reading that right, does that mean that if I go to 9.04 my choices are:

1. Stay on older unsupported proprietary drivers
2. Move to the open drivers and not get 3D until 3D support comes to the open drivers?

---

### Post by krippa on 2009-04-26
I suppose you would need the 9.4 proprietary driver for 3D effects. But as I understand it 9.4 is the most recent one and what do you mean by unsupported?

---

### Post by Josef_A on 2009-04-26
According to this [http://support.amd.com/us/gpudownload/linux/legacy/Pages/radeon_linux.aspx?type=2.4.2&product=2.4.2.3.11&lang=English](http://support.amd.com/us/gpudownload/linux/legacy/Pages/radeon_linux.aspx?type=2.4.2&product=2.4.2.3.11&lang=English)

Catalyst beyond 9.3 will not support the 1250. So it kind of looks to me like I'd either need to run 9.3 on my own or accept the open source driver if I were to upgrade to 9.04.

---

### Post by shrndegruv on 2009-04-27
> **krippa said:**
> How do you install different versions of this driver? 

I have just installed Jaunty on my brand new Dell Studio XPS 16 with an ATI Radeon HD 3670 graphics card and am experiencing some problems with the proprietary driver which I have described in the following bug report: [https://bugs.launchpad.net/ubuntu/+bug/363533]("https://bugs.launchpad.net/ubuntu/+bug/363533")

In short the proprietary driver which I need for 3D support makes most graphics operations unstable when used with an external screen and resume from sleep also does not work.

krippa, did you get suspend to disk working.  I can not suspend or hibernate.  The machine goes to sleep just fine, but can't resume; when I try to restart I get a cursor on a black screen.

---

### Post by krippa on 2009-04-27
> **shrndegruv said:**
> krippa, did you get suspend to disk working.  I can not suspend or hibernate.  The machine goes to sleep just fine, but can't resume; when I try to restart I get a cursor on a black screen.

Nope, same behavior with hibernate, I can only see the unlock-screen as an out of focus gray square and the computer does not respond to anything. Everything up until that seems to be going fine, e.g. going to sleep etc... Disabling the driver solves the problem but I want the 3D. I guess my best bet is to wait for release 9.5 of the driver.

By the way, is there a way to check which version is installed? Will the 9.5 automatically be downloaded and added as an option when it is available or will I have to download it manually?

---

### Post by INTERPEGASUS on 2009-04-27
I have an ATI mobility Radeon 3400 in Ubuntu Jaunty 9.04 and I have noticed that enabling the ATI driver degrades performance on the following cases:

1-> When restoring a minimized window.
2-> When switching video to full screen.

Without the ATI driver restoring a window takes less than a second. Switching to full screen video is also very fast.

But with the ATI hardware driver it can take 2-3 seconds to restore a minimised window and 4-5 seconds to switch to full screen video using VLC.

I also have compiz enabled. Does anybody know how to fix this issue? 
thanks in advance!

---

### Post by gumbeto on 2009-04-28
No suspend here either... I also have a dell studio xps 16, with ATI Radeon HD 3670 and with the catalyst 9.4 drivers installed on intrepid. Before I installed the drivers, suspend worked (except for the touchpad). With the drivers and compiz, I get a black screen when resuming. Ctrl+Alt+Backspace has no effect (I have it enabled). Trying to switch to Ctrl+Alt+F1 (or any other) doesn't work either.

---

### Post by gumbeto on 2009-04-28
Krippa, I don't know how to check which version is installed. I would also like to know that. 

To install a new version, I guess you have to do it manually. I did it, according to the how to, for upgrading from 9.3 to 9.4 and it worked perfectly without having uninstalled the previous version.

INTEPEGASUS, I don't have anything like that here. I am using catalyst 9.4 in intrepid, with compiz, and I am glad, apart from the suspend and some video issues. The video issues are solved if I fall back to metacity.

---

### Post by shrndegruv on 2009-04-28
> **INTERPEGASUS said:**
> I have an ATI mobility Radeon 3400 in Ubuntu Jaunty 9.04 and I have noticed that enabling the ATI driver degrades performance on the following cases:

1-> When restoring a minimized window.
2-> When switching video to full screen.

Without the ATI driver restoring a window takes less than a second. Switching to full screen video is also very fast.

But with the ATI hardware driver it can take 2-3 seconds to restore a minimised window and 4-5 seconds to switch to full screen video using VLC.

I also have compiz enabled. Does anybody know how to fix this issue? 
thanks in advance!

I also have this issue.  I read on another thread that it is caused by old configs in your home directory.  try creating a new user and see if the problem persists.

I tried to use the open source drivers and noticed that my graphics card was generating a ton of heat ~60C.  I guess there are no good options for us xps studio 16  owners yet...:(

---

### Post by gallenwolf on 2009-04-28
Hello mates!
I'm planning to get a new laptop with a HD3670 and run ubuntu but I'm kinda worried seeing all these posts. Question: How are things back on 8.10 with this card? I'm was running 8.10 with a X1600 and it runs great, "upgraded" to 9.04 and some of my opengl apps stopped working. I'm sure I can stick with 8.04 for awhile :)

Thanks!

Alvin

---

### Post by INTERPEGASUS on 2009-04-28
Thanks for the replies!

Compiz is causing the issue. Metacity improves the performance a lot. However compiz is one of the reasons I switched to Linux.

Is it possible to fix the slow performance in compiz? I remember it was working fine with an older version. 

Maybe compiz 0.7? will work better...

---

### Post by gumbeto on 2009-04-29
> No suspend here either... I also have a dell studio xps 16, with ATI Radeon HD 3670 and with the catalyst 9.4 drivers installed on intrepid. Before I installed the drivers, suspend worked (except for the touchpad). With the drivers and compiz, I get a black screen when resuming. Ctrl+Alt+Backspace has no effect (I have it enabled). Trying to switch to Ctrl+Alt+F1 (or any other) doesn't work either.

Sorry, I just noticed it might not be obvious: the Ctrl+Alt+F1 and Ctrl+Alt+Backspace don't work only when in the black screen I get after suspending. Otherwise they work fine.

gallenwolf, I havent tried 9.04, but I am using 8.10 and I am glad with it. The only trouble I have is this suspend thing and I don't know if that is due to the ati drivers or to something compiz related. I didn't try dual monitor either and, from what I hear, that might be an issue.

cheers

---

### Post by Chancey on 2009-04-29
> **gumbeto said:**
>  I didn't try dual monitor either and, from what I hear, that might be an issue.


Also running 9.04 on an XPS Studio 16, I have played a bit with dual monitor (only as a clone to a projector) but I have had no problems with it.  I am of course unable to resume from suspend or hibernate.  As with the rest I get either black screen or a cursor, and sometimes an inactive password prompt.  I'd love to hear anyones suggestions.

---

### Post by superbondbond on 2009-05-06
I also have this problem with a studio xps 16.

I broke down and removed the proprietary ATI driver, and suspend/resume works for me now.

Right now the ability to suspend/hibernate trumps the visual affects.

Hopefully [COLOR="RoyalBlue"][Bug 363533]("https://bugs.launchpad.net/ubuntu/+bug/363533")[/COLOR] will get a fix someday...

---

### Post by shrndegruv on 2009-05-06
> **superbondbond said:**
> I also have this problem with a studio xps 16.

I broke down and removed the proprietary ATI driver, and suspend/resume works for me now.

Right now the ability to suspend/hibernate trumps the visual affects.

Hopefully [COLOR="RoyalBlue"][Bug 363533]("https://bugs.launchpad.net/ubuntu/+bug/363533")[/COLOR] will get a fix someday...

can you handle the heat?  I found it to be unbearable...

---

### Post by krippa on 2009-05-06
Me too, for me 3D support is very important and so is sleep... For now I am forced to live without sleep. 

Out of curiosity, are you running on 64-bit ubuntu like I am?

---

### Post by superbondbond on 2009-05-06
> **shrndegruv said:**
> can you handle the heat?  I found it to be unbearable...
I usually sit at a table, or if I'm using my lap, I put the computer on a large hardcover book.
I do agree though, you could cook an egg on that guy.

> **krippa said:**
> ...are you running on 64-bit ubuntu....
Yes

---

### Post by jac_tict on 2009-05-18
Overheating is because opensource drivers lacks PowerPlay support (to reduce clock and core voltage when maximum performance are not needed).

Have you tried to manual downclock the GPU with ATIpower?

I want to buy a Studio XPS 16 but I will not until ATI doesn't solve standby issues or OS drivers don't implement a downclocking feature.

---

### Post by krippa on 2009-05-19
I am having no problems with neither heat nor fan noise running ATIs proprietary driver. Still though, sleep does not work.

---

### Post by Chancey on 2009-05-19
For the record, the suspend problems are NOT fixed with the latest ATI drivers (9.5).  Still resumes from suspend to a blank screen.

---

### Post by shrndegruv on 2009-05-19
> **Chancey said:**
> For the record, the suspend problems are NOT fixed with the latest ATI drivers (9.5).  Still resumes from suspend to a blank screen.

do the 9.5 drivers fix the jaunty issues people had been having around performance?

---

### Post by krippa on 2009-05-20
> **shrndegruv said:**
> do the 9.5 drivers fix the jaunty issues people had been having around performance?

I have now installed the 9.5 driver and gained some (for me at least) new insights.

The short answer is no, the performance issues I was experiencing have not been affected. These issues are however modest. What I notice is that it takes around a second for window actions such as maximize, unmaximize (minimize is instantaneous). This is a little annoying but not really a big issue for me. 

Further more it seems that these issues are related to compiz rather than ubuntu/xorg itself. This at least the case with the 9.5 driver. 

This is also true for suspend, which works great if I use metacity as window manager.

As for multiple screens the behavior has changed and I would call it an improvement. This is what I experienced regarding this:

- The keyboard button for switching between modes seems to work (even in Compiz!!) now which is great for having presentations etc. 
- The Display application under preferences now seems to work consistently across compiz/metacity. However many things have broken it seems and I am not able to use it to do advanced multi-screen settings.

---

### Post by superbondbond on 2009-05-21
> **krippa said:**
> Further more it seems that these issues are related to compiz rather than ubuntu/xorg itself. This at least the case with the 9.5 driver. 

This is also true for suspend, which works great if I use metacity as window manager.

I just confirmed the same behavior.

---

### Post by shrndegruv on 2009-05-21
> **superbondbond said:**
> I just confirmed the same behavior.

What I am gathering is that all the problems around maximize/minimize being slow are related to compiz, not to the ATI driver?  This would imply that it is safe to upgrade to jaunty; just don't use compiz?

---

### Post by superbondbond on 2009-05-21
> **shrndegruv said:**
> What I am gathering is that all the problems around maximize/minimize being slow are related to compiz, not to the ATI driver?  This would imply that it is safe to upgrade to jaunty; just don't use compiz?
That seems to be the case from what I'm seeing. At least in the case of the 9.5 version of the ATI driver. When krippa pointed that out yesterday, I immediately installed the latest driver, then turned off the visual effects. Since then I've had no performance issues (glxinfo reports back as it should with the proprietary driver), and suspend/resume work like they're supposed to.

Looks like [bug #363533]("https://bugs.launchpad.net/ubuntu/+bug/363533") might need to be re-examined to discuss Compiz.

---

### Post by krippa on 2009-05-21
> **superbondbond said:**
> Looks like [bug #363533]("https://bugs.launchpad.net/ubuntu/+bug/363533") might need to be re-examined to discuss Compiz.

More or less, but there are still some multi-screen issues left that needs to be taken care of. I will update that bug report soon.

---

### Post by krippa on 2009-05-21
A couple of days using ATI's 9.5 driver and I am inclined to go back to whatever is automatically installed because I am experiencing more issues with compiz now. With the default window manager metacity it still seems to work better but my general impression now is that the performance issues with compiz are worse and also I got a black screen twice and had to shut down my computer by force (ctrl+alt+backspace didn't work).

For me this is a stopper since I want compiz effects but foremost I want a stable system that I do not perceive as being annoyingly slow. I will stick with 9.5 for a while though to see if this impression changes...

---

### Post by zika on 2009-05-22
> **krippa said:**
> (ctrl+alt+backspace didn't work)
*simply use Alt(left)+SysRq(PrintScreen)+K*

---

### Post by krippa on 2009-05-22
> **zika said:**
> *simply use Alt(left)+SysRq(PrintScreen)+K*

To do what exactly? I have already reenabled the ctrl+alt+backspace function that was disabled in jaunty if that's what this is supposed to do.

Also, while ctrl+alt+backspace works like a sharm normally Alt(left)+SysRq(PrintScreen)+K hangs my computer with a black screen.

---

### Post by zika on 2009-05-22
> **krippa said:**
> To do what exactly? I have already reenabled the ctrl+alt+backspace function that was disabled in jaunty if that's what this is supposed to do.

Also, while ctrl+alt+backspace works like a sharm normally Alt(left)+SysRq(PrintScreen)+K hangs my computer with a black screen.
sorry to hear that... it works in my case ...

---

### Post by shrndegruv on 2009-05-23
> **superbondbond said:**
> That seems to be the case from what I'm seeing. At least in the case of the 9.5 version of the ATI driver. When krippa pointed that out yesterday, I immediately installed the latest driver, then turned off the visual effects. Since then I've had no performance issues (glxinfo reports back as it should with the proprietary driver), and suspend/resume work like they're supposed to.

Looks like [bug #363533]("https://bugs.launchpad.net/ubuntu/+bug/363533") might need to be re-examined to discuss Compiz.

Alright i tried an update to jaunty.  With no compiz/no effects at all it works fine; no performance issues.  As soon as I enable composite (on metacity or e16) I am back to where I started with unusable minimize/maximize/resize. 

So I am back on intrepid until all this gorp gets sorted.  In this case newer does not mean better, and I can do everything I need with Intrepid.

---

### Post by krippa on 2009-08-05
No change with the 9.7 driver on 64-bit Ubuntu 9.04 Jaunty. Resume still hangs the computer and I am not able to force restart of X server. Performance issues also remain.

Does anyone have any idea if this is likely to be fixed?

---

### Post by shrndegruv on 2009-08-05
> **krippa said:**
> No change with the 9.7 driver on 64-bit Ubuntu 9.04 Jaunty. Resume still hangs the computer and I am not able to force restart of X server. Performance issues also remain.

Does anyone have any idea if this is likely to be fixed?

the xserver with no back fill fixed my performance issues with 

ATI Technologies Inc Radeon Mobility HD 3670

---

### Post by toseethefruit on 2009-08-06
Hello, everyone,

I'm new here, and actually just migrated to Ubuntu (9.04, dual booting XP Professional) for the first time a few weeks ago. This forum has been a lot of help to me in figuring things out, so thank you all. I am running Ubuntu on a Dell Studio 15 and have been having the same problems as you all describe, especially with Suspend and Hibernate

I just wanted to post, though, following what Shrndegruv posted directly above, that "the xserver with no back fill fixed my performance issues with ATI Technologies Inc Radeon Mobility HD 3670," that I have done the following, which has solved the suspend/hibernate problem for me, even continuing to use Compiz (please note that I'm a Linux beginner, so to be precise and also for anyone else in my position as a beginner, I'm going to go through what made things work for me step-by-step):

1) I removed the ATI/AMD FGLRX driver that had been running my video card under Admin/Hardware Drivers
2) I ran lspci in Terminal and noted the graphics card (for me, a Radeon HD 3400)
3) I went to the AMD website at [http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx) and downloaded the Linux driver for the above-mentioned video card, which I had never realized was available. I then installed the driver, which comes with a nice GUI, following the instructions provided on the download website.

Suspend and Hibernate have since both worked through several tries, Compiz works like normal, and I even have a new ATI Control Center added to my Applications menu. While, as another poster mentioned, there is still a slight (perhaps 1.5 second) delay in maximizing windows (from Gnome Do Docky), the Suspend/Hibernate problem appears to have a fix right from AMD that works on my computer.

Does this work for anyone else? And please excuse the length of my post; like I said, I don't know at this point what's unimportant enough to leave out.

Thank you!

---

### Post by shrndegruv on 2009-08-06
> **toseethefruit said:**
> Hello, everyone,

I'm new here, and actually just migrated to Ubuntu (9.04, dual booting XP Professional) for the first time a few weeks ago. This forum has been a lot of help to me in figuring things out, so thank you all. I am running Ubuntu on a Dell Studio 15 and have been having the same problems as you all describe, especially with Suspend and Hibernate

I just wanted to post, though, following what Shrndegruv posted directly above, that "the xserver with no back fill fixed my performance issues with ATI Technologies Inc Radeon Mobility HD 3670," that I have done the following, which has solved the suspend/hibernate problem for me, even continuing to use Compiz (please note that I'm a Linux beginner, so to be precise and also for anyone else in my position as a beginner, I'm going to go through what made things work for me step-by-step):

1) I removed the ATI/AMD FGLRX driver that had been running my video card under Admin/Hardware Drivers
2) I ran lspci in Terminal and noted the graphics card (for me, a Radeon HD 3400)
3) I went to the AMD website at [http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx) and downloaded the Linux driver for the above-mentioned video card, which I had never realized was available. I then installed the driver, which comes with a nice GUI, following the instructions provided on the download website.

Suspend and Hibernate have since both worked through several tries, Compiz works like normal, and I even have a new ATI Control Center added to my Applications menu. While, as another poster mentioned, there is still a slight (perhaps 1.5 second) delay in maximizing windows (from Gnome Do Docky), the Suspend/Hibernate problem appears to have a fix right from AMD that works on my computer.

Does this work for anyone else? And please excuse the length of my post; like I said, I don't know at this point what's unimportant enough to leave out.

Thank you!

The driver you got from the website you posted is a closed source driver.  I believe it is one version above the one in the repos.  

The delay you mention wrt min/max windows will be fixed with the xserver no backfill ppa.  You can do a search in these forums/google and get the link.  Its really easy to do.  

I have a studio xps 16; suspend/hibernate does not work for me.  I might try the catalyst 9.7 driver just to see if i can get those nuggets.

welcome to ubuntu.  You must be extremely competent to have succesfully installed a driver by hand.  ;)

---

### Post by gumbeto on 2009-08-06
Hi there,

Same here: with 9.7, suspend still doesn't work (when coming back from it).

I never had the performance issues you mention, though.

Cheers

---

### Post by krippa on 2009-08-06
I can confirm that the xserver with no backfill patch worked for me to resolve all performance issues I had seen. I still can't get out of resume when I have compiz enabled though.

To install it add the repositories for the patch from [here]("https://edge.launchpad.net/~ubuntu-x-swat/+archive/xserver-no-backfill").

Then update the repositories, locate the packages: xserver-common and xserver-xorg-core in synaptics package manager and select upgrade to apply the patch. 

Reboot/restart X

---

### Post by krippa on 2009-10-29
I was hoping this would be fixed in Karmic but it is not...

Well, I might add that I experienced some instability to my system after installing the no backfill patch. I will run karmic for a while without compiz to see if it is still unstable before I reinstall the patch. Note that instability was only seen very rarely for me, though when it hit, everything froze...

---

### Post by shrndegruv on 2009-10-29
> **krippa said:**
> I was hoping this would be fixed in Karmic but it is not...

Well, I might add that I experienced some instability to my system after installing the no backfill patch. I will run karmic for a while without compiz to see if it is still unstable before I reinstall the patch. Note that instability was only seen very rarely for me, though when it hit, everything froze...

there is another no-backfill ppa for karmic...works fine for me

---

### Post by krippa on 2009-10-30
> **shrndegruv said:**
> there is another no-backfill ppa for karmic...works fine for me

For anyone trying to find it, don't go to the jaunty page that I linked to above since it has a source for karmic that will get you a 404 message. This one should work (although I am unable to access ubuntu key server to be able to install it at the moment):

[https://launchpad.net/~launchpad-weyland/+archive/xserver-nobackfill](https://launchpad.net/~launchpad-weyland/+archive/xserver-nobackfill)

/K

---

### Post by bmdavis on 2010-03-06
any indication this will be fixed in the next release?

---

### Post by krippa on 2010-03-06
It's actually working quite well in karmic already! I am using all kinds of effects with virtually no lag.

---

### Post by Ghost_Programmer on 2010-03-06
i have HD 3200. mine is a desktop with AMD Phenom X4. Ubuntu 9.10 is working fine with  fglrx driver.

---

### Post by cijucherian on 2010-06-15
I have fglrx driver installed on my ubuntu dell xps 16 (ati radeon hd 3670). I have installed no-backfill update so no performance issues. But lately, on opening some sites in Firefox (once in opera also), the compiz crashes and I am logged out of the system. 

Here is the pasty of the relevant dmesg
[http://pastebin.com/RR56CWPj](http://pastebin.com/RR56CWPj)

I have no clue as to how a crash could be activated by some page being opened in Firefox, but this behavior is reproducible. 

Could somebody help me with out with any details. Example, what IRQ 32 is. Or point me to a forum where I can get/post details about the problem.

---

### Post by cijucherian on 2010-06-15
Seems like Compiz is not causing the problem. Disabled Compiz, and the bug persists. Here is the log now.

[http://pastebin.com/i2LwbaTt](http://pastebin.com/i2LwbaTt)

This is the only information I get from dmesg.

---

### Post by venky80 on 2010-12-16
Could anyone tell me how does suspend and resume work with Mobility radeon ATI HD3670 with free ati drivers in ubuntu/kubuntu stable release.
Thanks

I have DELL STUDIO XPS 1640 WITH ATI HD3670

---

### Post by krippa on 2010-12-17
I can't remember having any issues with the last installs or even while upgrading to Maverick. You shouldn't have any problems I would imagine.

---

### Post by lpwaqas on 2011-09-16
I have this 3670 in one of my laptops; Dell xps-1640 and I installed the propriety driver from the administration > additional drivers with meerkat and it worked like charm.

With previous versions of ubuntu I had to manually install the driver; now the compiz works just fine and 3d is awsome no lags at all.

---

