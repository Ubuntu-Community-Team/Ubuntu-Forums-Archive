---
title: "Installing Sakai on Ubuntu"
date: 2009-09-10
forum: Installation &amp; Upgrades
---

### Post by Funi on 2009-09-10
Hi

I would like to install Sakai on Ubuntu.....i dont even know where to start....would u pls help me with steps. Its sakai 2.5.3 version.

Thanks
:confused:

---

### Post by Funi on 2009-09-10
help on installing sakai on ubuntu.....

---

### Post by skinny honkie on 2009-09-27
I can make a recommendation that might help a lot - assuming that you're installing 2.5 and not 2.6, follow the [sakai 2.5.3 install guide]("http://confluence.sakaiproject.org/display/DOC/Install+Guide+-+Source+Install+(2.5)") with the following exceptions:

Don't use the tomcat 5.5 in the ubuntu repositories, download a binary version instead and set up the paths in .profile as indicated in the documentation. Ditto with Java - this will make things a bit more straightforward for you to understand and troubleshoot.

Other than that, you might want to also consider using the binary version of mysql or compiling your own for the sake of transparency. It all seemed much easier to me when I was able to go to one obvious location for a homedir for any given app, rather than having parts of apps scattered between /usr/share/, /usr/local/, and /etc/ as far as adapting the sakia install guide for ubuntu is concerned.

Good Luck!

---

### Post by yannoo on 2009-10-27
I have tried installing with the Tomcat 5.5 package from Ubuntu and can confirm it is a nightmare.

Actually, I'm developer of Dokeos, another LMS, and I have received a lot of complaints about how difficult it is to install the videoconference module (it also uses a Java server), but I can honestly say it is *much easier* to install the full set of features with Dokeos than it is with Sakai, for a similar feature set and possibly better performances.

This being said, I haven't tried installing from Tomcat, Java and MySQL sources or binaries, I have only used my Ubuntu packages directly, but I find it very surprising not to find a real installation manual for Debian or Ubuntu, using the default packages (after all, it *is* possible to run Java 1.5 *and* Tomcat 5.5 from the default packages).

What a horrible feeling...

---

### Post by i.r.id10t on 2009-12-03
Going thru the same, only trying on a debian server (ubuntu for desktop, debian for servers).  Sure wish they'd (rsmart maybe?) make a debian package...

---

