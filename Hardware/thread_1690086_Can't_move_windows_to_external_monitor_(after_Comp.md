---
title: "Can't move windows to external monitor (after Compiz install)"
date: 2011-02-17
forum: Hardware
---

### Post by demii on 2011-02-17
I installed Compiz today and since, I am unable to drag windows from my laptop to my external monitor (they window will just move to the next workspace of my laptop). I am also unable to open programs on the external monitor because they instead open on my laptop. All of Compiz's effects seem to work just dandy on both monitors. 

I'm sorry if this was already asked. I spent the last 20 minutes searching ubuntuforums and Google but didn't find much. Though, I did see something about X servers being separate workspaces or something along those lines. 

Any help would be greatly appreciated. 

I'm running Ubuntu 10.10 on a MacBook Pro 4,1.

---

### Post by Stephann on 2011-02-17
There are features like cube and such that allow you to drag windows to a different virtual workspace.  It can take a while to figure out which option was activated to cause the problem.

Also, the beta nVidia drivers have an option to run your system with two separate X servers.  I think it's great (for me) because I don't drag windows, and it lets me run a movie full screen on one monitor, while working on the other, but obviously that's not what you want.

---

### Post by demii on 2011-02-17
Well the problem only started after I installed Compiz. Everything worked swimmingly before. 

As far as nVida drivers, I do have two separate X servers (at least, I'm pretty sure I do). However, I can't get any application to the external monitor because 1.) I cannot drag the window and 2.)When I click the application on the external, it opens on my laptop.

---

### Post by demii on 2011-02-17
Ah, it appears it's because nVidia was set to "Separate X screen" instead of "TwinView". 

I unplugged my monitor, restarted Ubuntu, plugged it back, and enabled the second monitor as TwinView. Everything appears to be in order now.

---

### Post by Stephann on 2011-02-17
Good deal; I thought that might be it, since my macbook pro uses the same nVidia driver system.

---

