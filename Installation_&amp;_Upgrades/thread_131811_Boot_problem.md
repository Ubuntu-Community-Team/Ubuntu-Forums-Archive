---
title: "Boot problem"
date: 2006-02-17
forum: Installation &amp; Upgrades
---

### Post by Patrol on 2006-02-17
Hi all !

I've installed Ubuntu 5.10 just 2 days ago.
The installation process finished successfully.
I installed nvidia drivers, my wifi, kubuntu, applications... Everything was perfect :D .

BUT, now, when I try to boot ubuntu, the system blocks.
Ubuntu loads successfully( black screen with brown colour ) with *[ok]* for each checking, then the nvidia screen appears, and then a black screen comes.
I don't know how to describe this screen, but the system blocks just after
*checking battery state                              [ok]*.

I spotted the following problem on the screen:
*filesystem NOT clean* .

I don't know what to do. Everything has been installed with official sources.
I installed only "basic" applications and kubuntu.

PLease help me ^^

( sorry for my English ... )

---

### Post by Patrol on 2006-02-17
EDIT : I just spotted this :
 *filesystem is in read-only ...*

I guess it's the problem...

How can I change it ?

---

### Post by Patrol on 2006-02-17
EDIT : In fact the problem comes from my xserver. The command *gdm* returns a lot of errors and it seems my xserver isn't well set up.
What can I do to reconfigure X ?

---

### Post by alfonz on 2006-02-17
type this in your command line


```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by Patrol on 2006-02-17
[QUOTE=alfonz]type this in your command line


```
sudo dpkg-reconfigure xserver-xorg
```[/QUOTE]

I have already tried it. 

But when it is finished, it comes back to the precedent screen and I don't know what to do...

If I reboot, the problem comes back again. It is weird because it was well configured and I didn't get any problem before this...

May my hd be brocken ? Because it is quite old now...

---

