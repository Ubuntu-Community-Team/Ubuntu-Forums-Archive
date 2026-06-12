---
title: "DVD issues 8.10, 64bit"
date: 2008-12-15
forum: Hardware
---

### Post by RatPackSopra on 2008-12-15
I recently bought a new Asus X83VB-X1 laptop and was slightly bummed that it had Vista Home Premium 64bit installed, but I digress. 

I decided that I had put off installing ubuntu for too long and decided to make the plunge last week. To my total delight I had it up and running on my laptop through a Wubi folder in no time flat and was very tickled that by the end of the day I had everything running smoothly with even a very successful install of Compiz-Fusion to add some true eye-candy to the picture. Then it happened ...(cue scary music) I tried to play a DVD and it didn't go well, as a mater of fact the LG GSA-T50L DVD player suddenly went dead ...no sign of life at all. I shrugged my shoulders and tried unsuccessfully to find a line of code that might "wake it up," but had no luck. I will mention that I'm a newbie to Linux, but I've worked with computers for over 20 years, so I'm not clueless, but I might as well be in the Linux world. ;)

After having no luck waking the drive up I relented, rebooted into Vista and the drive functioned perfectly. I went back into ubuntu and tried to load another dvd only to have the same error pop up telling me I was missing codecs (I had installed what was suggested from the irc channel earlier) and then the drive went dead again, so repeat the reboot into Vista cycle and all is well yet again until I arrive back in ubuntu for the 3rd try. I'm sorry that I can't remember every single step that I took as I was receiving some guidance from the irc channels and it becomes a little cloudy remembering every step, but when the drive died this time I rebooted and tried to reload ubuntu wondering if the drive would come back without going into Vista and then I would do some more reading. The only problem was ubuntu refused to load at all and gave me some error message (which I scribbled down hastily thinking the screen might time out.) I've typed it out below and I'm not positive that every character is totally correct as I was scribbling as fast as I could in order to make sure I got as much as I could.

I also want to mention that I tried two different media players, Totem and VLC.

[I]-Boot ARGS (cat/proc/cmdline)
  -check root delay=(did sys wait for long enough)
  -check root=(did sys wait for right device)
-Missing modules (cat/proc/modules;ls/dev)

Alert! /dev/disk/by-uuid/548E01C920cb0dab
does not exist Dropping to a shell

Busy Box v1.10.12 (ubuntu 1:1.10.2-1ubuntu6)
built in shell (ash)

enter help for a list of built in commands
(initramfs) [58732129] ata2:comrest failed (errno=-16)
[63.756106] ata2:comrest failed (errno=-16)[/I]


Now maybe I just wasted a ton of my time typing all of that, but I'd rather cram it all in here and it serve no purpose than make someone waste their time asking for it.

When I had to resort to unplugging my laptop and removing the battery to get the unit to do anything but sit frozen on the screen of info from above I knew I needed some help. ;)

I booted into Vista and at that point even Vista did not see the drive, so I picked up the phone and called Asus tech support and we removed a line of code from a registry setting, rebooted the machine and it reinstalled the DVD drive and has worked flawlessly ever since. 

I know that I'm a bit over my head with this problem and really need some advice ...maybe the drive is bad, but its odd that it works perfectly in Vista, maybe its just simply a compatibility issue, maybe it has to do with some little thing concerning ubuntu 64bit, but regardless of what I think I really need some good advice.

---

### Post by carml on 2008-12-15
I suggest you to try what follows.
I'm using Ubuntu since a month,and one of the first things I've done was to download the codecs listed under Applications->Add/Remove->Audio & Video,named Gstreamer.
Using all these codecs I'm able to play videos and DVD also under Ubuntu,as I were under Windows;tell me if it works for you or look for suggestions on the forum if someone else can help you. :p

---

### Post by RatPackSopra on 2008-12-15
Thanks for the suggestion, but unfortunately I've already installed that exact set of codecs. 

