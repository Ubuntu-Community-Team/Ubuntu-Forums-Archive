---
title: "Horizontal drop shadows missing - compiz-emerald - Ubuntu 8.10"
date: 2008-10-27
forum: General Help
---

### Post by quickfished on 2008-10-27
I use compiz/emerald.  This happened after upgrading to 8.10: some drop shadows (the horizonal ones) of some applications are missing.  This is the case in Firefox, Rhythmbox, F-spot and a few other apps (see att.).  Other apps like gedit or terminal don't have the problem.
Funny thing is: they all worked mighty fine in 8.04.

The problem persists after replacing NVIDIA driver version 173 with 177.

I checked and updated all sorts of settings in ccsm but to no avail.  Does anyone have an idea with this can be?  Well, it's not blocking.  In fact it's the only problem I have with 8.10 for the moment.  But it just bothers me a bit :)

---

### Post by hictio on 2008-10-27
You can clearly see the cut in the Firefox drop shadows on your screenshot.
Does it happen while you drag the window too?
Personally I'd freak out, I love drop shadows.

---

### Post by quickfished on 2008-10-27
> **hictio said:**
> You can clearly see the cut in the Firefox drop shadows on your screenshot.
Does it happen while you drag the window too?
Personally I'd freak out, I love drop shadows.

Me too.  If not, it would be easier just to disable desktop effects :)
But, the cut doesn't go away, pardon my french.  
This is on a more or less clean install, although my home folder with all my personal settings are on a separate partition.  Maybe I should try to clean out all that, but I have no idea where to begin.

---

### Post by Yes_It's_Me on 2008-10-29
I have the exact same issue, it's very annoying, it seems to happen to most emerald themes but not all, it also seems to happen to all rendering engines, be it legacy, trueglass etc.

---

### Post by owagner on 2008-11-07
I have the same issue, always reproducible with X-Chat, sometimes happening with gnome-terminal. Nvidia 177 drivers, 8600GTS, two monitors.

This only happens when I set the shadow radius in emerald-theme-manager to a value >= 12. At 11.9 and below, the problem goes away.

Best Regards,
Olli

---

### Post by quickfished on 2008-11-07
> **owagner said:**
> I have the same issue, always reproducible with X-Chat, sometimes happening with gnome-terminal. Nvidia 177 drivers, 8600GTS, two monitors.

This only happens when I set the shadow radius in emerald-theme-manager to a value >= 12. At 11.9 and below, the problem goes away.

Best Regards,
Olli

Indeed, this is working.  Thanks a lot! I had to set it to 8 or below, but ok: it's gone.

Another step closer to a perfect desktop :D

---

### Post by jsully1 on 2008-11-09
Thanks - I had to go down to 8 as well.  Also, I'm on an ATI card, so this is likely an Emerald specific issue.

---

### Post by pgrilo on 2008-11-09
> **owagner said:**
> I have the same issue, always reproducible with X-Chat, sometimes happening with gnome-terminal. Nvidia 177 drivers, 8600GTS, two monitors.

This only happens when I set the shadow radius in emerald-theme-manager to a value >= 12. At 11.9 and below, the problem goes away.

Best Regards,
Olli

Perfect, thanks alot for the fix!

---

### Post by ModeBiller on 2008-11-17
This seems to be a "relative" issue. The dropshadows disappear the larger a window is. Reducing the the radius allows larger windows with dropshadows, but with large enough windows the bug will reappear. Perhaps some memory allocation problem.

---

### Post by cmb11 on 2008-11-21
Does someone have a real solution that eliminates this bug ?!?! I had the shadows in 8.04 working on a radius > 12, but now anything > 10 will crop the horizontal shadows!!

@ModeBiller: same thing happening with me...

---

### Post by tum.quan on 2008-11-22
ModeBiller - comment #9 - I think is dead on correct in his explanation.

The lower the shadow radius is set, the wider any window can be with no horizontal/top-bottom shadow problem.

The higher the shadow radius is set, the more narrow (left to right) a window has to be for the bug not to show up.

