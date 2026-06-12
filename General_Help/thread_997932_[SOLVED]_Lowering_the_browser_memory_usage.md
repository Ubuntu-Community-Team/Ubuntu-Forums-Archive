---
title: "[SOLVED] Lowering the browser memory usage"
date: 2008-11-30
forum: General Help
---

### Post by siddartha on 2008-11-30
I'm using a laptop with only 512M of RAM. That is good enough for almost all apps, less for the browser. Now, get a browser and a few tabs open and at that point it should be the only thing running or everything else gets to swap. As the hard drive has a high latency this is uncomfortable.

Firefox - huge and it gets larger by hour
Epiphany - about the same problems, waiting for the webkit version to be delivered
Dillo - lack of javascript makes some sites unusable
Kazelahaze - crashes quite often
Opera - nice, yet goes at about the same memory consumption as firefox

Anyway, with the needs of current web the flash plugin (with all its problems) is also a must.

So what other options are out there with Javascript and Flash, yet much lighter than firefox?

---

### Post by OrangeCrate on 2008-11-30
> **siddartha said:**
> I'm using a laptop with only 512M of RAM. That is good enough for almost all apps, less for the browser. Now, get a browser and a few tabs open and at that point it should be the only thing running or everything else gets to swap. As the hard drive has a high latency this is uncomfortable.

Firefox - huge and it gets larger by hour
Epiphany - about the same problems, waiting for the webkit version to be delivered
Dillo - lack of javascript makes some sites unusable
Kazelahaze - crashes quite often
Opera - nice, yet goes at about the same memory consumption as firefox

Anyway, with the needs of current web the flash plugin (with all its problems) is also a must.

So what other options are out there with Javascript and Flash, yet much lighter than firefox?

Some extensions can be memory hogs. If you use a lot of them, check memory usage by removing them one at a time, and see if one (or more) of them might be creating problems.

Edit:

Just to give you a reference point, I only use the following extensions, and Firefox is as quick as a weasel, with no memory problems.

NoScript
Adblock Plus
Gmail Manager
Yahoo Mail Notifier
CustomizeGoogle
Better Gmail 2

---

### Post by siddartha on 2008-11-30
So far is adblock, foxmarks (as I use more computers and I keep my bookmarks in sync) and the ubuntu extension. Well, there's java, java script, flash and totem movie player.

---

### Post by Arup on 2008-11-30
Turn off Java and limit automatic cache to 64mb and reduce visited site history to 500 and you will see it drop drastically in Opera.

---

### Post by OrangeCrate on 2008-11-30
> **Arup said:**
> Turn off Java and limit automatic cache to 64mb and **reduce visited site history** to 500 and you will see it drop drastically in Opera.

That's a good thought.

In fact, in Firefox, I limit History to just one day, and I do not have Firefox remember what I enter in forms and the search bar.

I don't know for sure, but that might certainly help reduce Firefox's memory footprint.

(Edit > Preferences > Privacy > History)

---

### Post by siddartha on 2008-11-30
The difference is quite small, but it is visible. To your suggestion I killed the remember forms part, I killed the history, I disabled Java and in System Monitor from 101,3M it went after restart to 90,9M.

---

### Post by OrangeCrate on 2008-11-30
As they say, a picture is worth a thousand words, so here you go...

---

### Post by siddartha on 2008-12-01
Hehehehehe
With no restriction (java, addons, flash, 3 month history) I have a 7% memory usage reported by top for firefox. The desktop has 2G of RAM which leads to roughly 4 times more space. As an estimate (far from being precise) this would lead to a 28% usage on your computer. Which is about the same.

I'd still wait for the webkit browser - lower memory footprint and hopefully snappier performance at least when you go from one browser tab to another.

---

### Post by siddartha on 2008-12-01
On the laptop with all the limitations (and same distro, all updates) the usage for 500M is 32% as I have quite a lot of things opened in tabs.

Bottom line is unless for some broken add-on the real problem is how web pages are handled. With geko having a lot of open pages (tabs, windows, whatever) means a lot.

---

