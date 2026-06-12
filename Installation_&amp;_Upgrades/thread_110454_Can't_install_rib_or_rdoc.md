---
title: "Can't install rib or rdoc"
date: 2005-12-30
forum: Installation &amp; Upgrades
---

### Post by yyong on 2005-12-30
I just installed Ubuntu 5.1 vmware image. It worked like a charm, except that I couldn't install the ruby interative shell (irb). I tried both apt-get and synaptic package manager, but neither succeeded. When using apt-get (sudo apt-get install irb), I got the message "couldn't find package irb". Searching irb on Synaptic did not return anything back either. However, I was able to install ruby-1.8 using Synaptic, even though apt-get still failed (it kept asking me for ruby CD release, but I guess it's another issue I can come back later for). So, may I know if anyone knows how to install the irb? Thanks!

---

### Post by yyong on 2005-12-30
I figured it out. irb is not supported or not tested by ubuntu team, so its source site is not included in the default sources.list file under /etc/apt. I uncommented the lines that contain unrestricted sources, and now everything is installed. I guess I should give myself a big fat RTFM.  :-) Thanks anyway. OT: why the hell can't we have a single package that contain everything for ruby (or any other tools)? Does it even make sense to install ruby but not irb or rubygem? Even if there is such need to install them separately, can't we just make a bundled installation that allows people to select what needs to be installed (just as windows installation, even though I know this would irratate some people here).

---

### Post by Felipe_U on 2006-01-01
COuld you post which line you uncomented on sources.lists to be able to install irb, I have all the universe and multiverse activated and I cant find irb through apt-get or synaptic


Regards,
Felipe

---

