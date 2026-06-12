---
title: "[SOLVED] Java stopped working after last 8.04 update"
date: 2008-07-12
forum: General Help
---

### Post by Kappity on 2008-07-12
I have two programs other than web browsers that use Java.  One is Jin, a GUI for playing on the Internet Chess Servers.  The other is Shredder Classic for Linux, a chess playing program which runs in a Java environment.

When I first updated to Hardy Heron, they both worked fine.  However, after running the last series of updates, I noticed that neither one would even start.  Then I discovered that java applets would not work inside either Firefox or Opera.  I think I may have had a problem with Opera before, but Firefox had been okay.

So java seems to be broken all of a sudden.  Has anybody else encountered this with a recent 8.04 update?  If so, did you find a way to fix it?  All I could think of was to go into synaptic package manager and download any java stuff that I didn't already have.  Didn't help.  Then I went to the Java site and downloaded the RPM for the latest jre, but when I tried to install it, I got a slew of error messages.  Sorry, don't have the list in front of me at the moment.  I'm typing this from somewhere else on a different computer while I have some down time.

I'm kind of hoping that this is a known bug that will be fixed in the next series of updates, because I don't really know where to start troubleshooting.

---

### Post by jamesstansell on 2008-07-13
For the Hardy release the default java was switched to openjdk.  Getting the command-line apps and the browser applets working is a little different, so lets start with the apps.

```
$ sudo apt-get install sun-java6-jre
$ sudo update-java-alternatives -s java-6-sun

```

(BTW, if for some reason you ever do want to install from java.com you should get the appropriate .bin file instead of an .rpm file.)

---

### Post by Kappity on 2008-07-14
> **jamesstansell said:**
> For the Hardy release the default java was switched to openjdk.  Getting the command-line apps and the browser applets working is a little different, so lets start with the apps.

```
$ sudo apt-get install sun-java6-jre
$ sudo update-java-alternatives -s java-6-sun

```

(BTW, if for some reason you ever do want to install from java.com you should get the appropriate .bin file instead of an .rpm file.)

That fixed it.  Shredder and Jin are both working again.  Although you seemed to imply that getting java working in the browsers might need additional steps, both Opera and Firefox are now able to handle the java applet on one site where I went to check.([http://www.time.gov/timezone.cgi?Eastern/d/-5/java](http://www.time.gov/timezone.cgi?Eastern/d/-5/java))

Guess I need to do more reading on apt-get and when I need to use it.

Thanks for your help!:biggrin:

---

### Post by nlchap0 on 2010-07-10
> **jamesstansell said:**
> For the Hardy release the default java was switched to openjdk.  Getting the command-line apps and the browser applets working is a little different, so lets start with the apps.

```
$ sudo apt-get install sun-java6-jre
$ sudo update-java-alternatives -s java-6-sun

```(BTW, if for some reason you ever do want to install from java.com you should get the appropriate .bin file instead of an .rpm file.)

Hi, I thought I was going crazy when my java also seemed to spontaneously stop working.  However, for me this fix does not make java work in Firefox or Epiphany.  I've done the standard trick of cd'ing to the plugins directory and manually doing an ln -s to the appropriate plugin path, but Firefox still can't recognize java.  I don't know what I would do for Epiphany if it also doesn't recognize java.

Note, I am using 8.04 on a Thinkpad T43.  commandline java apps seem work fine.  My googling has suggested that I remove an icedtea plugin, but I don't have that installed, so that's not the problem.  Any suggestions?

---

