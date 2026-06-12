---
title: "Diving completly into ubuntu, removing dual boot"
date: 2008-07-27
forum: General Help
---

### Post by DrFugly on 2008-07-27
Howdy ubuntu gurus,

Just today I realized that I really have no use for grub. My bios allows me to hit 'esc' and boot into which ever drive. And since I hardly ever choose windows, it is just annoying me.

So I want to remove grub completely, mbr and all. I've seen plenty of articles on removing grub and going to back to windows but none about how to just completely stick w/ ubuntu. (Which is kinda depressing)

So how do I get the mbr to just go for ubuntu?

Thank you!

---

### Post by jonian_g on 2008-07-27
Go to Applications>Add/Remove and search and install "Startup-Manager". When installed go to System>Admin>Startup-Manager. On the window that appears check the checkbox before "Use timeout in..." and if you don't want to see a timeout message give "0" in "Timeout in seconds".

You can't remove completely grub. By doing what I described you just wont see it.

---

### Post by steveneddy on 2008-07-27
Welcome to Full Time Ubuntu.

---

### Post by DrFugly on 2008-07-28
> **jonian_g said:**
> Go to Applications>Add/Remove and search and install "Startup-Manager". When installed go to System>Admin>Startup-Manager. On the window that appears check the checkbox before "Use timeout in..." and if you don't want to see a timeout message give "0" in "Timeout in seconds".

You can't remove completely grub. By doing what I described you just wont see it.

Well that is no fun. Right now I have it at 0, that was when i realized that I just don't need it, but grub still flashes. Oh well, I guess I just have to settle :(

And thank you for the welcoming! :)

---

### Post by jonian_g on 2008-07-28
What you mean when you say it flashes? For some seconds?
Welcome to full time ubuntu from me too :)

---

### Post by DrFugly on 2008-08-01
> **jonian_g said:**
> What you mean when you say it flashes? For some seconds?
Welcome to full time ubuntu from me too :)
It flashes for about 1 second then disappears. I can't hit 'esc' in time to stop it or anything, but its there.

And thankyou!

---

### Post by zvacet on 2008-08-01
If you want some time to be able to press Esc button then put in menu list time out 3 or 5 sec.If you don´t want to use windows anymore why don´t you delete them and add free space to Ubuntu?

---

### Post by DrFugly on 2008-08-01
Well it turns out that I didn't have my startup-manager setup correctly (I didn't see the options at the bottom) So now everything is working nicely.

Also I don't really have a need for space and I still have some useful stuff on my windows, no need to mess with it for now. 

Hehe don't wanna become overzealous with Ubuntu now!

Thanks everyone!

---

