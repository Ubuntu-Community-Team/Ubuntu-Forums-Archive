---
title: "[SOLVED] displayconfig-gtk is now obsolete. Help needed"
date: 2008-11-01
forum: General Help
---

### Post by adityakavoor on 2008-11-01
Ubuntu does not detect my monitor automatically.

Its Viewsonic 17 inch, widescreen.

The resolution is 1280x720.

displayconfig-gtk is now obsolete in Ibex, Which package do I use?

Please help!:confused:

---

### Post by SunnyRabbiera on 2008-11-01
you may have to manually edit xorg, i knew this might happen with some people.
here is hoping more options are made into the scren resolutions app in Jaunty...
For now i can only suggest going back to hardy, or if you want to keep current use Mint as it has a semi rolling release now

---

### Post by adityakavoor on 2008-11-01
So, there is no way Ibex could detect my monitor? 

I cannot afford a fresh installation again now.

Please suggest an alternative

---

### Post by SunnyRabbiera on 2008-11-01
> **adityakavoor said:**
> So, there is no way Ibex could detect my monitor? 

Sad :(

Yeh unless you manually configure stiff.
It was really a stupid idea to get rid of displayconfig without the improvements we were promised for jaunty.
I think it should be put back into the repositories, but it wont happen.
Like i said if its that much of an issue change distos, Mandriva and mint are good suggestions.

---

### Post by adityakavoor on 2008-11-01
> Like i said if its that much of an issue change distos, Mandriva and mint are good suggestions.

No way, I am not leaving Ubuntu.

Hardy re-install is what I would be doing it I don't find a solution in 24 hrs.

---

### Post by SunnyRabbiera on 2008-11-01
> **adityakavoor said:**
> No way, I am not leaving Ubuntu.

Hardy re-install is what I would be doing it I don't find a solution in 24 hrs.

Well if you use mint it will still be ubuntu, as Mint uses the same repositories and base as ubuntu.
Plus you will have access to more recent packages, like firefox 3.0.3.

---

### Post by wgrant on 2008-11-01
Why on earth would one change to another distribution just because there's no tool to perform the one-off resolution configuration for broken monitors!? That is a ridiculous suggestion.

See [the appropriate section of our X configuration documentation](https://wiki.ubuntu.com/X/Config#Adding%20undetected%20resolutions) for how to set it up manually.

Your incorrect Linux Mint suggestions are also unwelcome - Ubuntu 8.04 and 8.10 have Firefox 3.0.3, and Linux Mint is *not* Ubuntu.

---

### Post by SunnyRabbiera on 2008-11-01
> **wgrant said:**
> Why on earth would one change to another distribution just because there's no tool to perform the one-off resolution configuration for broken monitors!? That is a ridiculous suggestion.

See [the appropriate section of our X configuration documentation](https://wiki.ubuntu.com/X/Config#Adding%20undetected%20resolutions) for how to set it up manually.

Your incorrect Linux Mint suggestions are also unwelcome - Ubuntu 8.04 and 8.10 have Firefox 3.0.3, and Linux Mint is *not* Ubuntu.

But one should not have to configure it manually, I thought the goal was to make the user experience in Ubuntu easy.

---

### Post by wgrant on 2008-11-01
> **SunnyRabbiera said:**
> But one should not have to configure it manually, I thought the goal was to make the user experience in Ubuntu easy.

That is correct. However, we didn't have time to fit this support into gnome-display-properties this release. People who have this issue (mainly caused by buggy hardware) can perhaps stay with Ubuntu 8.04 for now, or add the whopping three lines to xorg.conf.

---

### Post by SunnyRabbiera on 2008-11-01
> **wgrant said:**
> That is correct. However, we didn't have time to fit this support into gnome-display-properties this release. People who have this issue (mainly caused by buggy hardware) can perhaps stay with Ubuntu 8.04 for now, or add the whopping three lines to xorg.conf.

well for you even though its just a few lines a lot of newcommers are going to be scared away because you have to add those lines to begin with.
I think that there should have been at least a transition package or something for beginners who want more recent packages but those who dont want to manually edit stuff just to get it working.

---

### Post by eaidoido on 2008-11-01
this may not apply to you (possibly not having an nvidia card), but the nvidia-settings tool has done wonders for my xorg.conf.

---

### Post by adityakavoor on 2008-11-01
Its not just 3 lines that have to be put into xorg.conf. There is a whole lot of work to be done.

This was my previous xorg.conf - Just after Installation

```
Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
```

After an hour of circus, I rewrote the xorg.conf and finally got things working.

Here is my new xorg.conf 

```
Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"Intel Corporation 82G965 Integrated Graphics Controller"
	Boardname	"intel"
	Busid		"PCI:0:2:0"
	Driver		"intel"
	Screen	0
EndSection

Section "Monitor"
	Identifier	"VA1701wb"
	Vendorname	"Plug 'n' Play"
	Modelname	"Plug 'n' Play"
   modeline  "1280x720@60" 74.48 1280 1336 1472 1664 720 721 724 746 -hsync +vsync
  modeline  "1280x800@75" 107.21 1280 1360 1496 1712 800 801 804 835 -hsync +vsync
  modeline  "1280x768@75" 102.98 1280 1360 1496 1712 768 769 772 802 -hsync +vsync
  modeline  "1280x720@50" 60.47 1280 1328 1456 1632 720 721 724 741 -hsync +vsync
  modeline  "1280x800@60" 83.46 1280 1344 1480 1680 800 801 804 828 -hsync +vsync
  modeline  "1440x900@75" 136.49 1440 1536 1688 1936 900 901 904 940 -hsync +vsync
 
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82G965 Integrated Graphics Controller"
	Monitor		"VA1701wb"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1920	1200
		Modes		"1280x720@60"	"1280x800@75"	"1280x768@60"	"1280x768@75"	"1280x854"	"1280x720@50"	"1152x768@54"	"1280x800@60"	"800x600@60"	"1440x900@75"	"800x600@75"	"1440x900@60"	"800x600@72"	"1600x1024@60"	"800x600@56"	"1680x1050@60"	"1680x1050@75"	"1920x1200@60"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
EndSection
Section "Module"
	Load		"glx"
	Load		"GLcore"
	Load		"v4l"
EndSection
Section "ServerFlags"
EndSection
```

So, getting back to the basics worked. Thanks to #ubuntu for the help.

Hoping for some respite in JJ.

:)

---

### Post by adityakavoor on 2008-11-01
> However, we didn't have time to fit this support into gnome-display-properties this release

You could have always retained displayconfig-gtk! I see no reason for having made that obsolete.

> People who have this issue (mainly caused by buggy hardware)

I do not agree. Same hardware worked like a charm right from the times Edgy Eft.

---

### Post by wgrant on 2008-11-01
> **adityakavoor said:**
> You could have always retained displayconfig-gtk! I see no reason for having made that obsolete.

It had a bad habit of breaking xorg.conf.

---

### Post by adityakavoor on 2008-11-01
> **wgrant said:**
> It had a bad habit of breaking xorg.conf.

Never happened in my case. Infact it was the one which managed xorg.conf and made life easier whenever I switched from widescreen to square.

Now, a bit of work is to be done each time I switch. :(

---

### Post by wgrant on 2008-11-01
> **adityakavoor said:**
> Its not just 3 lines that have to be put into xorg.conf. There is a whole lot of work to be done.

This was my previous xorg.conf - Just after Installation

[snip thoroughly excessive xorg.conf]

So, getting back to the basics worked. Thanks to #ubuntu for the help.

Hoping for some respite in JJ.

:)

I fail to see how much of that has anything to do with video resolutions. Most of that is for a tablet, the modules section is unnecessary, most of the stuff in the screen, serverlayout, monitor and device sections is cruft, and that's an excessive number of resolutions.

---

### Post by SunnyRabbiera on 2008-11-01
> **wgrant said:**
> It had a bad habit of breaking xorg.conf.

so does a lot of clueless newbies who have no idea what they are doing in xorg, at least displayconfig had a easy to use frontend.

---

### Post by adityakavoor on 2008-11-01
> **wgrant said:**
> I fail to see how much of that has anything to do with video resolutions. Most of that is for a tablet, the modules section is unnecessary, most of the stuff in the screen, serverlayout, monitor and device sections is cruft, and that's an excessive number of resolutions.

Having excessive is not a problem IMHO. Its very important to make sure that I have what I need.

BTW, Its the same Ubuntu that generated the above xorg.conf with a Gutsy Live CD

---

### Post by adityakavoor on 2008-11-01
> **SunnyRabbiera said:**
> so does a lot of clueless newbies who have no idea what they are doing in xorg, at least displayconfig had a easy to use frontend.

I agree!

---

### Post by madhusudancs on 2008-11-01
This decision to make displayconfig-gtk was simply an absolute non-sense. One could have done that after delivering all the features they had intended to in Jaunty Jackapole. This clearly shows that Ubuntu developers don't have clear vision or just not committed to their vision of making the Desktop Linux experience as easy and as intuitive as possible.

Its really disgusting to see that we are associated with such a stuff  where there is no commitment towards the community on which Ubuntu largely relies on. Wake up people, please don't be so arrogant towards the users. They are the most integral part of the community and reason for Ubuntu's growth today to this scale in such a short time. It may be hardly few lines of code for you people who are spending all your lives in millions of lines of code. But its definitely a potential scare away thingie for any newbie with the monitor. 

And I seriously feel you cannot call the hardware that sells like hot cakes in certain part of the world buggy, since it may not be so in your region. If something is selling well like this, its the responsibility to support it as best as possible. If its not possible it all then thats another issue altogether as in NVIDIA and ATI cards. But I don't think this is something impossible.

---

### Post by adityakavoor on 2008-11-01
This is where Ubuntu developers have to learn from KDE's vision.

They had specific visions for KDE 4.1 and made things happen. 

They do not wait for things to happen, they make it happen.

---

### Post by wgrant on 2008-11-01
> **adityakavoor said:**
> Having excessive is not a problem IMHO. Its very important to make sure that I have what I need.

BTW, Its the same Ubuntu that generated the above xorg.conf with a Gutsy Live CD

You said that a lot more than a few lines were required, and cited the excessive xorg.conf as evidence.

---

### Post by wgrant on 2008-11-01
> **adityakavoor said:**
> This is where Ubuntu developers have to learn from KDE's vision.

They had specific visions for KDE 4.1 and made things happen. 

They do not wait for things to happen, they make it happen.

And we didn't hear a single person complaining that KDE 4.0 was missing features, did we?

---

### Post by wgrant on 2008-11-01
> **madhusudancs said:**
> This decision to make displayconfig-gtk was simply an absolute non-sense. One could have done that after delivering all the features they had intended to in Jaunty Jackapole. This clearly shows that Ubuntu developers don't have clear vision or just not committed to their vision of making the Desktop Linux experience as easy and as intuitive as possible.

Your logic is faulty.

> Its really disgusting to see that we are associated with such a stuff  where there is no commitment towards the community on which Ubuntu largely relies on. Wake up people, please don't be so arrogant towards the users. They are the most integral part of the community and reason for Ubuntu's growth today to this scale in such a short time. It may be hardly few lines of code for you people who are spending all your lives in millions of lines of code. But its definitely a potential scare away thingie for any newbie with the monitor.

It was simply *not practical* to have an optimal solution for Intrepid. We don't not want to fix these things, we just didn't have time. Most of us have work or studies to contend with, as well as Ubuntu development work. And before you continue to complain that we don't have a commitment towards the community, we are part of the community! Nobody is stopping you from joining us.

> And I seriously feel you cannot call the hardware that sells like hot cakes in certain part of the world buggy, since it may not be so in your region. If something is selling well like this, its the responsibility to support it as best as possible. If its not possible it all then thats another issue altogether as in NVIDIA and ATI cards. But I don't think this is something impossible.

Whether it is popular or not has nothing in the slightest to do with how buggy it is. Bugginess is easily objectively defined.

---

### Post by adityakavoor on 2008-11-01
> **wgrant said:**
> And we didn't hear a single person complaining that KDE 4.0 was missing features, did we?

Exactly, that is the point I want to make.

Once KDE 4.0 failed, they set specific goals and worked towards it and as a result, KDE 4.1 is what we all see today, booming.

We are not here to discuss KDE 4.0's missing features, btw

---

### Post by madhusudancs on 2008-11-01
KDE 4.0 was a huge change altogether, a major release, whole lot of changes in the entire code base. Did Ubuntu have the same vision for Intrepid. If yes, I think I must admit that this is an error which will be fixed in Jaunty. But still for a distro 6 months is a long long long wait.

---

### Post by adityakavoor on 2008-11-01
OK. We will end this.

One last statement I want to make - 

Before removing a package, please make sure that an alternative solution is ready.
Thank you for your time and support.

---

### Post by forger on 2008-11-01
The package is still available at:
[http://packages.ubuntu.com/search?keywords=displayconfig-gtk](http://packages.ubuntu.com/search?keywords=displayconfig-gtk)

I believe you can get the hardy version on intrepid, although I don't recommend it either - buggy is buggy and should not exist! :)

---

### Post by adityakavoor on 2008-11-01
> **forger said:**
> The package is still available at:
[http://packages.ubuntu.com/search?keywords=displayconfig-gtk](http://packages.ubuntu.com/search?keywords=displayconfig-gtk)

I believe you can get the hardy version on intrepid, although I don't recommend it either - buggy is buggy and should not exist! :)

There are a lot of dependency issues in that package and cannot be installed. I did that first even before posting at this forum.

---

### Post by shookmon on 2008-11-05
Come on.. Removing existing functionality because it ain't perfect is no excuse. This will definitely have negative impact for those folks who can't afford the latest and greatest hardware. At the very least there should have been a warning on the download page stating that Ubuntu is no longer providing a GUI to fix video issues and a link to full instructions. Have you seen how many people have asked this question in the last few days? I wonder how many have simply given up and moved on to another product.

Perhaps your simply trying to create a market for support?

This is simply the product of letting the due date drive a release and not product readiness. I wonder if it's even possible to be a large software company anymore without shooting yourself in the foot.

---

### Post by adityakavoor on 2008-11-06
> Perhaps your simply trying to create a market for support?

hmm... Good Point

---

### Post by wgrant on 2008-11-06
> **adityakavoor said:**
> hmm... Good Point

Most of us are volunteer community members. I don't see why we'd want more people complaining to us.

---

### Post by pluckypigeon on 2008-11-18
what a depressing thread:(

people like me need displayconfig-gtk

now i can't change my default graphics card because i don't know how. now compiz fusion won't work.

linux for humans!

---

### Post by vancelongwell on 2008-11-27
Hi guys.  I've been using these forums for months.  This marks the first occasion where I felt compelled to post a comment.  So much so that I just registered, for the sole purpose of commenting here.

I don't have a dog in this fight, though I was researching *displayconfig-gtk* hoping it would solve my problem.  Without knowing for sure I believe this thread to be a conversation between a developer, and a user.  As such, my bias lies with the user.

I've been using Ubuntu, several distro's, for about six months now.  I've installed it on dozens of machines comprising a veritable plethora of equipment makes, and vintages.  Not once, not one single time, have my efforts produced a stable, truly usable, operating system.

Question?  Isn't the blanket ethos that is thrown over the entirety of the Linux community one of accessibility?  Let me ask that a different way.  Isn't Linux for poor people?  Isn't Linux here to offer alternatives to commercial operating systems?

Given that this is true, why is it such a surprise to Ubuntu developers that users of this product are trying to deploy it on, 'funky', equipment?  I can't get this stuff to be reliable on the i386 architecture it's supposed to be designed for.  I about laughed myself to death trying to stabilize it on the PowerPC architecture.  Old PC's and Macintosh products...hmm.  I wonder if ya'll do any market research?

So I resent the tone.  I really do.  I have precisely $0 invested in my entire system.  Which was my maximum allowable budget for my stuff.  Likewise, I volunteer at a non-profit refurbishing Pentium IIs, and IIIs, ya go ahead and laugh.  We then donate these computers to poor people who don't have any computer at all.

On that note, Ubuntu has been a tremendous boon.  That, however, is the rub.  Ubuntu creates a very high expectation, and then let's the user down in a snowfall of dependency miasma.  Perhaps less coders and more mathematicians, yes?  This is essentially free for my foundation to use, and I'm personally eternally grateful.  Nonetheless, an O/S that works would be so incredibly kool.

"Run an older distro", doesn't wash because there usually isn't as pressing a need for newer ones.  Time and time again I see references to editing the *xorg.conf* file, something I've done hundreds of times now, and it ends up the same way every time.  A dependency grenade goes off.  Probably one of the reasons it's being phased out.

So please give this user a break.  Clearly they are frustrated.  The auto detect features being consistently added to Ubuntu are breaking stuff that worked, not the other way around.  Furthermore, the attitude from support is one of, "Buy newer equipment".  I mean c'mon, what are we all doing here?  And what's this, "Oh feel free to do it yourself", garbage?  Are you deving for Ubuntu to contribute something, or to be gratified by users benefiting from your work?

With that said, I'm running Ubuntu 8.10 Intrepid Ibex on my Sony Vaio PCV-J200 AMD Duron 902MHz, 512MB RAM, integrated video...etc.. I'm lucky to have a ViewSonic Gfb90 VCDT23283-2S Flatscreen CRT that runs at 66Hz flat-out.  Why is that so bad?  *xorg.conf* is the problem, not DisplayConfig-GTK.  THAT worked awesome!  THAT wouldn't have been needed without the underlying problem with *xorg.conf*.  I wish you weren't obsoleting this as I would have loved to write an editor with a GUI.  If you say *xandr* I will lose my civil tone.  All that was needed was an editor that accepted input specs, and spat out the correct *Section* and *Modeline* syntax.  I digress.

Oh, well.  As long as I don't want to play a movie, listen to music, watch youtube, look at a .jpeg, write an email, or any other superfluous activities one never gets up to with a computer, Intrepid oughta do me just fine.

I'm poor and I thank Ubuntu developers for all they have done.  This is a truly awesome product, all frustrations aside.  If you guys would hire me, maybe I could afford a system that would run yer stuff better!

---

### Post by siecoban on 2008-12-03
I concur,  displayconfig-gtk or a similar tool needs to be part of the Intrepid release.  There is no excuse to replace a tool that was working fine with nothing.  The settings I had worked just fine in 8.04 and the upgrade to 8.10 broke them.  I tried manually setting the xorg with no success (Intel GMA 3100 graphics adapter, and Samsung SyncMaster 953w Monitor).  The driver seems to be working, but I just cannot change the resolution to 1400x900.  This really sucks, as I was trying to advertise Ubuntu in an enterprise environment, and I was getting close to convincing some key people... Now we are back to square one.  Hmm...

---

### Post by DJToman on 2008-12-03
> **wgrant said:**
> That is correct. However, we didn't have time to fit this support into gnome-display-properties this release. People who have this issue (mainly caused by buggy hardware) can perhaps stay with Ubuntu 8.04 for now, or add the whopping three lines to xorg.conf.
I have the same problem...trying to install and use Xubuntu 8.10 on a Dell C600 (actually using it now...). It has an ATI Rage 128 card. I have another C600 with 8.04, and it runs nicely, but I have to use WICD to manage the wireless card.  
I like 8.10; especially the improved network manager...but if I can't get the resolution to be correct, the release is useless to me. 
I'd be delighted to add the trivial 3 lines to xorg.conf if I could find out what the appropriate lines are.

---

### Post by Sensiva on 2009-09-18
Hello folks :D

This thread has been started about a year ago let's say. 
Intrepid and Jaunty released, and till this moment I wasn't able to fix my display settings in Ubuntu (Dell Desktop Optiplex 755 with Intel Q35 chipset). :D

I am not replying to state my problem, I am sticking with Hardy, I don't need Ibex, Jaunty or Karmic (I just tried Alpha6 and its display settings are screwed too)

What I am trying to say is, Something is wrong, and has to be fixed. Three Ubuntu releases and alot of people are having problems with their displays!!. Although it didn't exist in Hardy, Gutsy or Feisty. Seriously I stopped inviting anyone to migrate to Ubuntu, because once he/she sees low graphics mode messages, he/she get scared. And I am not going to tell anyone to mess with what is so called Xorg configuration file, because it will scare him/her more.

    How come with all those thousands developers all around the world and such issue still exist for twelve months. Why can't we do like old days? Download ISO, Burn, Boot, Install, Reboot then voila our lives are happy.

I hope this drama ends with Karmic (no? :confused:)

Thanks all for your support.
Sensiva

---

### Post by sbomer on 2009-10-30
I have the same problem with intel integrated graphics - in the past, displayconfig-gtk has solved the issue. However, I am now using karmic, and the resolution is stuck at 800*600 once again. How can I manually specify drivers in karmic?

---

### Post by Sensiva on 2009-10-31
> **sbomer said:**
> I have the same problem with intel integrated graphics - in the past, displayconfig-gtk has solved the issue. However, I am now using karmic, and the resolution is stuck at 800*600 once again. How can I manually specify drivers in karmic?
I have the same problem and asked a question about it in Launchpad

(not detecting your intel graphics adapter properly) and (not detecting resolution ranges of your monitor) are entirely two different things.

If you can enable desktop effects or start any 3D application then the kernel is driving uyour graphics adapter properly but yet supported range of screen resolutions isn't detected yet. which is my case.

If you can't enable desktop effects, then the driver in this kernel isn't serving you well, try this guide maybe it helps you [http://wiki.ubuntu.com/X/Config](http://wiki.ubuntu.com/X/Config)

---

### Post by markackerman8@gmail.com on 2009-11-21
I concur, displayconfig-gtk or a similar tool needs to be part of the ubuntu.

It is very sad that in this new era of graphics that a simple but effective gui for adjusting this is not available for us poor newbie whose first experience with Ubuntu invariably is problems with graphics or sound.

---

### Post by sparrowt on 2009-11-26
what are those easy 3 lines? ...oh and why has displayconfig-gtk 'obselete' when nothing has replaced it, because that has helped me fix screens many times? and its not an isolated '1 in a 100' problem because of all my Ubuntu installs on computers i've needed to do this many many times.

---

### Post by ericson578 on 2010-02-11
My monitor is not being correctly recognized, I have a Sceptre X20WG-naga, with a max resolution of 1680 x 1050.  I had this exact problem in 7.10 but was able to manually set the monitor to a Generic LCD with a resolution of 1680x1050 using the displayconfig-gtk command. I recently did a fresh install of ubuntu 9.10 and have spent several hours trying to increase my resolution beyond 800x600. My nvidia geforce 5700le was detected and the driver is working fine, if only I could select the correct monitor to allow higher resolutions :(

I read over this thread but I can't find a solution, only a lot of complaining that displayconfig-gtk was removed (I second that!).

What lines of code can I add to my xorg.conf file to allow 1680x1050, I wasn't able to find any good documentation on adding lines to this file.

Is there a solution for people using 9.10 to select the appropriate monitor?

---

### Post by ericson578 on 2010-02-11
I used gtf to figure out the modeline:

 Modeline "1680x1050_60.00"  147.14  1680 1784 1968 2256  1050 1051 1054 1087  -HSync +Vsync

But I can't figure out where this needs to go for ubuntu 9.10

---

### Post by ericson578 on 2010-02-11
wow, what a pain in the but that was! I wasted so many hours trying to figure out nvidia driver issues, then remembered it was a monitor detection problem.

I followed the instruction in this thread: [http://ubuntuforums.org/showthread.php?p=8302145#post8302145](http://ubuntuforums.org/showthread.php?p=8302145#post8302145)
to figure out how to create a proper xorg.conf file

I SHOULD have been able to select a generic LCD monitor that supports 1680x1050@60hz instead of all the file editing like I could have several releases ago...

---

### Post by Mayfairy on 2010-02-23
Thanks ericson578, going to see if that thread helps. 

Just installed 9.10 on top of my old 8.04 system and can't get higher than 800x600 resolution. Using the restricted hardware drivers only brings the resolution down to 640x480. 
Been trying for few hours to fix the drivers before I found some threads that lead me here. Some nvidia tool thinks my Acer AL1916 LCD monitor is generic CRT monitor so I'm strongly believing displayconfig-gtk would help in my case. 
So, we need it back! 

Anyways, going to see if I can configure the monitor by hand.

---

### Post by inyoka on 2010-04-12
Why is this thread marked solved? Has displayconfig-gtk been added to the repo, or has an reasonable alternative been suggested?  

displayconfig-gtk is essential (to many people)and as far as I am aware is still not available.  I know we are working towards a "Mac" like user experience, but we don't control the hardware like Apple can, for that reason alone we will always need something like displayconfig-gtk.  Either that or we go back to command line tweaking which I thought we were trying to avoid.

I have 75 pc's which are pretty much exactly the same, but for some reason 5 of them require me to manually override the default resolution.  This is a school, and we need to be able to cope with these issues which occur from time to time on cheap or old hardware.

---

### Post by clarkkillick on 2011-04-03
Yep, I've just run into this problem, too.   There are various PCs that I installed 8.04 on.  It looks like I won't be upgrading them to 10.04.

---

### Post by inyoka on 2011-04-04
Never fear, Shuttleworth in his infinite wisdom and push towards Mac'i'ness has removed display-gtk and replaced it with something much more modern and user friendly.  Its call xrandr, it doesn't use the archaic GUI system, but the much more modern 'Command Line Interface'.  

The excellent article below should help, and because its command line its scriptable so should ease your issues rolling out multiple systems.  Alternately use remastersys to role your own pre-configured Ubuntu with the new display settings in place.

[http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html]("http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html")

If you are in a school doing IGCSE do NOT upgrade to 10.04.  The combination of JRE, Sun/Oracle Report Builder and OOo is very unstable when doing Database work, and makes it impossible for iGCSE and A-Level students to use Ubuntu for exams.  

Be Warned!  (Yes its ironic that all three of these pieces of software are produced by the same company and yet do not work together.) Moving to LibreOffice, using different versions, or the GNU JRE does not resolve the frequent crashes when running reports.

---

### Post by tiger015 on 2011-06-30
This problem is not solved. Very sad to see, that instead of viable solutions being offered to newbies like me, some people just want to mark it "solved". I am getting more reasons to go back to other distros or even Windows.

---

### Post by inyoka on 2011-06-30
Yes I have to agree, although I went to Mac not Windows.   My family gave me a Mac Air for Christmas and despite my scepticism I have found it like Ubuntu but less awkward and more reliable.  It even provides VIM on command line, Ubuntu only ships with vi.

Although this particular displayconfig-gtk problem is just pig headedness from Ubuntu.  I get the impression linux as a whole is suffering a skills shortage brought about by devs moving to Android.

Ubuntu was the best thing to happen to Linux, but I now know there will never by a year of the Linux Desktop.  Google trends shows a distinct flattening/drop-off in interest since Android emerged.
android Blue, mac Red,  windows Yellow, ubuntu Green
[IMG]http://dl.dropbox.com/u/30316457/viz.png[/IMG]

90% of my servers have moved from Linux to the cloud, and my desktop contains a mix of Android, iOS, and Snow Leopard.  Sure the cloud servers use Linux, but theres little room left for Linux on the Desktop.  

I run a school in Indonesia and we are buying iPads not Netbooks, and when we refurbish the computer rooms I honestly do not know what we'll use next.  

Ubuntu is the sum of its parts and caused us MAJOR issues during our exam period with the combination of OOo, Sun/Oracle Report Builder and JRE crashing A LOT, it seriously effected ICT exam results.  I know strictly speaking thats not an Ubuntu issue, but OOo is a flag bearer for FOSS and a good office system is essential, and although LibreOffice will improve the situation I am sure many will not want to risk Linux in exams, and its the OS's in education that get traction.

---

