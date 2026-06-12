---
title: "Higher resolution: distortion"
date: 2005-06-27
forum: Hardware &amp; Laptops
---

### Post by Breepee on 2005-06-27
I've been editing my xorg.conf, in order to get my screen to 1280x1024. I of course added these resolution to the file, and I also set the refreshrates according to my monitors manual. My hardware is a NVidia Geforce FX5900XT (no NVidia drivers installed) with a iiyama Prolite E431S screen (17" TFT).

I can select and go into 1280x1024, but some things are distorted. When I make a screenshot and it shows the distortions too, but when I switch back to 1024x786 (which works fine) even the screenshot is 100% OK. The cursor is not distorted by the way, not even when I hover above a letter that is.

The distortions are pixelated, not smooth.

Any thoughts?

---

### Post by Breepee on 2005-06-28
I've just installed Fedora Core 4, and it shows exactly the same behaviour. Anyone?

---

### Post by GTvulse on 2005-06-28
[QUOTE=Breepee]I've just installed Fedora Core 4, and it shows exactly the same behaviour. Anyone?[/QUOTE]
You can't force the resolutions if the X driver doesn't support them in the first place.  Some ideas:

[list=1]
[*]Read through /var/log/X.0.log to find out the resolutions supported by the combination of your video card and monitor.
[*]Try using the propietary Nvidia drivers if you haven't already.
[/list]

---

### Post by Breepee on 2005-06-29
[QUOTE=dradul]You can't force the resolutions if the X driver doesn't support them in the first place.  Some ideas:

[list=1]
[*]Read through /var/log/X.0.log to find out the resolutions supported by the combination of your video card and monitor.
[*]Try using the propietary Nvidia drivers if you haven't already.
[/list][/QUOTE]
 My hardware supports it, I'm running it in Windows fine (I'm not that stupid :)).

Do think the NVidia drivers solve it, or is it a guess? I thought maybe someone has had this before and came up with a solution.

---

### Post by GTvulse on 2005-07-04
[QUOTE=Breepee]My hardware supports it, I'm running it in Windows fine (I'm not that stupid :)).

Do think the NVidia drivers solve it, or is it a guess? I thought maybe someone has had this before and came up with a solution.[/QUOTE]

You haven't done your homework! If you did, you would know that different versions of the Nvidia drivers perform better than others with different Linux (kernel) versions and hardware models from the manufacturer. And that as a rule of thumb, the xorg nv drivers fail to give proper hardware acceleration (unless your are willing to be running the latest CVS snapshot of Xorg, in which case a source-based distro such as Gentoo , Lunar Linux or SourceMage Linux might be better playgrounds for such efforts).

---

### Post by brim4brim on 2005-07-04
I installed the nVidia drivers on my old laptop running mandrake and it worked fine and really improved performance.  The installation is really easy.  About as easy as the ATI with the .run file has become which I just working today and doesn't perform nearly as well nVidia's did on my old laptop.

---

### Post by Breepee on 2005-07-04
[QUOTE=dradul]You haven't done your homework! If you did, you would know that different versions of the Nvidia drivers perform better than others with different Linux (kernel) versions and hardware models from the manufacturer. And that as a rule of thumb, the xorg nv drivers fail to give proper hardware acceleration (unless your are willing to be running the latest CVS snapshot of Xorg, in which case a source-based distro such as Gentoo , Lunar Linux or SourceMage Linux might be better playgrounds for such efforts).[/QUOTE]
 The NVidia driver always worked fine, but I wonder why the OS nv driver is displayinh these distortions I discribed.

---

### Post by GTvulse on 2005-07-14
Somehow I missed the email notification on your post, sorry about that. 

The Xorg drivers are reversed engineered for the most part (with some notable exceptions, that I can't recall off the top of my head) and are not as good as would be the ones from the hardware vendors, the problem is that video hardware vendors think that the APIs to their hardware are trade secrets and that somehow, someone can reverse engineer the chips from such APIs. Rather silly, because you only need to dissect the chip with the proper tools to recover the design and the most probably owners of such equipment (laser nanocutters, scanning electron microscopes, etc.) are their industry competitors, not the driver writers...

---

### Post by RJARRRPCGP on 2005-07-14
[QUOTE=Breepee]My hardware supports it, I'm running it in Windows fine (I'm not that stupid :)).

Do think the NVidia drivers solve it, or is it a guess? I thought maybe someone has had this before and came up with a solution.[/QUOTE]

I agree and if the monitor didn't support the resolution, it would be unreadably scrambled.

---

