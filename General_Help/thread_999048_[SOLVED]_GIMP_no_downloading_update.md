---
title: "[SOLVED] GIMP no downloading update"
date: 2008-12-01
forum: General Help
---

### Post by Tony_photoplus on 2008-12-01
I did as the gimp site told in a terminal and all I gat was this:
tony@tony-desktop:~$ apt-get install gimp
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
tony@tony-desktop:~$ 
How do I over come this please

Tony

---

### Post by binbash on 2008-12-01
sudo apt-get install gimp

---

### Post by scarf on 2008-12-01
yes, for administrative tasks like that, you will need to prepend the command with sudo.  'man sudo' for more info.  alternatively, you could have just installed gimp thru the "add/remove..." button in the applications menu.  i would recommend to check that applet first before installing something thru the command line.  hmm, but doesn't gimp come pre-installed?  anyway, sorry i might not have an exact grasp of your situation, but these are just some thoughts....

---

### Post by ranch hand on 2008-12-01
Yes, you will have to "sudo" your comand and enter your password.  This will do the trick.

I find that, for me, the terminal is the best way to get updates or new packages.  I use the Update Manager, Synaptic and Add/Remove for research.

---

### Post by glotz on 2008-12-01
What page did you read that instruction on? (just a lil thing I'd like to check.)

---

### Post by ranch hand on 2008-12-02
[http://gimp.org/downloads/](http://gimp.org/downloads/)

I would say that is where he got it.  I haven't tried it as I am too busy and it is abit ahead of what comes with Hardy and I haven't learned to use it the way I want yet.  Nice program for working on photos.

---

### Post by glotz on 2008-12-02
The point I was thinking was if the command was preceded by a $ or a #. What's the difference you ask?
[B]
username@computer:~$[/B] sudo su
[sudo] password for username: 
**root@computer:/home/username#**

So # means you're the root and $ means you're not. GIMP is lovely!

---

### Post by Tony_photoplus on 2008-12-02
Thank you it is now resolved.  I deleted it and redownloaded and that seemed to have done the trick.  Thanks

Tony

---

