---
title: "Desktop Performance"
date: 2005-11-30
forum: General Help
---

### Post by jstobern on 2005-11-30
Hi Everyone,

Does anyone else notice that Ubuntu and Kubuntu runs very slow when loading applications? I'm comparing this to Red Hat distributions (FC3, EL3, EL4 using KDE) and the dreaded Windows XP. I absolutely love this distrobutions and after a short evaluation running Breezy in VMWare I decided to switch to (K)Ubuntu as my main linux OS. 

The slow start up of applications is really starting to bother me. Usually these types of problems get resolved with some kind of tweaked setting that I've missed. Can anyone help me out?

I specifically notice is takes a long time to load Firefox (1.07 and 1.5), Thunderbird, VMWare, Azureus. I'm using the default theme for KDE and Clearlooks in GNOME. 

So what is my definition of slow? Firefox takes less then 3 secs to start on my EL3, FC3, EL4 installations. On Ubuntu 1.07 take > 15 secs while 1.5 takes 10 secs. 

I haven't started to complaint about the cmoputer boot times because that seems to be a problem with all distrobutions (until initng is implemented).

What I'm really looking for is a guide to speed up Ubuntu by getting rid of a bunch of stuff I don't need. 

Cheers,
Jens.

---

### Post by kwaanens on 2005-11-30
Firefox 1.0.7 takes 3-4 seconds to start on my computer. Thunderbird 1.0.7 takes <3 So, no complaints here :)
Do you have more extensions on one or the other? Some extensions really affect start time.

- Ketil

---

### Post by jstobern on 2005-11-30
Hi Ketil,

I do not have extensions on the (K)Ubuntu installs and only a couple on the other boxes.

Does anyone think that prelinking will help? I found this in a development forum for Hoary.

[http://ubuntuforums.org/showpost.php?p=9864&postcount=80](http://ubuntuforums.org/showpost.php?p=9864&postcount=80)

Cheers,
Jens.

---

### Post by 23meg on 2005-11-30
It will help, but you're best off using it sparingly, with certain apps, not system-wide. Are you sure your hd operation is optimized (DMA, caching, etc.)?

Also, comparing to Windows would be unfair, because binaries are statically linked in Windows in contrast to Linux, which naturally speeds up application launching.

---

### Post by jstobern on 2005-11-30
23meg,

Is there a command that I can run to tell me this information? The only tweak that I've done to the drives is for the CD. I turned on DMA according to the FAQ. 

Cheers,
Jens.

---

### Post by jstobern on 2005-12-01
I've done some investigation and there must be some setting wrong on my computer.

If I load the Live CD and run Firefox, the application loads quick. Firefox loads in less than 3 secs. It's almost as quick as XP. :) I installed Ubuntu in VMWare and loading firefox is also very quick. Again 3-4 secs. I don't have alot of stuff in my Ubuntu system so I might just reinstall. Or can someone recommend a better way to reset all the applications?

Cheers,
Jens.

---

### Post by SirKillalot on 2005-12-01
[QUOTE=kwaanens]Firefox 1.0.7 takes 3-4 seconds to start on my computer. Thunderbird 1.0.7 takes <3 So, no complaints here :)
Do you have more extensions on one or the other? Some extensions really affect start time.

- Ketil[/QUOTE]
try firefox 1.5, it starts much faster for me than the old versions!

---

