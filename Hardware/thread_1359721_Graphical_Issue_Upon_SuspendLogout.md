---
title: "Graphical Issue Upon Suspend/Logout"
date: 2009-12-20
forum: Hardware
---

### Post by cajual on 2009-12-20
I just picked up a new Laptop; [http://www.newegg.com/Product/Product.aspx?Item=N82E16834114719&cm_re=a505-_-34-114-719-_-Product](http://www.newegg.com/Product/Product.aspx?Item=N82E16834114719&cm_re=a505-_-34-114-719-_-Product)

*Update!* I have the **same issue** as this individual: [http://ubuntuforums.org/showthread.php?p=8536868](http://ubuntuforums.org/showthread.php?p=8536868)

> 
[http://www.nvnews.net/vbulletin/showthread.php?t=139657](http://www.nvnews.net/vbulletin/showthread.php?t=139657)
[http://www.nvnews.net/vbulletin/showthread.php?t=141204](http://www.nvnews.net/vbulletin/showthread.php?t=141204)
[http://www.nvnews.net/vbulletin/showthread.php?t=138205](http://www.nvnews.net/vbulletin/showthread.php?t=138205)

All these people have the same issue.  I think we need a fix for this growing problem -- reported as early as **OCTOBER 2009**!!!
It has an nVidia GT 230M graphics card, and I recently popped in the 190.xx stable drivers from their website.  This issue has occurred on both the 185.xx and now 190.xx drivers.

When I log out, or suspend my laptop, the graphics turn fuzzy, like a bad porno on rabbit ears.  I can still use the laptop fine, but it just looks terrible.  I checked the nVidia X Server Settings, and it says it detects my monitors EDID just fine, and I don't have any display issues upon resume, it just looks bad.  On initial boot and after hibernate, everything is fine as well.  Any ideas?

> 
There is already a bug submission, let me link you to it so you can register and let them know it affects you too:
 
[https://bugs.launchpad.net/ubuntu/+s...80/+bug/482456]("https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/482456")
_**Fixes tried:**_
Manually setting DPMS on and off.
Manually setting the EDID grep'd from windows using SoftMCCS.
Using completely minimal xorg.conf.
Manually issuing "on startup" HAL service.
Using 185.xx, 190.xx, 195.22 & **195.30** nVidia drivers.
Using the "6 screen" fix.
Using "suspend 2" in place of the standard suspend/logout.
Using "sleep.sh" instead of suspend.
Removed *vbetool* to no avail.
/etc/init.d/gdm restart failed.
**New**: sudo nvidia-xconfig --no-nvagp did nothing.
**New**: Option "AddARGBGLXVisuals" "True" and Option "AddARGBVisuals" "True" had no effect.

*None of these worked!*

**The issue does not exist if I uninstall the nVidia drivers, so this is a DRIVER SPECIFIC ISSUE.**

---

### Post by cajual on 2009-12-20
Help?

---

### Post by cajual on 2009-12-21
Well I have isolated it to nVidia drivers.  If I restart the X-Server without the drivers installed or activated, the issue doesn't occur.  If I do it with the drivers installed the issue occurs.  This includes 185-190 drivers.  Also, I have figured out that the issue occurs during:

1. CTRL+ALT+F1
2. Suspend
3. Logout

The fuzzy/shaky graphics get worse from left to right as well.

Anyone have any ideas?

---

### Post by cajual on 2009-12-21
I can confirm that 195.22 does not fix the issue.  Again when I uninstalled the nVidia drivers, the issue went away.  Upon installation of the new drivers, the same error occurred again.

---

### Post by cajual on 2009-12-21
I tried Egghead's fix for Sony Vaio computers, but it doesn't have any effect on the display issues.  Forcing the EDID did nothing.

Is it just bad hardware+driver setup?

---

### Post by badllama77 on 2009-12-21
I am having the same problem with my Toshiba A505 with gt230m.  I tried latest beta and the problem persists.  I submitted a bug to nvidia using the procedure from the manual.  I haven't heard anything from nvidia yet.

---

### Post by cajual on 2009-12-21
> **badllama77 said:**
> I am having the same problem with my Toshiba A505 with gt230m. I tried latest beta and the problem persists. I submitted a bug to nvidia using the procedure from the manual. I haven't heard anything from nvidia yet.
 
 
There is already a bug submission, let me link you to it so you can register and let them know it affects you too:
 
[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/482456](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/482456)

---

### Post by cajual on 2009-12-22
Bumping for knowledge.

---

### Post by cajual on 2009-12-22
Bump until a solution.

---

### Post by cajual on 2009-12-22
[http://www.nvnews.net/vbulletin/showthread.php?t=139657](http://www.nvnews.net/vbulletin/showthread.php?t=139657)
[http://www.nvnews.net/vbulletin/showthread.php?t=141204](http://www.nvnews.net/vbulletin/showthread.php?t=141204)
[http://www.nvnews.net/vbulletin/showthread.php?t=138205](http://www.nvnews.net/vbulletin/showthread.php?t=138205)

All these people have the same issue.  I think we need a fix for this growing problem -- reported as early as **OCTOBER 2009**!!!

---

### Post by cajual on 2009-12-22
Bump.

---

### Post by cajual on 2009-12-22
Bump... Anyone have any input?

---

### Post by cajual on 2009-12-22
Trying now with the new 195.30 drivers.

[http://www.nvnews.net/vbulletin/showthread.php?t=142929](http://www.nvnews.net/vbulletin/showthread.php?t=142929)

---

### Post by cajual on 2009-12-22
195.30 Fixed some issues with the nvidia-settings config, but we still have fuzzies!

---

### Post by sleepee on 2009-12-23
i'm pretty much a linux noob, so i probably won't have anything constructive to add as far as fixing the problem... but i have the exact same video card, with the exact same problem...
even though i am using version 185 of the driver.. i'll see if upgrading the driver will have any effect tomorrow..

---

### Post by iponeverything on 2009-12-23
Everyone with this problem should note that they are affected on the launchpad bug report mentioned by cajual. This will help raise the profile of bug.

---

### Post by cajual on 2009-12-23
> **iponeverything said:**
> Everyone with this problem should note that they are affected on the launchpad bug report mentioned by cajual. This will help raise the profile of bug.

This is exactly what should be done to raise awareness about the problem.  With a laptop and multiple accounts, I am almost forced to use windows because of this error.

---

### Post by cajual on 2009-12-24
Bump

---

### Post by cajual on 2009-12-24
Bump

---

### Post by cajual on 2009-12-25
I know I am being annoying, but bump for any workaround.

---

### Post by cajual on 2009-12-25
Updated some workaround attempts.

---

### Post by cajual on 2009-12-26
Bump.

---

### Post by cajual on 2009-12-28
Amy updates?

---

### Post by cajual on 2009-12-28
Still searching for help.

---

### Post by sleepee on 2009-12-31
so what's the next step here?  we have a launchpad report, and nvidia seems to be aware of the bug...  is there anything else we can do??

---

### Post by cajual on 2010-01-03
> **sleepee said:**
> so what's the next step here?  we have a launchpad report, and nvidia seems to be aware of the bug...  is there anything else we can do??

Guess not :)

---

### Post by sleepee on 2010-01-09
so i was just checking the nvidia linux forums..
apparently this issue is supposed to be solved in a future 195.xx driver release, according to nvidia..

[http://www.nvnews.net/vbulletin/showthread.php?t=141204&page=3](http://www.nvnews.net/vbulletin/showthread.php?t=141204&page=3)

woohooo!!!!  can't wait!!!

---

### Post by MoGa on 2010-01-09
The problem still exist even with the 195 beta driver my Nvidia is GeForce GTS 250M

Exactly the same problem .. only occur when I switch to Alt+fX console or logout / suspend.

---

### Post by sleepee on 2010-01-10
> **MoGa said:**
> The problem still exist even with the 195 beta driver my Nvidia is GeForce GTS 250M

Exactly the same problem .. only occur when I switch to Alt+fX console or logout / suspend.

well, the guy said a "future 195.xx driver release", so i'm guessing he doesn't mean the current 195.30 beta driver...
we might have to wait until the next driver after that, but i hope i'm wrong...  :grin:

---

### Post by Que20 on 2010-01-16
I have the same problem and it is very troublesome (Asus N71VN, GT 240M).

 Think of you that it is the equipment or righteous man driver it?

---

### Post by defaria on 2010-02-05
A work around that's working for me is to hibernate instead of suspend. Ugly but works for now. We need this fixed though!

Interesting. If you drop to a (fuzzy) command console with Ctrl-Alt-F1 and do a hibernate --force you'll hibernate. When you come back you'll be placed in this command console unfuzzy. You can Ctrl-Alt-F7 to get back to the GUI. 

It must be something when booting up that resets the monitor such that there is no shakiness as the grub menu comes up clean. Whatever that resetting code is needs to be put into the driver when the user suspends or goes to a command console or basically when the video mode changes. Nvidia engineers need to fix this! How do we let them know about this important data point?

---

### Post by sleepee on 2010-02-08
hey guys, the fix is here!!!!! the new 195.36.03 drivers fix this problem!!!!
well, at least according to nvidia, and another user who says it works for him..  i might as well try it out right?

you can download it here:
[ftp://download.nvidia.com/XFree86/](ftp://download.nvidia.com/XFree86/)

now if anybody could give this noob here a little walkthrough on how to install this thing, i'd very much appreciate it... seeing as nvidia makes their driver installation very noob unfriendly.

btw, i got the link from the nvidia forums... from here:
[http://www.nvnews.net/vbulletin/showthread.php?t=141204&page=3](http://www.nvnews.net/vbulletin/showthread.php?t=141204&page=3)

EDIT:  tried it out... it works!!!
now, when i close the laptop and open it again (suspend), i get no more fuzziness!!
But i still get the garbage graphics on shutdown splash screen... i mean, it's not THAT big a deal, because it doesn't really affect functionality or anything, but it's not exactly eye-pleasing or attractive to look at...
oh, and i also get this green nvidia splash screen for a split second right before the login screen.. but again, it's not that big a deal.  it's only for a split second..
but it's still something nvidia should fix so their product will look polished and work like it should..

---

### Post by defaria on 2010-02-10
Yippie! I'm up too.

Here's a tip: Sometimes I boot (well my desktop but I guess this could also happen on the laptop) and get a dialog box saying there was a problem and Ubuntu is running in low graphics mode. You can start a root shell to fix things. So I put these NVIDIA...run files in /root so I can install the driver again.

Now onto other problems like:

. Getting the mic to work
. Getting sound out the HDMI port
. Getting Bluetooth stereo headset to work
. Getting the finger print reader to work
. Getting the TV tuner to work
...

---

### Post by sleepee on 2010-02-10
> **defaria said:**
> Yippie! I'm up too.

Here's a tip: Sometimes I boot (well my desktop but I guess this could also happen on the laptop) and get a dialog box saying there was a problem and Ubuntu is running in low graphics mode. You can start a root shell to fix things. So I put these NVIDIA...run files in /root so I can install the driver again.

Now onto other problems like:

. Getting the mic to work
. Getting sound out the HDMI port
. Getting Bluetooth stereo headset to work
. Getting the finger print reader to work
. Getting the TV tuner to work
...

still no luck with that bluetooth i see.. or with anything else apparently..  i really wish i could help.  it sucks being a noob though..
and you got a fingerprint reader on your dv7!?  im jealous  lol!

anyway, just out of curiosity, do you also still get the garbage graphics on the shutdown ubuntu splash screen??  or is that just me?
btw, there were like 3 .run files that nvidia had there..
pkg0.run, pkg1.run, and pkg2.run
would you happen to know if there was a specific one we were supposed to choose?? because i only installed pkg0.run

---

### Post by defaria on 2010-02-13
Yeah I definitely added the fingerprint reader. Works like a champ under Windows 7. They even have something where you can register your finger print for web sites. So I just bop over to my WF bank site, slide my finger and I'm in. Definitely cool. If I do get the finger print reader working in Ubuntu I wonder if it'll only be for log in...

Yes I still get garbage at the bottom of the X logout screen. It looks a little different but really who cares?

I believe I read (what the README? Who woulda thunk it!) where it said that the .2 was the one to use or that it would work with anything. The .2 was bigger. It worked fine for me...

Ok, some research here. According to [ftp://download.nvidia.com/XFree86/Linux-x86_64/195.36.03/README/README.txt](ftp://download.nvidia.com/XFree86/Linux-x86_64/195.36.03/README/README.txt) under Chapter 3 Selecting and Downloading the NVIDIA Packages for Your System it states:

[INDENT]The package suffix ('-pkg#') is used to distinguish between packages containing the same driver, but with different precompiled kernel interfaces. The file with the highest package number is suitable for most installations.[/INDENT]

So I went with the .2 package...

I also have the webcam and internal mic. I wanted to use Skype. On my desktop my external mic doesn't work at all. On the laptop, initially the mic worked but in an effort to resolve other sound issues I updated that driver. The mic broke! Again, in Windows everything works fine. I'm no Windows aficionado or zealot. I'm a Linux guy. And I want to jettison Windows. But come on people, you need to get up to the (I hate to say it) quality of Windows first. Surely we can kick their a$$es! Let's get this stuff working!

---

### Post by defaria on 2010-02-14
OK so having no more fuzzy problems is great. Now I can kinda use Linux most of the time. The things that are keeping me from removing the Windows 7 installation are getting smaller and smaller. Now what I'd really like to get working are:

. HDMI sound - video works but sound does not go down the HDMI cable
. TV Tuner. I ordered the card. Works in Windows - doesn't work in Ubuntu.

The other things I'm struggling with are the finger print reader and headphones - neither are show stoppers - both would be nice however.

Back to the issue at hand however. From what I've read somewhere else, having sound going down the HDMI cable is the responsibility of the NVidia drivers(?). I'm kinda surprised by that and would have though it was a sound driver issue. In any event, HDMI sound is broken. If it's a task for the NVidia driver then that NVidia driver is broken. 

Thoughts.

---

### Post by seenthelite on 2010-03-20
I have noticed some of these issues have been addressed in 10.04 Beta 1

---

