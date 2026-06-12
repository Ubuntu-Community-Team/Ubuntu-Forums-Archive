---
title: "403 Webcat Access Denied"
date: 2009-01-11
forum: Installation &amp; Upgrades
---

### Post by sanjeevchatterjee on 2009-01-11
Hi Everybody,

I am very new to Linux. I have installed ubuntu 8.10 with the intention of making an internal mail server using Zimbra. But for installing Zimbra I would need some prerequisite ie to start with SSH deamon. But the problem I am facing is whenever I try to install anything via synaptic or through command line interface (apt-get install ssh openssh-server) or trying to go for the available updates, I am encountering the error "[COLOR="Red"]403 webcat access denied[/COLOR]" either right at the starting point or after some progress. I have tried by changing repositories which did not helped. FYI I am behind a hardware firewall, an UTM (Unified Threat Management) Device by Cyberoam. 

It would be very helpful to me if you can suggest any remedy to this. Thanks in Advance.

---

### Post by mikewhatever on 2009-01-11
A similar error and a solution is provided here ->[http://ubuntuforums.org/showthread.php?t=766683&highlight=gstreamer+plugins](http://ubuntuforums.org/showthread.php?t=766683&highlight=gstreamer+plugins)

> FORBIDDEN 403 ERROR

Those of you receiving the "Forbidden 403" error should change your sources from "http" to "ftp". You can change it by opening the sources file with your default or favourite text editor (substitute "gedit" for "kwrite" in Kubuntu and "mousepad" in Xubuntu) from within the terminal:


---

