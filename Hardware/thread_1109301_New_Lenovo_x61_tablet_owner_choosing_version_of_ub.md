---
title: "New Lenovo x61 tablet owner choosing version of ubuntu"
date: 2009-03-28
forum: Hardware
---

### Post by SnickerSnack on 2009-03-28
Hi,

This is my first post here.  I found a few threads for which my question might be appropriate, but I wanted to avoid hijacking a thread with my first post.

I've purchased a new Lenovo x61 tablet on ebay, and I am eagerly awaiting its arrival via UPS.  I intend to dual boot Vista and Ubuntu.  I'll use Ubuntu primarily for work/school, but I have a few programs (read: video games) that I'd rather just use in Vista - at least until I feel like struggling with wine.

I got a tablet because I will use it for work and school (college adjunct/grad student), and I need to be able to use a Windows-Journal-like app for lectures and my own studies.  So, it is of great importance that I get the tablet functions working properly.  I will also need to get the vga-out to work so I can use a projector.

Browsing these forums, it seems like there are a lot of people trying to get 8.10 (ibex) to work with x61 tablets, so my question is this: Should I choose 8.10 (ibex) over 8.04 (heron)?

Particularly, the first line in this thread: [http://ubuntuforums.org/showthread.php?t=1038949](http://ubuntuforums.org/showthread.php?t=1038949)

> 
This HOW TO installs the linuxwacom driver 1.0.8.2-2 (the latest) in Ubuntu Intrepid (8.10) --May work for Hardy (8.04)

Indicates that 8.10 would be the better choice.

Or, have any problems with 8.04 already been worked out - making it the better choice?

A little linux background:  I used debian (sarge, I think) for a few years, but that was a few years ago.  I've forgotten most of the terminal commands and the things I learned from messing with X86conf and wine.  I have two people who can help me gets things working, though.

Also, I have been to thinkwiki.org, but the site is frequently down for maintenance (I'll probably check out the google cache), so if anyone could link to a good tutorial on getting ubuntu working with this particular laptop, that would be great.

Thanks.

---

### Post by Favux on 2009-03-28
Hi SnickerSnack,

I didn't mean to imply that.  It's just that the last linuxwacom I compiled  on Hardy was was 0.8.1-6, I think.  So I couldn't vouch for how the later versions worked.  That's what I was trying to say.  You would probably be OK with the 0.8.1-4 drivers and tools that are default in Intrepid.  Or you could download the 0.8.1-6 deb.s on Loic2's Wacom wiki (linked on the compile HOW TO also)

[https://help.ubuntu.com/community/Wacom]("https://help.ubuntu.com/community/Wacom")

A Thinkpad X61 tutorial:

[http://www.thinkwiki.org/wiki/Installing_Ubuntu_8.10_(Intrepid_Ibex)_on_a_ThinkPad_X61]("http://www.thinkwiki.org/wiki/Installing_Ubuntu_8.10_(Intrepid_Ibex)_on_a_ThinkPad_X61")

Which is for Intrepid.  I don't know which is best for a X61.  Of course with Intrepid you do get the newer kernel, with the usual improvements that implies.  The main problem folks had with Intrepid was the switch to HAL (hardware abstraction layer) and its .fdi files.  Actually the problem was the decision they made to remove the example Wacom sections from the xorg.conf.  A lot of people ran into nearly "empty" xorg.conf's and didn't know what to do.

Good luck!

---

### Post by SnickerSnack on 2009-03-28
Thanks for the reply.

I'll go with 8.10 then, since it's newer.

I hope to have it in my hands by the weekend, but I may not be able to find the time to install ubuntu for a couple of weeks.

I'll post here (or in the right thread if it already exists) if I run into any problems.

---

### Post by schmolch on 2009-03-28
Use Intrepid or Jaunty (beta).
The pen works on any version including the old Hardy but there are issues with the intel video-driver regarding the performance on a rotated screen.
For your video-card (gma 3100) you need the driver from Intrepid (or later), older cards like mine (gma 950 from my 2 x60ts) require the latest version from Jaunty.

---

### Post by SnickerSnack on 2009-03-28
> **schmolch said:**
> For your video-card (gma 3100) you need the driver from Intrepid (or later), older cards like mine (gma 950 from my 2 x60ts) require the latest version from Jaunty.

That's good to know; thanks.

---

### Post by jdos2 on 2009-04-11
I've been trying to find the "Best" Linux distro for my X61 Tablet.
I've a 7767-96U, but somehow have the 1.4GHz processor instead of the listed 1.5.
4 GB ram, 7200 RPM 160GB fixed disk. I've the high resolution screen.

I like the laptop. In fact, I liked Vista on it, after I installed the 64 bit stuff, but as a Unix admin, I can't rationalize that too much.

I've tried several different distributions on the laptop in the hopes of solving several different problems. Yesterday, I wiped Ubuntu in favor of Fedora, and now have a completely different problem set. 

Here are my requirements:
Laptop specific:
    64 bit.
    Dimming of the screen for power saving.
    Automatic screen rotation.
    Wacom functionality.
    "Thinkvantage button" functionality (it needs to bring up a gnome-terminal session)
    Working wireless
    Bluetooth, and an easy ability to shut it off.
    HDAPS.

Distro specific:
    Codecs. I'm a realist- I want to be able to watch a DVD, listen to MP3's and AAC's.
    OpenOffice 3.0- I really like Word when used as it's supposed to be, and OO is getting close (Anyone want StarOffice for OS/2 install media? :-)    )
    Amarok. Like it. Always used it. Love it enough to build it from scratch because Ubuntu dropped AAC tagging support.
    Gnome. It's gotta work pretty well, be pretty, and have a decent initial setup. 
    Flash. Gotta work for YouTube.


That doesn't sound like a huge list, but no Linux gets 'em all right. Every time I install a distribution I have to work <i>hard</i> on getting the list implemented. For every plus, there seems to be a minus. Ubuntu covers the most out of the gate, but:
Current implementations of it don't allow screen dimming by any mechanism I've found. Lots of bug reports, no working kernel/module combinations.
Wacom? Ubuntu again does it best, but put the laptop to sleep and re-awaken it and it's likely that the scaling of the tablet is wrong- put the pen somewhere, the pointer moves somewhere ELSE. The older drivers don't suffer from that, seemingly, but because of serial port numbering (and picket fencing!) the older Wacom software suffers if the laptop is booted on the expansion base- the drivers refusing to load until reconfigured.
64 bit- all seem to have that down well enough.
Thinkvantage. Only gotten it working under Ubuntu. Getting close with Fedora, having found several other resources- the information is on the ThinkWiki, but very buried- to the point where it's easier to find on other sites. The ACPI generated events, if trapped by X, can't generate a keycode because X can't handle keycodes higher than 255... OpenSUSE doesn't even give a ACPI key-generator application, and Fedora, like I said, is almost there. 
Wireless was a PAIN in Ubuntu prior to 8.04. It's much better now.
Bluetooth: There are instructions about to allow fn-f6 to shut it off without having to cycle through the fn-f5 combinations that drive the Gnome networking application int apoplectic fits. Ubuntu again seems easiest, but I'll know better when I play with it tonight on Fedora.
Automatic Screen Rotation: Ubuntu by far makes it easiest, but know there's scripting involved with whichever solution. Silly that there's no package- there are enough tablets out there. On Fedora, again, I'm ALMOST there, but can't seem to catch the generated ACPI event. Wacom rotation works well enough, but see the above comment about scaling, which becomes more obviously a problem when rotated.
HDAPS. Borked. Broken. Badly. I guess Kernel Developers never drop anything. PIA. Hey- I'm not in any way afraid to recompile drivers, but I HATE having to do it every time an update brings in a new kernel version, and I hate it when I get caught unawares during an update after just recompiling. It's happened. More of a general Linux grouse, I know.

So far as CODECs are concerned, I'll take the standard lumps. Yeah. I listen to media that costs money. Flash? The 64 bit stuff works pretty well, and isn't hard at all to install, except for finding the right plugin directory. Gnome has been a good experience across the board.
Amarok is just a nuisance. Bumbed me out, though, when Ubuntu stopped compiling it with the AAC support enabled.
OpenOffice. I'll admit it. I use Word styles. After working with Word for so many years, I've gotten good with it. I like it. I love the "This document was created with Word for OS/2" warning that shows up on my Mac when I read my old journals. OO is getting close, and 3.0.1 is the closest YET. Sure wish they'd show me the styles in the gutter like on Word... Ubuntu is not yet released with 3.0. That's a problem for me.

No distro is perfect. None do all I want. I can get close, though.

---

### Post by Shwan.c on 2009-04-13
> **jdos2 said:**
> I've been trying to find the "Best" Linux distro for my X61 Tablet.
I've a 7767-96U, but somehow have the 1.4GHz processor instead of the listed 1.5.
4 GB ram, 7200 RPM 160GB fixed disk. I've the high resolution screen.

I like the laptop. In fact, I liked Vista on it, after I installed the 64 bit stuff, but as a Unix admin, I can't rationalize that too much.

I've tried several different distributions on the laptop in the hopes of solving several different problems. Yesterday, I wiped Ubuntu in favor of Fedora, and now have a completely different problem set. 

Here are my requirements:
Laptop specific:
    64 bit.
    Dimming of the screen for power saving.
    Automatic screen rotation.
    Wacom functionality.
    "Thinkvantage button" functionality (it needs to bring up a gnome-terminal session)
    Working wireless
    Bluetooth, and an easy ability to shut it off.
    HDAPS.

Distro specific:
    Codecs. I'm a realist- I want to be able to watch a DVD, listen to MP3's and AAC's.
    OpenOffice 3.0- I really like Word when used as it's supposed to be, and OO is getting close (Anyone want StarOffice for OS/2 install media? :-)    )
    Amarok. Like it. Always used it. Love it enough to build it from scratch because Ubuntu dropped AAC tagging support.
    Gnome. It's gotta work pretty well, be pretty, and have a decent initial setup. 
    Flash. Gotta work for YouTube.


That doesn't sound like a huge list, but no Linux gets 'em all right. Every time I install a distribution I have to work <i>hard</i> on getting the list implemented. For every plus, there seems to be a minus. Ubuntu covers the most out of the gate, but:
Current implementations of it don't allow screen dimming by any mechanism I've found. Lots of bug reports, no working kernel/module combinations.
Wacom? Ubuntu again does it best, but put the laptop to sleep and re-awaken it and it's likely that the scaling of the tablet is wrong- put the pen somewhere, the pointer moves somewhere ELSE. The older drivers don't suffer from that, seemingly, but because of serial port numbering (and picket fencing!) the older Wacom software suffers if the laptop is booted on the expansion base- the drivers refusing to load until reconfigured.
64 bit- all seem to have that down well enough.
Thinkvantage. Only gotten it working under Ubuntu. Getting close with Fedora, having found several other resources- the information is on the ThinkWiki, but very buried- to the point where it's easier to find on other sites. The ACPI generated events, if trapped by X, can't generate a keycode because X can't handle keycodes higher than 255... OpenSUSE doesn't even give a ACPI key-generator application, and Fedora, like I said, is almost there. 
Wireless was a PAIN in Ubuntu prior to 8.04. It's much better now.
Bluetooth: There are instructions about to allow fn-f6 to shut it off without having to cycle through the fn-f5 combinations that drive the Gnome networking application int apoplectic fits. Ubuntu again seems easiest, but I'll know better when I play with it tonight on Fedora.
Automatic Screen Rotation: Ubuntu by far makes it easiest, but know there's scripting involved with whichever solution. Silly that there's no package- there are enough tablets out there. On Fedora, again, I'm ALMOST there, but can't seem to catch the generated ACPI event. Wacom rotation works well enough, but see the above comment about scaling, which becomes more obviously a problem when rotated.
HDAPS. Borked. Broken. Badly. I guess Kernel Developers never drop anything. PIA. Hey- I'm not in any way afraid to recompile drivers, but I HATE having to do it every time an update brings in a new kernel version, and I hate it when I get caught unawares during an update after just recompiling. It's happened. More of a general Linux grouse, I know.

So far as CODECs are concerned, I'll take the standard lumps. Yeah. I listen to media that costs money. Flash? The 64 bit stuff works pretty well, and isn't hard at all to install, except for finding the right plugin directory. Gnome has been a good experience across the board.
Amarok is just a nuisance. Bumbed me out, though, when Ubuntu stopped compiling it with the AAC support enabled.
OpenOffice. I'll admit it. I use Word styles. After working with Word for so many years, I've gotten good with it. I like it. I love the "This document was created with Word for OS/2" warning that shows up on my Mac when I read my old journals. OO is getting close, and 3.0.1 is the closest YET. Sure wish they'd show me the styles in the gutter like on Word... Ubuntu is not yet released with 3.0. That's a problem for me.

No distro is perfect. None do all I want. I can get close, though.

There is alot of easy sloutions for the problems you list above : 
DVD ? ubuntu-restricted-extras   should do it, I use VLC media player it plays Everything ?!
there is a PPA for Open office3 in 8.10 easy! and  it is included in Jaunty .
HDAPS , I agree, it breaks auto rotation too. 

try PPA for Amarok Nightly or the one from Kubuntu , maybe the one in Jaunty works too.
Autorotation , doesn't work for me so goot , have made a two line script instead and an shourtcat on my desktop and it works just fine so long, of course I would love a package for that! 
Thinkvantage ! how did you do it ?
 Dimming works fine , I just added a line somewhere , look for a  workarounds in launchpad's bug repports. It works fine in Jaunty out of the box.

And I most say I love Ubuntu and Xournal for the tablet part! :p

---

### Post by SnickerSnack on 2010-04-18
I'm not sure if you're asking a question, or what you expect in response, but:

    64 bit. _I opted for the 32 bit kernel since I had read that the 64 bit had some problems.  I intend on installing it on an extra partition once I have some time for it._
    Dimming of the screen for power saving. _Works out-of-the-box afaik._
    Automatic screen rotation. _I never bothered trying to get this to work.  I find it to be more of an irritation than a feature._
    Wacom functionality. _Works via instructions on thinkwiki, which you probably know._
    "Thinkvantage button" functionality (it needs to bring up a gnome-terminal session) _The keyboard shortcut tool adds it easily._
    Working wireless _Mine works without any special configuration that I can remember._
    Bluetooth, and an easy ability to shut it off.  _Also easy.  I have mine set to turn off on startup.  I've never used bluetooth, so I don't know if it actually works, though._
    HDAPS. _I don't know what that is._

Distro specific:
    Codecs. I'm a realist- I want to be able to watch a DVD, listen to MP3's and AAC's.  _MP3s work fine, though I don't have a dock, so I don't bother watching dvds on it._
    OpenOffice 3.0- I really like Word when used as it's supposed to be, and OO is getting close (Anyone want StarOffice for OS/2 install media? :-)    ) _Is there something wrong with 3.1?_
    Amarok. Like it. Always used it. Love it enough to build it from scratch because Ubuntu dropped AAC tagging support. _I've never used it._
    Gnome. It's gotta work pretty well, be pretty, and have a decent initial setup.  _Works fine.  Most of Compiz works too._
    Flash. Gotta work for YouTube.  _Works.  I don't recall having to do anything to get it working._

---

### Post by jdos2 on 2010-05-20
> 
Distro specific:
    Codecs. I'm a realist- I want to be able to watch a DVD, listen to MP3's and AAC's.  _MP3s work fine, though I don't have a dock, so I don't bother watching dvds on it._
    OpenOffice 3.0- I really like Word when used as it's supposed to be, and OO is getting close (Anyone want StarOffice for OS/2 install media? :-)    ) _Is there something wrong with 3.1?_
    Amarok. Like it. Always used it. Love it enough to build it from scratch because Ubuntu dropped AAC tagging support. _I've never used it._
    Gnome. It's gotta work pretty well, be pretty, and have a decent initial setup.  _Works fine.  Most of Compiz works too._
    Flash. Gotta work for YouTube.  _Works.  I don't recall having to do anything to get it working._



Thanks for reviving the thread and reminding me what it was like on distros just a year ago. So much has change in the year! So much has stayed the same, too. Nice that we got the nspluginwrapper stuff working very well so 32 bit Flash works, and that 64 bit Flash is available with just a little digging around. OpenOffice still doesn't have a style gutter. Compiz does finally work fine- and not just does it work well, but it can now be rotated, now that the Intel drivers are finally up to speed.

Thanks again for the memories.

---

### Post by SnickerSnack on 2010-05-30
> **jdos2 said:**
> Thanks for reviving the thread and reminding me what it was like on distros just a year ago. So much has change in the year! So much has stayed the same, too. Nice that we got the nspluginwrapper stuff working very well so 32 bit Flash works, and that 64 bit Flash is available with just a little digging around. OpenOffice still doesn't have a style gutter. Compiz does finally work fine- and not just does it work well, but it can now be rotated, now that the Intel drivers are finally up to speed.

Thanks again for the memories.

Heh, I didn't even notice the year.  I just saw April 11 and April 13, and figured that those were recent posts.

---