I've attached a screen-shot of the bug.

[IMG]http://www.broadskies.net/testing/ubuntuforum/Screenshot.jpg[/IMG]

---

### Post by joesnose on 2008-12-06
i also have this issue after an upgrade to 8.10, ati graphics card, had to set the radius to below 8.

---

### Post by Chachee on 2008-12-06
Same issue as well.  Hopefully it gets patched soon.
 
Seems to depend on the size of the window.

JT

---

### Post by reader4 on 2008-12-09
Ditto.  Wider windows los the horizontal shadow while smaller windows do not.  Changing the offset did not help for me.  Is there a bug report for this?

---

### Post by rcpilot on 2008-12-30
Getting the same problem.  I have noticed that how low you need to set the shadow size is proportional to how wide you make your window though.

---

### Post by cmb11 on 2008-12-30
well... we need a proper solution for this bug....

---

### Post by atulai on 2009-01-06
My resolution is pretty big, and this is totally ruining my awesomely macish ubuntu.

/cry

---

### Post by Kanji_Man on 2009-01-09
I can also confirm this bug on many different machines. Under 32bit, 64bit, and PPC. Under both ATI and nVidia.

The bug is definitely related to the size of the window as you can resize a running window affected by the bug to a smaller size and the shadow re-appears. Resize it to a larger size and the shadow disappears again.  Using a smaller dropshadow radius will let you get away with larger windows but even with a dropshadow of 1 the bug appears on very large windows.

I could not get this bug to appear on the vertical drop shadows even after stretching a window beyond 3,000 pixels high on the same setup where the bug appears on the same window only a few hundred pixels wide.

---

### Post by BOYerchen on 2009-01-16
The problem is not ubuntu specific. Got the same issue on Fedora. At least I could not reproduce it on my netbook with Intel graphics, but this could be related to the small resolution. I hope there will be a fix soon.

---

### Post by hictio on 2009-01-18
> **atulai said:**
> My resolution is pretty big, and this is totally ruining my awesomely macish ubuntu.

/cry

What resolution are you people running at? I'm at 1280x800 on the laptop, and 1440x900 (when I hook up an external monitor) and I don't have that problem, as I don't use any radius bigger, [as explained earlier](http://ubuntuforums.org/showpost.php?p=6122886&postcount=5) on this same post.

Not a total solution, but its working in the mean time.

---

### Post by Kanji_Man on 2009-01-19
> **hictio said:**
> What resolution are you people running at? I'm at 1280x800 on the laptop, and 1440x900 (when I hook up an external monitor) and I don't have that problem
For what it is worth I am running 6 monitors each at 2048x1536. Though I am only able to stretch a single window across two monitors (effectively 4096x1536 or 2048x3072) due to current limitations of xinerama & compiz.

However, I have been able to trigger this behavior on systems with as low of a resolution as 800x600 when using a large shadow radius and larger windows so I do not think the desktop resolution has a direct impact. Smaller resolutions obviously encourage the user to use smaller windows and are therefore less likely to trigger the bug.

---

### Post by GlennW on 2009-02-04
I have the same issue. However, I have an nVidia card. I have a 20" monitor and usually have several apps open concurrently. I don't have anything maximized and can get away with the radius at 10.2. 

This is ridiculous. How can something like this get by? 

Does anyone have an answer to this issue? Drop shadows, while considered eye candy for some, are important for app separation and just plain ole making life easier when having to spend long hours in front of a monitor.

Thanks.

---

### Post by naouf on 2009-02-05
No one will fix this since emerald isn't maintained anymore...

