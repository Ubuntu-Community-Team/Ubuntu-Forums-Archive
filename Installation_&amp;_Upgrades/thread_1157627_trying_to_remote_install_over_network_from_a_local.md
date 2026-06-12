---
title: "trying to remote install over network from a local repo on different computer"
date: 2009-05-12
forum: Installation &amp; Upgrades
---

### Post by dbuttera187 on 2009-05-12
Hey everyone, I am a high school student who has been using linux for a few months. In the few weeks my IT class at my high school, has been starting an exploratory linux lab. I recommended Ubuntu 8.10 to my teacher so this is what we went with. Now, here is the issue. Obviously, in order to download something, an internet connection is needed. One of the students has a copy of the Intrepid release repositories DVD set and we want to put them on one computer and use that as the download mirror/server. So far, my friend and I have gotten it so that we have the local repository working so that we can use our own folders as a source for the software being downloaded in the package manager. Where we are a little caught up is how we should go about getting these packages to all of the other computers on the network. Like I said, we are not allowed to be hooked up to the internet during lab. District will not allow it. We looked into something called apt-cacher and thought that might be a good route, although, I am not quite sure that it is the best. I need an opinion on whether setting one computer up as an FTP server with all of the repositories from the intrepid release on it might be the better choice. This way everyone could download specific packages and put them in their own local software directory to get them into synaptic, but this seems kind of alot of extra work. Would setting up a proxy-server work best for the other computers to download from one computer with all of the repos on it? also would CVS work here?

---

### Post by 3nt on 2009-05-14
I have a few computers running Ubuntu. I use apt-proxy to keep them all in line but only downloading packages once. If you are not using too many third party packages then it is quite easy to set up. Basically you load packages only to the computer you have decided to use as the server and the others all load their packages from there. If you have problems trying, let me know and I will post sections of my configuration files. As I recall the apt-proxy site has quite good instructions.
I also recommend setting up a cron job to restart apt-proxy every night - and if you seem to be getting problems during the day, my first port of call is to restart apt-proxy. It seems to just hang every so often and I haven't had time to work out why.

---

