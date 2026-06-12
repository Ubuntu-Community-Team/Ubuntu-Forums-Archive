---
title: "[SOLVED] The Complete Removal and Reinstaltion of Compiz in Ibex"
date: 2008-10-29
forum: General Help
---

### Post by employeeno5 on 2008-10-29
Hey all. I just has a great upgrade to Ibex.

Compiz is working great along with everything else with the exception of animations. The rollup animation is working, all others are not.

All other compiz plugins are fine.

I can redo my settings easily enough, I'm just looking to purge everything and start fresh to see if that helps.


I've diligently searched for and "completely removed" every single package in synaptic that's related to compiz. I then deleted all my ~/.compiz folder and my ~/.config/compiz folder and logged out.

I logged back in, and diligently reinstalled every single package. 
To my surprise, compiz remembered every last custom settting I had.

What am I missing? How to do I truly reinstall in a clean manner?

Thanks for any ideas and help!

---

### Post by employeeno5 on 2008-10-29
I've attached a screenshot of synaptic as an easy to list what I'm removing (completely).

Anyone see anything missing? Any suggestions? 

I hope the screenshot is helpful; let me know. :)

---

### Post by employeeno5 on 2008-10-30
Can anyone at least identify in which package or file compiz settings are stored? I'm just trying to get back to a clean install with default settings.

I'm deleting and removing everything I'm aware of/can find. Clearly I'm missing something though...

I'm also curious if anyone else is having this issue. I found several posts about this happening between Gutsy and Hardy upgrades, but none for Ibex yet.

In the Hardy cases it had to do with how compiz read parameters changing in between releases. That's why certain customized animations did not work while all other plugins remain fine. 
The problem is (if this is even the root of my issue), is that I don't know what new ones would look like to work of. If I can do a clean re installation, than I can just modify what it provides to my liking. 

Many thanks again! :)

---

### Post by employeeno5 on 2008-10-30
I found what I was missing, and as predicted it solved my problem and animations are working fine!


The files I had not yet found and deleted were in ~/.gconf/apps/compiz

So there you go. 
I feel a bit silly all on my own with this one, but maybe it will help someone else out with a similar upgrade issue.

Happy Halloween everyone!

---

