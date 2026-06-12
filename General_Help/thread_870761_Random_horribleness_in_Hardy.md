---
title: "Random horribleness in Hardy"
date: 2008-07-26
forum: General Help
---

### Post by maze1612 on 2008-07-26
Randomly my computer will do one of the following....
close whatever application is open currently.
lock up all my applications including top and bottom desktop bars but leave the mouse running.
lock up everything completely including the mouse.
log me off
and rarely sometimes fail on shutdown or do something weird on startup (i don't remember what the error codes were on those but on the last shut down the last part of the error from shutting down the network was dbus-connect = fail or something like that.

i'm using a cheap ati graphics card and an hour ago or so i posted in the hardware forum for recommendations on a new agp 8x card (so if you know about graphics cards look for that post :) but i got to thinking, what if it isn't my graphics card causing the lockups an stuff. what if it's something else, like my network card. sometimes my computer will crash every few minutes and other times i can play open arena for hours. sometimes i can download a torrent all day and reboot once, an others if i start downloading a torrent and it locks up in 2 minutes. sometimes i'll be reading something in gedit and suddenly get logged out or i'll have firefox open with 18 tabs loading pages and get logged out. it doesn't seem to match up to any one program or any single event. also firestarter always fails on startup. seems to be working just fine but still says failed on startup.

so what i really want to know is, when i randomly get logged out what error log can i read to find out why. or what error log can i check to find out what made it lock up when i have to do a hard reboot. or what causes programs to just randomly close, where are those error logs.

thanks in advance for any help or idea as to what to look for to track down what is really causing this.



sk8v AMD AthlonFX 64, ati radeon 9200, don't remember sound card, 1gb ram. Ubuntu 8.04 32 bit

---

### Post by northern lights on 2008-07-26
> **maze1612 said:**
> so what i really want to know is, when i randomly get logged out what error log can i read to find out why. or what error log can i check to find out what made it lock up when i have to do a hard reboot. or what causes programs to just randomly close, where are those error logs.
After one of those forced logouts, log back in and run ```
dmesg
``` first thing. Post the output, if you can't find the relevant information.

[EDIT]
Alternatively to posting the whole output, you can also run```
dmesg > ~/dmesg.txt
```which will create a textfile with the output in your home folder, attach that to the next post.
[/EDIT]

---

### Post by maze1612 on 2008-07-26
thank you so much, but fortunately, or unfortunately, this seems to be one of the non locking up days.... i'll get that posted as soon as possible.

will that also help with the random lock ups too? or does that get cleared at restart?

---

