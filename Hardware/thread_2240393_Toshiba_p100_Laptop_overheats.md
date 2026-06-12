---
title: "Toshiba p100 Laptop overheats"
date: 2014-08-19
forum: Hardware
---

### Post by bryan27 on 2014-08-19
Good Day Folks, 

I had an old laptop I wrote off, Let my kid play with it unpowered for years, It had XP on it and was painfully slow and more or less had become useless. 

As a project more for fun than anything I pulled it out of the closet and have been playing with it a lot lately since I put Lubuntu on it.  I feel like I have a new laptop! I have been having so much fun. 

The only problem I have been having is that it gets really hot if I use it very long at all.   I think I hear the Graphics card fan going because  the temp on card according the Nvidia software maintains 80 degree's, however the laptop gets up to 104 pretty consistantly after some use. 

Once in a while I hear the fan gear up high, for a few seconds and then it stops.

I am searched hours through posts and there there was a lot of talk of fans and this laptop way back in 2007 obviously with older versions of Ubuntu.  

I am looking for anything new that might give me direction, My understanding of linux isn't a lot.  But I am learning more every day. 

If you answer and need more details, Please try to be specific with how I find any data you might need, as I said I'm very new to linux. 

Thanks so much, 

Bryan

---

### Post by weatherman2 on 2014-08-19
I have seen rare cases where a laptop runs hotter than it should in Ubuntu, and with a "watt meter," I can even tell it is using more power running Linux than Windows.  But this is an unusual case - most laptops I've put Ubuntu consume about the same power at idle in Ubuntu as they do in Windows.

More likely, your problem is a physical issue not an "Ubuntu issue."  Laptop cooling systems - metal heat sink with "fins", exhaust vents through which the fan blows out hot air, etc. - tend to get clogged over time with dirt and dust. This causes them to run a lot hotter than they should.  (that's also bad for the laptop over time too, to run excessively hot.)  After cleaning, a clogged laptop where the fan ran all the time due to heat will become rather quiet and cool again.

What you should do is take the laptop apart and clean out the heat sink area.  This can be intimidating work if you aren't used to taking something like this apart.   Getting to the heat sink area that cools the CPU (and maybe the graphics card) varies depending on the design.  Sometimes it's very easy to get to from the bottom of the laptop, but in most cases I have seen, you have to take the keyboard off and some of the attached brackets etc. to get to the heat sink and fan from the top.  If you go to YouTube, you might be lucky enough to find a "disassembly guide" for your laptop, showing you exactly how to take it apart.  You might also seek out a service manual, which would explain exactly how to do it as well.

---

### Post by bryan27 on 2014-08-19
Hrmm.. That is a great idea, I have no idea why I didn't think of it.. Going to type this... Then turn it off and then whamo ripping this pig apart! Thanks.. I'll you ya'all know.

---

### Post by Jeff_Malterre on 2014-08-20
Glad someone else posted on this recently because this is a very old issue with the p100.  I had it fixed, but with the recent upgrade to 14.04, I'm having overheating issues again.

[http://ubuntuforums.org/archive/index.php/t-771223.html](http://ubuntuforums.org/archive/index.php/t-771223.html)  This helped me before, however I don't think I'd need to do this again, thought it'd be a one time thing.

I disassembled my current ACPI and checked it with a copy of my old one, they are identical.  I also checked it for errors and there weren't any, just a couple irrelevant warnings that I remember I had before while it was working.

SYMPTOM: While watching a video in full screen I'll watch the temperature of the GPU reach up to 69[FONT=sans-serif][COLOR=#252525]°C and the video starts to choke (pretty sure that's NVIDIA slowing it down to lower the temperature.)  If I change the size of the video window and make it smaller (to ease up on the GPU) the GPU temperature starts to decrease and the video starts playing smoothly again.[/COLOR][/FONT]

[FONT=sans-serif][COLOR=#a9a9a9]NOTE:  I did recently uninstall libav and installed ffmpeg, then switched it back again (re-installed libav package.)  Half of my videos won't play anymore.  I don't think that's related but I figured I'd throw it in just in case.
[/COLOR]- fixed, unrelated[COLOR=#a9a9a9][/COLOR][COLOR=#252525]

EDIT: [/COLOR][/FONT][FONT=Verdana]I too haven't cleaned this laptop - which is what, 8yrs old?  I'm sure it's disgusting inside.[/FONT]

---

