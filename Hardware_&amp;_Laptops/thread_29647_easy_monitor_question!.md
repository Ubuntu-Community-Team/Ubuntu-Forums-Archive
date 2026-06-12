---
title: "easy monitor question!"
date: 2005-04-25
forum: Hardware &amp; Laptops
---

### Post by veritas366 on 2005-04-25
This has to be an easy question but I can't find the answer by searching.  When I installed FC3 sometime ago, although it didn't do most things as well as Ubuntu, it did allow me to choose my monitor from a list and then get the added screen sizes and refresh rates that entails.  How do you do this in Ubuntu?  I know how to go to the x11.conf file and manually make the changes, but isn't there a list or menu of common monitor types so I don't screw it up!  .  For example, I am not actually sure of this monitor's refresh rates.  And while I can look these things out, picking "viewsonic-A70" off a list would be a lot easier.  Thanks!

---

### Post by nad on 2005-04-25
Keeping a list like this up to date would be a Herculean task.

Volunteers anyone?

---

### Post by veritas366 on 2005-04-25
Further searching showed me that there is not such a feature.  I wonder how FC3 has it?  I guess it filters in from the paid employees who do Redhat.  Well, I revise my question. Finding supported monitor resolutions and refresh rates is easy.  But I also see references to things like "vertical sync rates" and this has me flummoxed. In general, if I know the refresh rate and screen res. sizes, is that all I need to add?

---

### Post by nad on 2005-04-25
Yes, but you do so at your own risk. It is possible to fry your monitor with over-optimistic timings. One of the development problems is ensuring that a usable screen is working at installation without doing just this, even if it is sub-optimal. Some displays when probed actually lie about their abilities which makes auto-configuring a good setup even more difficult.

---

### Post by veritas366 on 2005-04-25
But if the specs for my monitor say 90 hz, I'm okay adding that, right?  that's the question...I'm not going to randomly change the numbers.

---

### Post by nad on 2005-04-25
There are no guarantees. 90hz is certainly a reasonable value. The first place to search for your monitor's specs is the paperwork that came with it, failing that, the manufacturers site.

---

### Post by veritas366 on 2005-04-25
I guess I"m not making myself clear.  I have the manufacturer's specs.  the confirm 90hz.  I'm just wanting to make sure there is nothing else besides that value that I need to add in the xorg.conf.

---

### Post by nad on 2005-04-25
Are you adding or changing values?

You can start a flame war mentioning whether you need to tweak an X config file.

---

### Post by veritas366 on 2005-04-25
I'm confused about the possibility of a flame war. My monitor, according to documentation, can support 90hz refresh rate.  The automatic config went only to 60.  If my documentation says it can support 90 (and I'm getting some flicker, so I really want to change this) can I simply change that number to 90 in the xorg.conf.  The second part of the question is, is that the only thing that needs to change or do other things have to change as well?  I suppose I could reinstall fc3 temporarily and use their pulldown menu...copy the xorg.conf they generate and paste it into my ubuntu.  

I guess what I keep trying to ask is:  in ubuntu, is there something bad that can happen when changing the default refresh rate to the one that is in the manufacturer specs?

---

### Post by nad on 2005-04-25
[QUOTE=veritas366]I guess what I keep trying to ask is:  in ubuntu, is there something bad that can happen when changing the default refresh rate to the one that is in the manufacturer specs?[/QUOTE]

I'm sorry to be playing devils' advocate here but originally you were looking for guarantees. There are no guarantees.

Is there something bad in ubuntu that could happen? Search these forums for issues people are having with their X server. Enough said.

It is highly unlikely that the monitor will suffer from this modification. Edit the HSync and VRefresh together and /or individually and try the new settings out. This is the only way to test your configuration in your computer with your components and your os, software and hardware. The point that I am trying to make is that we are all beta testers. Unless you find someone with an identical setup configured in an identical way, there is no way to know for sure. You do remember to make a copy of a good existing configuration first?

---

### Post by veritas366 on 2005-04-25
I don't know where I asked for guarantees...but of course if there were pull down menus, that would be close.

I don't have my documentation with me, but will that give me vertical and horizontal sync rates, correlated to refresh rate?  Are those two even related? I don't know what those sync rates do.  I haven't searched on that yet, however. Obviously my original question had an easy answer, which, unfortunately was:  you can't do that in ubuntu.  I know there are threads about adjusting your xorgs for refresh rates...

---

### Post by gil-galad on 2005-04-25
Usually I look up my monitors specifications on the internet to edit my x.org file.  Search for "<monitor model> specifications" on google and you should be able to find the information you need for the horizontal and vertical range.

---

### Post by nad on 2005-04-25
No, no, no. Of course you can do it in ubuntu. But only you can tell us if it works with your setup. If it doesn't just change it back.

