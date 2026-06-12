---
title: "Java not working in Firefox : Tried everything"
date: 2008-07-17
forum: General Help
---

### Post by tech_cheetah on 2008-07-17
I have tried everything but java plugin is not working in firefox 3.
I have multiple JRE versions and have selected the default one from J2SDK from Sun. I have also copied the libjavaplugin.so to firefox-plugin directory with suitable permissions. I have also installed java plugin from synaptic but it didn't do any good either.
I have given up finally.
Can anybody help me with it ??

---

### Post by cheeto234 on 2008-07-17
I just switched to opera and everything works fine

---

### Post by SuperSonic4 on 2008-07-17
Are you running 32 bit or 64 bit ubuntu?

For 32bit I suggest you type: 
```
sudo apt-get remove gnash gnash-common libflash-mozplugin libflashsupport mozilla-plugin-gnash swfdec-mozilla && sudo apt-get install alsa-oss faac faad flashplugin-nonfree gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-pitfdll liblame0 non-free-codecs sun-java6-fonts sun-java6-jre sun-java6-plugin unrar
```

(source: [http://ubuntuforums.org/showthread.php?t=76668](http://ubuntuforums.org/showthread.php?t=76668) )

If you have 64bit I suggest installing 32bit firefox, instructions are [here](http://ubuntuforums.org/showthread.php?t=202537)

---

### Post by tech_cheetah on 2008-07-18
Its working now. The problem was that java was not enabled under Content.

---

