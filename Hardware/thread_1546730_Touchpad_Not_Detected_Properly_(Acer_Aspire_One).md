---
title: "Touchpad Not Detected Properly (Acer Aspire One)"
date: 2010-08-05
forum: Hardware
---

### Post by BrokenKingpin on 2010-08-05
I am running Ubuntu 10.04 (and now 10.10) Desktop on my Acer Aspire One 532h-2807 netbook and I do not have the touchpad tab under the mouse preferences. The touchpad is working fine, but I want to play with the tapping settings.

When I run cat /proc/bus/input/devices I get the following:
```

I: Bus=0011 Vendor=0002 Product=0005 Version=0000
N: Name="ImPS/2 Generic Wheel Mouse"
P: Phys=isa0060/serio1/input0
S: Sysfs=/devices/platform/i8042/serio1/input/input11
U: Uniq=
H: Handlers=mouse1 event9 
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=103

```

So it seems to be recognizing it as a generic mouse instead of the synaptics touchpad. Anyone have any idea to get it detecting properly?

---

### Post by BrokenKingpin on 2010-08-06
anyone???

---

### Post by ubun_two on 2010-08-07
I have a similar issue on my Acer Aspire TimelineX 1835t, but I unfortunately have no solution yet.  Values are slightly different in my case, but either way, Alps touchpad is not recognized as such.

> I: Bus=0011 Vendor=0002 Product=0001 Version=0000
N: Name="PS/2 Generic Mouse"
P: Phys=isa0060/serio1/input0
S: Sysfs=/devices/platform/i8042/serio1/input/input5
U: Uniq=
H: Handlers=mouse0 event5 
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=3


---

### Post by MountainX on 2010-08-23
same problem here.
See [http://ubuntuforums.org/showthread.php?t=1559690](http://ubuntuforums.org/showthread.php?t=1559690)

I found this bug report:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/359363](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/359363)
But the devs closed the bug report for some reason...

---

### Post by BrokenKingpin on 2010-10-11
Has anyone resolved this yet? This is still an issue for me in 10.10.

---

### Post by BrokenKingpin on 2010-10-23
Bump. This is really starting to frustrate me. When I am typing my palm hits the touchpad and really screws up my typing.

Does anyone have any clue on how to go about resolving this?

---

### Post by p_code on 2011-01-12
> **BrokenKingpin said:**
> Bump. This is really starting to frustrate me. When I am typing my palm hits the touchpad and really screws up my typing.

Does anyone have any clue on how to go about resolving this?

I have a Gateway LT23 series Netbook which is also getting nailed badly by this same Ubuntu bug.

When I first discovered this, I didn't think it would turn out to be as big of deal as it is, but this bug has me ready to chuck Ubuntu, so I agree that this needs to be fixed NOW.

Yes the touchpad works, but because it's not properly recognized, you can't enable the touchpad specific options, like multi-touch and the all important 'disable touchpad while typing'.

It's now clear that this bug effects several models from more than one manufacture, and it is undoubtedly causing MAJOR aggravation to literally thousands of Ubuntu users, but Canonical it seems is too busy adding more cutesy 'skins' and other desktop GUI changes (which are absolutely worthless to me).

For the record, I use the simple familiar 'clear looks' theme, have moved the tray and start menus back to the bottom WHERE THEY BELONG, and could care less about further cutesy ipad-like 'refinements' to the GNOME desktop.  What I want is a nice solid usable machine, which doesn't crash, and which has stable drivers for modern peripheral devices. 

Call me eccentric, but I value simple things like being able to type without the cursor jumping all over the place randomly more than more upside down pastel brown B.S.

---

### Post by p_code on 2011-02-25
Someone else bumped this thread before, and I find that it needs to be bumped again.

Following the above linked bug threads indicates that this still hasn't been fixed.

One correction to the final impression given in the bug thread which is to the effect that "how can you blaim the pooooor developers just because they don't have access to every new type of hardware  . . ."

FACT:
Older versions of Ubuntu DO RECOGNIZE THESE "NEW" TOUCHPADS PROPERLY (as touchpad devices).

Can you say REGRESSION BUG boys and girls?

So what we REALLY seem to have here is the case where some 'helpful' developer wanted THEIR NEW TOY to be able to use all of its NIFTY NEW 'MULTI TOUCH' FEATURES IN UBUNTU and in the process of getting this garbage to work on THEIR ONE TYPE OF HARDWARE, he or she BROKE basic touch pad detection on many if not most other newer touchpads.

If you can't get 'multi-touch' working FINE, please at least provide support for easily reverting to the older drivers so the touch pad is detected.

