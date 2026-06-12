---
title: "How to correctly uninstall evolution?  eee pc 901 UNR"
date: 2009-07-06
forum: Installation &amp; Upgrades
---

### Post by bunkertruck on 2009-07-06
I'm trying to keep my 8gb partition clean of everything I can and realize I don't need evolution.  How do I correctly uninstall evolution without removing other important files?  If there is anything else that I could uninstall that takes up useful space could you let me know?

Thank you,
Bunkers

---

### Post by wojox on 2009-07-06
Check this out

[http://www.psychocats.net/ubuntu/purexfce](http://www.psychocats.net/ubuntu/purexfce)

---

### Post by bunkertruck on 2009-07-06
wojox, it looks as though that long command will remove many things.  can you generally explain what it will do if I run it?  Of course, I'm still learning the universe outside of windows and mac.

thanks

---

### Post by wojox on 2009-07-06
Scroll down to the evolution part and just use those for uninstalling evolution.

---

### Post by tripzilch on 2010-08-26
> **wojox said:**
> Scroll down to the evolution part and just use those for uninstalling evolution.

Heh. I just did that, wasn't paying attention entirely, so I got this:

```
tripzilch@tripzilch-netbook:~$ sudo apt-get remove evolution evolution-common evolution-couchdb evolution-data-server evolution-data-server-common evolution-exchange evolution-indicator evolution-plugins evolution-webcal
[sudo] password for ritz: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package evolution-couchdb is not installed, so not removed
The following packages will be REMOVED:
  evolution evolution-common evolution-data-server evolution-data-server-common evolution-exchange
  evolution-indicator evolution-plugins evolution-webcal [B]gnome-applets gnome-panel gnome-session
  indicator-applet indicator-applet-session indicator-me libedataserverui1.2-8 ubuntu-netbook[/B]
0 upgraded, 0 newly installed, 16 to remove and 3 not upgraded.
After this operation, 87.8MB disk space will be freed.
Do you want to continue [Y/n]? 
(Reading database ... 128300 files and directories currently installed.)
Removing evolution-plugins ...

(etc)
```

Somehow, apparently, the bolded bits were linked to all those evolution-related packages (if someone could explain in a few words how that works, that'd be cool btw).

Anyway, when I saw that, I figured I might have removed more than I wanted, so I rebooted to check if that was the case. Lo and behold, it was :)

Basically the entire taskbar-like panel at the top of the screen is now gone. Thankfully, the main desktop menu is still there.

It's not that bad actually, I know my way around and can still run most things, PLUS the system seems a whole lot more responsive and smooth! So I guess some of those panel applets were eating up quite a bit of performance.

Still, I kind of want part of that taskbar-panel back. Especially the clock. I like being able to see the time :) But when I tried to **apt-get install ubuntu-netbook**, it wanted to install all those Evolution packages again as well.

I'm probably just going to try installing those other packages, to see what they bring. Starting with **gnome-panel**, which sounds promising.

But I thought I'd post my experiences here, both for letting other people know what happens, if they intend to do this, and maybe someone more knowledgeable than me can shed some light on what's best to do next :)

---

### Post by snowpine on 2010-08-26
Try installing ubuntu-netbook without its "recommends" packages:

```
sudo apt-get install ubuntu-netbook --no-install-recommends
```

Evolution is a recommended package but not a "dependency."

---

### Post by tripzilch on 2010-08-26
Thanks for the info, snowpine! 

I tried that, to see what I would get, but I hit "no", cause I got these packages:

```
evolution-data-server-common gnome-applets gnome-panel gnome-session indicator-applet
  indicator-applet-session libedataserverui1.2-8 ubuntu-netbook
```

what's **evolution-data-server-common**? sounds like it's part of Evolution?

and, what would happen if I'd just install **gnome-panel** (maybe also with no recommends)?

[I will try it out anyway, playing around is the best way to learn]

---

### Post by snowpine on 2010-08-26
> **tripzilch said:**
> what's **evolution-data-server-common**? sounds like it's part of Evolution?


I believe it is required to show the little calendar that pops up when you click the clock on the gnome-panel. :)

---

### Post by grizzler on 2010-08-26
You can't remove everything with 'evolution' in the name without messing things up. Some items are used by other parts of GNOME (don't ask me exactly what/where). I also tried to get rid of as much of evolution as possible, but these bits (I just checked) are still installed:

evolution-common
evolution-data-server-common
evolution-webcal

Like it or not, GNOME *needs* at least the second of these.

---

### Post by tripzilch on 2010-08-26
Well, I did it! Thanks a lot for the help, Snowpine! At first I wasn't so sure, cause I hated to think I had one single package installed for an application I don't have or want, like having half an application. But your info about the little popup calendar gave me confidence that this single "evolution" package *is* indeed useful :)

So I ran *sudo apt-get install ubuntu-netbook --no-install-recommends* (oh, after also removing Empathy and installing Pidgin, which I prefer), and got the  evolution-exchange evolution-indicator evolution-plugins evolution-webcalpackages as I mentioned in my previous post.

After a reboot I got the taskbar panel back and everything is fine. Pidgin even appeared in the envelope icon menu, where Empathy used to be!

*And*, as I mentioned before, the whole interface is still a lot more responsive than it was at first (a reasonably fresh UNE install).
For example, in the Desktop menu / "home screen", when I hover the big icons, the white border highlight effect appears slightly quicker. 
Or, when I click the battery icon in the taskbar panel, it opens the battery menu, and then move my cursor to the right, over the speaker icon and then over the envelope icon, their respective menus appear and disappear almost instantly, while before they were kind of sluggish.

... and I just checked, *really everything* that does graphics related stuff is faster, not just the menus, but also panning images in GIMP, or working with Inkscape! (Inkscape was almost unusable at first, I'd have a blurred object and another two objects with gradients or something simple like that, while it ran perfectly smooth back when I still had WinXP last month. It's still slightly slower than I remember from XP, but definitely workable)

Which is awesome, and great, but I just happened across this because I thought it might be a good idea to de-install Evolution since I got another client and wasn't using it anymore. Can anyone tell me how I can figure out what odd and unexpected packages (or processes or .. things) are still out there (in here) eating up my performance? And, any idea what could exactly be the thing that made the Evolution packages consume so much performance?

So in conclusion, thanks for the help, and I hope that my report of what I did will be useful to someone in the future :D And to sum it up, I *think* that if I would have done this right away:

```
sudo apt-get remove evolution evolution-common evolution-couchdb evolution-data-server evolution-exchange evolution-indicator evolution-plugins evolution-webcal
```

(note the lack of **evolution-data-server-common**), then I would have arrived immediately to where I am now (extra speed, no Evolution) without having to reinstall the panel stuff. ... But I'm not sure, so if someone knows, or tries it, please do report.

And for completeness sake, I just saw the topic title, I don't have an EEE PC 901, but a Medion Akoya E1212, 1GB RAM/1.6GHz (which is the same hardware as a MSI Wind, I've heard).

---

### Post by amendt on 2010-09-06
I freed up 74 MB of Hard Drive by doing that command. Thanks!

"sudo apt-get remove evolution evolution-common evolution-couchdb evolution-data-server evolution-exchange evolution-indicator evolution-plugins evolution-webcal"

---

