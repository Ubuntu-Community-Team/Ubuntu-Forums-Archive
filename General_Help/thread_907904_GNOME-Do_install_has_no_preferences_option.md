---
title: "GNOME-Do install has no preferences option?"
date: 2008-09-01
forum: General Help
---

### Post by inchaos on 2008-09-01
So, I was browsing the GNOME-Do website looking for plugins and I saw that all the screenshots had cool colors other than the default black for their GNOME-Do.  While trying to figure out how to do this, I realized that for whatever reason, my install doesn't have a preferences option.

You're supposed to be able to either click the triangle dropdown menu from GNOME-Do and select preferences, or just begin typing 'GNOME Do preferences' but somehow I don't see anything like it anywhere.  Not in my system menu either.

I've uninstalled and reinstalled but I'm just getting it from the Hardy repositories and I still have the same issue..  I realized they're up to version 0.6.0.0 while the repos are stuck on 0.4, but trying to update proved to be a hassle because there are GTK, glib, and gdk dependencies for which the repos aren't up to date and I got frustrated and gave up after a fashion.  

So, to summarize, why the heck don't I have any way to change my preferences?

---

### Post by inchaos on 2008-09-02
bumpity-bump

---

### Post by daradib on 2008-09-10
You probably have an older version of Gnome Do, 0.4 (Ubuntu 8.04) or 0.42 (Intrepid).

To upgrade, add the Gnome Do PPA Repository to your Software Sources.

