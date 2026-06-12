---
title: "Install Firefox 2.0"
date: 2009-09-29
forum: Installation &amp; Upgrades
---

### Post by indigo001 on 2009-09-29
Hi everyone
.
I'm building a website so I want to test it on a specific version of **Firefox 2.0.0.19**.

So basically I want to install that version, may I prevent it from updates ?  and still I want to keep my default web browser as my default browser and keep receiving updates:

Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.1.4pre)
Gecko/20090923 
Ubuntu/9.04 (jaunty)
Shiretoko/3.5.4pre

---

### Post by aysiu on 2009-09-29
Paste these commands into [the terminal](http://www.psychocats.net/ubuntu/terminal): ```
wget -c http://ftp.pwr.wroc.pl/pub/mozilla/firefox/releases/2.0.0.19/linux-i686/en-US/firefox-2.0.0.19.tar.gz
sudo tar -xvzf firefox-2.0.0.19.tar.gz -C /opt
sudo mv /opt/firefox/plugins /opt/firefox/plugins.backup
sudo ln -s /usr/lib/xulrunner-addons/plugins /opt/firefox/plugins
sudo ln -s /opt/firefox/firefox /usr/bin/firefox2
``` Then the command ```
firefox2
``` will launch Firefox 2.0.0.19

---

### Post by indigo001 on 2009-09-30
Thanks it's working fine, just one more thing: can I have both browser running at the same time ?

You see, if I'm running shiretoko and I launch firefox2 it opens a new window of shiretoko and the same goes when I run firefox2 and try to open shiretoko, I get another window of firefox2.

---

### Post by aysiu on 2009-09-30
> **indigo001 said:**
> Thanks it's working fine, just one more thing: can I have both browser running at the same time ? I don't think you can, since they're both Firefox.

A possible workaround is to create a new test user and install the *xnest* package. Once you've done that, paste in the command ```
gdmflexiserver --xnest
``` A new login window will appear inside your session. Use that to log in as the new test user. In that test user session, launch Firefox 2 while you're using Shiretoko in your session.

---

### Post by khelben1979 on 2009-09-30
I would like to thank you aysio for this one. :) 
I'm testing it as well.

---

