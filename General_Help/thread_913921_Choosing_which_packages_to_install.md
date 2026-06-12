---
title: "Choosing which packages to install"
date: 2008-09-08
forum: General Help
---

### Post by frankvw on 2008-09-08
Hi, everyone,

I'm a former RedHat / CentOS user, an Ubuntu noob, and maybe an idiot... :-) but after taking Ubuntu through the newbie plug-and-play phase and being amazed about how easy Ubuntu is to install and how well it works (it rocks!) I'm now struggling to butcher it, and it won't let me. :-)

When installing RH / CentOS, it allows one to select the desired packages at install time. No matter what I do, Ubuntu installs everything *and* the kitchen sink, while I need a more light-weight install for a digital signage application. In other words I do need things like vlc and php-cli, but I don't need OpenOffice.org or Gimp. I can't find where (if at all) I can make these choices during installation.

I've gone through the Synaptic Packet Manager, but I'm a bit intimidated by all the dependencies. For example, if I remove the docbook-xml package (seeing as I won't need to write documents in DocBook XML format) I end up blowing away things like the fast-user-switch-applet and update-notifier packages (to name only two of a long list) as a result, and things like user switching or update notifications are not trivial - it's stuff I don't necessarily want to loose.

I'd hoped the OEM install CD would give me the options I am looking for, but if it does I haven't seen them. Elsewhere in this forum it has been suggested that one can install a minimalist command line system or a very light weight "flybuntu" install and then build it up from there, but that seems a lot of unnecessary work when all I want is a little more control on what I want and don't want installed. Ubuntu as it comes off the workstation CD is great, and all I need it to trim off some of the fat (i.e. the stuff I happen not to need).

Surely there must be a good way to do this? :-)

Thanks for reading - all response is greatly appreciated!

// FvW

---

### Post by driven1 on 2008-11-19
It may not be the most efficient way to do it, but if you go to Synaptic, you can deselect individual packages and see what dependencies are affected before you pull the trigger. If you are looking to replicate that setup over multiple machines, once you get everything configured a tool like [[COLOR="Blue"]_aptoncd_[/COLOR]]("http://aptoncd.sourceforge.net/") might work for you.

---

### Post by SamNSane on 2008-11-19
This issue of the determination of the initial packages to be installed is one of my very few serious grievances with Ubuntu. I have exactly the same concerns about trying to remove packages via Synaptic when I see it listing other packages which, to my mind, are totally unrelated.

I mean, I get how parts of Evolution, for instance, are intertwined with various other parts of the total environment. But trying to remove a single application and being told that you're about to lose gnome-desktop is a little bit off-putting.

So far, I've just coped with this by removing everything I don't want any truck with from the menu. Obviously, this is the head-in-the-sand approach to system customization, but I'm not comfortable enough in my new OS to start performing surgery on it.

---

### Post by frankvw on 2008-11-20
I'll give it a try - thanks!

// FvW

---

### Post by frankvw on 2008-11-20
I'll give it a try - thanks!

// FvW

---

### Post by driven1 on 2008-11-20
It certainly isn't an ideal situation, but I hope this helps.

---

