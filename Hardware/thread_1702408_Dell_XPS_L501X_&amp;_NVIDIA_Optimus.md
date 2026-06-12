---
title: "Dell XPS L501X &amp; NVIDIA Optimus"
date: 2011-03-07
forum: Hardware
---

### Post by kornfan71 on 2011-03-07
Hello all,
I understand that NV Optimus does not work in Linux, which is OK with me. What I don't know, however, is which graphics card *does *Linux use? I'd prefer to only use the Intel HD Graphics, since it'd conserve battery life, and because I wouldn't be needing super-awesome accelerated graphics in Linux.

So, does an Optimus machine (a Dell XPS L501X, in my case) running Linux use the NVIDIA card or Intel card? If it uses the NVIDIA card, is there a way to use the Intel card instead?

Thanks!

---

### Post by svast on 2011-03-09
It does use the Intel card by default.
There is even wome way to shut down the nvidia card with some acpi_call script.

---

### Post by kornfan71 on 2011-03-09
Sounds good. Thanks!
I'll have to look for that method of shutting off the nvidia adapter...

---

### Post by iammeagain on 2011-03-12
[http://ubuntuforums.org/showthread.php?t=1703301](http://ubuntuforums.org/showthread.php?t=1703301)

Here you go. That should explain most of it. I just got my laptop a week ago so I trying real hard to get this working well with Ubuntu. It appears that both video cards are on by default. But you can turn off Nvidia, I don't believe Intel can be turned off because Nvidia uses it to connect to the display. Or at least thats how I understand it.

---

### Post by kornfan71 on 2011-03-12
Thanks for the link! I'll follow the instructions whenever I have time. :D

---

### Post by iammeagain on 2011-03-13
It is still a work in progress, but it gets the job done for now.

Going to try and incorporate some of this in the next few weeks. [http://ubuntuforums.org/showpost.php?p=10553459&postcount=23](http://ubuntuforums.org/showpost.php?p=10553459&postcount=23)

---

### Post by Madskillzz on 2011-04-10
Just ordered this laptop. Just checking how the optimus would run  in linux. Nice job on getting that script. The added bat life was a concern for me in ubuntu. How u guys liking yours any regrets? i didn't get the 1080p screen and am thinking of calling in an upgrade.

---

### Post by beew on 2011-04-10
> **Madskillzz said:**
> Just ordered this laptop. Just checking how the optimus would run  in linux. Nice job on getting that script. The added bat life was a concern for me in ubuntu. How u guys liking yours any regrets? i didn't get the 1080p screen and am thinking of calling in an upgrade.

If battery life is all that concerns you why not just get a laptop without Nvidia? It would be cheaper. Disabling the Nvidia card is not what I would call "working". It is just a least bad scenario if you can't return your laptop.

---

