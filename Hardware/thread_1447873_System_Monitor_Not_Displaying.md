---
title: "System Monitor Not Displaying"
date: 2010-04-05
forum: Hardware
---

### Post by kshawkeye on 2010-04-05
I feel that this issue is graphic related, anywhere, I really have no idea how to explain it other then I cannot view my System Monitor. Here is a link to a screenshot that shown my issue, thanks! [http://cid-c4075b6ccbf45620.skydrive.live.com/self.aspx/.Public/Screenshot.png](http://cid-c4075b6ccbf45620.skydrive.live.com/self.aspx/.Public/Screenshot.png)

---

### Post by kshawkeye on 2010-04-06
Hey, I could really use some help, does anyone have any ideas?

---

### Post by rcaca0 on 2010-04-06
What is it that you are trying to view?  What type of graphic card do you have?

---

### Post by kshawkeye on 2010-04-07
That's me "viewing" System Monitor.

Based on [http://h20000.www2.hp.com/bizsupport/TechSupport/Document.jsp?lang=en&cc=us&taskId=120&prodSeriesId=96357&prodTypeId=321957&prodSeriesId=96357&objectID=c00009293](http://h20000.www2.hp.com/bizsupport/TechSupport/Document.jsp?lang=en&cc=us&taskId=120&prodSeriesId=96357&prodTypeId=321957&prodSeriesId=96357&objectID=c00009293) I have:

ATI Mobility™ Radeon™ Graphics

• 4X AGP for enhanced video,  graphics and 3D performance

• Enhanced DVD playback and 3D  performance

• Maximum internal resolution of up to 1600 x 1200 x  16M; with external monitor - 1600 x 1200 non-interlaced

• 32 bit  color provides up to 16M brilliant colors

• Video Player (AVI,  MPEG2 and others)

 • S-Video TV-Out

• MPEG2 full-motion  video playback

• Microsoft® Directshow

---

### Post by rcaca0 on 2010-04-07
Are you using the proprietary drivers for ATI Radeon card?  I'm asking this because I ran into something somewhat similar with Nvidia (blank screen at first then add to load in safe driver mode, with this the screens acted funny until I loaded the proprietary drivers for Nvida).  
 
Also dumb question and sorry about asking since you probably all ready did this but have you tried to run the live cd on your notebook to check if you run into this problem?

---

### Post by kshawkeye on 2010-04-07
[quote=rcaca0]Are you using the proprietary drivers for ATI Radeon card?[/quote]

The only "drivers" that I am using are the ones that installed when ubuntu installed onto my system, no other drivers have been installed. 

If you know where I could find proper drivers for my system could you please post a link?

[quote=rcaca0]have you tried to run the live cd on your notebook to check if you run  into this problem? 	[/quote]

I'm not sure what you mean, I just installed ubuntu 3 days ago, so I'm really new to all of this.

---

### Post by rcaca0 on 2010-04-07
I was afraid that you were going to ask where to get the drivers (Community we could use some help here).  

I am not good with the command lines so I am not going to waste your time having you run some commands.  I always have to take some time to read them and ask questions on this forum to understand them.  

With that being said go to System --> Administration --> Hardware Drivers

It should tell you if you are running any proprietary drivers.  I'll do a little bit of research to see what I can find just in case we need to go to the command lines.

---

### Post by rcaca0 on 2010-04-07
Forgot, as for the live cd, you just start up your computer with the Ubuntu cd in the dvd-player and have it boot from it.  Similar to how you install the OS system.  On the menu it should say something about using Ubuntu without install (something like that).  Try it and see if you run into the same problem..

---

### Post by 2hot6ft2 on 2010-04-07
> **rcaca0 said:**
> System --> Administration --> Hardware Drivers

It should tell you if you are running any proprietary drivers.
Right it will show if any are active and if any are available. You may want to run this first for the most recent drivers to show up
Open a terminal
Applications > Accessories > Terminal
and run
```
sudo apt-get update
```
You will have to enter your password which wont be displayed just type it in and hit Enter
When it finishes close the terminal and go to
System --> Administration --> Hardware Drivers
and if it recommends one select it in the top window and click on Activate at the bottom.
It will download and install it, then it will require a reboot (it will tell you).

---

### Post by kshawkeye on 2010-04-08
System --> Administration --> Hardware Drivers found nothing, even after doing:

sudo apt-get update
I'm going to try putting the disc in and booting up that way, we will see if that works.

---

### Post by kshawkeye on 2010-04-08
[quote=rcaca0]Forgot, as for the live cd, you just start up your computer with the Ubuntu cd in the dvd-player and have it boot from it. Similar to how you install the OS system. On the menu it should say something about using Ubuntu without install (something like that). Try it and see if you run into the same problem..[/quote]

Tried it, issue still remains in testing mode.

---

### Post by kshawkeye on 2010-04-10
Any ideas? Anyone?

---

### Post by rcaca0 on 2010-04-11
So were you able to install the drivers?

---

### Post by efflandt on 2010-04-11
That is an old laptop.  That may be from not enough video RAM, but it does not say how much video RAM is has or if it is shared RAM.  How much system RAM do you have?

I had that issue with an older desktop with 32 MB ATI video RAM.  Other alerts were also cross hatched.  I think it has something to do with direct rendering, but cannot remember how to find the post with details about that.

You might try using Synaptic to install **fglrx-kernel-source** and see if that helps.  I think that helped me, but I eventually put Qimo for kids (based on Ubuntu 8.10) on that PC and gave it to my niece for her twin boys.

---

### Post by vlaptops on 2010-04-11
I have the self same problem with a Compaq Evo N160 running 9.10, which was fine until I ran a system update last week and then I got the striped display for System Monitor.  All else is fine, it gets on the internet, plays flash content (slowly) and does a decent fist of playing DVDs full screen.
 
I suspect that something in the update broke some part of the graphics support. It's a Radeon Mobility M, ATI again and I'm sure that it's not supported by any of the latest Catalyst drivers. So something must have been broken with the update.
 
Shame as I went back to the N160 (1.0GHz)  as I'd just updated a Compaq Evo N800v (1.6GHz) to the 10.04 Beta on Thursday and was just giving it a rest as it was having some boot up bugs and the screen effects weren't running (where they were on 9.04)  and all I use my laptops for is to quickly boot up and get my travel checking and news updates before I go to work. (Eithe boots just as quick as my wife's NC10 Notebook on XP and the 14" screens make the morning websearches a little more civilised).
 
I'll keep an eye on this thread to see if anyone has a solution.

---

### Post by kshawkeye on 2010-04-13
[quote=rcaca0]So were you able to install the drivers? 	[/quote]

No, I was unable to find any that worked.

[quote=efflandt]How much system RAM do you have?[/quote]

256 MB PC133 SyncDRAM, upgradeable to 1.0GB.

[quote=efflandt]You might try using Synaptic to install **fglrx-kernel-source** and see if that helps.[/quote]

It was already installed when the problem was discovered.

[quote=vlaptops]I'll keep an eye on this thread to see if anyone has a solution.[/quote]

Same here, but I did quite extensive research on the problem, regarding my system and graphics card, and in most cases the solution was to buy new hardware, or in this case, a new laptop.

---

### Post by rcaca0 on 2010-04-13
I would hope you don't have to get either new hardware and a new laptop.  Community does anybody have an idea?
 
I did find someting on ATI cards: [http://www2.ati.com/drivers/linux/linux_8.16.20.html#172394](http://www2.ati.com/drivers/linux/linux_8.16.20.html#172394)
 
I don't know if it will help, I have not had a chance to read it all.

---

### Post by vlaptops on 2010-04-17
Yeah thanks, I tried the ATI route but the the software is saying that it's not identifying the GPU (i.e. no ATI card found). I suspect that the Radeon M on the N160 is a little older than the list that you linked.
 
It doesn't matter, both laptops are free and recovered from very broken kit so Ubuntu is fine, I ditched Ubuntu 10 beta on the N800v back to 9.10 but doing that killed the DVD playback (dodgy Optical drive contributes to that), no big deal as I use it for quick internet access and it has broken speakers so audio is through a pair of Logitech auxilary speakers which take time to set up and put away. 
 
Otherwise the N160 works fine playing my DVDs such as Blackhawk Down and for impromptu internet access downstairs, otherwise I have 2 XP machines, 1 for games upstairs and another for streaming iplayer and youtube to the main TV and Hifi downstairs.
 
Not being able to see System Monitor is only a small niggle compared to the benefits of the 2 free Ubuntu OS's I'm running.:lolflag:

---

### Post by vlaptops on 2010-05-01
I've just updated the Evo N160 (the older laptop) to Ubuntu 10.04, noted that System Monitor is now fine, just running it through the day to see if there are any issues with anything else and if not will update the Evo 800.
 
I did have problems with the 10 Beta very recently but this release seems good, also very dinky new loading screen and colours, familiar steps but now more "CBBC" style of graphics (UK users will understand this reference).

Will get back to this post if I have any more old Radeon M related issues

---

### Post by vlaptops on 2010-05-01
10 install is okay and everything is working except for 3 or 4 system freezes so far, will try a re-install after lunch and make sure it wsn't a glitch.....shame this is a PIII 800 Mhz system, looks pretty plays You Tube, keeps crashing running Firefox and any other programme, shame as I think I have 1Gb memory.

---

### Post by vlaptops on 2010-05-04
It was fairly simple, 10.04 sets the display by default at mid-settings with some visual effects, the PIII N180 never did effects under 8.04 or 9.04, a quick setting to no visual effects means that there have been no freezes since. Everything now works, System monitor displays, DVD can now be played after installing libdvdcss, etc.
 
Now both the N180 and the N800v have 10.04, one clean installed from an iso and one upgraded. The upgrade path took over 2 hours, the clean install around 30 mins.:D

---

### Post by ghilliker on 2010-05-04
I am running a Compaq nc6400.  It worked super with 9.10 and external KDS 17" external monitor.  After upgrading to 10.04 the monitor no longer works at all (either flutters or displays "Mode Not Supported").  No amount of tweaking helps.  The main display on the laptop goes through all kinds of girations before it finally stabalizes.  It is curious that on boot, the external monitor displays the boot sequence just fine, then garbage.  It looks like the drivers are hosed.  One wonders if there is some way to use the 9.10 drivers???
 
George

---

### Post by vlaptops on 2010-05-05
Wow, that;s a way newer machine than even my TV server, it's a Centrino Duo based laptop with proper modcons but running Intel Graphics.
 
Incidentally, we were having trouble with ancient Mobility Radeon chipsets and under Ubuntu 9.04 the display on "System Monitor" from the Administration Bar with just static in the window.  In the end we installed 10.04 and with a couple of tweaks we were back in action.
 
For your problem, try a clean install again, with the monitor disconnected, get the laptop screen running smoothly, I'd bet 10.04 handles the Integrated Intel Graphics straight out of the box (or broadband connection as most of us do). 
 
Once you are happy with the set up, restart with the monitor attached (is it off the VGA or S-video connector ?(can't help you with the latter) and just go through the monitor set up screen.
 
Good luck mate.):P

---

### Post by ghilliker on 2010-05-05
Any way to avoid the new clean install?  I hate to spend 4-6 hours installing software, not to mention the download time to reinstall Ubuntu Studio.
 
George

---

### Post by vlaptops on 2010-05-06
Sorry G,
 
Didn't realise that you were using Ubuntu Studio, unfortunately a clean install will ensure that you've got rid of any underlying problems or mad, bad or unstable dependencies from an upgrade (In my case it only took 30 minutes clean install on the older laptop 800Mhz (PIII) vs over 2 hours for the online upgrade on the newer (P4 1.6Ghz mobile CPU) and then ages to get reading resttricted format DVDs going again .
 
I also cheat bigtime and use my MS Windows machine and download the iso images and burn them to Disc before trying installs on any of the Ubuntu laptops.
 
You also might want to take your problem to a new thread as this one was about a programme window not displaying properly and not about a add-on monitors, also ourt problem was solved by installing Ubuntu 10.04, whereas it looks as though yours was caused by Ubuntu Studio 10.04 (which may have a multitude of separate issues).
 
I'd search for Ubuntru Studio problems first and then narrow it down to problems with attached monitors.
 
 
Regards
:lolflag:
 
Victor

---

### Post by ghilliker on 2010-05-07
vla...
 
I downloaded the most recent 10.04 ISO and tried a little experiment (without Ubuntu Studio).  First I booted the 10.04 CD.  Same problem, the laptop display flutters and the KDS 17" monitor is recognized as a Plain Tree Systems 17.  Nothing will get it to display correctly - tried changing refresh frequency and resolution, ZIP!  I then booted from the original 9.10 CD and wallah! the laptop display came up fine and the KDS 17" external monitor came up perfectly as a PTS 17, 60Hz, 1080x760.  One can assume that PTS and Plain Tree Systems are the same but 10.04 is clearly has a video driver issue in the kernal or at least x11.  I have looked at the x11.config file and in both cases (9.10 and 10.04) the file is total vanilla - no entries at all.
 
It appears I will have to go back to 9.10 if I want to use the external monitor or until something is fixed.
 
George

---

### Post by vlaptops on 2010-05-07
George,
 
Looks like you did all you can do for a little while.  perhaps look out in the forums for issues with the Intel GMA chipsets and 10.04.
 
Incidentally, the much older and slower N160 (I keep typing 180) updated to 10.04 actually works with both my Sony LCD TVs 32" and 15" and my Mitsubishi Diamond Pro 15" CRT on on the VGA port, so I'm stumped at what's wrong with your set up.
 
Good luck mate.
 
Regards
 
):P

---

