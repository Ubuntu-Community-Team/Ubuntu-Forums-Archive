---
title: "Kopete Facebook Plugin deb?"
date: 2009-06-12
forum: Installation &amp; Upgrades
---

### Post by aftermarketgirl on 2009-06-12
Has anyone been able to get [this facebook plugin (link)]("http://duncan.mac-vicar.com/blog/archives/545") compiled and working under (k)ubuntu? Is there a deb, repository, or howto out there anywhere, because compiling from scratch is a bit over my head.

thanks.

---

### Post by MonsterTrimble on 2009-06-17
The Karmic Koala repos has the facebook plugin. I haven't checked Jaunty's yet, but I'm running Karmic anyway. (FYI - if you ant to use the karmic repos, just change 'jaunty' to 'karmic' in your sources file, save and update/upgrade/dist-upgrade. But remember, Karmic is Alpha 2, so it's not totally together yet)

I have no review of the plugin yet since I found out at work and haven't been home to get it set up. In fact, I haven't run Kopete in 4 or 5 months since switching to Pidgin specifically because it had the facebook plugin.

---

### Post by aftermarketgirl on 2009-06-17
thanks!

It'll probably crash and burn my system later, but I installed the .deb and its dependencies after downloading them directly from [http://packages.ubuntu.com](http://packages.ubuntu.com) ... it only took 4 .debs but it dug all the way down to gcc-4.4-base, so i'm feeling pretty sketchy.

At any rate, it's working for now. I'm chatting with a friend, it echoes to facebook and everything.

---

### Post by MonsterTrimble on 2009-06-18
I installed it directly last night and it works reasonably well, although I have experienced a few hiccups with the restart of usage with Kopete. I find the notifications continue even after I turn them off which is supremely annoying - just make the system tray icon spin when I have a new message. Another thing is that if I have a meta contact with both (or example) Yahoo & facebook, facebook wins, even if I set it up like before where Yahoo is the main messenger. Kind of annoying.

Now to get webcam back up and rolling...

---

### Post by rivera151 on 2009-07-12
I tried a different approach.  I compiled it from source.  All dependencies were in the jaunty repo's, except for qjson, which isn't so I had to compile that from source before compiling the plugin.  Easy compile.  After that, compiled the source, installed, and restarted kopete.

I'm still trying it out, but it seems that after a while it stops updating my facebook friends' statuses.  If I set facebook to offline then online though, it updates and keeps updating for several minutes after that before it stops updating again.  I'm still trying it out so I'm not sure if this has to do with auto away or something.  But so far so good.

---

### Post by MonsterTrimble on 2009-07-17
I know they have done at least a couple updates to the plugin in the repos, although currently my Kopete is broken due to Akonadi & mysql and my running of Karmic Koala. Which means I'm back using Pidgin.

Depending on the weather and my level of energy this weekend I might reinstall Jaunty just to get back to something more stable.

---

### Post by peterbuldge on 2009-08-05
I found a jaunty deb at this ppa:

[https://launchpad.net/~daniele.domenichelli/+archive/ppa](https://launchpad.net/~daniele.domenichelli/+archive/ppa)

but after installing it I see no signs of it anywhere in kopete.  might just need to be updated for 4.3 or something.

---

### Post by MonsterTrimble on 2009-08-07
> **peterbuldge said:**
> I found a jaunty deb at this ppa:

[https://launchpad.net/~daniele.domenichelli/+archive/ppa](https://launchpad.net/~daniele.domenichelli/+archive/ppa)

but after installing it I see no signs of it anywhere in kopete.  might just need to be updated for 4.3 or something.

Two days ago I added the repo you gave and I found facebook in the regular list of 'add new accounts'. However once I did that Kopete crashed. Then last night there was an update to 1.3 and voila! It works!

I also have the KDE 4.3 repositories on my computer as well and I forgot how much I liked Kopete. Now I just need to get webcam support back up and I'm good as gold!

BTW, if you want me to post my sources.list I will.

---

### Post by roameo on 2009-09-09
Hey. I tried the package in that repository and it had had some karmic dependencies. Is there any chance of installing this plugin and not upgrading?

---

### Post by MonsterTrimble on 2009-09-18
Not really. Although Karmic is in Alpha 6 now and works pretty well.

All-in-all, I would not worry about installing this one yet. They still have chat problems with it (or I do).

---

