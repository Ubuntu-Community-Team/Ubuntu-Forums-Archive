---
title: "Installing Ubuntu on a machine which has no screen"
date: 2009-03-06
forum: Installation &amp; Upgrades
---

### Post by Manthis on 2009-03-06
Hi guys,

I'm having an issue. I'd like to setup ubuntu server on a machine I just got, and on which it is not possible to plug a screen.

I have absolutely no idea about how I should do that, so if anybody has an idea, help would be appreciated

Regards,

Manthis

---

### Post by pedja_portugalac on 2009-03-06
maybe if you connect that machine with another who have the screen? for that try to use network cable (cross cable). ???

---

### Post by LegendofTom on 2009-03-06
I would just use a monitor for the install, install ssh on there, and then shell into it from then on.  That way there is no need for a monitor.

---

### Post by yther on 2009-03-06
You should be able to do it with [System Rescue CD]("http://www.sysresccd.org/").  Put it in and let it boot up, press Enter twice (once each time you hear the CD spin down).  Type "dhcpcd eth0" and Enter again, this should get it online.  It starts sshd by default.  The only other thing you'd need to do is set the password; by default the root password is random.  So you'd type "passwd" and then some short password twice.  After that, you have to determine the IP it got, which you could do using **nmap**.

You could also set up your router to give the new box a static IP so you wouldn't have to portscan your own network.  That would save some time.  ;)

So now you have a root shell... one of the alternative Ubuntu installation methods should work from here.  If it were Gentoo, you'd use **chroot** somehow to set up the environment and begin the installation, but I'm not sure the exact procedure here.  ****FOUND IT!****  [Installing from existing Linux system]("https://help.ubuntu.com/8.10/installation-guide/i386/linux-upgrade.html")

*Edit:*  Another idea I was just reminded of, you could take out the hard drive, install Ubuntu Server on it using another PC, enable ssh, then put it back into the headless box.  Shell in and do the rest of your setup from there.

*Edit Again:*  Check out [Appendix B]("https://help.ubuntu.com/8.10/installation-guide/i386/appendix-preseed.html") of the i386 alternative install guide.  You can provide an installation script and completely automate the process if you know the answers to the questions it asks.

---