deb [http://ppa.launchpad.net/do-core/ubuntu](http://ppa.launchpad.net/do-core/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/do-core/ubuntu](http://ppa.launchpad.net/do-core/ubuntu) hardy main

(replace hardy with the Ubuntu code-name release you are using)

You can do this by navigating to System -> Administration -> Software Sources and adding each entry on the Third Party Software tab. When you exit, select the option to reload all the sources. After a few moments the Software Update notifier in the panel should show an update for Gnome Do. Install this to get the new preferences dialog.

A side note: [Bug #26702]("https://bugs.launchpad.net/ubuntu/+source/gnome-do/+bug/267020") has been filed requesting a freeze exception to allow Gnome Do 0.6 to be included in Intrepid (Ubuntu 8.10). Without the freeze exception, Ubuntu 8.10 would ship with Gnome Do 0.42, which does not include the preferences dialog.

---

### Post by SammichDinosaur on 2008-09-12
I had the same problem as inchaos. Tried the suggested software source fix. No result - gnome do didn't update

---

### Post by Stefanie on 2008-09-12
look here [https://wiki.ubuntu.com/GnomeDo/Installation](https://wiki.ubuntu.com/GnomeDo/Installation) 

you need to purge your current gnome-do installation before you install the new one. everything is explained, just follow the link. 

I really hope they will allow the freeze exception...

---

### Post by Vinay92 on 2008-09-13
> **Stefanie said:**
> look here [https://wiki.ubuntu.com/GnomeDo/Installation](https://wiki.ubuntu.com/GnomeDo/Installation) 

you need to purge your current gnome-do installation before you install the new one. everything is explained, just follow the link. 

I really hope they will allow the freeze exception...

I just followed the purge/install instructions and I still can't get to preferences. It still says I have 0.4.0.1.

---

### Post by daradib on 2008-09-13
FYI:

The [feature freeze exception]("https://bugs.launchpad.net/ubuntu/+source/gnome-do/+bug/267020") was granted and we now have gnome-do 0.6.0.0-0ubuntu1 in Ubuntu Intrepid (to become 8.10).

Changelog:
```
gnome-do (0.6.0.0-0ubuntu1) intrepid; urgency=low

  * New upstream version, packaging based on the soon-to-be uploaded Debian
    package in pkg-cli-apps svn. FFe is LP: #267020
  * New upstream version fixes erratic positioning bug (LP: #204372)
  * debian/control
    + Update build-depends for new version
    + Update standards version to 3.8.0, adding README.Source
  * debian/gnome-do-autostart.desktop
  * debian/gnome-do.install
    + Delete our desktop file, install upstream's translated desktop file
      to /etc/xdg/autostart instead.
  * debian/gnome-do.preinst
    + Remove old autostart file on upgrade (if unmodified). Otherwise
      GNOME Do will appear twice in the autostart list.
  * debian/gnome-do.1
    + Manpage updated for new version
  * debian/rules:
    + Fix get-orig-source target to run properly from any directory; now should
    be policy compliant.
  * debian/copyright:
    + Refresh for new upstream version
    + Update to more recent CopyrightFormat proposal

 -- Christopher James Halse Rogers <raof@ubuntu.com> Sun, 14 Sep 2008 10:09:40 +1000
```

Thank you [Chris Halse Rogers]("https://launchpad.net/~raof")!

---

### Post by Stefanie on 2008-09-15
> **Vinay92 said:**
> I just followed the purge/install instructions and I still can't get to preferences. It still says I have 0.4.0.1.

what exactly did you do? where did it go wrong? you must add a line to your sources.list file.

---

### Post by Vinay92 on 2008-09-15
As far as I could tell, nothing *did* go wrong. Yes, I added the Software Sources, via the GUI.

---

### Post by Stefanie on 2008-09-17
maybe something went wrong while using the GUI. 

type this in the terminal:

```
gedit /etc/apt/sources.list
```

and copy paste the contents of the file here (wrapped in code tags).

---

### Post by Gimmeliberty on 2008-09-18
I have the same problem as Vinay92.

I completely purged Gnome Do from my system, added the repositories and updated, and installed via Synaptic version 0.5.9.9. It says it has installed fine, but when I start Do, it acts like 0.4.0.1, and when I go to About, it shows the version number as 0.4.0.1.

Now here's where it gets weird.

I grab the deb from Getdeb.net. I have Amd64 architecture, so I get gnome-do_0.6.0.0-0~getdeb1_amd64.deb, install it, and I have the exact same problem. After uninstalling it, I manually go through every folder that the package touches and I make sure that it's completely removed from my system. I even check /usr/local/ to make sure that there's nothing somehow there. Nothing.

So I pull out file-roller and extract *just* the gnome-do binary from the 0.6.0.0 deb file onto my Desktop. Nothing else. I run it from the terminal. It comes up as 0.4.0.1.

Now I'm clearly not a complete beginner when it comes to working with Linux, and I *can't figure out how that's even possible.*

Does anyone have any ideas?

---

### Post by Vinay92 on 2008-09-18
Well I fixed my problem by reinstalling Ubuntu :P I was meaning to do it anyway, since my initial install was within Windows.

---

### Post by albemuth on 2008-09-18
Hi I'm with the same problem, did the purge thing and nothing, here goes the repo list. I also tried removing all the sources but the "http://ppa.launchpad..." but it did not work :/

```
# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://ppa.launchpad.net/do-core/ubuntu hardy main
deb-src http://ppa.launchpad.net/do-core/ubuntu hardy main

deb http://cr.archive.ubuntu.com/ubuntu/ hardy main restricted
deb-src http://cr.archive.ubuntu.com/ubuntu/ hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://cr.archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb-src http://cr.archive.ubuntu.com/ubuntu/ hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://cr.archive.ubuntu.com/ubuntu/ hardy universe
deb-src http://cr.archive.ubuntu.com/ubuntu/ hardy universe
deb http://cr.archive.ubuntu.com/ubuntu/ hardy-updates universe
deb-src http://cr.archive.ubuntu.com/ubuntu/ hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://cr.archive.ubuntu.com/ubuntu/ hardy multiverse
deb-src http://cr.archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://cr.archive.ubuntu.com/ubuntu/ hardy-updates multiverse
deb-src http://cr.archive.ubuntu.com/ubuntu/ hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://cr.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
# deb-src http://cr.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu hardy partner
# deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://security.ubuntu.com/ubuntu hardy-security main restricted
deb-src http://security.ubuntu.com/ubuntu hardy-security main restricted
deb http://security.ubuntu.com/ubuntu hardy-security universe
deb-src http://security.ubuntu.com/ubuntu hardy-security universe
deb http://security.ubuntu.com/ubuntu hardy-security multiverse
deb-src http://security.ubuntu.com/ubuntu hardy-security multiverse

```

---

### Post by Stefanie on 2008-09-25
this is weird... i was in the same situation but for me the purge/reinstall worked flawlessly. i am by no means an expert but the sources list seems ok.

have you tried deleting ~/.local/share/gnome-do (completely, not only the plugin folder)? maybe that will do the trick.

---

### Post by gldblade on 2008-09-28
This is a silly question, but it can't hurt to ask: Did you guys make sure to quit Gnome-Do before doing the upgrade?  Gnome-Do continually runs in the background until you quit it.  If you upgrade Gnome-Do without quitting it, the older version of Gnome-Do will still be running, so it'll look like you have the older version installed even though you've upgraded.

---

### Post by albert_ein on 2008-10-03
> **gldblade said:**
>  Did you guys make sure to quit Gnome-Do before doing the upgrade? 

Well ;) I've just googled this thread with the same problem... and I must humbly say :) yes the problem of upgrading was solved thanks to this simple, yet efficient suggestion.

---

