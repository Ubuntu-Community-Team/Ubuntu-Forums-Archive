---
title: "Not all flash sites work"
date: 2009-09-23
forum: Installation &amp; Upgrades
---

### Post by LoopyWolf on 2009-09-23
I'm having a problem similar to others, but their solutions don't work..

I have Ubuntu 9.04 Jaunty Jackalope

Flash works on some sites, such as Youtube, but not on others, such as Songza

Following advice from others I did a complete uninstall of absolutely everything "flash" in Synaptics, and ran the .deb for Ubuntu from the Adobe site.   

Flash still works on YouTube, but still does not work on all sites..  Do I need to give more info?

---

### Post by mikewhatever on 2009-09-25
It could be an IE only site, but just to make sure you don't have other plugins, can you post the output of the following command:

dpkg -l | grep 'gnash\|swfdec\|flash'

---

### Post by junke1990 on 2009-09-25
most of the time it helps to install **flashplugin-nonfree** and for java the sun plugin: **sun-java6-plugin** with those 2 you should be able to browse everything normally

---

### Post by drew_austin on 2009-09-26
I'm having the same problem with 9.04. Youtube works OK, but when I try to play something at songza, it goes into an endless loading cycle. I've installed flashplugin-nonfree and sun-java6-plugin, but still no luck. Here's the output of dpkg -l | grep 'gnash\|swfdec\|flash':

ii  adobe-flashplugin                          10.0.32.18-1                              Adobe Flash Player plugin version 10
ii  flashplugin-installer                      10.0.32.18ubuntu0.9.04.1                  Adobe Flash Player plugin installer
ii  flashplugin-nonfree                        10.0.32.18ubuntu0.9.04.1                  Adobe Flash Player plugin installer (transit
ii  flashplugin-nonfree-extrasound             0.0.svn2431-3                             Adobe Flash Player platform support library 
rc  gnash-common                               0.8.5-0ubuntu1                            free SWF movie player - common files/librari
ii  libswfdec-0.8-0                            0.8.4-1                                   SWF (Macromedia Flash) decoder library
ii  swfdec-gnome                               2.26.0-1                                  Tools to play SWF files (Macromedia Flash) o
ii  swfdec-mozilla                             0.8.2-1ubuntu1                            Mozilla plugin for SWF files (Macromedia Fla

Any ideas?

---

### Post by satyaas on 2009-09-26
I do have the same problem. Flash is not working in few sites. It is like endless process. I've installed flash and it is working fine in youtube. I'm a newbie to Ubuntu..

---

### Post by drew_austin on 2009-09-26
OK, I finally got it working. I followed this HOWTO:
[http://ubuntuforums.org/showthread.php?t=766683&highlight=streaming+audio+problem](http://ubuntuforums.org/showthread.php?t=766683&highlight=streaming+audio+problem)

---

