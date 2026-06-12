---
title: "AWN simple launcher only shows some icons, and i don't know which"
date: 2008-10-08
forum: General Help
---

### Post by ChrisBookwood on 2008-10-08
Hi,

I'm using AWN with the simple launcher and it works great except for the fact that it's only some images it will show. I have a lot of beautiful png's it just won't show, i'm afraid.
It shows firefox' (application-)icon great, kTorrent, Terminal and Amarok's too, but thats it. I can't get the rest of my applications images to show.
I talked with some dude on irc who said png's and others should work, but i just can't get em to.

What do i do?

---

### Post by timcredible on 2008-10-08
did you install awn from the ppa ([http://ppa.launchpad.net/awn-testing/ubuntu](http://ppa.launchpad.net/awn-testing/ubuntu)) repo?  if not, i would suggest you do that, and install awn-manager-trunk (that's how i added stuff to my awn dock) and awn-extras-applets-trunk.

---

### Post by ChrisBookwood on 2008-10-08
Sure I did; I followed [http://news.softpedia.com/news/Install-AWN-on-Hardy-Heron-82611.shtml](http://news.softpedia.com/news/Install-AWN-on-Hardy-Heron-82611.shtml) for the installation of AWN.

---

### Post by ChrisBookwood on 2008-10-09
Breakthrough!

Yesterday i tried dragging a png on a Simple Launcher at it promted me if I wanted to make the png the icon for the launcher ... It worked!
I tried adding some more and it worked. Then it stopped working, and now it's not working any more. I tried completely removing AWN (--purge) but somehow, my settings survived, and when i reinstalled AWN, the problem was still there...
Maybe it's some problem, that doesn't get removed by removing from apt, and maybe it's not. I dunno.

---

### Post by airtonix on 2008-10-09
settings for awn are in ~/.config/awn

you will also find all the launchers you have put on the bar there too.

---

### Post by ChrisBookwood on 2008-10-09
I just found that folder too, but even after removing AWN and deleting the awn folder in .config, when i reinstall AWN, the same settings apply.

---

### Post by loomsen on 2008-10-09
You should keep your home folder on a separate partition. Everything happens in it. Programs and libraries can be downloaded again and again, your configs are the things that are actually of any worth (at least you spent some more time configuring your dock/compiz/whatever than it took to install AWN) Simply reinstalling won't solve any problems. May work for windows, where every app ships everything it needs with it, but removing and reinstalling won't work. It's not windows. Make sure you have all libs installed. Again, it's not windows, your PC will NOT get slower the more libs you install. libpng should be a point you could start figuring out the problem. 
And yet again, removing & reinstalling, as well as restarting are solutions for other penetrating systems, not tho for unix. It is possible to find out why it doesnt work in linux. Removing and installing the same version again is just a waste of time.
And another yet again, try another dock ;) Not only AWN is free and opensourced.

*edit*

Try and run awn in a terminal window. Should give you some useful information :)

---

### Post by ChrisBookwood on 2008-10-09
Yeah... That's kinda why i'm asking for the settings dir, so i can get rid of everything screwed up in the settings files of awn...

I have tried a lot of other docs (Cairo-dock, screenlets, kiba-dock) but none of them has come close to AWN... I would choose AWN with only the X-icon, for my dock, over any other linux dock i have tried.
Still, doesn't help me anywhere... It's weird it worked and then it didn't.

---

### Post by loomsen on 2008-10-09
Well, you can find any settings-dirs in your home folder. Some apps have dirs, some have simply hidden files, like .conkyrc, .bashrc... files ending with rc in your home folder usually specify configurations (most likely they are called like the pkg they configure with "rc" appended to them)

Anyways, I'll never understand why so many people use AWN. I mean cmon, you may have max one dock? In the middle of your screen? This is ridiculous. Whatever, good luck, I'd take a good look if I have all Image libraries installed properly if I was you. Just a thought...

---

### Post by ChrisBookwood on 2008-10-10
Thanks...

I have all the neccessary packages installed, so it should work ... Still, it don't.

It's not a disastor no more, since i have changed the look of my desktop.
--- now using Gnome Global menu on my toppanel instead of windowlist, and have applied the launcher/taskmanager to AWN;

---

