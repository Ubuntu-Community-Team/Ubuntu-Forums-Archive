---
title: "autologin"
date: 2009-03-19
forum: Installation &amp; Upgrades
---

### Post by copland on 2009-03-19
i'm using a very buggy xubuntu on a ps3, i just followed these instructions to autologin;-
[http://ubuntuforums.org/showthread.php?t=221302](http://ubuntuforums.org/showthread.php?t=221302)

i can now autologin but it won't recognize my password anymore so i cant sudo and stuff

also how do you boot with an irqpoll option

---

### Post by jlochhead on 2009-03-19
Your sudo problem is quite serious. You cannot do a vast amount of stuff without root access.

You have probably removed yourself from the sudoers file.

You need to boot-up a live cd, mount your filesystem and add yourself back to the sudoes file (google it - can't remember how to do it offhand).

---

### Post by Partyboi2 on 2009-03-19
You should be able to follow [[COLOR=Blue]this[/COLOR]]("https://help.ubuntu.com/community/BootOptions#Change%20Boot%20Options%20Permanently%20On%20An%20Existing%20Installation") to add irqpoll as a boot option.

---

