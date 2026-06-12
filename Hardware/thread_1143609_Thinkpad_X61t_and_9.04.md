---
title: "Thinkpad X61t and 9.04"
date: 2009-04-30
forum: Hardware
---

### Post by Jofarmer on 2009-04-30
I recently got myself a X61t and now installed 9.04 on it. Pretty much everything works, albeit with problems:

_**Thinkfinger:**_
As suggested in both wikis (ubuntu & thinkwiki) I installed the patched version from the launchpad ppa by Jon Oberheide. Now on login and when sudo-ing I get asked for a "password or finger swipe" but only a password will work. This may be because the --adduser option does not work:```
~$ tf-tool --adduser *[me]*

ThinkFinger 0.3 (http://thinkfinger.sourceforge.net/)
Copyright (C) 2006, 2007 Timo Hoenig <thoenig@suse.de>

Two output paths specified, but you may only specify one:
  --adduser
  *[me]*

```

_**Tablet functions:**_
I can use the pen without problems. Touch input does not work (would have been a nice gadget, but not THAT important - I hope it will work some time in the future, though) and the eraser end of my stylus does not work (at least not in xournal or in inkscape) which is more of a concern. But most importantly no method of screen rotation works. Going manually over System -> Einstellungen -> Anzeige (German, should make: system -> settings -> monitor/screen or something like it in English) lets me rotate it exactly once and then the panel applets tells me screen rotation is not supported. I have to close and restart the app the rotate back. Not to talk about some form of auto-rotation.

And then of course pen input does not work any more, the mouse pointer is somewhat mirrored over the centre from where the pen is.

Yes, there ARE how-to's for this. But they all require editing my xorg.conf - which is a no-go from 9.04 on if I read the reports correctly - or [compiling a kernel module]("http://ubuntuforums.org/showpost.php?p=7093065&postcount=104") which seems a lot like open heart surgery to me.

I mostly got the x61t because of its perceived good compatibility with ubuntu, but right now it's not really usable as a tablet.

Also I got used to translucent Terminal windows, and the x3100 has no hardware acceleration in 9.04. (a little too much bleeding edge for my taste, btw.)

Maybe other users of this laptop could post their experiences with Jaunty here or better yet, how to use the full potential of the x61t in Ubuntu 9.04.

---

### Post by Favux on 2009-04-30
Hi Jofarmer,

I believe the X61t is a serial tablet pc.  If so you do not need to compile linuxwacom as gali98's tutorial does.  Only usb tablet pc's need the linuxwacom kernel driver wacom.ko.

In Jaunty (9.04) you no longer use xorg.conf.  Instead the HAL/.fdi file method is used.  Unfortunately there is a problem.  The callout in the .fdi file returns HAL/D-BUS names which are not recognized by linuxwacom.  Hence xsetwacom commands (wacom device rotation) and wacomcpl don't work.  While we are waiting for that to be fixed there are a three work arounds you can use.

