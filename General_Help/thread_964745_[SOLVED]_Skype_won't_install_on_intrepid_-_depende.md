---
title: "[SOLVED] Skype won't install on intrepid - dependecies problem"
date: 2008-10-31
forum: General Help
---

### Post by niska on 2008-10-31
After a clean install of intrepid, I got this message trying to install skype from the medibuntu repository:

```
sudo apt-get install skype
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  skype: Depends: libqt4-dbus (>= 4.4.3) but it is not going to be installed
         Depends: libqt4-network (>= 4.4.3) but it is not going to be installed
         Depends: libqtcore4 (>= 4.4.3) but it is not going to be installed
         Depends: libqtgui4 (>= 4.4.3) but it is not going to be installed
E: Broken packages

```

Worked fine on Hardy. any ideas?

---

### Post by PsychedelicReaction on 2008-10-31
go to "System->Administration->Software Source" and see if repositories are enabled

---

### Post by ww711 on 2008-10-31
> **niska said:**
> 
```
sudo apt-get install skype
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  skype: Depends: libqt4-dbus (>= 4.4.3) but it is not going to be installed
         Depends: libqt4-network (>= 4.4.3) but it is not going to be installed
         Depends: libqtcore4 (>= 4.4.3) but it is not going to be installed
         Depends: libqtgui4 (>= 4.4.3) but it is not going to be installed
E: Broken packages

```



You are missing the qt4 libraries.

You can get them from the commandline, use the below

```
apt-get -f install
```

the -f switch will attempt to correct a system with broken dependencies in place; yours being the libqt parts.

---

### Post by niska on 2008-10-31
Of course the repositories are enabled.

Using apt-get -f install made no difference.

---

### Post by Slug71 on 2008-10-31
WTF is up with this? Before i was able to go into Synaptic and type in libqt4-core and it would come up and i was able to install, now it doesnt even come up in Synaptic.

---

### Post by orbisonitrum on 2008-10-31
I just upgraded 8.04 to intrepid, added the medibuntu repos and synaptic was behaving strange. Seaching for "skype" gave me no results, searching for "libqt4-core" didn't give me any search hits in synaptic either. I tried installing skype through the command line

```
> sudo apt-get install skype
```

and that worked, skype is installed. Then I restart synaptic, and now I can search and find both skype and libqt4 stuff. I have no idea why this happened, but the "1. quit synaptic", "2. install skype using apt-get" and "3. restart synaptic" seems to have worked for me. But there's definitely something strange going on in the intrepid/medibuntu/synaptic combo.

---

### Post by tatsuno on 2008-10-31
Did you remember to change the Medibuntu repo from hardy to intrepid?

---

### Post by niska on 2008-10-31
Yes I added the correct repositories.
I have both skype and libqt4-core appearing on synaptic properly - however skype fails to install, my problem is obviously different.

---

### Post by tatsuno on 2008-10-31
> **niska said:**
> I have both skype and libqt4-core appearing on synaptic properly - however skype fails to install, my problem is obviously different.

What about skype-common?

---

### Post by niska on 2008-10-31
> **tatsuno said:**
> What about skype-common?

Skype-common installs properly.

---

### Post by tatsuno on 2008-10-31
These are the dependencies for skype:

```

$ apt-cache depends skype
skype
  Depends: libasound2
  Depends: libc6
  Depends: libgcc1
  Depends: libqt4-dbus
  Depends: libqt4-network
  Depends: libqtcore4
  Depends: libqtgui4
  Depends: libstdc++6
  Depends: libx11-6
  Depends: libxext6
  Depends: libxss1
  Depends: libxv1
  Depends: skype-common
  Depends: dbus-x11
  Depends: libv4l-0
  Conflicts: skype
    skype-static
    skype-static-oss
  Conflicts: skype-common
  Replaces: skype
    skype-static
    skype-static-oss
  Replaces: skype-common

```

Try to install all the dependent packages and then skype.

You could also try to install it with aptitude...

---

### Post by niska on 2008-10-31
Ok, turns out that the package skype-static installs skype and it ships it's own qt4 libraries. it installs and works fine.

---

