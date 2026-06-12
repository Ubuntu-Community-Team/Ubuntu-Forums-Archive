---
title: "Can't get onto the main graphical  OS"
date: 2008-11-16
forum: General Help
---

### Post by Xelax on 2008-11-16
Okay, here's what happened.

I recently updated Ubuntu, but I got a message saying 8 packages were broken. This stopped me updating or adding/removing programs due to errors. It kept advising me to use the Broken Package filter on the Synaptic Manager, so I did so, and removed the broken packages.

I continued as normal, but when I went onto Amazon (I doubt the site had anything to do with it- I think maybe the packages had only then been removed. Who knows) I got an error message that froze up the computer completely- I could move the mouse, but nothing happened.

I turned the computer off and rebooted the computer in recovery mode, and used the option that said it would sort out broken packages. Once that was done I chose log in as normal.

Unfortunately now I can't get onto0 the main log in screen. Ubuntu will load up as normal until the point where it *should* go onto the main orange screen and ask me for my user and password, and then lead to my desktop.

Instead I just get a black screen which asks me for my username and password- when I log in it asks me for commands. I'm not quite sure what to do.

Can anyone help? I've done anything totally retarded, feel free to tell me.

---

### Post by Xelax on 2008-11-16
Is everyone stumped, or just cba?

---

### Post by Xelax on 2008-11-16
Werl, thank you very much guys. I'll go off and experiment blindly.

---

### Post by Marcus Derekus on 2008-11-16
Boot up into Recover Mode and choose the option that mentions **fixing Xserver**

Not sure the exact wording the option is labled but its the only one that has anything to do with the above in bold

---

### Post by karlr42 on 2008-11-16
Don't be rude, someone will answer if they want to, they're not obligated to.
Try enter "startx" (without the qoutes) at that "black screen which asks me for my username and password-"

---

### Post by nikgare on 2008-11-16
> Werl, thank you very much guys. I'll go off and experiment blindly.

Please be more patient.  Storming off in a huff after waiting just half an hour for someone to sort your problems out for you is just plain rude.

---

### Post by Monotoko on 2008-11-16
type your username and password, then try:
```
startx
```

---