This issue really has me a bit sick as I was very happy with what I was seeing inside the ubuntu environment. :( I was taking it for a good test run trying out lots of different types of programs and seeing how much I could get done using the OpenOffice suite of apps. 

I really want this ubuntu experiment to work out and I even fantasize about a 100% move if I can get over the hurdles that are in place at the moment and broaden my knowledge base. 

I'm hoping that I have picked the correct spot to make this post and if by chance it would be better suited somewhere else I'd more than happy to move it.

---

### Post by carml on 2008-12-16
Excuse me,I read again your first post,and I've a doubt:<<To my total delight I had it up and running on my laptop through a Wubi folder>>.
Do you mean you installed the Live version of Ubuntu? :confused:

---

### Post by RatPackSopra on 2008-12-16
Please excuse my ignorance, but I'm not sure I'm following what you mean by Live version. I downloaded the cd from the ubuntu site and installed it by using a Wubi folder. I was told that its an easier way to install ubuntu on a vista machine and it was running VERY stable until I ran into this DVD issue. 

I'm afraid this one issue may keep me away from going any further with ubuntu and that is sad. I'm holding out hope that someone will swoop in and give me some ideas on how I might resolve this problem ...keeping in mind that I'm a newbie, so I really don't where else to look.

---

### Post by carml on 2008-12-16
Don't worry about your ignorance,it's a brief estate of the mind,followed and replaced by knoledge.:p

---

### Post by bodhi.zazen on 2008-12-16
Well, that seems like a bigger issue then a malfunctioning DVD player.

First, while wubi is an easy way to get a feel for Ubuntu, if you see what you like I suggest you go ahead and perform a standard install, including repartitioning.

Second, from your post I can not tell if it a DVD problem or a codics issue. "DVD" is fairly generic, codics are usually needed when playing a file , like a mp3 file or video file.

Can you describe what you were trying to do exactly ?

Last, it sounds as if you entered a few commands, but without knowing what you did it is hard to solve.

---

### Post by RatPackSopra on 2008-12-17
Late last night I rebooted into ubuntu and used it for a couple of hours until it was time to crash. Everything has continued to work very well with the install I have done through the Wubi folder and I have a hard time grasping that the install has anything at all to do with my DVD problem.

I have tried out lots of software and everything I've tried has worked like a charm, but before I turned in I decided to tempt fate and load an mp3 through my CD/DVD drive instead of a DVD and the second I tried to open it with Totem the drive went immediately DOA with no lights showing and the drawer will not even open, which is the way it has acted every single time regardless of what I've tried to load into the drive or what player I've used. I have not rebooted and decided to let the unit sit over night running ubuntu which after waking the computer up this morning is just as stable as its been since the very first time I ran ubuntu. a week ago. Of course the CD/DVD drive is still DOA, but everything else is working fine.

When I mentioned that I didn't remember every single thing/step I had tried I was referring to the exact order of things not sudo type commands as I never found any of those to run. There is not some "thing" that I did that I left out as I've tried to be as complete in my description as I can possibly be. 

There has to be a compatibility issue with this LG brand GSA-T50L CD/DVD drive as all the players installed in ubuntu play any media located anywhere on my system (internal HDD, external HDD, or USB flash drive) just fine until I load anything into the CD/DVD. I've really put every type of media to work every different way I can think of (streaming radio feeds, Mp3's, movies, PDF's, doc, txt, etc...) and once again they all work like a charm. By the way the drive is still dead this morning, but every piece of media I've tried from every location is still working to perfection in spite of the CD/DVD drive still being dead this morning.

I'm not sure what options one has if a piece of hardware is not compatible in ubuntu? Can someone explain if there are any options or is it a dead end street?

Once again I'd like to thank anyone who takes the time to help with this problem!

---

### Post by Dalkir on 2009-01-30
Hi all!  I actually ran into a similar problem with my new ASUS laptop (oddly, an X83VB... imagine that).  After a few hours of slamming my head against the wall, I found that the native SATA setting in the BIOS was causing Ubuntu to have fits.  Random HD and DVD problems, locking and all kinds of fun.  Just change the SATA setting in the BIOS to "Compatible" instead of "Enhanced" (and be prepared to re-install Vista with the new BIOS setting..... if you don't, the SATA setting will make it blue screen every time.  After a clean install (Vista first, then Ubuntu if you want to dual-boot)), both Ubuntu and Vista should run fine.  

I would also recommend that you NOT use Wubi if you plan on dual-booting.  Just use the guided install from the CD, and resize your partitions to whatever you want..... the installer handles everything, sets up Grub no fuss (Grub is a boot menu program, lets you decide what OS to launch).

I also found that the alternate CD worked a bit better than the Live CD after another install (I tend to break things quite often.... for me, that is half the fun of using Ubuntu! :G ).

Good luck!

---

