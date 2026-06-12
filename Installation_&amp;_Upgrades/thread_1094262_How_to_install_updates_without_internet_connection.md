---
title: "How to install updates without internet connection"
date: 2009-03-12
forum: Installation &amp; Upgrades
---

### Post by Kenobi on 2009-03-12
Hello,

I have a PC without internet connection and want to install some new updates or a new program from time to time. My first idea was to download updates or the program at a friends machine and copy all the new .deb files to my computer and then go to that directory and use:

sudo dpkg -install *

Sometimes this works fine, but mostly this breaks the whole system. Dependencies are not cared for properly. If I let the computer auto-fix them it always wants to remove hundreds of megabytes of essential packages (or half of my distro!!).

So my question is: How can you install many packages without internet but also without breaking the system?

Thanks alot, need the time now to reinstall ubuntu ...

---

### Post by dstew on 2009-03-12
There used to be a web service called NoNetDebs that would help you get all the updates with the dependencies. It seems to have disappeared though. Does anybody know if there is something similar that can be used?

---

### Post by Neo_The_User on 2009-03-12
> **epimeteo said:**
> Hi,

sorry for loosing this discussion, but I've been busy. Can't add much more to what it's been said, but to confirm what jenkinbr suggested: to use [http://packages.ubuntu.com/](http://packages.ubuntu.com/) to search packages, although a new "apt-get update" feature is available now. It's not simple, though.

First, the news. I'm not hosting the website anymore. The website is now kindly hosted by unixpod.com at [http://nonetdebs.unixpod.com](http://nonetdebs.unixpod.com). The registration mail will come from there, obviously. You still can use [http://nonetdebs.homeip.net](http://nonetdebs.homeip.net). DynDNS will redirect you to unixpod.com.

I've managed to finally integrate drupal, apt-get as normal user and nonetdebs code (90% redone, so please say if something is broken). Now the site is more quick and its use is more similar to the real use of apt-get.

There are several improvements, and the "apt-get update" one is the most important, as it finally breaks the isolation of the offline apt-get system. [Based in this comment]("http://ubuntu.wordpress.com/2005/09/22/upgrade-install-ubuntu-on-slow-internet/#comment-54908") I've found while browsing, I've made nonetdebs get those files for you even if you don't have the status file in your account. I think it's very useful. 

Now you can save what is downloaded by apt-get when you run "apt-get update" with the selected repositories. The offline apt-get system will know what is available on the repositories! You will be able to browse Synaptic as if you where online. And Synaptic can create download scripts with this. Also, "apt-get -qq --print-uris" will work offline.

"apt-get update", sources.list visible, several APT lines in sources.list and also the execution of "dpkg -l" if a package is not listed and the user knows it isn't installed will help (I hope) to clarify this mysterious "amarok" problem. Vitesse, when you can, please say what you see if you try to install it again, please.

I hope to ear some feedback on this major changes.

That might... help? Links are dead. unixpod seems up though (main page)

---

### Post by Kenobi on 2009-03-12
Good ideas, unfortunately these services do no longer exist.

The idea of download scripts sounds promising. I'd love to use synaptics or adept "as if I were online". But how can I get the content of the repositories in my computer?

---

### Post by mac9416 on 2009-04-21
Use Keryx. It will be your cup of tea.

---