I am typing this from UBUNTU, because that's where I have this Support Forum bookmarked, but my day to day OS is now back to Windows, because not being able to uses touchpad critical options like disabling the touchpad during typing and disabling tap to click, make Ubuntu TOTALLY UNUSABLE AND WORTHLESS.

SO THANKS A LOT FOR THE REALLY NASTY REGRESSION BUG - NOW PLEASE FIX THIS!

---

### Post by A4orce84 on 2011-02-26
bump

---

### Post by BrokenKingpin on 2011-03-01
Does anyone know if any other distro has this resolved. I am willing to ditch Ubuntu for another distro that has this working.

---

### Post by MountainX on 2011-03-01
> **BrokenKingpin said:**
> Does anyone know if any other distro has this resolved. I am willing to ditch Ubuntu for another distro that has this working.

You have the touchpad working, but you want to access advanced settings, right? 

I believe you can do that in Ubuntu with some effort. Unfortunately, I can't give you specific steps because I have not done it myself.

If you want to try other distros, look into openSUSE or Linux Mint. If you try openSUSE, give KDE a try. It might have additional tools for the touchpad (just guessing). Good luck. Let us know what you find out.

---

### Post by MountainX on 2011-03-01
> **p_code said:**
> 
FACT:
Older versions of Ubuntu DO RECOGNIZE THESE "NEW" TOUCHPADS PROPERLY (as touchpad devices).



How do you know that? If you have an older version that recognizes the touchpad on the same computer, I suspect it would be easy to find a solution. We would look at the driver(s) and settings that the touchpad uses in the prior version of Ubuntu. Then we would load that same driver and the settings in the recent version of Ubuntu. I'm not an expert on this, but I suspect we could all figure it out from the starting point of a working system. So if you can get the touchpad working with all features on an old version of Ubuntu, let us know.

---

### Post by p_code on 2011-03-02
> **MountainX said:**
> How do you know that? If you have an older version that recognizes the touchpad on the same computer, I suspect it would be easy to find a solution. We would look at the driver(s) and settings that the touchpad uses in the prior version of Ubuntu. Then we would load that same driver and the settings in the recent version of Ubuntu. I'm not an expert on this, but I suspect we could all figure it out from the starting point of a working system. So if you can get the touchpad working with all features on an old version of Ubuntu, let us know.

Here is [another post]("http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg2432385.html") that confirms that this worked in the previous release, but got broken in Lucid

Here's the full link -

[http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg2432385.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg2432385.html)

Unfortunately, if you read the above post, you will see that it's not just a simple matter of reverting the driver because the current version of Ubuntu has ditched HAL and uses a different method of detecting and loading the touchpad driver.

---

### Post by p_code on 2011-03-02
> **MountainX said:**
> You have the touchpad working, but you want to access advanced settings, right? 

I believe you can do that in Ubuntu with some effort. Unfortunately, I can't give you specific steps because I have not done it myself.

If you want to try other distros, look into openSUSE or Linux Mint. If you try openSUSE, give KDE a try. It might have additional tools for the touchpad (just guessing). Good luck. Let us know what you find out.

That's right, it's just an 'advanced' feature so everyone should quit whining right?

The only problem is that if you have a NETBOOK, then not having access to the 'advanced' feature that lets you disable the touchpad during typing will cause you to want to chuck Ubuntu in the nearest garbage can pretty quickly.

Unlike larger Laptop PC's, on a Netbook the tight physical spacing of the keyboard and touchpad puts the damn thing DIRECTLY under your thumbs while typing, and the problem of it getting brushed accidentally is about 400 times worse than on a larger machine.

Also without the correct driver loaded, touchpads that work flawlessly in Windows7 seem to suddenly flake out and refuse to work at all for no reason, requiring a complete power down to reset.

This is NUTS!  Ubuntu invested tens of thousands of hours to invent a so-called 'Netbook Edition', but then doesn't bother to fix a simple bug that makes their Ubuntu 10 release essentially WORTHLESS on a very large percentage of Netbooks?

How dumb is that?

---

### Post by BrokenKingpin on 2011-04-04
Good news, I tried the Ubuntu 11.04 Beta 1 and the issue is fixed!

---

### Post by p_code on 2011-05-11
> **BrokenKingpin said:**
> Good news, I tried the Ubuntu 11.04 Beta 1 and the issue is fixed!

No it's BAD NEWS because no one has bothered to fix this in 10.04 LTS.

The fact that they now obviously know how to fix this, but haven't bothered to fix it in the mainstream LTS release, is ridiculous.

