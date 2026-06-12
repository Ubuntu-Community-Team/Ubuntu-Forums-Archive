---
title: "Can't locate boot.disk , drooping into shell...can't get into Ubuntu"
date: 2008-07-17
forum: General Help
---

### Post by notoriousmic24 on 2008-07-17
Hey. I'm an Ubuntu noob, so bare with me please. I've seen threads on my particular issue, but have no idea on how to get this fixed. 

Alert! Can't find ...boot.disk Dropping into another shell.

I get a message like that after a few minutes of trying to load Ubuntu. Any ideas of where to start here?

---

### Post by billrad1 on 2008-07-17
did this just happen after an update to the new kernel or headers, and therefore has rewritten your menu.lst?

if so, go to the command line session as sudo or root(ok folks, help me here), and go to boot\grub\and gedit your menu.lst, maybe by copying the essential parameters from the backup file.

hope that helps

billrad1

---

### Post by notoriousmic24 on 2008-07-17
ok well I have no idea what you mean by that...by noob i mean like retarded. You want me to go to that through windows or through terminal?

---

### Post by avtolle on 2008-07-17
Let's take a step back here. As I read the initial post, an attempt was made to boot Ubuntu, and the alert came up. So, first, is Ubuntu installed already, or was this from the Live CD? If from an installation already made, then was this failure, as mentioned above, after an update?

---

### Post by notoriousmic24 on 2008-07-17
No i've been using Ubuntu fine for a few months now. Sorry if i misused the word boot. More like load. The screen where the orange bar goes side to side. Yeah well that stays on for a few minutes until i get the error.

---

### Post by notoriousmic24 on 2008-07-17
And yes after a software update

---

### Post by billrad1 on 2008-07-17
my guess is it cannot find the correct harddrive after grub loads.

Mine did this until I figured it out.

You can also boot a live cd then edit menu.lst to fix it.

Billrad1

---

### Post by notoriousmic24 on 2008-07-17
How'd you figure it out?

---

