---
title: "[SOLVED] Reduce Firefox CPU load"
date: 2008-07-26
forum: General Help
---

### Post by natirips on 2008-07-26
How do I reduce Firefox' CPU load? It clogs up to 100% when loading simplest html pages even though I have a powerfull 64-bit dualcore proccessor running at 800HMz (everything else including 3D games runs smoothly).

---

### Post by RealPSL on 2008-07-26
I had a similar problem with firefox but it was related to running sites with flash. Using flashblock to [http://flashblock.mozdev.org/]("http://flashblock.mozdev.org/") to control the number of flash sites improved the performance significantly.

---

### Post by MatthewPlanchard on 2008-07-26
There's also always the option of [Swiftfox]("http://getswiftfox.com/"). It's tailor suited to your computer's architecture, resulting in faster load times and less system usage.

---

### Post by natirips on 2008-07-27
> **RealPSL said:**
> I had a similar problem with firefox but it was related to running sites with flash. Using flashblock to [http://flashblock.mozdev.org/]("http://flashblock.mozdev.org/") to control the number of flash sites improved the performance significantly.
I have already turned off flash, totem, vlc, ... plugins. It now loads only basic content (text, images, and very few other things like java).

---

### Post by natirips on 2008-07-27
> **MatthewPlanchard said:**
> There's also always the option of [Swiftfox]("http://getswiftfox.com/"). It's tailor suited to your computer's architecture, resulting in faster load times and less system usage.

I'll be giving it a try.

---

### Post by natirips on 2008-07-27
> **natirips said:**
> I'll be giving it a try.

My CPU (AMD Turion 64 x2) is not listed. Which do I use? 

Besides, > All Swiftfox builds are 32-bit, including the AMD64 build.How does that speed-up things? So far with my expirience a same application built for 64-bit runs much faster then the same application built for 32-bit.

Edit: Sry, didn't notice *THAT* chart.

---

### Post by natirips on 2008-07-27
> **MatthewPlanchard said:**
> There's also always the option of [Swiftfox]("http://getswiftfox.com/"). It's tailor suited to your computer's architecture, resulting in faster load times and less system usage.
So fine, I switched to Swiftfox, but it's still CPU intesitive, and moreover, I can't access firefox any longer:confused::mad:. And I wondered why it wasn't in the repository...

Edit: At some point firefox poped out instead of swiftfox, said that 4 new plugins were insalled, which I never asked it to do, but then again, I can't find what would those new plugins be (I can't see anything diffrent in the list). However, now I can't access Swiftfox anymore. What kind of malware did you sugest me?

Edit2: I found a way to control which opens (although I still can't open both at the same time), but now each time I swich them, they keep "updating" and installing "new" plugins.

Edit3: Incident closed - I uninstalled it (Swiftfox) (hopefully once and for all). That sowftware was just to unstable.

---

### Post by natirips on 2008-07-30
For some inexplainable reason it got faster again (like the old prerelease versions of Firefox 3) after a recent update, even though it said there were no changes...

Anyway, my problem got solved in a manner as misterious as it arose. So I'm still clueless why did it start eating my CPU and I'm even further clueless why did it stop eating the CPU.

But then again, it's not like I really care so long as it works - that's why I'll be closing this thread.

@RealPSL and MatthewPlanchard: Thanks for your effort anyway.

---

### Post by soxs on 2008-07-30
> **natirips said:**
> For some inexplainable reason it got faster again (like the old prerelease versions of Firefox 3) after a recent update, even though it said there were no changes...

Anyway, my problem got solved in a manner as misterious as it arose. So I'm still clueless why did it start eating my CPU and I'm even further clueless why did it stop eating the CPU.

But then again, it's not like I really care so long as it works - that's why I'll be closing this thread.

@RealPSL and MatthewPlanchard: Thanks for your effort anyway.

Firefox got really nasty, I switched to opera and it pimped (in fact decreased by 50% (just feeling)) my loadtimes.

---

### Post by sdennie on 2008-07-30
I'm not completely sure what you meant in your first post but, if Firefox gets the CPU to 100% while it's loading a page, that's not really a bad thing as long as it's only for a brief moment.  If it pushes it to 100% for a long period of time, something else is likely happening.

---

### Post by natirips on 2008-07-30
> **vor said:**
> I'm not completely sure what you meant in your first post but, if Firefox gets the CPU to 100% while it's loading a page, that's not really a bad thing as long as it's only for a brief moment.  If it pushes it to 100% for a long period of time, something else is likely happening.

I meant the CPU suffers heavy load (CPU usage jumps to 100%, and doesn't drop even after the page has fully loaded). Even disabling all my custom-installed plugins didn't help. Anyway, it's fine now.

================
> **soxs said:**
> Firefox got really nasty, I switched to opera and it pimped (in fact decreased by 50% (just feeling)) my loadtimes.

I just don't like Opera's interface for some reason I can't explain (a matter of taste). BTW, I can't find it in the repos (I have set the Add/Remove programs to show all available applications).


=================
Why is it that good ideas always come up the moment you solve your problems? :| :S

---

### Post by r4lly on 2009-10-11
I think this link will help 

[http://allredb.wordpress.com/2009/05/07/speed-up-flash-and-firefox-in-ubuntu-jaunty-904/](http://allredb.wordpress.com/2009/05/07/speed-up-flash-and-firefox-in-ubuntu-jaunty-904/)

[IMG]http://ubuntuforums.org/images/icons/icon12.gif[/IMG]

" dont worry , be happy "

---

### Post by natirips on 2009-10-11
> **r4lly said:**
> I think this link will help 

[http://allredb.wordpress.com/2009/05/07/speed-up-flash-and-firefox-in-ubuntu-jaunty-904/](http://allredb.wordpress.com/2009/05/07/speed-up-flash-and-firefox-in-ubuntu-jaunty-904/)

[IMG]http://ubuntuforums.org/images/icons/icon12.gif[/IMG]

" dont worry , be happy "

Or in short, just add a CPU scaling applet and a CPU usage monitor applet to your panel, and if the CPU usage is high and CPU speed is low, set the speed to a higher value manually. (I often do this for MPlayer).

Off topic: What actually happened to flash? Back in 90s I used to play YETI sports on a win98 box with 266MHz CPU, 32MB RAM and all went smoothly. The very same .exe file ran very choppy on a 1,8GHz CPU, 1GB RAM winxp box. Flash being slow is not an Ubuntu 32-bit/64-bit issue...

---

