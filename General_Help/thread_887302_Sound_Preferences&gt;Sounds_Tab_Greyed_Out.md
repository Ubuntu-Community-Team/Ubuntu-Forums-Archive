---
title: "Sound Preferences&gt;Sounds Tab Greyed Out"
date: 2008-08-12
forum: General Help
---

### Post by rrradio on 2008-08-12
I've searched the forums for an answer to this, to no avail, and I have yet to actually be acknowledged at all in the IRC channel, so here's my post.  

First of all, the sound on my computer is working perfectly.  However, when I go to System>Preferences>Sound, the Sounds tab is completely greyed out, and I cannot change or edit anything.  I'm mainly trying to turn off the supremely annoying Error beep that goes off at full volume even when my computer is muted.

Let me know what info I need to post, rather than me trying to guess what your questions are going to be, so you can help me figure this out.  Thanks in advance.

---

### Post by phyrewall on 2008-08-21
If you run it from the console, do you get something like this?

# EDIT - Output from console:

```
(gnome-sound-properties:9410): libglade-WARNING **: could not find glade file 'sound-properties.glade'

(gnome-sound-properties:9410): sound-properties-WARNING **: Bad setup, install the freedesktop sound theme
bateau@Section9:~$ gnome-sound-properties 

(gnome-sound-properties:9811): libglade-WARNING **: could not find glade file 'sound-properties.glade'

(gnome-sound-properties:9811): sound-properties-WARNING **: Bad setup, install the freedesktop sound theme


```[There is a bug report on it: ]("https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/258703")

               [[IMG]https://bugs.launchpad.net/@@/person[/IMG] Sebastien Bacher]("https://bugs.launchpad.net/%7Eseb128")          wrote     on 2008-08-18:     [              (permalink)     ]("https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/258703/comments/5")   
                   [FONT=monospace]thank you for your bug report, that's because the new libcanberra requires the freedesktop sound theme to work correctly and this one is not available yet in ubuntu
[/FONT]

---