L-T-S stands for (L)ong (T)erm (S)upport, so it's total B.S. to expect people to load a flaky 'beta' version to have a serious bug fixed.

This isn't a 'new feature' - IT'S A BUG, SO, NOW THAT THE FIX IS KNOWN, IT NEEDS TO BE FIXED IN THE MAINSTREAM LTS RELEASE.

---

### Post by RockTeam on 2011-05-12
I'm fully agree with p_code. I don't want to upgrade to 11.xx because I like my current version of Ubuntu. And LTS it's should be true.

---

### Post by p_code on 2011-05-21
Ubuntu 10.04 

My Ubuntu 10.04 installation is current, and system update reports 'system up to date'

So I open an terminal and run -  cat /proc/bus/input/devices

result - 

I: Bus=0011 Vendor=0002 Product=0005 Version=0000
N:** Name="ImPS/2 Generic Wheel Mouse"**
P: Phys=isa0060/serio1/input0
S: Sysfs=/devices/platform/i8042/serio1/input/input9
U: Uniq=
H: Handlers=mouse1 event9 
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=103

So my touchpad is STILL being incorrectly detected as a "PS/2 Generic Wheel Mouse"

So, naturally, I am rather curious as to the justification for changing the category of this bug to "SOLVED"?

Perhaps the clever individual responsible for assigning this bug as 'SOLVED' can explain it.

Let's see - the problem reported was that touchpads are not properly detected in Ubuntu 10.04 

My Ubuntu 10.04 system now reports that it is 'up to date' and clearly the touchpad is still being incorrectly detected as a Generic PS/2 mouse device.

Sorry if I seem to be harping out this, but time and again I have seen perfectly valid bugs reassigned as 'SOLVED' and blown off by the Ubuntu development team.

- I can't reproduce it on my specific hardware (though 5000 other people can) -> "SOLVED"
- Sounds kind of like another bug somewhere that was already blown-off -> "SOLVED"
- Sort of works some of the time, for some people (maybe) -> "SOLVED"
- Get's sucessfully ignored for several weeks (so it must ok by now, right?) -> "SOLVED"

I would say 'grow up and act like professionals', but sadly this is exactly the kind of garbage that often goes on in 'for profit' software development organizations; so, all I will say is that I had hoped for more from the Ubuntu team.

---

### Post by Mattlcape on 2011-08-01
Bump. Fix needed also for Samsung NF110

---

### Post by psychoelf on 2011-09-05
How is this solved? Still exists on a new install of 10.10 with updates.

---

### Post by psychoelf on 2011-09-06
And tried upgrading my wifes Acer Aspire One to 11.04 and it does have touchpad settings...that don't work.  If you disable touch to click it still ends up reading clicks if you don't press hard when dragging your finger.  

THIS IS NOT SOLVED.  If it is, please tell me how.

---

### Post by BrokenKingpin on 2011-09-08
You guys are correct, it is not solved. It appeared to work in the beta, but I only checked that the touchpad tab was showing in the mouse settings, but it still does not work.

The bug is confirmed, and is a kernel issue:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/737051](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/737051)

From there there is also an attached kernel bug. I have tried the latest kernel available in the 11.10 version, but still has not fix.

This is very frustrating.

---

### Post by sciwhiz on 2011-09-12
Bump

Using Kubuntu 10.04 with all the updates. Still can't access the touchpad section in the system settings, and xinput list still reports as a generic PS/2 mouse. This is on an acer aspire 1430.

---

### Post by RetainYerDiggity on 2011-09-24
Toshiba Satellite, touchpad was working fine for a long time, now it's stopped.  I think it broke when I added nautilus "open terminal here" right-click menu option.

cat /proc/bus/input/devices shows a
Name="PS/2 Synaptics TouchPad" 

System-Preferences-Pointing devices does nothing useful

grr

---

### Post by Clicksights on 2011-09-27
bumb

using NETbook (MSI wind) it works perfect, using NOTEbook (MSI X460DX) it doesn't work
both running 11.04! 

Maybe a good idea to make one topic about these touchpad/mouse problems!
And make it a sticky!
It seems to be a really big problem for a lot of laptops.

