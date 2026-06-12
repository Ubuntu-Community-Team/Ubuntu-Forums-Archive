---
title: "Intel 945GC + Atom 230 Issues"
date: 2009-05-04
forum: Hardware
---

### Post by alphaniner on 2009-05-04
I'm running 8.04 on the [Intel BOXD945GCLF]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813121342") with 2GB RAM. It installed flawlessly but Firefox (actually many graphical apps, but specifically Firefox) can be painfully slow. An Ebay product search is a nightmare (first to load, then to scroll through). But pretty much anything other than minimally formatted text preforms poorly. The only extension I have installed is AdBlock. Desktop effects seemed to work very well though. Emphasis on seemed, because I turned them off; although I don't notice a difference. FF works wonderfully in dual-booted Windows. I did a search and didn't turn up anything useful, so any information/suggestions on this it would be greatly appreciated.

---

### Post by cariboo on 2009-05-04
I'm using the same motherbaord in my media center pc, I installed Intrepid 32-bit when I origionally put it together, and updated to Jaunty 64-bit last week. I watch videos full screen and since installing the drivers for jaunty from [here]("http://edge.launchpad.net/~ubuntu-x-swat/+archive/x-updates/"), even the slight tearing issues have disappeared.

---

### Post by alphaniner on 2009-05-04
Do you ever use Firefox though?  The performance of video is intriguing, especially since my one attempt to view video in Linux was a bit of a disaster.  Still, I'd like to know about FF if possible because that is what I use it for most.  In any case, thanks.  I'll give Jaunty a try at some point.

One more thing I just thought of.  If I recall, this mobo has some video settings in the BIOS that I'm not really familiar with, including DVMT.  Is this related to the drivers you were talking about?  If I get the specific options I'm thinking of, is there any chance I could get you to look into your BIOS and tell me how it's set up?  In any case, thanks again.

---

### Post by cariboo on 2009-05-04
I did use firefox with the previous version and you tube worked well. I give it a try a little later on and get back to you. It seems my bios somehow got corrupted so I'm missing some settings, it hasn't bothered me so far, but one of these days I'll reflash the bios.

---

### Post by mikedep333 on 2009-05-04
Have you checked gnome-system-monitor? Is anything taking up all the CPU time or memory?

---

### Post by cariboo on 2009-05-04
I just fired up the media center pc, opened firefox and tried several graphics heavy sites, including ebay and youtube. I didn't see any problems with pages loading and all the videos on youtube worked as they should. I didn't see anything you discribed.

I'm running firefox 3.0.10. 

I also am only running 1Gb pc5400/667 ram

---

### Post by alphaniner on 2009-05-05
Thanks for the advice and the effort you put in to help me out, cariboo907.  I took said advice and tried Jaunty (which I dl'd with a torrent! :tongue: ) from a USB stick.  Not only was the performance of FF *much* better, many other X apps performed better as well.  I went ahead and installed, but kept my old installation for the time being.  Now, I don't suppose you could tell me why the update manager window pops up every ~30 minutes, or how I can bring back the (updates) notification icon, could you?
Edit: I noticed you posted in a thread about Deluge on Jaunty.  I saw the link for the deluge PPA in that thread, but unfortunately I have no idea what a PPA is or what to do with it at this point. :confused:
I'm gonna try to figure it out but if you happen to see this message, I'd appreciate any suggestions.  

And thanks for the suggestion, mikedep333.  I had System Monitor applet on my panel monitoring CPU, RAM, Load and HDD, and there were no processes hogging my resources.

---

### Post by cariboo on 2009-05-05
The devs have changed the way update manager works, if there are important security updates, the whole app pops up and wants you to do the updates, with non-security updates, by default it only pops up once a week. I'm running karmic Koala on my main computer, I usually update twice a day so I don't see the bad behaviour here.

A ppa is a personal package archive on launchpad.net. When you go to one of the there is usually a couple of lines that look like this:

> deb [http://ppa.launchpad.net/chromium-daily/ppa/ubuntu](http://ppa.launchpad.net/chromium-daily/ppa/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/chromium-daily/ppa/ubuntu](http://ppa.launchpad.net/chromium-daily/ppa/ubuntu) jaunty main

These lines should be added to /etc/apt/sources.list in order for you to install the program. To add the lines to /etc/apt/sources.list press Alt-F2 and type:

```
gksu gedit /etc/apt/sources.list
```

copy them from the webpage and paste them in the file.

to add the pgp keys, click on the Follow these instruction link on the webpage.

---

### Post by alphaniner on 2009-05-06
Thanks.  I had already gotten it installed by following the instructions, despite running into some issues when adding the key.  But then I was drawn into an epic battle with Deluge to import my old info.  And the GUI is still a lethargic resource hog it seems, a fact that didn't help things.  I really wish there were a version of utorrent for Linux.  But I digress.

Regarding the Update Manager, I found a closed [thread]("http://ubuntuforums.org/showthread.php?t=1122292&highlight=jaunty+update+manager+notification+icon") from the testing period talking about it.  It had a command that disables the pop-up and re-enables the icon (I think), so I gave that a try.  I had already updated though so I don't know what it actually did.

Anyhoo, thanks again, I'm gonna mark... err *consider* :( this thread closed.

---

