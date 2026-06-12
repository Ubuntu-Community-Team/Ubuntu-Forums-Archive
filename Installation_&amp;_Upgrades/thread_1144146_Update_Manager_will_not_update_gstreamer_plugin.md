---
title: "Update Manager will not update gstreamer plugin"
date: 2009-04-30
forum: Installation &amp; Upgrades
---

### Post by SteveDee on 2009-04-30
Since upgrading to 9.04 the Update Manager includes:-
gstreamer0.10-plugins-bad
under Distribution Updates, but this never gets updated. The checkbox is ticked but greyed out.

The Synaptic Package Manager shows that 0.10.8-1 is installed and that 0.10.11-2 is available.

Can anyone explain whats happening?

---

### Post by mattlach on 2009-04-30
> **SteveDee said:**
> Since upgrading to 9.04 the Update Manager includes:-
gstreamer0.10-plugins-bad
under Distribution Updates, but this never gets updated. The checkbox is ticked but greyed out.

The Synaptic Package Manager shows that 0.10.8-1 is installed and that 0.10.11-2 is available.

Can anyone explain whats happening?

I have this same problem.  

[[img]http://farm4.static.flickr.com/3395/3490061692_18c944d414_o.jpg[/img]](http://www.flickr.com/photos/mattlach/3490061692/)


I find it odd that it lists updates that are greyed out and don't update.

---

### Post by SteveDee on 2009-05-01
I'm glad I'm not the only one.

I think the greyed out component is due to a conflict, because if I mark gtreamer0.10-plugins-bad for update in Synaptic, it warns me that gstreamer0.10-fluendo-mpegdemux will be removed. I don't want to risk this at the moment, so hope to find more details somewhere.

Is there any Help on the Update Manager? If so, I've yet to find it. This often surprises me, that someone has produced a great app but could not find the time to add a Help button and a few lines of text describing functionality.

---

### Post by theonlywalks on 2009-05-01
i have the same problem, basically...  although mine is unticked and I cannot tick it, and it is also greyed out.  At one point I was able to click the update and view the description and it says in the description something along the lines that it is unstable and they are working on releasing a stable update...  although I can no longer click it and view the description, so I'm going from what I read last night.

---

### Post by rtimai on 2009-05-15
I'm having the same symptoms as previously reported in Update Manager and Synaptic Package Manager. I read elsewhere that there may be a bug in apport. Hopefully posting here will allow me to monitor this issue. Still, I'm having far fewer issues than I've ever had in Windows, though.

I'm running Ubuntu 9.04 Jaunty. I updated my profile, but this post doesn't refresh my profile, apparently. Uh. No. I guess it does.

---

