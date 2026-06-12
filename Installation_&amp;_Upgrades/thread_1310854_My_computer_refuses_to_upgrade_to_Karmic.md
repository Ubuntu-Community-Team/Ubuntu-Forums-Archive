---
title: "My computer refuses to upgrade to Karmic"
date: 2009-11-02
forum: Installation &amp; Upgrades
---

### Post by rivode on 2009-11-02
Hi,

The update manager refuses to upgrade my computer to Karmic.  I get this message:

```
Your system is up-to-date 

There are no upgrades available for your system. The upgrade will now 
be cancelled. 

```

I haven't found any answer to this problem (it's pretty hard to search for).  I've tried deleting /var/cache/apt/archives and /var/lib/apt/lists before trying again.

I've attached the full output and my sources.list.  Can anyone give me any clues about what's going on?

---

### Post by NE Key on 2009-11-02
Have you tried;

Press Alt+F2

enter the command  ```
update-manager -d
```

---

### Post by slakkie on 2009-11-02
> **NE Key said:**
> Have you tried;

Press Alt+F2

enter the command  ```
update-manager -d
```

Don't (see why? Check the upgrade ubuntu link in my sig)

Could you post the output of lsb_release -a please.

---

### Post by rivode on 2009-11-02
Here it is:

```
LSB Version:	core-2.0-ia32:core-2.0-noarch:core-3.0-ia32:core-3.0-noarch:core-3.1-ia32:core-3.1-noarch:core-3.2-ia32:core-3.2-noarch:core-4.0-ia32:core-4.0-noarch:cxx-3.0-ia32:cxx-3.0-noarch:cxx-3.1-ia32:cxx-3.1-noarch:cxx-3.2-ia32:cxx-3.2-noarch:cxx-4.0-ia32:cxx-4.0-noarch:desktop-3.1-ia32:desktop-3.1-noarch:desktop-3.2-ia32:desktop-3.2-noarch:desktop-4.0-ia32:desktop-4.0-noarch:graphics-2.0-ia32:graphics-2.0-noarch:graphics-3.0-ia32:graphics-3.0-noarch:graphics-3.1-ia32:graphics-3.1-noarch:graphics-3.2-ia32:graphics-3.2-noarch:graphics-4.0-ia32:graphics-4.0-noarch:qt4-3.1-ia32:qt4-3.1-noarch
Distributor ID:	Ubuntu
Description:	Ubuntu 9.04
Release:	9.04
Codename:	jaunty

```

(I was wondering if there was a command to tell me that!)

---

### Post by slakkie on 2009-11-02
You're running Jaunty, which is good.

Could you use the following sources.list?

[http://pb.opperschaap.net/83](http://pb.opperschaap.net/83)

Replace CODENAME with jaunty.

Then open [http://tinyurl.com/ubuupgrade](http://tinyurl.com/ubuupgrade) and see the update instructions.

---

### Post by rivode on 2009-11-02
I'll give that a shot next time I'm somewhere with a worthwhile internet connection (it could be a while though).

---

### Post by rivode on 2009-11-02
I've also tried various combinations of the distribution in sources.list, tried different mirrors and so on.  I might have to scratch through the update manager's source to see what's going on.

---

### Post by rivode on 2009-11-03
I just notced that there's a log file, and this was in it:

```
2009-11-02 19:37:51,831 DEBUG Marking 'ubuntu-desktop' for upgrade
2009-11-02 19:37:52,979 DEBUG About to apply the following changes
2009-11-02 19:37:53,306 DEBUG Keep at same version: bluez-gnome bluez-gstreamer kdelibs5-data smartdimmer mtools .......

```

Why might it choose to keep every package?  My current "ubuntu-desktop" version is the one from Jaunty.

---

### Post by rivode on 2009-11-03
I also remember experimenting with Intel xorg drivers, both from an alpha of Karmic and some older version 2.4 drivers (which I currently have installed).

---

### Post by fanglinyong on 2009-11-03
i think the version 9.04 is very good !
so ,i din't upgrade to 9.10

---

### Post by rivode on 2009-11-03
> **fanglinyong said:**
> i think the version 9.04 is very good !
so ,i din't upgrade to 9.10

Jaunty isn't too bad, but I'm keen to try out the new Intel graphics drivers.

---