[http://ubuntuforums.org/showthread.php?t=1841660](http://ubuntuforums.org/showthread.php?t=1841660)
[http://ubuntuforums.org/showthread.php?t=1772092](http://ubuntuforums.org/showthread.php?t=1772092)
[http://ubuntuforums.org/showthread.php?t=1850443](http://ubuntuforums.org/showthread.php?t=1850443)
[http://ubuntuforums.org/showthread.php?t=1734886](http://ubuntuforums.org/showthread.php?t=1734886)
[http://ubuntuforums.org/showthread.php?t=1546730](http://ubuntuforums.org/showthread.php?t=1546730)
[http://ubuntuforums.org/showthread.php?t=1839100](http://ubuntuforums.org/showthread.php?t=1839100)

Too just name a few from the last day alone!!!
This is crazy! 
There must be a better solution than no solution!

(this means 5 years times 365 days times (say) 5 people with a touchpad problem = over 9000 people with problems....)

---

### Post by marks11marks on 2011-10-03
I have an Acer aspire 1 with n450 532.  New to ubuntu with 11.04 natty narwhal.  Touchpad problems.  Also sleep/hibernate issues.  Anyone have a clue... I don't.

---

### Post by CaKiwi on 2011-10-18
I have the same problem. The touchpad on my Toshiba C655 is recognized as a PIXART USB OPTICAL MOUSE. (On a Toshiba N255 netbook it is recognized correctly). It works but is extremely sensitive and cannot be adjusted. Has this been resolved?

---

### Post by donnybud on 2011-10-21
> **BrokenKingpin said:**
> Bump. This is really starting to frustrate me. When I am typing my palm hits the touchpad and really screws up my typing.

Does anyone have any clue on how to go about resolving this?

I found this while I was trying to restart my Aspire One touchpad.

Click on the little symbol at the top of your screen, just to the right of your logged in name.
Click the SYSTEM SETTINGS choice in the drop down menu.
Choose HARDWARE from the left of that window, and you'll get another window.
Click on MOUSE.
That window will have three tabs, the last one being TOUCHPAD. Choose it. Check the box to Disable Touchpad While Typing.

What this does is turn off the Touchpad wilist you are typing and after a short pause in your typing it turns back on, then off when you resume typing.

---

### Post by donnybud on 2011-10-21
> **RockTeam said:**
> I'm fully agree with p_code. I don't want to upgrade to 11.xx because I like my current version of Ubuntu. And LTS it's should be true.


I am running 11.4 (Natty) on my Aspire One 521, before I upgraded my touchpad worked fine. Because of it being too sensitive to accidental touches (I didn't know about the option to turn it off while typing, at the time), I started using a Mouse that uses a USB dongle. Then came the upgrade (?) and my Touchpad is no longer servicable.

Any ideas?  Is it possible to downgrade?

---

### Post by BrokenKingpin on 2011-10-26
Okay, I finally have a fix.

The fix was reported in this bug report (post #57):
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/737051](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/737051)

I downloaded and installed the following .deb package in Xubuntu 11.10:
[http://people.canonical.com/~sforshee/alps-touchpad/psmouse-alps-0.10/psmouse-alps-dkms_0.10_all.deb](http://people.canonical.com/~sforshee/alps-touchpad/psmouse-alps-0.10/psmouse-alps-dkms_0.10_all.deb)

After rebooting my scrolling worked fine, and the touchpad can now be configured.

I installed gpointing-device-settings and it allowed me to turn off tap to click, which did not work before the patch. The only issue was that the settings did not stick after rebooting. I was able to fix this by running the following command on startup (through the Xfce control panel):
```

xinput set-int-prop "AlpsPS/2 ALPS GlidePoint" "Synaptics Tap Time" 32 0

```

Just replace "AlpsPS/2 ALPS GlidePoint" with the name of your touchpad, which you can get from gpointing.

Hope this helps, it has made my netbook far more usable. Hopefully this patch will makes it in the repos soon. I am marking this as solved as the fix is good enough for me.

---

### Post by psychoelf on 2011-10-26
What about disabling while typing?  And disabling tap to click?

---

### Post by BrokenKingpin on 2011-10-27
I know that disabling tap to click works, as that is what I did. I didn't try the disable while typing, but a person in that bug report mentioned that it was resolved with the patch.

---

### Post by psychoelf on 2011-11-01
Confirmed working.  I tested the patch on my wife's netbook.  No more tap to click and my palms don't cause the typing to go nuts anymore.  Big hands little keyboard = bad.

---

### Post by BrokenKingpin on 2011-11-02
Glad to hear that it worked for you... it really does make a huge difference.

---

### Post by p_code on 2012-01-04
If this patch does work, why hasn't it been cleaned up as needed and rolled into the mainstream 10.04 LTS release?

---

### Post by siersmak on 2012-03-15
Nevermind...

---

### Post by siersmak on 2012-03-16
Turns out I am having similar problems as to those discussed in this thread on 11.10 with a new Sony Vaio VPCSA laptop.  Ubuntu is treating my touchpad as an ImPS/2 Generic Wheel Mouse so I am unable to configure it.  The only configuration option I am interested in is the ability to turn the touchpad off while typing.  I've followed the instructions in [http://ubuntuforums.org/showpost.php?p=11397628&postcount=30](http://ubuntuforums.org/showpost.php?p=11397628&postcount=30) but when I reboot, gpointing-device-settings still shows only the ImPS/2 Generic Wheel Mouse.  I have booted with the i8042.nopnp option and even added the i8042.reset i8042.nomux i8042.noloop options, but those don't make a difference.  It sounds like the psmouse-alps module has helped everyone to  be able to configure their touchpad, but I must be missing something.

---

### Post by earthmeLon on 2012-04-15
> **siersmak said:**
> Turns out I am having similar problems as to those discussed in this thread on 11.10 with a new Sony Vaio VPCSA laptop.  Ubuntu is treating my touchpad as an ImPS/2 Generic Wheel Mouse so I am unable to configure it.  The only configuration option I am interested in is the ability to turn the touchpad off while typing.  I've followed the instructions in [http://ubuntuforums.org/showpost.php?p=11397628&postcount=30](http://ubuntuforums.org/showpost.php?p=11397628&postcount=30) but when I reboot, gpointing-device-settings still shows only the ImPS/2 Generic Wheel Mouse.  I have booted with the i8042.nopnp option and even added the i8042.reset i8042.nomux i8042.noloop options, but those don't make a difference.  It sounds like the psmouse-alps module has helped everyone to  be able to configure their touchpad, but I must be missing something.

Did you ever figure this out?

---

### Post by siersmak on 2012-04-15
> **earthmeLon said:**
> Did you ever figure this out?

No, I wish.  I'm currently disabling the touchpad when a USB mouse is plugged in using udev, but that's a temporary fix with hopes that the touchpad will be fully tweakable in 12.04.  

I'm also testing and tweaking AureiAnimus' scripts at [http://ubuntuforums.org/showpost.php?p=10869949&postcount=8](http://ubuntuforums.org/showpost.php?p=10869949&postcount=8), but I'm not fully happy with them.  I wish I didn't have to setup a keyboard shortcut to get them working when I first login, and I've been trying different delays in toggling it on/off that are less than 1.0 because 1 second is too long to wait for the touchpad to become active again after I stop typing, but AureiAnimus said using values less than 1.0 could open up a bug.

---

### Post by earthmeLon on 2012-04-15
Well, if you haven't tried sforshee's package/patch psmouse-alps-dkms, maybe give it a try.

He has multiple version available on [this cononical page]("http://people.canonical.com/~sforshee/alps-touchpad/"). Start with .10, and I'm pretty sure there is no reason to try any previous versions.

Although there are many threads discussing this problem and this patch, the one I've found most enlightening is [this one]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/550625").

If you're willing to give it a try, please report back with your experience, either good or bad, to help in his endeavor.

---

### Post by siersmak on 2012-04-23
> **earthmeLon said:**
> Well, if you haven't tried sforshee's package/patch psmouse-alps-dkms, maybe give it a try.

He has multiple version available on [this cononical page]("http://people.canonical.com/~sforshee/alps-touchpad/"). Start with .10, and I'm pretty sure there is no reason to try any previous versions.

Although there are many threads discussing this problem and this patch, the one I've found most enlightening is [this one]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/550625").

If you're willing to give it a try, please report back with your experience, either good or bad, to help in his endeavor.

I tried psmouse-alps-dkms-0.10 out previously without success, on both my SA (xinput says Touchpad == ImPS/2 Generic Wheel Mouse) and my VPCF121GX (xinput says Touchpad == AlpsPS/2 ALPS GlidePoint).  

For kicks I'm trying it out again on the VPC with 12.04beta and kernel 3.2.0-23-generic and installing using dpkg -i dkms.  No good, I get a compile error.  I found a fix at [http://ubuntuforums.org/showpost.php?p=11853192&postcount=13](http://ubuntuforums.org/showpost.php?p=11853192&postcount=13).  I appreciate sforshee's work but it seems like he could post a 0.11 version of his package with this simple fix so people like me wouldn't have to search for how to fix it.

I've rebooted after running through z4k4ri4's instructions in the post I just mentioned.  I've confirmed that the psmouse-alps-dkms driver is being used with modinfo.  The touchpad does correctly respond to vertical scrolling and double clicks, which is nice, but it doesn't get disabled while typing even though I have that option selected in the GNOME System Settings -> Mouse and Touchpad -> Touchpad window.

Too bad.

---

