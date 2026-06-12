---
title: "Howto find/install all tools to set screen resolutions"
date: 2006-11-14
forum: Hardware &amp; Laptops
---

### Post by Jim-BobH on 2006-11-14
This is a simple request, but the lack of an answer is wasting countless hours for Ubuntu newbies and those trying to help, all because

====> It's not in the Ubuntu User Manual where it belongs!

So here's the request:

We need to fix the Ubuntu User Manual so that it answers all the hundreds of questions posted that all boil down to, "Why can't I just change the screen resolution to whatever I want, within the hardware limitations of my video card and monitor, which are correctly handled by Windows on the same hardware?"

Background:

When we choose System >> Preferences >> Screen Resolution and it's all wrong (many valid resolutions and refresh rates are missing) and running

dpkg-reconfigure xserver-xorg

doesn't change anything (verified by comparing the new xorg.conf to the backup it just created),

and we've got the valid resolution and refresh rate combinations from our monitor manufacturer,

and we know our whiz-bang video card will do all we want (as proved by the fact that it does it on Windows and/or it's in the specs for that card),

and we've done "man xorg.conf" and followed the instructions and entered the specs for our Monitor in the Monitor section of xorg.conf,

and then we found out that then our Ubuntu box won't run X any more,

and we have to learn how to get to a command prompt so we can sudo cp xorg.conf-<backup> xorg.conf,

and we read 18,375 postings on Ubuntu forums and X forums and 38 other forums about Screen and Resolution and xorg.conf and cry along with all the frustrated newbies and count all the hours wasted trying to teach them how to recover from disasters that should have been avoided in the first place,

and we notice that nearly all the forum postings are caused by the same few blasted problems over and over and over, and it seems only the employees of video card manufacturers actually know how to build an xorg.conf that's correct for their card with a known monitor, and they do it in their forums in 5 minutes,

we realize this is a BIG PROBLEM with a KNOWN ANSWER, and the Linux community needs to fix this situation.

It's hurting all flavors of Linux, not just Ubuntu.

It's consuming hours that should be spent writing the missing chapter in the User Manual.

Many people would benefit from the fix.

How do we go about an _orderly_, _effective_, _efficient_ process to fix the User Manual?

Where is the knowledge documented that allows those manufacturer's techs to answer a forum posting of a messed-up video problem, with an xorg.conf that works perfectly the first time, every time, in 5 minutes? Clearly, man xorg.conf is inadequate.

Why doesn't our Screen Resolution tool give us the right options (what does it look at in xorg.conf)?

Why doesn't dpkg-reconfigure xserver-xorg fix anything sometimes?

Why is this so hard?

I know this is _really_ scary, but we even need to address multiple monitors and multiple video cards, and >1 model of each on/in the same computer. And the monitors (e.g. new widescreen LCDs) that are _not_ 4:3.

I am volunteering to help fix this situation, but I can only write part of the Chapter we'll call "Every tool and every bit of knowledge you will ever need to make a beautiful video setup in xorg.conf" or something to that effect.

Will others please join in, especially if you are one of those video card manufacturer techs (and the other three persons) that really do know how to do this?

What about the authors of the Ubuntu Screen Resolution tool? Where is the documentation on it?

Should we start with a sticky posting that will begin by gathering the URLs of all _original_, _reliable_ (i.e. stable URLs) source documentation about how xorg.conf actually works?

Is there a good, current book that will actually teach us how to do this? I'll buy it in a minute. Please suggest one.

Can we even answer the point in man xorg.conf (in Ubuntu Dapper) that says "maybe nobody knows" (about one of the Sections)?

What other ideas are out there?

Respectfully submitted,

Jim Harris

---

### Post by ReaderRat on 2006-11-15
I concur with the need for more appropriate Resolutions to the monitor resolution problem. There is a thread on it: [**Monitor Resolution**](http://ubuntuforums.org/showthread.php?t=269052)
I am sure the developers are working to alleviate the drivers problem in Ubuntu. It just takes time to configure the hundreds of different systems that they have to provide drivers for. I am constantly reading and responding to problems (that I can handle - simple newbie stuff{I am a noob}). The moderators are doing their best (with no payback but an occasional 'Thanks').

---

### Post by DJiNN on 2006-11-15
I agree. As someone who has recently tried installing a new (Widescreen) monitor, i have had no end of trouble changing the resolution (Running Xubuntu "Edgy"). It seems that running ```
 dpkg-reconfigure xserver-xorg
``` doesn't seem to do much. It picks up the new monitor here, which is great, but the available resolutions are still the same. Of course it could be the fact that my Graphics are old & of the "Built in" kind...... but still, it's an area where there needs to be more info made available. 

For now, i'm stuck at 1280x1024...... which is OK, but 1440x900 would be nice. :)

---

### Post by Coldbird on 2006-11-15
Lucky you... Im stuck on 1024x768...

With damn Vesa Drivers on my X1300 Mobility :(

Its weird... The ATI Drivers install fine (fxglr) - not one single error... But on startup Xorg Display fucks up - and I need to copy my old Vesa Backup xorg.conf back into its old place so it works again...

Im doomed... and if that wasnt enough... Im stuck on 1024x768 max... on my nice Widescreen LCD :(

---

### Post by Henry Rayker on 2006-11-15
The sudo dpkg-reconfigure xserver-xorg always fixed my resolutions...this is granted I'm using a built in video chipset (SiS...no XGL/Beryl/Compiz/whatever for me).

The only display problem I have is that every single time a new kernel is installed, I have to change an option in the grub menu.list.

---