Jaunty Users near the top of this HOW TO explains two of the work arounds:  [http://ubuntuforums.org/showthread.php?t=1038949](http://ubuntuforums.org/showthread.php?t=1038949)  In the first option all you need to do is install rec's script (called haltowacom).  You can ignore all the other stuff.  Then go to section 3 on the first page to calibrate with wacomcpl.  The included 10-wacom.fdi in Jaunty should work with a serial tablet pc.

Or if you want to use xorg.conf you could compile 0.8.3-2 (oops, open heart surgery!).  But at least you don't have to worry about the kernel driver.

The other way is to follow rec's and Tom Jaeger's suggestion of finding out what names HAL is returning by using:
```
xinput --list
```
and then renaming things appropriately.

If you follow the method of of installing rec's script and then calibrating with wacomcpl you should be able to use a rotation script.  Methods 1 or 3 should work on this thread:  [http://ubuntuforums.org/showthread.php?t=996830](http://ubuntuforums.org/showthread.php?t=996830)  I know there have been some problems with Intel drivers in Jaunty, but supposedly fixes are on the way.  If you try rotation, make sure Compiz is not enabled.  At least initially.

I hope this is helpful.

---

### Post by Jofarmer on 2009-05-01
Installing the haltowacom script did not change a thing :-( Also wacomcpl is not found, cannot be installed alone and is not installed with wacom-tools.
I would prefer to go the HAL/.fdi way, but creating a custom_wacom.fdi has not even brought back the eraser. Thinkwiki at least has a good and working mouse-wheel.fdi that allows me to scroll.

Thank you for your extensive how-to, but I have to confess that adjusting it for use with my x61t is a little too complicated to me. I just got good at understanding and editing the xorg.conf, but that's useless now. I don't want to put hours and days of work in finding a workaround that could break with the next update.

After gulping down the initial pint of frustration about this being WAY more work than I anticipated I am set to wait a little, maybe linuxwacom gets updated soon. Or something like that, I have not even fully understood the plethora of incompatibilities at work here.

Maybe staying with LTS versions is a good idea after all, I just really need the good 3G/UMTS functionality present from 8.10 on.

---

### Post by hoggy on 2009-05-08
While admittedly this may not help you, Joe, it did work for me.  Applying the wacom-names script was the only step I needed to take under 9.04 to get the rotate script that I found on another site working as written.

([http://wiki.control-d.com/index.php?title=Ubuntu_Intrepid_Ibex_(8.10)_on_a_Toshiba_Protege_M400](http://wiki.control-d.com/index.php?title=Ubuntu_Intrepid_Ibex_(8.10)_on_a_Toshiba_Protege_M400))

I still need to map it to a button, but it does now rotate both the screen and the stylus when I manually call the script.

Again, I simply followed the snippet here:  [http://ubuntuforums.org/showthread.php?p=7068115#post7068115](http://ubuntuforums.org/showthread.php?p=7068115#post7068115)

It was awesome, by the way, because the xorg.conf stuff was locking up the desktop...

---

### Post by Jofarmer on 2009-05-15
Thank you, hoggy, that really helped. After installing wacom-names I followed [this How-to]("http://ubuntuforums.org/showthread.php?t=604896"), and now the screen rotates when I swivel into tablet mode and back.

Just: the rotate button does not work (so there is just the one tablet mode 'as a right-handed book') and the cursor is not where the pen is...

And touch still doesn't work.

EDIT: while Touch still doesn't work, installing wacom-tools helped the cursor to find the stylus' tip (simply had forgotten to do that after the last reinstall)

---

### Post by Favux on 2009-05-15
Hi Jofarmer,

Congratulations!  You got it working.

I don't think the X61t has touch.  I know the X200t does.

From what you've said I couldn't tell if you've used "wacomcpl".  It's in wacom-tools and it lets you calibrate and configure the stylus, stylus button(s), and eraser.  Open up a terminal and type:
```
wacomcpl
```
To see how to apply the settings it will make for you through each boot see Section 3 here:  [http://ubuntuforums.org/showthread.php?t=1038949](http://ubuntuforums.org/showthread.php?t=1038949)

---

### Post by Jofarmer on 2009-05-16
Thank you, Favux, using wacomcpl I am now able to use the stylus for a right-click, have not figured out how to convince it use the eraser yet.

But after I shut it down yesterday evening, happy that everything was goin so well and booted it this morning, I get the strangest errors:

gnome-panel takes ages, goes through was seems to be a restart loop, all applet are scattered across it, and after some time finishes. But network-manager, battery status, bluetooth are still missing, and most importantly, I cannot start cellwriter - or any application.

Since all I did yesterday was installing the swivel script (and flash player, acro reader and air) this has to be connected, right?

Is there a settings file I could delete? (I come from OS X ;-))

---

### Post by Favux on 2009-05-16
Hi Jofarmer,

You are correct.  For the "loop" check in "/etc/X11/xinit/xinitrc". Everything in there (xinitrc) should be commented out. If you see:
```
# invoke global X session script
. /etc/X11/Xsession
```
Then comment it out like:
```
# invoke global X session script
#. /etc/X11/Xsession
```
I think I'm going have to change the HOW TO.  This almost never happened before.  Now it seems common in Jaunty!

Eraser only works for certain programs that can detect it like Gimp and Inkscape.  You have to configure the input devices section they have.  In Xournal your stylus button should be the eraser.

I hope this helps.

---

### Post by Jofarmer on 2009-05-16
Thank you again, Favux, that indeed was all that was necessary to get my system back to usable again.

Now all I need is a hint how I can get those standard-applets back: network-manager, battery status (it's somehow a different than the one that can be added manually), bluetooth... Bluetooth is set to show up when an adapter is present and I tried switching all radio on and off using the hardware switch at the front, but nothing reappeared.

And strangely cellwriter still does not add a panel-applet when running now. Nor does Transmission.

---

### Post by Favux on 2009-05-16
Hi Jofarmer,

Since right clicking on the panel doesn't give you the applets you need try Synaptics Package Manager.  Search gnome.  You should see gnome-panel.  Right click it and mark for reinstallation and click apply.  It will probably also want to reinstall gnome-panel-data.  See if that fixes it.  You can try the same thing with CellWriter.

---

### Post by Jofarmer on 2009-05-16
Hi Favux, thanx a lot for your fast response. I tried a lot by now, but what helped in the end was this [archived thread]("http://ubuntuforums.org/archive/index.php/t-109524.html"). Somehow in all the hassle the notification area got dropped, readding it was all I needed to do.

Thanks for all the help and your How-To....

:popcorn:

---

### Post by Favux on 2009-05-16
Hi Jofarmer,

Great!  Nice work.  I should have realized that's what happened.  You're welcome.

---

### Post by geedew on 2009-05-16
I have touch working on my x61t using just HAL.

[http://geedew.com/blog/x61-tablet-ubuntu/](http://geedew.com/blog/x61-tablet-ubuntu/)


Enjoy.

---

### Post by Favux on 2009-05-16
Hi geedew,

By touch I mean what linuxwacom means.  Not using the stylus but using your finger.  Does the X61t support touch (the finger)?  And do you know the HAL identifier for your tablet?  Is it WACf008 or WACf009?

---

### Post by aiwarrior on 2009-05-18
Hi
Does any of you have the suspend to RAM/disk working?
In mine when i suspend it doesnt do anything even with gnome-power-cmd suspend.

Thanks

---

### Post by Favux on 2009-05-18
Hi aiwarrior,

I can't answer you question directly but I thought it might help to make you aware that there are some .fdi files upstream of the 10-wacom.fdi that may have a bearing.

The one I'm guessing is relevant is "20-video-quirk-pm-lenovo.fdi" located in "/usr/share/hal/fdi/information/10freedesktop/".  You might want to take a look at it and check out some of the others.

If you can't find a solution you may have to post a launchpad bug.  Actually since checking the launchpad for your bug before you post is standard you could check now.  If the bug is posted often a solution is there.

---

### Post by aiwarrior on 2009-05-18
I got it sorted i accessed the /var/log/pm-suspend and there was a script that i had try to insert to make the computer hibernate but to no avail. I deleted it and now everything is working, at least the suspend is. The suspend to disk is not.

I also edited the fdi to my hardware.

---

### Post by Favux on 2009-05-18
Hi aiwarrior,

Good!  So you removed a script that wasn't working.  Do you want to share your edited .fdi file?

How big is your swap file?  While the recommendations for it are all over the place occasionally I have seen smaller ones not work for suspend to disk.  You'd think equal to RAM would work but some seem to need it bigger, say 1.5 x RAM.

---

### Post by aiwarrior on 2009-05-18
I read some info in here, its a good guide:
[http://people.freedesktop.org/~hughsient/quirk/quirk-suspend-try.html](http://people.freedesktop.org/~hughsient/quirk/quirk-suspend-try.html)

I only made a small change and i even don't know if it actually made a difference.

```
<!-- X61t 7767 96U-->
      <match key="system.hardware.product" prefix="776796U">
        <merge key="power_management.quirk.s3_bios" type="bool">true</merge>
        <merge key="power_management.quirk.s3_mode" type="bool">true</merge>
      </match>
```

I added this below the first </match> tag. Notice that the prefix is from my machine and can vary. You can check your prefix by running:

```
>lshal | grep system.hardware
```

For more details refer to the page above

---

### Post by aliencam on 2009-06-28
Hi all, sorry for responding to an old topic, but I wanted to point out that the X61t DOES have "touch" capabilities.  

When purchasing the x61t, you were given two options, one was for a higher resolution screen (1280x1024?) and the other was for a touch-capable screen.  If your x61t's maximum screen resolution (in System > Preferences > Display)  is 1024x768, then your x61t has "touch" capabilities.  This means that you can use your finger to poke the screen.  

"touch" does not work with hover, but it does work to actually click the mouse. It has to be calibrated in wacomcpl after applying the script mentioned earlier.  


If anyone needs another guide on setting up the tablet functions of an x61, I wrote one here: 
[http://blog.aliencam.net/2009/06/ubuntu-setup-guide-viii-wacom-tablet-config/](http://blog.aliencam.net/2009/06/ubuntu-setup-guide-viii-wacom-tablet-config/)

---

### Post by Favux on 2009-06-28
Hi aliencam,

Thanks for clearing up the "mystery".  Now I understand why X61t's can identify with two different "WAC"'s.  I thought that was what was going on.  Nice to have it confirmed.

Great guide.

---

