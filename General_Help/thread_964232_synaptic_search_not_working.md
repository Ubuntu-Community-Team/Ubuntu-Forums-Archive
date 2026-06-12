---
title: "synaptic search not working"
date: 2008-10-30
forum: General Help
---

### Post by monkeyking on 2008-10-30
Hi I can't make the search in synaptic work.

If I search for frozen-bubble in synaptic it finds nothing.

But i'm able to install it from commandline.
That is If I type,
```
frozen-bubble
The program 'frozen-bubble' is currently not installed.  You can install it by typing:
sudo apt-get install frozen-bubble
bash: frozen-bubble: command not found

```
So my sources.list is ok.

Does anyone have the same problem.

---

### Post by Pamphagus on 2008-10-30
yeap i did too but

Michael Vogt suggested to do "sudo update-apt-xapian-index" and restart Synaptic, which does help.

from

[https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/288797](https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/288797)

---

### Post by monkeyking on 2008-10-30
I'm using the wubi way of using ubuntu,
and after rebooting,
it's apparently working.

This is a strange error.
Highly annoying that you can't trust the search in synaptic.

How did this get by the betatesters.
I have to install adept then.

---

### Post by snova on 2008-11-01
I was having this same problem. Unfortunately neither Adept or KPackage were any improvement.

I tried the command suggested by Pamphagus and have had no further difficulties.

---

### Post by CbrPad on 2008-11-01
Thank you so much for this, I've been doing my nut in and it's saved the day.  I did a complete new install yesterday and half of my usual apps have been missing from synaptic (eg Gnumeric, Thunderbird, build-essential, etc etc).  I've checked my sources over and over and did everything I could think of to no avail and was thinking I was going crazy !

> **Pamphagus said:**
> yeap i did too but

Michael Vogt suggested to do "sudo update-apt-xapian-index" and restart Synaptic, which does help.

from

[https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/288797](https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/288797)

---

### Post by heatpumpcontrol on 2008-11-03
> **Pamphagus said:**
> yeap i did too but

Michael Vogt suggested to do "sudo update-apt-xapian-index" and restart Synaptic, which does help.

from

[https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/288797](https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/288797)

This worked great. Thank you

---

### Post by Capa Pinbacker on 2008-11-11
Thanks a lot... "sudo update-apt-xapian-index" fixed the same problem for me!

---

### Post by mikebailey on 2009-02-26
I also find i have this same problem, i ran the "sudo update-apt-xapian-indexcommand", and everything worked great, but after i reloaded my repos lists the problem showed itself to be present again. i'm running ubuntu intrepid and its using the wubi install, not that wubi would make a difference i figure.  i can manually look for the package in the list and find it, just the search part doesn't work, shows nothing, even for packages already installed

---

