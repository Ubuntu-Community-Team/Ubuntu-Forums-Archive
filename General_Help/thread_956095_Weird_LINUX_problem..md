---
title: "Weird LINUX problem."
date: 2008-10-22
forum: General Help
---

### Post by andrewwg94 on 2008-10-22
This sort of doesn't have much to do with ubuntu in particular but...

Everytime I run linux on my computer, it boots up, and the loading light just won't stop, as if it was stuck. no matter if i'm bootingg off the hard drive, live cd, or anything. It did the samething with the fedora 9 live cd. but when i go into xp, everything just works like normal. It's clearly not a hardware problem. anyone has any ideas?

---

### Post by dagoth_pie on 2008-10-22
im not sure what it is, but I think theres a key combination to show a text output rather than the splash screen, ctrl+F1 I think, something like that

---

### Post by andrewwg94 on 2008-10-22
> **dagoth_pie said:**
> im not sure what it is, but I think theres a key combination to show a text output rather than the splash screen, ctrl+F1 I think, something like that

what does that have to do with my problem?

---

### Post by dagoth_pie on 2008-10-22
It's getting up to the loading screen then stopping isn't it? if thats the case getting the text output of whats happening rather than seeing the loading screen should give you an idea as to whats stopping it from loading, or have I misunderstood you somewhere?

---

### Post by dannybuntu on 2008-10-22
Maybe it has to do with your video card. I dunno. 




________
I'm not an ubuntu expert. So if I write something and don't come back, that means I don't know.

---

### Post by DGortze380 on 2008-10-22
> **andrewwg94 said:**
> This sort of doesn't have much to do with ubuntu in particular but...

Everytime I run linux on my computer, it boots up, and the loading light just won't stop, as if it was stuck. no matter if i'm bootingg off the hard drive, live cd, or anything. It did the samething with the fedora 9 live cd. but when i go into xp, everything just works like normal. It's clearly not a hardware problem. anyone has any ideas?

Lights mean nothing. There probably isn't anything written into the current kernel or drivers to control the light.

---

### Post by dave.com on 2008-10-22
Linux can act strange because a description of the system architecture is reported incorrectly. This could be compatability, or dbus system device detection or OS version/platf related. It could be the wrong selection of OS target architecture (you may have opted to install i686 instead of i386, or similar). We don't know. 

What is the output for: ```
# ls -FGg / 
```  

Detail to us your platform architecture and cpu wordsize - running a 64bit x86 Intel, or a 64 bit x86 AMD for example. Is the "Loading light" a HDD 'active' LED telltale in front of your pc box?

---

### Post by hyper_ch on 2008-10-23
It is adviced to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

Or in short terms: Help others to help you

Also, when you are asked to post output from (config) files or from a command, use ```

``` brackets around (each) output. That makes it also easier to read.

---