[http://bugs.opencompositing.org/show_bug.cgi?id=1060](http://bugs.opencompositing.org/show_bug.cgi?id=1060)

You can still comment the bug report, but if anyone want to take a look at sourcecode instead of waiting, there will be a little hope to have it fixed.

---

### Post by naouf on 2009-02-07
Bug reported there also:
[https://bugzilla.redhat.com/show_bug.cgi?id=484204](https://bugzilla.redhat.com/show_bug.cgi?id=484204)

If anyone can help locating the difference, I will be glad to help if I can by fixing this.

---

### Post by m4cks on 2009-02-16
deleted post. nevermind.

---

### Post by m4cph1sto on 2009-02-16
> Hi Everyone, for those using nvidia, this is a known bug with the nvidia framebuffer driver.

It can be fixed by following these instructions:

[http://tombuntu.com/index.php/2008/04/28/workaround-for-pink-shadows-with-compiz/](http://tombuntu.com/index.php/2008/04/28/workaround-for-pink-shadows-with-compiz/)

(although i realise the problem you are having may not necessarily be pink shadows, this solution will fix the messed up horizontal shadows too.)


I foolishly tried this solution, and it killed my X.  I can get a command prompt, that's it.  Can someone tell me how to undo this?  Here's the command I did:

```

sudo ln -sf /usr/lib/nvidia/libwfb.so.xserver-xorg-core /usr/lib/xorg/modules/libwfb.so

```

---

### Post by olejon on 2009-02-23
> **naouf said:**
> No one will fix this since emerald isn't maintained anymore...

[http://bugs.opencompositing.org/show_bug.cgi?id=1060](http://bugs.opencompositing.org/show_bug.cgi?id=1060)

You can still comment the bug report, but if anyone want to take a look at sourcecode instead of waiting, there will be a little hope to have it fixed.

Annoying bug!

Is Emerald really not maintained anymore? Any replacement coming up?

EDIT: Wikipedia told this:

Recently there has been work in the Compiz Fusion project to create a replacement for emerald, the current leading candidate for which is Jasper a much more customizable window decorator which supports plugins, scriptable buttons and animation.[4]

---

### Post by thelamer on 2009-02-28
I am surprised no one has posted this yet, but all you have to do is reduce the radius in the Emerald settings; 

[IMG]http://www.ryankuba.com/DropBox/Emerald.png[/IMG]

It should be sitting at around 10-14 if you are having problems, I would recommend a number, but honestly the best way to do it is to expand a window to the biggest you will ever have it and keep reducing the value until the border extends horizontally. 

:guitar:

---

### Post by olejon on 2009-03-02
Great, it works.

I have to set it at 7.9.

---

### Post by swoll1980 on 2009-03-09
> **thelamer said:**
> I am surprised no one has posted this yet, but all you have to do is reduce the radius in the Emerald settings; 
It should be sitting at around 10-14 if you are having problems, I would recommend a number, but honestly the best way to do it is to expand a window to the biggest you will ever have it and keep reducing the value until the border extends horizontally. 

:guitar:

It was posted several times it only works with lower resolution monitors

---

### Post by MeduZa on 2009-05-10
> **owagner said:**
> I have the same issue, always reproducible with X-Chat, sometimes happening with gnome-terminal. Nvidia 177 drivers, 8600GTS, two monitors.

This only happens when I set the shadow radius in emerald-theme-manager to a value >= 12. At 11.9 and below, the problem goes away.

Best Regards,
Olli

the radius depends on the windows size, I need to put it on 9.1 to avoid the problem

---

### Post by sumo_su on 2009-07-27
Hmm... I'm not sure but I might have fixed it for me...

It appears that Compiz and Emerald are BOTH rendering drop shadows, so all I did was disable drop shadows in Compiz to get only the Emerald shadows.

Did this via Compiz Config Manager/Window Decoration/ and deleted "any" in the field "Shadow windows" (just blank in there)

EDIT: nope didnt fix it completely. sorry false alarm.

---

### Post by hictio on 2009-07-28
This is a real PITA, and as posted somewhere above, it'll never be fixed at this point.
Personally, I keep using Emerald, I really, really love my [Human Tiger](http://gnome-look.org/content/show.php/Human+Tiger?content=69772) theme, but I simply choose to never enlarge single windows beyond the point where the drop shadow effect dies (it completely freaks when I go beyond, and loose the effect).

---

