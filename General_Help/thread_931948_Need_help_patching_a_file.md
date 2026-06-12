---
title: "Need help patching a file"
date: 2008-09-27
forum: General Help
---

### Post by coldfire204 on 2008-09-27
I'm trying to install wine from source code, because I have to patch a file in to get a game to work.. sooo I got the source installed, and I have the patch file, but when I use the syntax my walkthrough gives me, it doesn't work.  I checked out the help for patch, but can't make heads or tails out of it.

I have wine installed, I switch to that dir, and then do this:

patch -p0 nameofpatch.patch

The terminal accepts that, but then just hangs, does anybody know the correct way to install a patch?  I'd love to get this game running so I don't have to go into Windows to play it. (the game is Final Fantasy Online.)

---

### Post by spiderbatdad on 2008-09-27
not a user of wine myself but...are you the owner of the wine directory?
ls -al will show you info on the files in the present working directory, including owner and group. Also a link to the tutorial you are following might help someone to see just what you are trying to do.

---

### Post by coldfire204 on 2008-09-28
Hey, thanks for the response, I think I got it figured out, I just had to do patch -p1 -i filename.patch

It seemed to install fine, hopefully this helps someone else if they run across a similar situation.

---