As far as your questions regarding sync and refresh settings. Yes they are dependent upon each other. Your X server computes timings based on the parameters it is given, through automatic probing or manually in a config file, and will output a display if it has calculated valid values. One way to interactively play with these timings is the xvidtune program included on your computer. Read the warning and proceed, with caution. It will expose you to some of the technical issues involved in creating a workable display. Other than that, there are tens of thousands of technical documents out there regarding video issues and pcs as the video subsysytem is integral to interfacing with any modern personal computer, unless of course you have special needs, but I digress.

---

### Post by veritas366 on 2005-04-25
LOL...I have never been so mininterpreted before.  What I said this thread was about was being able to take a pulldown menu with a list of monitors on it and pick my monitor to automatically adjust all the values we are discussing.  THAT is what I said is obviously not possible in Ubuntu, though it was in FC3. THAT was my original question! I know you can change these values manually, which I also mentioned in the original post.  Sheeesh.

My questions had more to do with which values had to be changed other than the refresh rates to make the new refresh rate work.  anyway, I will do some of my own research to get a better understanding of all this. As I mentioned, I know there are threads about this already..this thread started out on a different question, which was is there a GUI way to pick your monitor.  In my own defense, having done exactly that in FC3, I don't think it was an unreasonable question.

---

### Post by nad on 2005-04-25
No defense needed. As I am not familiar with fc3 and you mentioned the xorg.conf file I figured that you knew how to use the command line. I didn't understand your issue.

Perhaps with all of the xorg problems lately, the devs will consider a gui to handle test configurations. At this point probably half of the ubuntu users are already famiar with linux. If  they want to make it simple to use, a gui will be necessary.

Do try out the xvidtune program. It will help you to begin to understand all of the inter-relations involved.

Regards,

---

### Post by Mat10 on 2005-04-25
I think maybe the question is best answered by saying the maximum refresh rate is different for each screen resolution.  The higher the resolution the less the refresh usually is.  If you start out and take a look at 800x600 you will notice a nice steady screen with little distress to the eyes.  The refresh is high and the screen blanking is not seen.  As you go higher in resolution the screen blanking becomes noticible and hard on the eyes.  Good monitors go to 1600x1200 with that 90 refresh, most cheaper monitors that have the 1600x1200 don't go that high and it is very noticeable.  This monitor I use now is four years old and an ADI.
Almost time to retire it and go with a 21 inch, but you can bet I won't be looking for the cheapest out there, I'm looking for the best resolution with highest refresh rate available.  If I have to pay extra then that's what I will do.  My eyes are 57 years old and they know what refresh means.    :-P

---

### Post by Mat10 on 2005-04-25
I'm sorry , I should have also recommended to google the manufacturer of your card , and the specs you ask about are there.  I used Fedora Core 3 also and I know what you were describing about the choice list.  I also used six other distros and each were a little different in their approach to installing the best monitor module.  One distro was at least three to four years behind for KDS which is the monitor I use on my Linux machines.  The most important thing is the highest resolution and refresh your monitor can support.  I think it has been a few years since monitors were damaged from bad settings.  In windows I have had a few things go wrong and the screen starts going crazy.  Always gaming and not normal everyday work.  There was a time not to many years ago just leaving an unattended or idle screen would burn images onto your monitor.  This was called ghosting, and that problem has been done away with due to the newer lower energy and different Tube building technologies.  I still have that old habit of using a screen saver and I worry about it to this day.  Now of course I don't think this is really an issue, even though you will find many savers with every operating system out there.

Once you get your settings where they should be you will like this distro and this Debian based package management is just wonderful for dummies like me.  I saw a few post on other forums about the Debian management and I was wondering what they were talking about.  With Ubuntu everything is more refined and so eassssy.

Tom

---

### Post by flanker on 2005-04-25
Try these settings,

        HorizSync       30-91
        VertRefresh     50-85


Modern monitors are not easily damaged by incorrect refresh rates.

---

### Post by veritas366 on 2005-04-25
Mat10:  Thanks. Ghosting...lol...I'm old too!  

And thanks to all. I'm going to simply try the simple xorg change of the horizontal and vertical changes.  If that doesn't work, I'll leave it alone till I can feel more comfortable. Me no like flicker.

---

### Post by veritas366 on 2005-04-25
My eyes THANK YOU!!!!  I'm not even going to worry about upping the resolution one notch to 1280 right now.  I'll take what I've got!  Thanks again.

---

### Post by X5-655 on 2005-09-07
If Ubuntu read the monitors own DDC information (built into the monitor itself), it could figure it out itself.  This is how Windows does it, Plug-and-Play.

---

