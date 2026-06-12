---
title: "Installing applications to a specific location."
date: 2009-04-05
forum: Installation &amp; Upgrades
---

### Post by dE_logics on 2009-04-05
How do you do it?...I mean if an application is installed from a repository, then where does it get installed to? (of course the root folder by default); can we change the default location?

Also can I download the packages from these software repositories in from of deb/rmp/tar etc...?...for instance for installation in a computer without an internet connection and not necessarily working on UBUNTU...for instance Gentoo.

I wanted a graphical deb/tar installer; and while installing we can specify the location where they need to be installed right?

Also do we have a graphical RPM to DEB converter?

---

### Post by pbpersson on 2009-04-05
> **dE_logics said:**
> How do you do it?...I mean if an application is installed from a repository, then where does it get installed to? (of course the root folder by default); can we change the default location?

Also can I download the packages from these software repositories in from of deb/rmp/tar etc...?...for instance for installation in a computer without an internet connection and not necessarily working on UBUNTU...for instance Gentoo.

I wanted a graphical deb/tar installer; and while installing we can specify the location where they need to be installed right?


Packages written specifically for Ubuntu I would not try to install on another distro.

You can download packages as DEB files, burn them to a CD, and then take them to another computer I believe....however I have never tried this.  The difficult part would be getting all the dependencies also loaded on the CD.  It sounds very time consuming.

A package installs where it needs to be

symlinks, docs, binary, and library files all go to various places.

Application settings typically are in a hidden directory/files in your /home mount point

There is no way to change how this works.....why would you want to?

---

### Post by dE_logics on 2009-04-05
You mean to change the destination directory I gotta work hard!


I wanna increase the number of drives to reduce the access times (I'm on windows 7 currently and have 2 partitions (2.5 GB and 1.25 GB) for software to speed it up)

And the dependencies for binaries should be less right?

---

### Post by dE_logics on 2009-04-05
So what will be the consequence (relative to installing in a different directory) of installing the whole application (and its components) in the root directory?


I mean does it have an advantage over the alternative?

---

### Post by pbpersson on 2009-04-05
We must not be on the same page here

I told you that **symlinks, docs, binary, and library files all go to various places.**

You cannot change it - that is how it is.

dependencies are a different story

when we speak of dependencies we are talking about things that need to be in place

For instance, let us say you are building a house and you want to add a porch light to the front of your house.  Before you add a porch light you need a wall, before you put up the wall up you need a foundation, before you lay the foundation you need a section of land.

---

### Post by pbpersson on 2009-04-05
> **dE_logics said:**
> 
I wanna increase the number of drives to reduce the access times (I'm on windows 7 currently and have 2 partitions (2.5 GB and 1.25 GB) for software to speed it up)

Linux works on mount points - things like /var, /home, /usr, etc.

If you took your mount points and spread then across several drives....PHYSICAL drives working in parallel I suppose you might be able to increase your performance.....

It depends upon what you are doing with your computer

---

### Post by dE_logics on 2009-04-05
You mean like RAID...that's what we do to the page files also.



Ok thanks!...but what about the graphical DEB installer?

---

