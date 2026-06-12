---
title: "Getting gitweb browsing to work"
date: 2009-01-29
forum: Installation &amp; Upgrades
---

### Post by DWStrauss on 2009-01-29
Does anyone have any experience getting browsing of a git repository to work on Ubuntu?

I have a fairly generic Ubuntu 8.04 installation, with an Apache2 web server installed (and running).  I'd like to get the server to serve up a git repository I have on the machine but I'm having problems getting it to work.  gitweb is installed (downloaded from the Ubuntu apt repository), and I've got git-daemon running.  /etc/gitweb.conf has the following defines $projectroot to be /var/cache/git, so I added an alias to that in my Apache2 setup (in other words, [http://my.machine.name/git](http://my.machine.name/git) should serve up /var/cache/git).  So what's the next step?  Do I need to put some sort of html or php or ??? file in /var/cache/git ?  If so, what should it be?

For reference, assume the repository I want to be able to browse is in /users/myname/git_tree/.  How do I get this set up?

Thanks.

---

### Post by Cwolly on 2009-03-30
I know this is an old post, but since no one answered. This is what helped me get gitweb straight. Great article

[http://vafer.org/blog/20080115011320](http://vafer.org/blog/20080115011320)

---

