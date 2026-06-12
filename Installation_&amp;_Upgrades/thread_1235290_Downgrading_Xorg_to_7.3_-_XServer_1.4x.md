---
title: "Downgrading Xorg to 7.3 - XServer 1.4x"
date: 2009-08-08
forum: Installation &amp; Upgrades
---

### Post by amites on 2009-08-08
Been trying to figure this one out for a while now

I have a Matrox G450 Dualhead card - Great card for a dualscreen workstation

the newest Linux driver available for this card fails on XServer 1.5 - been a number of attempts to get around this which I'm not ready to try and tackle (let alone 1.6 the version included with 9.04)

anyway - I've been trying to downgrade Xorg to 7.3 based on Hardy Heron sources.list

following the directions at [http://www.uluga.ubuntuforums.org/showthread.php?t=1171445](http://www.uluga.ubuntuforums.org/showthread.php?t=1171445)
for downgrading to XServer 1.5 using Intrepid

steps completed so far:
```
1) apt-get remove 'xserver-*'

2) apt-get remove libdrm2 libdrm-intel1 libgl1-mesa-dri

3) copy /etc/apt/sources.list /etc/apt/sources.list.jaunty

4) substitute 'jaunty' with 'hardy' everywhere in /etc/apt/sources.list

5) apt-get update
```


**6) apt-get install xserver-xorg-core**
here's where I get into trouble
```

#apt-get install xserver-xorg-core
... generic reporting ...
The following packages have unmet dependencies:
  xserver-xorg-core: Depends: xserver-xorg but it is not going to be installed
E: Broken packages
```

I then try
```

# apt-get install xserver-xorg
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  xserver-xorg: Depends: x11-xkb-utils but it is not going to be installed
                Depends: xserver-xorg-core (>= 2:1.4-3) but it is not going to be installed
                Depends: xserver-xorg-input-all but it is not going to be installed or
                         xserver-xorg-input-2
                Depends: xserver-xorg-video-all but it is not going to be installed or
                         xserver-xorg-video-2
                PreDepends: x11-common (>= 1:7.3+3) but it is not going to be installed
                Recommends: displayconfig-gtk but it is not going to be installed
                Recommends: libgl1-mesa-dri but it is not going to be installed
E: Broken packages
```

try installing each of those at once and the loop of dependencies continues

any ideas?

---

### Post by Light-kun on 2011-06-26
Hi. Have the same problem just after trying to install fglrx driver to my ubuntu 10.04.
Deleted  xserver-xorg from packages and can't install them back with same error:

```
#apt-get install xserver-xorg-core
... generic reporting ...
The following packages have unmet dependencies:
  xserver-xorg-core: Depends: xserver-xorg but it is not going to be installed
E: Broken packages
```

Can anyone help?

---

### Post by jocko on 2011-06-26
> **Light-kun said:**
> Hi. Have the same problem just after trying to install fglrx driver to my ubuntu 10.04.
Deleted  xserver-xorg from packages and can't install them back with same error:

```
#apt-get install xserver-xorg-core
... generic reporting ...
The following packages have unmet dependencies:
  xserver-xorg-core: Depends: xserver-xorg but it is not going to be installed
E: Broken packages
```Can anyone help?
You'll probably have to follow the chain of dependencies back until you find out why it won't install. So with your error, your next step is:
```
sudo apt-get install xserver-xorg
```

---