### Post by OrangeCrate on 2008-12-01
> **siddartha said:**
> Hehehehehe
With no restriction (java, addons, flash, 3 month history) I have a 7% memory usage reported by top for firefox. The desktop has 2G of RAM which leads to roughly 4 times more space. As an estimate (far from being precise) this would lead to a 28% usage on your computer. Which is about the same.

I'd still wait for the webkit browser - lower memory footprint and hopefully snappier performance at least when you go from one browser tab to another.

Time out.

We might have a different idea on what's excessive memory usage. Linux manages memory much differently that Windows. Here's a good read on how Linux does it...

**Linux Memory Management or 'Why is there no free RAM?'**

> Traditional Unix tools like 'top' often report a surprisingly small amount of free memory after a system has been running for a while. For instance, after about 3 hours of uptime, the machine I'm writing this on reports under 60 MB of free memory, even though I have 512 MB of RAM on the system. Where does it all go?

[http://forums.gentoo.org/viewtopic-t-175419-postdays-0-postorder-asc-start-0.html?sid=619cda6e4dae2a0651c474f9f5e4dfcf](http://forums.gentoo.org/viewtopic-t-175419-postdays-0-postorder-asc-start-0.html?sid=619cda6e4dae2a0651c474f9f5e4dfcf)

I hope you're not confusing Firefox's memory footprint, with what's happening with the RAM overall in Linux. Rereading your original post, you may be.

If Firefox is working O.K., don't worry about how much RAM is being used. Linux is going to use it all anyway, no matter what you do.

---

### Post by siddartha on 2008-12-01
Nope.

I know how it works and how things go faster if you have enough RAM. I'm counting ONLY the memory footprint of firefox and nothing more. 32% going up, than some pdf reader, maybe a few other tools and when you want to open a file in some office suite you wait and you wait and you wait. Because of all this the memory is almost full, there's almost no caching at this point and while one app is loading from an old laptop hard drive things get pushed down to the swap wich resides on the same slow drive to make room. And when you are switching apps you just have the same thing over again - getting from swap some libs, throwing into the swap some other libs hopefully unneeded.

I also know that most people make a confusion between real life constraints and server optimisation read online. Sure, a faster drive will make a lot of difference. More RAM will make even more difference. Putting the swap on a second phisical drive also helps. Using different phisical connections to the (now) two hard drives helps. Changing from dumb IDE to SATA or SCSI also makes a difference. It's pleasant to waste time on this kind of philosophy, yet in reality that wouldn't change a thing.

And follow me on this one: if an app goes fast with all the above real life constraints it will go even faster with the theoretical improvements also. The untrained developers of today (2008!) have some traces of knowledge about code optimisation and nothing more. Making a GUI to work in 8M is just a fairy tale for them quantity workers. This is the source of all the banter about getting a faster system. They have no idea how to make an app fit 8M... and anyway, the java interpreter will take another 8M. This is what pushed the development of personal computers as newer apps were unable to conform to the old standards. This stride to have a computer that is faster and with a larger memory also implied lowering costs - lowering quality of the hardware along the way and making crippled choices based on costs. This way it took more than a decade to partially lose the IDE. Maybe you don't know, but back in the old day the drive controller wasn't onboard and the price for IDE and SCSI were almost the same. With time IDE was cheper for the manufacturer so it was pushed more agresively (more money in marketing, more incertives). This lead to SCSI being considered more reliable as opposed to the popular choice. That in turn lead to SCSI having a higher price. Which lead to SCSI being less used, so less manufacturers meant less products, meant higher prices even without counting the premium for more reliable technology. I guess you know the rest. A less complicated path was taken in the CPU wars with crappy, hot, buggy, badly designed Intel technology being mainstream and eliminating something like Alpha RISC. In time all goes down to marketing which tries to help the cheaper unqualified labour get at the same level with highly trained individuals and companied. With all its bugs and recalled CPUs word on the street was do not buy other units than Intels as they (the others!) are buggy. And you know what? In order to reach the speeds of today and hail the poor man that lead Intel as a visionary (Moore's law, a few words said without thinking at the time, now some sort of an unholy gospel) so to reach that the Alpha had to go bankrupt and the jackals take over their technology and fit it to their two bit products. Same goes for USB vs Firewire and the list can go on and on.

---

