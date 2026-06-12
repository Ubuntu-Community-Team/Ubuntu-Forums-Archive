---
title: "Providing remote support"
date: 2005-12-02
forum: General Help
---

### Post by sander marechal on 2005-12-02
I'm going to switch over my parents to Ubuntu 5.10 this weekend and one of the thinks I'd really like to do is to be able to log into their computer from my own (graphically, not just SSH terminal), so I can fix problems for them without requiring me to take a 40 min. bike ride through cold wind and rain :)

So far, I only found [this HOWTO](http://www.ubuntuforums.org/showthread.php?t=76638) but from the comments it seems that (a) it doesn't work properly and (b) I've heared that VNC eats up quite a bit of bandwidth so it's slow unless run over LAN (is that true?).

Is there a simple way to accomplish logging into my parents PC? Can I use SSHd and X to accomplish this perhaps? (it needs to be reasonably secure, as it's going over plain old internet, not a LAN or anything). Or do I need something else?

Thanks for your help!

---

### Post by Remmelas on 2005-12-02
i would check into freenx, i haven't used it on Ubuntu yet, but used in in a previous distro to support remotely my families machines

---

### Post by tim15856 on 2005-12-02
Per this "How to", installing TightVNC is better than the built-in VNC. [http://doc.gwos.org/index.php/Tightvnc](http://doc.gwos.org/index.php/Tightvnc)

---

### Post by cgjones on 2005-12-03
Check out the man page for ssh. There is a section on X11 forwarding. A friend of mine uses it between work and home. It works pretty well as long as you have a fairly fast connection.

---

### Post by sander marechal on 2005-12-06
Thank you all. I did it via FreeNX thanks to [this HOWTO](http://www.ubuntuforums.org/showthread.php?t=97277&highlight=freenx). The original HOWTO I posted in my first post is no good. It's far too insecure for use over a regular DSL line.

---

