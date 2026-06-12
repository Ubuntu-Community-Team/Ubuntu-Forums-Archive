---
title: "what to do to show the adesklets on my desktop?"
date: 2008-10-24
forum: General Help
---

### Post by 24dhruv on 2008-10-24
i have installed adesklets with synaptics package manager
then i have done typing the command adesklets -i got some dessklets get installed. but my question is how to make them shown on the desktop.

f.y.k.i. im usung ubuntu 8.04 LTS Desktop Edition(64-bit)(is it known as hardy heron?)
i m new to ubuntu yet i have some amount of knowledge of unix so can use that terminal.

---

### Post by 24dhruv on 2008-10-24
i ave then passed this command

```
dhruv@dhruv-laptop:~$ adesklets --nautilus
dhruv@dhruv-laptop:~$ 
```


it doesnt show any message.

---

### Post by dragonSBF on 2008-10-24
Try to dl the gdesklets and gdesklets-data in Synaptic.  Then go to Applications / Accessories / gDesklets

Or you may want to try screenlets.  Just dl screenlets in Synaptic and navigate to place above.

---

### Post by Ginsly on 2008-11-02
You need to register each desklet first, by navigating to its directory and running a command from within it...

```
./desklet_name.py
```
(choose r to register)

I've only downloaded individual desklets from the adesklets site, and unpacked them in my Home folder before. Ive not used the installer, so I'm not quite sure where they will have been put, sorry.

Then ```
adesklets --nautilus
```  to start
and  ```
adesklets --killall
```   to quit


This helped me to get started .... 
[http://ubuntuforums.org/showthread.php?t=183709&highlight=adesklets](http://ubuntuforums.org/showthread.php?t=183709&highlight=adesklets)

---

