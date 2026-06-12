---
title: "XUBUNTU 8.10 w/ VNC Update Managers Freeze"
date: 2008-11-28
forum: General Help
---

### Post by sjmahler on 2008-11-28
It all works fine from the keyboard and console, but if you connect by VNC most of it works but the Update Managers freeze.

See also ...
[http://ubuntuforums.org/showthread.php?p=6269429#post6269429](http://ubuntuforums.org/showthread.php?p=6269429#post6269429)

---

### Post by cariboo on 2008-11-28
I checked to see if there are any bugs concerning the  way you want to do the updates, but couldn't find any thing. Could run update-manager in a terminal to see  what the error actually is?

```
sudo update manager
```

Is the command you need.

Jim

---

### Post by sjmahler on 2008-11-28
Well, from a terminal session "sudo update-manager" yields ...

$ sudo update-manager
Xlib: extension "RANDR" missing on display "127.0.0.1:1.0" .

the update manager window opens, the starting update manager window opens, the slider moves to the 33% point, the text under the progress slider says ... Building dependency tree ... and hangs.

"top" says it is taking 4% of the cpu and 4% of the memory.

I don't even have a guess about this.  Any suggestions?

...S

---

### Post by concorde106 on 2008-11-28
A HA! I knew there was another thread on this! I will try the sudo update manager on terminal and see what it says. Right now, I need to find out what the IP address is for the computer now. It is a dynamic one. Not good for VNC. I'll ask my dad to see if there is a way to make the computers have a static IP address. Oh, and yes, I am younger that 18 and I can set up a home file server. Tell me if ya think that is pretty cool!:)

---

### Post by sjmahler on 2008-11-28
Concorde, my xubuntu box has a static ip, but it shouldn't play into this problem unless you reboot and get a different address.
...S

---

### Post by sjmahler on 2008-11-28
cariboo907 ... I just noticed ... when I start an update manager in a VNC session, it has never asked me for an SU password.  TOP shows "update-manager" is running as my uid, not root.

Is this expected?

...S

---

### Post by sjmahler on 2008-11-28
Is this topic in the correct forum group?

---

### Post by concorde106 on 2008-11-28
Well, mine pretty much does the same as sjmahler's. I'm just using 8.04. When I run the command, it opens update manager, and gets to 50% of building dependancy tree, then stops.
EDIT: Updated to 8.10

---

### Post by sjmahler on 2008-12-06
ping!

---

