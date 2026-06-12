---
title: "Update to Gnome 2.26"
date: 2009-03-19
forum: Installation &amp; Upgrades
---

### Post by chanders on 2009-03-19
Is there an easy way to do this on Intrepid? Like a repo or PPA?

Thanks!

---

### Post by ElTimo on 2009-03-19
I was wondering the same thing. There is, of course, Garnome, which pulls all of the source from git (not sure about this, correct me if I'm wrong) and compiles it all for you. but I'm guessing you're like me and don't feel like wading your way through dependency hell just to get a newer version of gnome. I'll look around and see what I can find.

---

### Post by yochaigal on 2009-03-19
I too would like to know!  
I thought maybe of finding out how people updated to 2.24 (without upgrading to intrepid) and maybe adjusting that!

---

### Post by ElTimo on 2009-03-19
Is that actually possible? I remember wanting to do it way back when Hardy was new, but I kept getting pointed back to compiling from source. If you could provide me with a link to a tutorial for that, I would give you candy. That's the only reason I don't use Hardy anymore, is because gnome is so outdated on it.

---

### Post by bradpurvis on 2009-03-19
its probably possible but i would rather wait until the new version of ubuntu comes out.

---

### Post by ElTimo on 2009-03-19
I cant say I blame you. I'm probably going to do the same thing. I just wish it were as easy to try out new releases of gnome as it is for KDE. O well, there's always Garnome...

---

### Post by chanders on 2009-03-20
There is supposedly an ISO you can download with the latest Gnome that comes with a live CD so you can try it out. It is at the bottom of the Gnome 2.26 release page. If you do download it, let us know how it goes!

---

### Post by MadAGu on 2009-03-20
It would be great to have it in intrepid...

---

### Post by bradpurvis on 2009-03-20
> **chanders said:**
> There is supposedly an ISO you can download with the latest Gnome that comes with a live CD so you can try it out. It is at the bottom of the Gnome 2.26 release page. If you do download it, let us know how it goes!

yeah i will definitely try that on a virtual machine

Edit:

*Downloading it right now

---

### Post by mikewhatever on 2009-03-21
> **MadAGu said:**
> It would be great to have it in intrepid...

What's so great about it? I've looked at the release notes and the review at [arstechnica]("http://arstechnica.com/open-source/reviews/2009/03/hands-on-gnome-226-brings-incremental-improvement.ars"), and there is really nothing breath taking. All this pointless clamor about updating to the newest version is annoying quite a bit.:tongue:

---

### Post by bradpurvis on 2009-03-21
lol i gave it 1GB of ram to use in my virtual machine and it went faster than my computer usually does normally, there isn't much difference besides how fast it is. there is a new theme in it though, called foresight.


here is a screenshot from my virtual machine

[http://bradpurvis.deviantart.com/art/gnome-2-26-116620694](http://bradpurvis.deviantart.com/art/gnome-2-26-116620694)

---

### Post by MasterPoulos89 on 2009-03-28
Why is Opensuse the only distro I've seen that has available repo's for the latest gnome. Is it really so much harder for Ubuntu to do that.

---

### Post by Nechi on 2009-04-25
Hey, guys!  This is what I did... and it worked!!!

I went to terminal. Opened my sources list file (sudo gedit /etc/apt/sources.list), and replaced "intrepid" with "jaunty" in all repositories with that name. I saved and closed the file.  I closed the terminal and opened Synaptic. I clicked on "reload" and when the repositories reloaded, I found "nautilus in the list. I marked it for update, and voilà my friends!!!!! You can pick the files you want to upgrade to their jaunty version or you can click on "Mark all updates" and have your new brand new Jaunty.
I'm using a Compac C700 laptop and everything works fine.
Enjoy!

---

