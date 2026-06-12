---
title: "Transparent Nautilus background?"
date: 2008-07-22
forum: General Help
---

### Post by detroit/zero on 2008-07-22
Is a way to make the background area of Nautilus windows have a transparent gradient? I've looked for settings to change and dug around for ways to do this, but I can't seem to figure out a way to make it happen.

Searches on the forums for the words transparent+nautilus turn up a lot of interesting posts on other subjects, but not exactly what I'm looking for.

I found [this thread]("http://ubuntuforums.org/showthread.php?t=607140&highlight=transparent+nautilus") from back in November.. I'm wondering if we've progressed any in the last few months. It points the way to a [gnome-look.org]("http://www.gnome-look.org/content/show.php?content=56631&forumpage=1") page that seems to offer some hope, but it turns out to be some sort of scam or broken link or something.

To illustrate:
[IMG]http://i150.photobucket.com/albums/s104/backup23/Screenshot-14.png[/IMG]

Does anybody know how to make those areas have a level of transparency - adjustable or not? Can I set a background image created in GIMP or something that is just a 75% opaque image?

Any advice is appreciated.

---

### Post by detroit/zero on 2008-07-28
bump

---

### Post by jordanmthomas on 2008-07-28
Not possible at the current time.
It's not that gtk isn't capable of doing it (see applications like affinity, for example), but nautilus can't do it.

The link you provided was just someone asking if it could be done, not someone claiming to have it working.

Maybe some day, eh?

---

### Post by detroit/zero on 2008-07-28
> **jordanmthomas said:**
> Maybe some day, eh?

I hope so. Not that it offers any functionality or anything, I just think it would look nice.

At any rate, inside the General tab of Compiz Manager, I set the transparency option to catch Nautilus windows and give them some transparency. It effects not only the background, but the entire window - title bar, icons, and everything. Not exactly what I was after, but it works. I tried adding an exception for icons (so they would stay 100% opaque), but I don't know how to title the rule. (Windows are titled after their applications, menus are just menus, tooltips are called tooltips, but icons are not called icons.)

Oh well.

---

### Post by dark_harmonics on 2008-07-28
Yea when nautilus supports GTK we will be able to have different desktop backgrounds on each cube face without sacrificing your icons (there is a patch for gutsy but not for hardy)

---

### Post by northern lights on 2008-07-28
It's not exactly true that transparency for nautilus cannot be achieved today.

Just not via gtk but through compiz transparency.

However, it will not effect background(s) only, but the entire nautilus window, i.e. icons and menus as well.

Enter ccsm (System > Preferences > Advanced Desktop Effects Settings) and navigate to the "General Options" menu, "Opacity Settings" tab.

Under "Window opacities" click "New" and type 'class=Nautilus' (case-sensitive!) move the slider around and select preference. I don't think you can go much lower than 85, cause that'll render menus unusable...

---

### Post by dzon65 on 2009-09-04
Posted the exact same question.[http://ubuntuforums.org/showthread.php?t=1256797](http://ubuntuforums.org/showthread.php?t=1256797) I've seen it somewhere,think it's possible to do.But if I recall well,this guy was using KDE.

---

### Post by lusguz on 2010-09-29
Dudes, Dudettes, Children of the Brain, 
Greetings:

I am exceedingly old & most of my formerly-robust brain cells have withered; please feel free to ignore this post.  For many years, longer than any of you have been alive, I have sought to make the background of a Directory (now "Folder") Window transparent. To define my goal: Without affecting the opacity of any other element of the window (e.g., window border, controls, file & folder lists) I would like the "background" element of the window "rewritten" such that each and every pixel therein be identical to the pixel WHICH WOULD HAVE OTHERWISE OCCUPIED THAT PIXEL OF THE DESKTOP were no "Folder Window" open.  (An example of this effect readily available to Ubuntu users: open a Terminal, select "Edit", "Profile Preferences", "Background", enable the "Transparency" option & pull the slider all the way to the left.  This is the precise effect of which I speak...the appearance that one is "looking thru" an actual "window", with the "data" written on the "glass".)

This is MY (and, therefore, THE TRUE) definition of a "transparent window".  This effect was first possible in Windows circa 2002 via an "Advanced Option" in WindowBlinds version 3.41 (from StarDock, Neil Banfield, programmer).  Mr. Banfield, however, was unimpressed with this effect and removed it as an option in WindowBlinds after version 3.42.  He has graciously refused my plea to reinstate the option.

During the same era (my memory fails me; please feel free to correct my mis-statements here and provide the correct details) Microsoft introduced their own version of "transparent windows", available via some "call" (13h?) to the Windows operating system.  This "call" has the effect of rendering THE ENTIRE window "transparent" to whatever degree, producing what I would have described as a "Window FADE Effect", not a "Window TRANSPARENCY Effect".  But as Microsoft decreed this effect to be "Transparent Windows", so it became known; hence all young brainiacs born after 1985 or so define a "Transparent Window" as the "entire window fading out" effect of the Microsoft variety.

As no one seems to understand or appreciate the distinction between a "transparent window" and a "faded window", and as no programmer in the entirety of the World ever succeeded in duplicating Mr. Banfield's version of a "truly transparent window" in the Windows O.S., I was reluctant to whine to the Linux world for their assistance. (I have attempted migrate to Linux many times over the years, always returning to XP simply because it--with WindowBlinds 3.42 loaded--was the only OS that let me see my Desktop more-or-less the way I wanted to see it.  Tragic, yes?)

When I recently became aware of the "true transparency" option in the Linux Terminal (at least on Ubuntu 10.04.1, which I'm currently using), I immediately loaded Ubuntu on all my computers, discarded all things Microsoft, had a small private ceremony in my bedroom and am now wedded to the Penguin for better or worse, in sickness and in health, til death do one of us part (presumably Me; the Penguin seems to be growing healthier every year).  

My theory is that, given a "truly transparent" Terminal window, "truly transparent" Nautilus windows can't be far behind.

It is in fact my suspicion that some young brainiac (perhaps in Poland) has already achieved "truly transparent Nautilus windows" and merely neglected to inform me.  Hence this post.

I have experimented with "transparent .png backgrounds" (failure) and "editing Compiz settings" (failure).  I am about to begin searching thru the Ubuntu forums; as the accepted definition of "transparency" seems to vary, however, I thought it might behoove me to post the definition of my own goal here in hopes the Polish kid (or other) might respond.

And in the unlikely event the programmers who produced the "truly transparent" Terminal window are listening: it would be very nice if one had the option of changing the font-size in the terminal window; i.e., I am approaching blindness as well as senility.

                              Best regards, 
                              The Penguin's new spouse

---

