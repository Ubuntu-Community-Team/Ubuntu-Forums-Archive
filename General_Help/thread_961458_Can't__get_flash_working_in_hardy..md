---
title: "Can't  get flash working in hardy."
date: 2008-10-28
forum: General Help
---

### Post by obl on 2008-10-28
Hey there,

I'm running hardy, and for all the fixes I've read online, none of them work. Basically, things like youtube or other flash driven things are on the page, and FF3 gives me a button to click to install the required plugin. I do, and then restart the browser, but no change, nor has anything changed in about: plugins.

I go to Adobe and download the .deb and the .tar.gz and install them, and neither of them work.

It's really getting frustrating. Has anyone else had and solved this issue?

Cheers.

---

### Post by snowpine on 2008-10-28
Open a terminal and type:

```
sudo apt-get install flashplugin-nonfree
```

That worked for me. Good luck!

---

### Post by SunnyRabbiera on 2008-10-28
What version of Hardy are you running?
The 64bit version or the 32bit one?
It will give me a start on giving you a solution.

---

### Post by obl on 2008-10-28
Hey, sorry, I'm on a 32 bit.

---

### Post by SunnyRabbiera on 2008-10-28
Alright, well for you maybe installing flash 10 via adobes website isnt the best idea for now.
Also you may have to play around a bit first but lets go down the steps:
Firstly i would try to install this package to start out with:
[http://mirrors.kernel.org/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_9.0.124.0ubuntu2_i386.deb](http://mirrors.kernel.org/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_9.0.124.0ubuntu2_i386.deb)

Now if you get any issues tell me, you may have to remove your flash 10 if you used the debian installer first but lets see how that goes.

---

### Post by obl on 2008-10-28
OK, that's installed and is listed in the about now, but when I go to youtube, although it nolonger says I need to upgrade my flash, there is just a grey square and I can hear the video playing in the background. This may just be a youtube thing however.

Thanks for the help.

---

### Post by aeronotix on 2008-10-28
I think what you might have done is installed multiple Flash Plugins. This is what I did when I first got Ubuntu (About 4 days ago now). It's a simple process of removing the old ones, which I did through the terminal with some code I found in a different thread. If you go into Synaptic you should be able to find all the different flash players you have on there.

I'd recommend removing them all. There is a way to get them all to uninstall from the terminal like someone showed me but I don't remember code too well.

Although I just found this and it might work. Just remember for me my problem came from having multiple players conflicting with each other.

sudo apt-get install flashplugin-nonfree flashplayer-nonfree  put that into your terminal and see if that fixes it.

---

