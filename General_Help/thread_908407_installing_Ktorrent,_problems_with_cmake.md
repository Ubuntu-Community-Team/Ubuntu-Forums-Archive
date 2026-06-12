---
title: "installing Ktorrent, problems with cmake"
date: 2008-09-02
forum: General Help
---

### Post by aliencam on 2008-09-02
I am trying to install the new version of ktorrent from source, but I keep getting errors.  

the directions at the ktorrent.org website say to use cmake to compile the program, so I apt-get installed cmake, and now I am getting this error: 


```


CMake Error: ERROR: cmake/modules/FindKDE4Internal.cmake not found in /home/cameron/.kde4/share/apps;/usr/lib/kde4/share/kde4/apps
```


I found out that this error means that I need to have **kdelibs5-dev** installed, however I can't install that because of it's dependencies.  

installing kdelibs5-dev depends on having **libasound2-dev** installed, but I can't install libasound2-dev because the version of **libasound** that I have installed is the wrong version. 

```
libasound2-dev:
  Depends: libasound2 (=1.0.15-3ubuntu4) but 1.0.16-0ubuntu0.1 is to be installed

```

so I went into synaptic, selected libasound2 and am trying to do a force version for version 1.0.15-3ubuntu4 (hardy), but if I were to do that, it would uninstall/break the following packages: 

```
flashplugin-nonfree
ia32-libs
ia32-sun-java6-bin
lib32asound2
nspluginwrapper
wine
```


is there any way to get this installed?  or does anyone have a .deb install of ktorrent 3.1.2-KDE4  (the only one I can find is in the repos for intrepid, and I am using hardy)

---

