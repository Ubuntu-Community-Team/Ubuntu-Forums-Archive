---
title: "Creating live cd from install"
date: 2008-07-25
forum: General Help
---

### Post by cyclobs on 2008-07-25
hey guys,

i was wondering if anyone knows of an app that will allow you to make a ubuntu live cd out of an install you have so that you have all your programs, themes and settings?

---

### Post by ryanhaigh on 2008-07-28
[http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html](http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html)

There is also another one although I can't recall the name right now.

---

### Post by Rhubarb on 2008-07-28
Try out UCK:
[http://uck.sourceforge.net/](http://uck.sourceforge.net/)

And I'm sure there was another one starting with re......
Can't remember atm.
(or maybe I was thinking of remastersys)

---

### Post by dexter.deepak on 2008-07-28
the name is Remastersys , if you are using hardy, its in the repos:
```
sudo apt-get install remastersys
```

it can help you get a full backup of your system ..or you have the option to make a custom live cd too.

another tool (i have not used it yet) is Reconstructor, it can only help you make custom live cd.

---

### Post by Rhubarb on 2008-07-28
> **dexter.deepak said:**
> another tool (i have not used it yet) is Reconstructor, it can only help you make custom live cd.
That's it!  So I wasn't going mad after all (I thought there was another one starting with re...)
Thanks.

You can grab reconstructor here:
[http://reconstructor.aperantis.com/](http://reconstructor.aperantis.com/)

---

### Post by robert shearer on 2008-07-28
this one works fine, [http://www.remastersys.klikit-linux.com/](http://www.remastersys.klikit-linux.com/)
for ubuntu or ubuntu derivatves.

 So far I have tried it on Ubuntu Hardy and Xubuntu Hardy.
 A p3/1000Mhz/512Mb and p3/450Mhz/256Mb respectively, took 1hr on the first and 1hr45 on the second.

Includes option to remaster current running install with all apps, desktop,data etc as a live cd/installer
or
option to make as a remaster of o/s with all apps but no personal data so as it can be given as an install to others.

The first option is just great as a simple but comprehensive backup.

And did I mention that it is so automated that all you need to type in the terminal is "sudo remastersys backup"

There is even a gui for those that prefer it. (install it ,reboot and look in System-> preferences(or admin can't remember which) for remastersys

---

