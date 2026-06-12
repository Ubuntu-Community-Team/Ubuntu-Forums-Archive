---
title: "Instability with Firefox, XMMS"
date: 2005-11-15
forum: General Help
---

### Post by TonyS on 2005-11-15
Hi all,

First off, sorry if I'm posting in the wrong place. I'm afraid I'm feeling unusually clueless and don't have the FIRST idea what might be causing my problem!

Second, congrats to everyone involved in Ubuntu. I've toyed with it over the last three releases, and its definitely improving steadily, getting closer and closer to "just working". Installation seems quicker and less painful than XP now, which is pretty impressive.

However...

I've installed 5.10 on a bog-standard P3 Compaq Deskpro to use as an MP3 jukebox in the office. Its the first Linux desktop here, and I have a cunning plan to gradually insinuate it in this way by proving that its not scary...

Sadly it has been scary, as it has a peculiar tendancy to crash, apparently spontaniously, on users using applications.

Firefox tends to just close itself down for no obvious reason, perhaps once an hour during normal use.

XMMS seems to take the whole session down with it, returning the user to the login screen (though not a full reboot). XMMS does this with absolutely no provocation... you can leave it playing for two hours, then it'll just cut out out of the blue.

The funny thing is, this machine was doing some similar things under Windows 2000 previously, which is why it was available to play with. I had assumed that was a Windows problem, and that it had probably been damaged by a trojan.

So, could be hardware, could be Ubuntu. Can anyone suggest a step forward? Is there logging in Ubuntu that'd tell me if I had (say) a dodgy RAM stick?

In fact, it'd really help me if someone said this type of instability was par for the course with 5.10... though I've never seen Linux behave this way before.

Any help appreciated!

Cheers,

Tony

---

### Post by kruz on 2005-11-15
that is odd
i would try the easiest solution first
and open ur terminal

apt-get and get rid of firefox and xmms
then reinstall them and check if the problem goes away

second try opening them from console
sometimes the icons have options 
xmms&
firefox&

if neither one of these work
try other browsers/mp3 players to get an idea if its hardware or software


also run the commands without the & command
so you can see if there are any error outputs

hope this helps a lil
keep us updated

---

### Post by mcduck on 2005-11-16
[QUOTE=TonyS]
So, could be hardware, could be Ubuntu. Can anyone suggest a step forward? Is there logging in Ubuntu that'd tell me if I had (say) a dodgy RAM stick?
[/QUOTE]
Have you tried running memtest? It's installed with ubuntu and you can choose to run it from grub menu.. Memtest86 is pretty much the only way to check that your memory works fine, and I was very pleased to see that it comes with Ubuntu.

You can of course also try to read through all the logs in /var/log/, if there would be something. But if windows was also actinng funny IU'd bet it's a hardware issue..

---

### Post by Mustard on 2005-11-16
This sounds exactly like the problem I had recently.  The desktop and apps would all start shutting down, at quite random and unpredictable times, and I would be returned to the gdm login screen.  Logs showed a 'Fatal X error'.  It proved to be a faulty RAM stick problem (running memtest showed up a number of errors).  Two new RAM sticks installed and the problem has disappeared.

---

### Post by ngms27 on 2005-11-16
Firefox is bugged and will do exactly as you say.

Try installing Opera, which is stable but it takes a while to get it working with plugins and printing.

Well worth it.

Don't even think about Firefox 1.5 as that hangs my machine after visiting 2 or 3 sites every time without fail.

JonnyT

---

### Post by sigma2805 on 2005-11-16
ive noticed this issue with firefox as well....it just randomly closes...very annoying.

---

### Post by TonyS on 2005-11-18
Hi all,

Well, I must have been unknowingly channelling the Great Spirit of Geekdom when I randomly nominated a dodgy ramstick in my original post, as that's exactly what it turned out to be.

As suggested I tried Memtest, and it indicated errors (not until test 6, but consistently there) and by a process of elimination I found that one of the three installed sticks was kaput.

With that removed everything seems MUCH happier.

As I mentioned, this machine has been problematic for ages... its been a year since that stick was installed, so I guess that long.... under both Windows and Ubuntu. Your collective efforts have saved it from the skip, and (even better) restored our MP3 music collection.

Thanks very much all! Its all about community in the end.

Cheers,

Tony

---

