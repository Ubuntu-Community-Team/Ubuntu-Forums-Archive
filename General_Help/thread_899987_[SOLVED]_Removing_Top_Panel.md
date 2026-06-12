---
title: "[SOLVED] Removing Top Panel"
date: 2008-08-24
forum: General Help
---

### Post by fparedesg on 2008-08-24
I want to remove the top panel, but the "Delete this Panel" option in grayed out. I removed the bottom one, but it looks like you *have* to have one, but I don't want it. I'm fine with Avant Windows Navigator. How can I delete the panel? Thanks!!

---

### Post by overdrank on 2008-08-24
> **fparedesg said:**
> I want to remove the top panel, but the "Delete this Panel" option in grayed out. I removed the bottom one, but it looks like you *have* to have one, but I don't want it. I'm fine with Avant Windows Navigator. How can I delete the panel? Thanks!!

Hi and this may help
[http://ubuntuforums.org/showthread.php?t=889886&highlight=delete+top+panel](http://ubuntuforums.org/showthread.php?t=889886&highlight=delete+top+panel)

---

### Post by SunnyRabbiera on 2008-08-24
You may still want to keep 1 panel around though just in case.

---

### Post by colobix on 2008-08-24
Well, you could do it like I did. Take a look here.

[http://scumbox.com/ubuntu/j.png](http://scumbox.com/ubuntu/j.png)

---

### Post by fparedesg on 2008-08-25
> **overdrank said:**
> Hi and this may help
[http://ubuntuforums.org/showthread.php?t=889886&highlight=delete+top+panel](http://ubuntuforums.org/showthread.php?t=889886&highlight=delete+top+panel)

I've tried the command in that link, but it doesn't work. When I use sudo, I get this error (below), and when I don't use sudo, nothing happens.

```
federico@Anchova:~$ sudo gnome-session-remove gnome-panel
[sudo] password for federico: 
Error: could not connect to the session manager
federico@Anchova:~$ gnome-session-remove gnome-panel
```

---

### Post by colobix on 2008-08-25
Have u tried to just move the panel down, delete the other one and add the things to the panel?

---

### Post by fparedesg on 2008-08-25
I went into Synaptic and uninstalled "gnome-panel" and rebooted. First time I tried, the desktop wouldn't load. Tried again and everything's working fine. Thanks everyone!

---

### Post by chaumurky on 2008-10-23
oh kay...

In Intrepid I get "sudo: gnome-session-remove: command not found"

:lolflag:

---

### Post by Trelane on 2008-11-04
This isnt solved, I just upgraded to Ubuntu 8.10 Intrepid Ibex and gnome-session-remove has gone!!!

I rely on this to remove that anoying panel that takes up valuable screenspace on a tiny eeepc screen. (Its all taken up with an embedded application)

Has anyone got another way to remove the panel?

---

### Post by homerjay on 2008-11-29
you could simply hide it by right clicking on the panel and clicking properties and checking the show hide button. then you can just collapse it by clicking on the arrow, then it's still around if you need it :)

---

