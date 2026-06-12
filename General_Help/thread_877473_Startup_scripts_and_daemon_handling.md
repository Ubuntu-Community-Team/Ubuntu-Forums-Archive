---
title: "Startup scripts and daemon handling?"
date: 2008-08-01
forum: General Help
---

### Post by Cool Javelin on 2008-08-01
I am using a fairly slow computer, and would like to remove some stuff from starting up at boot time.

One thing is I would like to remove any logging daemons.

I want the hard drives to go to sleep after some time and the logs tend to keep it awake. Not only do I see no real need for the logs, but the background processes use CPU time and keep accessing the drive.

#1, what is the difference between a 'service' and a 'daemon'? Are there other names for those things?

#2, Is there somewhere I can find info about the various daemons in my startup folder (in my case /etc/rc2.d) and what they do?

#3 what are the risks of not starting some daemons? I found one called S11klogd for example and I moved to another place, The drive seems to have quieted down a lot now. Will removing some daemons make the computer less stable?

I have the feeling there is a lot of previous talk on this, but I can't seem to find it. Links to information previously stated will get me to bookmark them for future reference.

Thanks a lot for your help.

Mark.

PS, I have Xubuntu Hardy on a slow (300MHz) machine.

---

### Post by pytheas22 on 2008-08-01
> Is there somewhere I can find info about the various daemons in my startup folder (in my case /etc/rc2.d) and what they do?

There's a nice guide [here]("http://ubuntuforums.org/showthread.php?t=89491") regarding how to make boot go faster, and which services you can safely turn off.
> 
what is the difference between a 'service' and a 'daemon'? Are there other names for those things?

I think they refer to the same things.  In principle, I think that 'daemon' is the more proper term according to Unix puritans, but in Windows it's called a service, which adulterates our lexicon.
> 
what are the risks of not starting some daemons? I found one called S11klogd for example and I moved to another place, The drive seems to have quieted down a lot now. Will removing some daemons make the computer less stable?

Some daemons (like init) are crucial, but you could remove most of them without making the system crash.  If you want to see what you currently have running, the command:
```

ps -e
```

will tell you.  If you want to kill a service, use:
```

sudo killall service-name
```

That's a good way to see whether killing a particular service is going to crash your machine, if you enjoy the trial-and-error approach to life.  Otherwise, google for the name of each service to figure out what it does.

> 
One thing is I would like to remove any logging daemons.

Removing logging daemons shouldn't hurt anything, even if that thread tells you not to; it will just make it difficult to traceback a problem if your computer ever starts doing weird things, or to investigate potential security breaches (which you don't really need to worry about on Linux unless you're a security nut like me).

By the way, you may want to look in to using a super light-weight desktop environment like fluxbox, which you can install with:
```

sudo apt-get install fluxbox
```

(xfce will still be available and you can choose which one to use for each session at the login screen).  By default Xubuntu uses xfce, which is lighter than Gnome or KDE, but on such an old processor, you may want to be using the simplest environment that you can.

---

### Post by Cool Javelin on 2008-08-07
Thanks pytheas22.

I have been going over the link you have referred to me and it has been very helpful if not a little old.

I am using Hardy, and there are several daemons not in i3dmaster's thread, but I found a lot of info in Google about those and his was a good read.

I think I will give fluxbox a try too. xfce is ok, but I which it was easier to edit the desktop and menu. I love gnome but it is way too big for my oldie but crusty Pentium 2.

---

