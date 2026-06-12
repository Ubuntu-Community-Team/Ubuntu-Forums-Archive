---
title: "Can't select items in alacarte/main menu"
date: 2008-09-03
forum: General Help
---

### Post by Bucky Ball on 2008-09-03
Hi all.

Ubuntu Studio 8.04 installed after running Gutsy pretty well flawlessly.

In terminal, just get '$' - no user or root@ ... even when I cd to a different directory. not 'media $', just '$' if you know what I mean.

Hit 'up' arrow keyboard key whilst in terminal, doesn't give me the last command I typed, just the code for the up arrow key:

```
$ ^[[A
```Instead of say

```
sudo blkid
```... if that was my last command (the other Ubuntu comps in the house do this and scroll back through commands from the current session with each press of the up arrow).

Probably causing/tied in with my major problem.

Preference->Main Menu (or type alacarte in terminal) and I have some fairly essential things unticked eg Synaptics Package Manager a and software sources. I tick them (or anything else) and the tick disappears after about a second.

I have posted and researched this, now getting desperate. Any help appreciated.

* Update on that - when I enter the sudo su command to become root, sure enough, gives me the correct signs, but hit exit and ... :

```
$ sudo su
root@ustudio:/media# exit
exit
$ 
```

Wondering if perhaps I have a user missing? Maybe should create one?

---

### Post by Bucky Ball on 2008-09-03
Just went to 'Users and Groups' and sure enough, there was a name missing for the user. Added that and it seemed to add it but won't let me unlock or modify anything, just locks up then throws the error:

'Unable to Authenticate'

Bamboozled, but as usual, will keep at it.

---

