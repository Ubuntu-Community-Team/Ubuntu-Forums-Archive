---
title: "Help with cairo clock.."
date: 2008-07-27
forum: General Help
---

### Post by mech7 on 2008-07-27
I am trying to start cairo clock with login... with the following:

cairo-clock -x 1200 -y 790 -w 120 -h 120 -t simple -s --seconds 

From the terminal it works ok... but when i save it in the session it does not work :(

---

### Post by MichaelSM on 2008-07-29
All I did with Cairo-Clock was go to Preferences>Sessions and enter cairo-clock in the 'Add' menu, as in cairo-clock followed by cairo-clock and that's about it. no comment.

As to making the analog clock re-appear in the same place you want it, twice, let me know how you went.

Mike.

---

### Post by mech7 on 2008-07-31
> **MichaelSM said:**
> As to making the analog clock re-appear in the same place you want it, twice, let me know how you went

It should be possible with the following parmaters: -x 1200 -y 790

change pixels to your screen resolution.. but grrr somehow theres a bug with me with the login hehe :p

---

### Post by MichaelSM on 2008-07-31
Sorry, I didn't read your post properly Mech7. About the session I mean.

I'm not a first-option terminal user which is why I use the gui.

I guess your terminal input with the -x and -y is  a 2d axes positioning command.

I'll give it a go.

Thank you, and all the best with the sessions and logins.

Mike.

---

### Post by Maucca on 2008-09-02
I tried these solutions but It wont work. Firstly the clock itself  only shows a piece of the pie :D Like a quarter, and the "hands of mickey" have their point of origin completely messed up regarding the center of the circle. 

This program is apparently filled with bugs. Why doesn't Ubuntu remember the last session, regarding correct settings for the clock? :(

Is there another plugin with better reliability out there?

I switched to linux three days ago, Im completely n00b.

Btw:

this was my command in sessions...

cairo-clock -x 1000 -y 200 -w 250 -h 250 -s -t simple -o -i -e &

---

