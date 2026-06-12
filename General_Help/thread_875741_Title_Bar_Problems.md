---
title: "Title Bar Problems"
date: 2008-07-31
forum: General Help
---

### Post by izzygalvez on 2008-07-31
This is my first post here. I've recently decided to try out Ubuntu over Windows (too much frustration!), and I'm loving it so far! It runs great!

However, my video card doesn't seem to like it as much. lol

I have an **nVidia GeForce 615**0.
I installed the drivers using **EnvyNG**.

The first problem I had was whenever I moved my mouse over the title bar buttons (minimize, max, close) they would flicker, and most of the time the title bar would then turn completely white.

I changed the window theme (**System > Preferences > Appearance**), and some themes didn't have the above problem. But I liked the **Ubuntu Human theme**. I found out installing **Emerald** and **Compiz Fusion** may help.

So, I did that, and my title bar problem seemed fix...

But I noticed in some applications, such as **OpenOffice.org Word Processor**, the title bar buttons would still flicker. The title bar didn't turn white, but the buttons still acted funny.

I couldn't find a fix online, so I opened up the **Compiz Fusion Icon > Settings Manager **to see if I could find anything that might be causing this problem. No luck. So then I checked out the Emerald Theme Manager, and voila! I unchecked "**Use Button Fade**" and "**Use Button Fade Pulse**", and it worked! No more flickering! (I didn't like the fade effect anyway)

And now for my current problem...
When available, the **Context Help** button in the title bar doesn't show. It looks like a patch of random colors.

It's not a big deal, but I would like to fix this if it is possible.

- Izzy

---

### Post by PmDematagoda on 2008-07-31
I think this is more a problem with the Nvidia drivers than anything else because 169.12 worked like a charm with compositing, but when I installed the 173 series things took a turn for the worse. If you have 169.12, I recommend you giving that a try and seeing if you get the same problems on it.

---

### Post by ad_267 on 2008-07-31
If this is a major problem you can turn off desktop effects and just use Metacity as a window manager by going to System - Preferences - Appearance - Desktop Effects - None.

I've had similar problems with a 6600GT using the default drivers from the repositories, whatever they are. But this doesn't happen very often.

The worst that's happened is the whole contents of a window in OpenOffice has gone black.

---

### Post by izzygalvez on 2008-07-31
Right now, I've simply disabled the Context Help button, by going to **Emerald > Edit Themes > Buttons**. It seemed like the best thing to do, since that was my only problem I was still having with the title bar.

Though, if I start having problems again, I think I will give the nVidia **v169** drivers a try. I don't have them downloaded, so how would I go about installing them correctly?

- Izzy

---

### Post by bobsmith2 on 2008-09-11
> The first problem I had was whenever I moved my mouse over the title bar buttons (minimize, max, close) they would flicker, and most of the time the title bar would then turn completely white.

I had the exact same issue. The Emerald fix didn't work for me, so I thought I'd post what did work in case someone else runs into this. 

Right click on the desktop and select "Change Desktop Background" > "Theme" > "Customize" > "Window Border". Select a different Window Border. The problem completely disappeared.

---

### Post by tobyadams on 2008-11-01
had a fiddle with the settings of the theme and used different borders, worked like a charm, here's looking now at nvidia to update those drivers!

---

