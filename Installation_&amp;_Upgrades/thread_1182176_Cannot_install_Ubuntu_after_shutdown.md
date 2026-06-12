---
title: "Cannot install Ubuntu after shutdown"
date: 2009-06-08
forum: Installation &amp; Upgrades
---

### Post by elstevodiablo on 2009-06-08
I posted something similar in General Help the other day but after several attempts at fixing Ubuntu I feel that it's more appropriate for it to be here. Basically I shut down Ubuntu one day manually after it froze and when turned back it said there was a failure to run fsdk or however it's spelled, so I ran it manually and all worked well but then it just took me to a black screen with the mouse cursor on it. I retried this a few times and did everything available to me in recovery mode, farthest I got was a message saying my graphical environment was damaged. Note this is the second time this happened after a bad shutdown.

    So this is where it got interesting, or should I say frustrating. I reluctantly had to delete Ubuntu and reinstall it, afterwords it took me to the same loading screen that I went to before, so I restarted which took me to a my login screen but after I logged in I saw the black screen (this time the 2 taskbars appeared on the top and bottom) my cursor turned into the circle to show that it's loading and it froze afterwards.

I reinstalled Ubuntu about 3 times after this each time using different file systems (my original was ext2 but it kept dying everytime ubuntu froze and I had to shutdown using the button). Ubuntu just plain won't work anymore. I'd be eternally grateful if somebody could explain how I can fix this and possibly fix any future errors after shutdown.

I'm using Jaunty Jackalope on a Dual Boot system (XP), and I tried every file system.

---

### Post by ronparent on 2009-06-08
I was unable to run the 9.04 live cd on any of my three pc's until I hit F6 on the first menu screen and selected (or deselected, however you look at it) noapic, nolapic. Ironically this seem to be a common problem with most current mb's (the more current the more likely). This is very likely related to your insallation freezes. You might try the noapic, nolapic options. Nothing lost whether or not it works.

---

### Post by elstevodiablo on 2009-06-08
Well the thing is everything ran before I shutdown, but it might possibly be the issue.
I have to finish my paper for school and then I'll try it out, thanks I'll keep you updated if it worked or not.

---

### Post by elstevodiablo on 2009-06-08
I can't find any options for noapic or anything like that, I think it's because my mobo is HP so it's probably locked.
But the thing is the livedisk worked and so did my previous ubuntu install untill I did an unclean install

---

### Post by ronparent on 2009-06-08
Booting into the live cd, the apic,lapic are found by hitting F6 on the intial booting menu. If installed from the live cd, the noapic,nolapic option are automatically added to the grub menu.lst boot instructions. That can also be added by maually editing the menu.lst. The fact that the mobo is HP is irrelevant. If it doesn't work then you are stuck looking for another cause!

---

### Post by elstevodiablo on 2009-06-08
Oh alright haha, sorry I'm kind of new to Ubuntu so I don't know all this I was looking at the BIOS for some reason XD. I'm gonna try it out now haha hope it works.

---

### Post by elstevodiablo on 2009-06-09
alright so I put in lapic and noapic, and it works! But it says it couldnt detect noapic and that dummy emulation had to be put into effect, what does this mean?

---

### Post by ronparent on 2009-06-10
Ignore the message. It is only the programer's message to prompt you to contact the mb maker to complain that the mb bios should be modified to suit ubuntu. In a windows centric world that is unlikely to gain much traction! How about the ubuntu programers writing the system so that it more compatible with crummy windows driven hardware design? That is unlikely also since it is patently obvious that linux implementations are purer than windows and that therefore it is unthinkable that standards be lowered to accomodate windows driven hardware.

Pardon my candor. These comment are only likely to draw fire. They  only reflect some burrs under my saddle that in my mind aren't being given serious attention.

---

