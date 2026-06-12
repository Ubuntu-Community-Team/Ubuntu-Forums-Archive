---
title: "fast system, but Ubuntu like molasses... why?"
date: 2008-08-10
forum: General Help
---

### Post by v8volvo on 2008-08-10
WinXP finally ate it on my folks' computer so I decided time to set them up with Ubuntu. Install went fine, but the thing does not run well now on Hardy. Physical specs of the machine are quite good, as follows:

MSI P4MAM-V motherboard
2.6GHz Celeron
768MB RAM
Integrated graphics with 32MB shared memory (Windows sees actual RAM as 736MB, while Ubuntu for some reason sees 725)
40GB hard disk
etc, etc, 

It's a modern machine, not a gaming fireball but it ran fast and smooth on XP. Ubuntu is jerky and constantly stalling, basic stuff like launching applications, doing file transfer operations, moving windows on the screen, opening webpages, etc seems to really tax it. Using OpenOffice or Evolution just about pushes it to the wall, the computer is almost unusable sometimes when receiving mail, etc. Of course Compiz cannot be enabled, it claims the system is not powerful enough. 

Everything works other than this, no non-functional components, but still the slow operation is annoying and weird. I have Ubuntu installed on my ancient IBM T21 laptop, with way worse specs (800MHz P3, 512 RAM, 8MB dedicated video), and it works much more smoothly and quickly. I'm new to this and stumped, anybody have an idea of where to start, or what might be wrong? Experience with this motherboard? Thanks in advance!

---

### Post by Vivaldi Gloria on 2008-08-10
May be there is a program slowing it down. I suggest you run 

```
top
```

in a terminal and check out the resources each program uses.

---

### Post by p_quarles on 2008-08-10
My guess would be that this is a purely graphics issue, and most likely with Compiz.

Try running:
```
metacity --replace
```
in a terminal to turn off the desktop effects. See if that improves overall performance

---

### Post by tacutu on 2008-08-10
does it get better if you turn off compiz?

---

### Post by Vivaldi Gloria on 2008-08-10
> **v8volvo said:**
> Of course Compiz cannot be enabled, it claims the system is not powerful enough. 

He has no compiz. ;)

---

### Post by tacutu on 2008-08-10
> **Vivaldi Gloria said:**
> He has no compiz. ;)
D'oh!

---

### Post by tacutu on 2008-08-10
indexing software? i.e. trackerd? cron running in the background, updating the system and running updatedb?

---

### Post by v8volvo on 2008-08-11
The indexing question and the program resource use are good ones. I will look into those first thing tomorrow AM. Unfortunately Compiz isn't an issue, as it cannot be turned on at all. Will report back with what I find. Thanks for the replies!

---

