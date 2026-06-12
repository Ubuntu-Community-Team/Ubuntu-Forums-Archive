---
title: "Swap Not Being Used On Hardy"
date: 2008-07-13
forum: Hardware
---

### Post by ajeetraj on 2008-07-13
Hello everyone, 

I just installed Conky and the first thing I noticed that my swap space is not being used. I just installed new Hardy few days ago. I then checked the system monitor and then I realized, my swap is not being used at all. My computer has 1GB of RAM but as now i realize that the computer is really slow. 

Can someone please help me with this, because it is really making me annoyed. 

Thanks in advance!

ps: if you need me to put any output from my computer then I will happily do that, but I didn't know what to do.

---

### Post by silkstone on 2008-07-13
Swap will normally be used only if your computer runs out of RAM - it's like virtual memory. My swap is never used.

As for speed, if you're finding it slow there may be other issues. 1GB is usually plenty to run Ubuntu, although 2GB is even better! Do you have Desktop Effects enabled (System > Preferences > Appearance)? Many people like the Compiz eye candy, but it can slow your machine down quite a lot, especially if the graphics card isn't all that fast. I had a play with all the effects and then turned everything off. You can turn the effects on again at any time if you really want. :)

---

### Post by ajeetraj on 2008-07-13
Well, I do have the desktop effects turned on but its at very low settings. I understand that swap is only used after the system runs out of the RAM, but I never had any problem like this that my system became slow when I had only few programs running. I have rythmbox, firefox and pidgin running with the scale + show desktop + Expo effects running. 

My computer was faster with 512MB RAM than 1GB. I just upgraded it to 1GB a few days ago and I installed Hardy on it again just to have a fresh install. 

Any Ideas?

---

### Post by silkstone on 2008-07-13
Look at Processes in System Monitor and see what's running. Also what load is the CPU under at idle - is anything hogging the processor?

Is the new RAM you bought 100% compatible? Have you tried putting the old RAM back in?

---

### Post by ajeetraj on 2008-07-13
Well, first of all, thank you for coming back to help me. 

I just did what you asked me to do, and I see that Firefox is taking 140MB of the RAM and then the rest of the programs are just using around 24MB each (there are 3 of them). 

The compiz effect is just taking 8MB, so I don't think that's causing the problem or stressing my computer. 

Regarding the RAM, I had 512 and then I added the new 512MB later. Yes, its was the same RAM what I had in my computer before. I checked everything on the DELL website and I bought the same RAM as my computer has. 

My computer has been up for almost 3 hours by now and still only 0% of the Swap has been used. 

once again, thanks for the help.

---

### Post by silkstone on 2008-07-13
The swap isn't the issue - if you have a reasonable amount of RAM, the swap may never be used.

What matters most is how much of the CPU the applications are using - not how much RAM they take up. You should be able to see in System Monitor > Processes the %CPU for each application that is running. It may be that something is hogging the CPU and slowing the machine down.

---

