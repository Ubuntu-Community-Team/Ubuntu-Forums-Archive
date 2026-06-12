---
title: "Ati mobility radeon X600 Driver?"
date: 2011-11-01
forum: Hardware
---

### Post by Brolyfanatic777 on 2011-11-01
Hello all!

I come to you with another problem that needs solving!!

I've recently installed Ubuntu 11.10 on my HP Pavilion ZD8000, even more recently than that I installed a game called "Vendetta Online" to find out that it does not work correctly. its very sluggish. So I figured "hey it must have something to do with a proprietary driver, the generic one offered by Ubuntu just aint cutting it" So I investigated a bit into it. I found the catalyst control panel in the ubuntu software center The machine in question has an ATI mobility radeon x600 (128MB), but when I try to run it I get this:

[IMG]http://www.myspace.com/my/photos/photo/25841945/Album[/IMG]                                                                      
Initialization Error 
--------------------------------------------------------------------------------------------------------------------------------------

There was a problem initializing Catalyst Control Center Linux edition.  It could be caused by the following.
 
 No AMD graphics driver is installed, or the AMD driver is not functioning properly.
 Please install the AMD driver appropriate for you AMD hardware, or configure using aticonfig.
--------------------------------------------------------------------------------------------------------------------------------------



What to do? I haven't a clue!! :confused: please advise

thanks: Jim

---

### Post by Jahid65 on 2011-11-01
I think support for ATI X600 is dropped in fgrlx (Proprietary Driver) a long ago. My formar pc had X600 & it didn't work with Proprietary Driver in Ubuntu 10.04.

---

### Post by Scut_Farkus on 2013-01-30
Oh my gosh!  This almost my EXACT situation!  I was trying to play COGS.  When I launch the game, I see a screen for a split second and then...nothing.  No errors.  Just nothing.  I figured the drivers weren't correct (same as OP!).  Then started a very frustrating search for how to get the proper drivers installed.  I learned some interesting things along the way, but they're also very confusing to me.  I'm new to UBUNTU, but not to computers, so I feel I'm pretty good at following directions/instructions.  I have come across a whole mess of instructions for how to install these drivers, but NOTHING works.  It seems that things are installing okay, but they're never actually used.  When I follow the instructions for removing the drivers, I can see all kinds of things being taken out.  The system tells me helpful things like, "Hey..we're gonna remove all this stuff.  55megs of space will be reclaimed.  Do you wanna do this?  When I hit the "y" key it proceeds to blow away lots of stuff so I know it worked a little.

Some weird stuff:  I don't appear to have this XORG.CONFIG thingy.  I see a log file for it, but no XORG.CONFIG.  Not sure what that means, really.  When I installed 12.04 I told the installation to go ahead and grab anything it needed from the Internet as it was installing.  I can see an AMD driver in the Additional Drivers from Dash.  It was activated, so I deactivated it thinking it was interfering with the better drivers.  Apparently that's not the case.  Graphics worked better with that running, though.  I guess I'll just turn it back on and forget about x600 drivers?  There were no additional posts after Jahid65 mentioned that the x600 drivers were dropped, so is that really true?  Am I screwed?  I'd just like to use this card.  This was a beefy laptop in it's day (HP Pavilian zd8000).  I'd love to make it work properly.

Thanks in advance.  Hopefully someone'll have good news for me.

---

### Post by Yellow Pasque on 2013-01-30
When you install Ubuntu 12.04, the correct drivers (open-source radeon) are used by default. The only thing you can accomplish by installing some other driver is to make things worse. fglrx/Catalyst no longer supports your card, so that's a dead-end.

---

### Post by Scut_Farkus on 2013-01-30
GAH!  DANG!  Well thanks very much for the reply.  I appreciate it.  I know now that I don't need to go searching around anymore, so that's a bit of a relief.  Although now I need to get rid of all that stuff I added that's not doing me any good.  Any additional tips for how to remove everything FGLRX/CATALYST related, or shall I simply use the web sources I've already found?  They seem pretty thorough.

---

### Post by Yellow Pasque on 2013-01-30
I prefer this:
[http://wiki.cchtml.com/index.php/Ubuntu_Quantal_Installation_Guide#Removing_Catalyst.2Ffglrx](http://wiki.cchtml.com/index.php/Ubuntu_Quantal_Installation_Guide#Removing_Catalyst.2Ffglrx)

---

### Post by Scut_Farkus on 2013-01-31
Great, thanks.  This is the one I was going to use anyway, but it's nice that someone that knows what they're doing confirmed it for me.  I really appreciate the help Temujin!

---

### Post by eamoc on 2013-06-14
Hi [ 						 					]("http://ubuntuforums.org/member.php?u=327594") 				 				 					 						 	[**[COLOR=#000000]Temüjin[/COLOR]**]("http://ubuntuforums.org/member.php?u=327594"),
I was wondering if you could help me? I have 12.04 installed but I replaced the default Radeon X600 driver the X.org one, now I don;'t know how to get it back! Any ideas??
Thanks in Adv,
E

---

### Post by eamoc on 2013-06-14
Hi  				 				 					 						 	[**[COLOR=#000000]Temüjin[/COLOR]**]("http://ubuntuforums.org/member.php?u=327594"),
I was wondering if you could help me? I have 12.04 installed but I  replaced the default Radeon X600 driver the X.org one, now I don;'t know  how to get it back! Any ideas??
Thanks in Adv,
E

---

