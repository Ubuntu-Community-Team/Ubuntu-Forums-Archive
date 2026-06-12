---
title: "&quot;Partial upgrade&quot; in update manager"
date: 2009-11-09
forum: Installation &amp; Upgrades
---

### Post by UnSandpiper on 2009-11-09
I've freshly installed Karmic a couple days before beta and since it has been recommended to never do a "partial upgrade" in the update manager, I haven't done it.

But now two weeks into Karmic official release, I still get the "partial upgrade" message in Update Manager.

How do I get rid of that message? Because someday I'm afraid, I will accidentally click on "yes". So, is it save to do the partial upgrade,  which will remove the packages listed below?

```

# sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  gstreamer0.10-plugins-bad libpulse-browse0 libpulse-mainloop-glib0 libpulse0 pulseaudio pulseaudio-esound-compat
  pulseaudio-module-bluetooth pulseaudio-module-gconf pulseaudio-module-udev pulseaudio-module-x11 pulseaudio-utils
  xserver-xorg-input-all
0 upgraded, 0 newly installed, 0 to remove and 12 not upgraded.
```

---

### Post by Tenebraxis on 2009-11-11
I have the same problem, after having a small problem with doing a partial upgrade with the beta version of 9.10, I got the advice on the Ubuntu forums not to do a partial upgrade when running a beta version, so I didn't.

Since the release of 9.10 stable I can still only do partial upgrades and I am unsure if I should just update my system or wait.

---

### Post by Tenebraxis on 2009-11-15
Is noone getting this, or is it just too stupid to answer?

I broke my system with a partial upgrade before and the reading material on this forum points out to a very strong no-no on partial upgrades, but every time I want to do an update in my update manager, it asks me if I want to do a partial upgrade, if I cancel the update manager exits.

I installed Ubuntu 9.10 as beta, is it safe to do a partial upgrade now that Ubuntu 9.10 is stable?

---

### Post by andresmh on 2009-11-15
> **Tenebraxis said:**
> Is noone getting this, or is it just too stupid to answer?

I broke my system with a partial upgrade before and the reading material on this forum points out to a very strong no-no on partial upgrades, but every time I want to do an update in my update manager, it asks me if I want to do a partial upgrade, if I cancel the update manager exits.

I installed Ubuntu 9.10 as beta, is it safe to do a partial upgrade now that Ubuntu 9.10 is stable?


I've been experiencing the same thing for the past few days. In my case it wants to remove: pulseaudio-module-udev 

Also, I am afraid of doing the partial upgrade because during the Beta we were adviced against  it.

---

### Post by krishna.988 on 2011-03-04
I upgraded from 10.04 LTS to 10.10 this morning. After upgrading it showed me some notification applet is not working with delete and don't delete option and later. I chose delete. 
When I tried to install startup-manager from ubuntu software center. It showed to enable universe source and started installing with updating cache it kept on asking for 10.10 CD as I had installed by directly mounting the cd  ISO..I could'nt insert the cd.I tried mounting again but it kept on prompting for CD. then I canceled updating cache, then startup manager installed successfully msg was shown..
Then I tried to update ubuntu, using update manager partial upgrade message is shown, saying not all updates were installed..Not sure what to do..Please help!!

---

### Post by tommcd on 2011-03-04
For those using Ubuntu 9.10, be aware that 9.10 will reach end of life (EOL) in April of this year: [http://www.ubuntugeek.com/ubuntu-version-names-and-end-of-life-details.html](http://www.ubuntugeek.com/ubuntu-version-names-and-end-of-life-details.html)
You should upgrade to 10.04 before April.
Or better yet just do a clean install of 10.04 or 10.10. A clean install is the fastest, easiest and most fail safe way to avoid problems with upgrading. This is especially true if any of you are using third party repos or PPA repos in your sources.list.

---

### Post by tommcd on 2011-03-04
> **krishna.988 said:**
> ... it kept on asking for 10.10 CD as I had installed by directly mounting the cd  ISO..I could'nt insert the cd. ...
Then I tried to update ubuntu, using update manager partial upgrade message is shown, saying not all updates were installed..Not sure what to do..
Is the option for the CDROM unchecked in your sources? 
If not, then open up synaptic package manager and go to: settings > repositories. Make sure the option for the CDROM is unchecked. Then reload the repositories when prompted and try again to install the updates.

---

### Post by krishna.988 on 2011-03-04
> **tommcd said:**
> For those using Ubuntu 9.10, be aware that 9.10 will reach end of life (EOL) in April of this year: [http://www.ubuntugeek.com/ubuntu-version-names-and-end-of-life-details.html](http://www.ubuntugeek.com/ubuntu-version-names-and-end-of-life-details.html)
You should upgrade to 10.04 before April.
Or better yet just do a clean install of 10.04 or 10.10. A clean install is the fastest, easiest and most fail safe way to avoid problems with upgrading. This is especially true if any of you are using third party repos or PPA repos in your sources.list.


Ya right, but this upgrade was done immediately after installing 10.04.. Any suggestions??

---

### Post by tommcd on 2011-03-04
> **krishna.988 said:**
> Ya right, but this upgrade was done immediately after installing 10.04.. Any suggestions??
As I said in my last post, **have you checked to make sure the CDROM is unchecked in your software sources**????
If you wanted 10.10, why did you not just do a clean install of 10.10 instead of installing 10.04 and then upgrading to 10.10?

---

### Post by krishna.988 on 2011-03-04
> **tommcd said:**
> As I said in my last post, **have you checked to make sure the CDROM is unchecked in your software sources**????
If you wanted 10.10, why did you not just do a clean install of 10.10 instead of installing 10.04 and then upgrading to 10.10?

Ya because I had downloaded an alternative CD ISO..when I previously tried to upgrade from 10.04 with many programs..I ran into many problems..so I though I'll install 10.04 again with Live Cd then upgrade to 10.10 with ISO mounting.. 

I'll check with the CDROM uncheck option and get back to on what happened..Thanks a lot!!:)

---

