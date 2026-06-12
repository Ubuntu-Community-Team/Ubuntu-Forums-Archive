---
title: "Converting server to desktop issues"
date: 2009-10-01
forum: Installation &amp; Upgrades
---

### Post by chronomitch on 2009-10-01
Right now I am running the server edition of Ubuntu 9.04 on a headless system. It is being used solely as a file server (running samba). I usually do configuration either by ssh or webmin.

I am slowly trying to get the machine in a configuration where it can run Skype while still being headless. As Skype and a few other config tools I need require X11, I installed the gnome package. With the help of Cygwin X, I was able to log into the machine and start a gnome session. However, there is still no audio server, such as Pulse Audio.

I am considering installing the ubuntu-desktop package which, I am told, will turn the server into a regular desktop. Will this automatically configure a sound server and do other things? Will it leave my previous configurations (raided drives, Samba, webmin, etc) intact? Am I asking for trouble by "upgrading" in this manner, or should I do a clean desktop install?

Remember, I still want to keep this machine in a headless configuration. Any time I need to do configuration via a graphical tool, I will just SSH into the box and start a gnome session.

Thanks.

---

### Post by lemming465 on 2009-10-03
I don't see why installing the *ubuntu-desktop* package would cause any problems for an existing server install.  I routinely add *kubuntu-desktop* on top of an ubuntu desktop install, and that works fine too.

---

