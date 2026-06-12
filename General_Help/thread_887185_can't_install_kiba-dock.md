---
title: "can't install kiba-dock"
date: 2008-08-11
forum: General Help
---

### Post by weweboom on 2008-08-11
I tried to install the program kiba-dock and everything worked fine the first time I ran it, but after that I got

** Message: Failed to merge unused desktop file /root/.kiba-dock/weweboom. notifications: Bad key or directory name: "/apps/kiba/launchers//file": Can't have two slashes '/' in a row

** ERROR **: Failed to read config from gconf: (null)
aborting...
Aborted
root@Duncan:/home/weweboom/kiba-dock/kiba-dock/kiba-dock#

---

### Post by Crafty Kisses on 2008-08-11
> **weweboom said:**
> I tried to install the program kiba-dock and everything worked fine the first time I ran it, but after that I got

** Message: Failed to merge unused desktop file /root/.kiba-dock/weweboom. notifications: Bad key or directory name: "/apps/kiba/launchers//file": Can't have two slashes '/' in a row

** ERROR **: Failed to read config from gconf: (null)
aborting...
Aborted
root@Duncan:/home/weweboom/kiba-dock/kiba-dock/kiba-dock#

What version of Ubuntu are you using? I'm not sure if it works with the later versions of Ubuntu.

---

### Post by weweboom on 2008-08-11
Hardy, but it was a post that explained how to install it in hardy

[http://ubuntuforums.org/showthread.php?t=766674&page=2](http://ubuntuforums.org/showthread.php?t=766674&page=2)

---

### Post by x1a4 on 2008-08-11
Hi,

Remove the extra slash from the text '/apps/kiba/launchers/**/**file' in file /root/.kiba-dock/weweboom

BTW you shouldn't use your computer as root.  That's a serious security risk.

---

### Post by Crafty Kisses on 2008-08-11
> **weweboom said:**
> Hardy, but it was a post that explained how to install it in hardy

[http://ubuntuforums.org/showthread.php?t=766674&page=2](http://ubuntuforums.org/showthread.php?t=766674&page=2)

I wasn't aware of that, there is AWM, that's probably the best alternative and you can install that through Synaptic.

---

### Post by weweboom on 2008-08-11
to X1a4 what file how would I change that?
to Codename thanks, but I already have awm and would like one with a physics engine

---

### Post by x1a4 on 2008-08-11
Open the file [color=blue]/root/.kiba-dock/weweboom[/color] using a text editor (gEdit for example) and find the text [color=green]/apps/kiba/launchers/[color=red]**/**[/color]file[/color] and delete the duplicate forward slash. Save the file and run Kiba Doc

---

### Post by weweboom on 2008-08-11
that file doesn't exist the folder .kiba-dock doesn't exist either, kiba-dock exists, but not .kiba-dock

---

### Post by weweboom on 2008-08-11
I don't know if I'm allowed to do this in the forum, but I guess I will know if my thread is shutdown, sorry please don't ban me if this is not allowed I genuinly don't know I still haven't solved my issue and people stopped responding to my thread so here is my problem again... when trying to run kiba-dock in hardy (it's worked before) I get this response in the terminal

** Message: Failed to merge unused desktop file /root/.kiba-dock/weweboom. notifications: Bad key or directory name: "/apps/kiba/launchers//file": Can't have two slashes '/' in a row

** ERROR **: Failed to read config from gconf: (null)
aborting...
Aborted
root@Duncan:/home/weweboom/kiba-dock/kiba-dock/kiba-dock#

---

### Post by djrobthaman on 2008-08-11
I would check your kiba config files to see if there was that entry with the double slash somewhere in there.  Also, move that desktop file somewhere else and see if you still get the same error about not being able to merge.

---

### Post by damis648 on 2008-08-11
> **weweboom said:**
> I don't know if I'm allowed to do this in the forum, but I guess I will know if my thread is shutdown, sorry please don't ban me if this is not allowed I genuinly don't know I still haven't solved my issue and people stopped responding to my thread so here is my problem again... when trying to run kiba-dock in hardy (it's worked before) I get this response in the terminal

** Message: Failed to merge unused desktop file /root/.kiba-dock/weweboom. notifications: Bad key or directory name: "/apps/kiba/launchers//file": Can't have two slashes '/' in a row

** ERROR **: Failed to read config from gconf: (null)
aborting...
Aborted
root@Duncan:/home/weweboom/kiba-dock/kiba-dock/kiba-dock#

Any mods, you might want to merge the threads or close one of them. On that issue, do not run it as root. type
```
exit
```
, making sure  you are logged in as your normal user and try again.

---

### Post by weweboom on 2008-08-11
thanks a lot not running  as root fixed it

---

### Post by damis648 on 2008-08-11
> **weweboom said:**
> thanks a lot not running  as root fixed it

Glad to help!:guitar:

---

