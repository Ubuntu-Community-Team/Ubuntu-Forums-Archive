---
title: "Cannot install 11.04 on Asus netbook"
date: 2011-04-28
forum: Hardware
---

### Post by bblinn on 2011-04-28
I've just purchased an Asus 1215T-MU17 that comes with Win7/Home and I'm hoping to install Ubuntu 11.04 along side. I've created a CD that will boot the machine and starts the process. The option I selected would install Ubuntu within Windows. The notebook then indicates that it will reboot to continue.

"Caught signal 15, shutting down".
CD ejects.
System hangs.
Power-off reset.
System reboots to Windows.

Might someone be able to offer a clue as to what I'm doing wrong?

Thanks!

---

### Post by abelmaio on 2011-04-28
Hello.

The Asus is a Netbook or a Notebook?


When it ask to reboot is after the installation process? Does it install everything correctly? 


Also, if it doesn't install correctly by CD you can try by USB. 


--
AM

---

### Post by techbyter on 2011-04-28
> The Asus is a Netbook or a Notebook?
It's a Netbook so it has no CD/DVD player, but I can set it to boot from a USB DVD player.

> When it ask to reboot is after the installation process? Does it install everything correctly? 
It's before the installation starts so nothing is installed.

> Also, if it doesn't install correctly by CD you can try by USB. 
That's a good idea. I'll try it and report back.

---

### Post by cairnzi on 2011-04-28
after a bit of google reasearch i think there is compatibilaty problems with that model.... they seem to be able to be solved with drivers if you digg around.... not sure but google and/or ubuntu wiki would be the place to look, hope this helps.

---

### Post by techbyter on 2011-04-28
Here's the "solution" I found. It's not ideal, but it works.

On revisiting the Ubuntu site, I was reminded of WUBI. Using the WUBI installer, I have added 11.04 to the netbook.

---

### Post by bcbc on 2011-04-28
If wubi works then so should installing from CD. Probably it's a bad burn on the CD. Or you could use a USB. Or keep wubi too.

---

### Post by kakesh on 2011-04-28
I have ASUS 1215T MU-10 and it seems that internal microphone doesn't work. Filed a bug, but it still doesn't. But it was working with 10.10. If someone managed to fix it let me know :) Here is the [LINK]("https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/770555") on a bug.

---

### Post by techbyter on 2011-04-29
> **bcbc said:**
> If wubi works then so should installing from CD. Probably it's a bad burn on the CD. Or you could use a USB. Or keep wubi too.
Bad burn seemed reasonable, but I used the same CD to install on another notebook system. It was an upgrade there, but everything worked as expected.

On the netbook, the problem occurred during the initial reboot: Shutdown starts, disc ejects, and before the shutdown is complete, signal 15 occurs and that's the end of the story.
WUBI isn't my preferred method, but it works.

And WOW! The interface has certainly changed.* I feel like I'm in a large and complex game of hide and seek.

*Not unexpected or a complaint, by the way. :)

---

