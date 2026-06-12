---
title: "Mandriva One 2009"
date: 2008-10-15
forum: General Help
---

### Post by jimbo99 on 2008-10-15
Yes, this is the Ubuntu forums.  In light of the fact that Mandriva just released their product in competition with Ubuntu 8.10, I thought I'd download it and see if these guys truly had been making progress.

Essentially I wiped an 8.10 beta install and installed Mandriva.  The process of install and the use of the live CD was a nice touch though it is very much like Ubuntu.  They did a good job on the installer, though there are times that it is a pain.  Other elements of the live CD do lack polish and swapping hardware (say for a better video card) can create real problems, especially for someone who knows nothing about computers.

I think the goal of any OS should be to provide access to the "function" hardware provides and to allow users to be productive with it.  I don't think much else is required nor desired, at least not for the average Joe.

With that in mind I'll cover some mistakes they made, though, I don't think it'll matter much to the Ubuntu 8.10 product about to be released.

The installer worked well, except when it came to the prompt where it asked whether I wanted to remove unnecessary packages.  I clicked on the option to display more info.  It did this and presented me a list of extremely cryptic names of packages.  Unfortunately we humans don't think in those terms.  It would have been best to use some form of the packages description such as the title instead of listing cryptic names.  My first attempt at this I told it to go ahead and remove them.  It did, I assume.

During the install it could have asked me for the root password and the name of the user account/password.  Instead, it waited till the first reboot to ask for these pieces of information.  Not that this is necessarily wrong but it has been demonstrated by Ubuntu that it does make more sense to ask for this information during the install.  And frankly, it should be one of the first things done just in case something goes wrong with the installation.  That way you have a user name and password you can rely on to resolve problems.

At the end of the install you are told to terminate your session, remove the CD and restart.  This worked only partially.  You finish th installer, then you click the menu button and say "leave".  At that point it begins the shutdown process, but near the end it hangs and won't continue.  You get no feedback as to the success of the shut down.  Hit the reset button, eject the CD and let it reboot.  That works, except it doesn't set the video resolution correctly.

To correct this I enter the control panel type program from KDE 4.  I switch the resolution to the proper resolution.  Sometime thereafter, after spending time working with it, I reboot again.  When it comes up the resolution is back to the incorrect one.  I have to open the display device in the control panel, at which point it immediately recognizes the resolution I set and adjusts the screen, even without me setting it.  It wouldn't do this in the restart, I had to do this myself, yet not totally by myself.

I then decided to look at compiz.   I had a crappy old ATI based card in the machine and wasn't happy so I grabbed a used FX5200 to see if that would work.  It didn't.  So I went to download the nVidia drivers.  nVidia has it's own set of problem on their website as no drivers were available for linux as I was taken to a 404 page message.

So, I hit Google and searched for nVidia driver installation for Mandriva one 2009.  I was taken to a site that explains that you need only run the software installation/removal program.  From there a lot of bothersome prompts were displayed mostly about setting up software sources and at the end it gave me some weird message about software source `. being set up correctly.  Whatever that is.

Once done I searched for nVidia and selected the driver that looked correct.  It was the 173 version, even though there are more up to date versions avail.  I figured the 173 is fine as this is an older card.  I then asked it to install and was prompted by a bunch of dependency prompts.  I let those be chosen.  I was then prompted about the fact that there were features of this driver and it wanted to know if I would like them set up automatically.  I said yes.

Upon reboot I got no where.  Just a blinking cursor in the upper left corner of the screen.

I was going to dump it at this point as I figured that if this thing couldn't allow the easy swap of video cards they just weren't there  yet.  But I got the notion that I would reinstall the OS with the card installed first.

So, I rebooted with the Mandriva One 2009 CD and chose to have the compiz feature installed.  When I hit the live CD desktop I tested the compiz to see if it was working.  It was.

I began the install again and when I got to the point that it wanted to remove unneeded packages I chose to see the list.  I saw that it had the nVidia drivers listed as unneeded so I was going to back out.  I looked for a cancel button.  None.  Only an OK button was listed.  I decided to click the X to close the window and that didn't just close the window, it closed the whole installer.

I started over and when I got to the point where it prompted me to choose to remove the alleged unneeded packages I chose to let them be.

I completed the install and when I got to end it had the same problem.  Would shut down properly.  So I hit reset and pulled the CD.

At the desktop I tested to see if compiz was working.  It was.  I tested to see if the nVidia drivers were listed in the list.  They were.  I choose to install.  They installed.  Reboot worked.  I had the nVidia drivers installed and compiz was working.  But, when I went into the nVidia control panel and was going to set the video resolution manually it generates some error.

I also noticed compiz is very choppy on screen whereas in Ubuntu even with an fx5200 it is pretty speedy.  I have a couple older Compaq notebooks that have crappy video chipsets that run compiz better.

I also noted that the version of compiz is an entirely old version.

I also noted that the nVidia version of their drivers, the proprietary ones that the software installer installed also were entirely way to old.

Also, working with the clock in the lower right corner of the screen I could not find a way to make it say AM/PM.  I don't want to see a 24 hr clock.  I also couldn't find how to change the calendar to be a 7 day week starting with Sunday.  Theirs is set to display Monday as the start of the week.  I really don't have the time nor desire to hunt that info down.  I just want it to work.

KDE 4.1 looked nice.  They put so much time into making this part nice that they forgot to work on the other elements and to fix performance issues.  I really felt like I was back 6 years in the past struggling with Linux again.

Ubuntu is FTW.  There's no doubt that the distribution is getting better but Mandrake is still entirely too messy and focus is going into the wrong areas.  Maybe it's just that they are a bit uneven in how they apply their focus.

I'd recommend against Mandrake due solely to the fact that there are better distributions that are much more polished, such as Ubuntu.

---

