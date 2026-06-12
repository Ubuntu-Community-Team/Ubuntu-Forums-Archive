---
title: "Speeding up Kubuntu For Headless App."
date: 2005-11-06
forum: General Help
---

### Post by grim1234 on 2005-11-06
Hi, I'm using kubuntu on a 1ghz C3 processor, with 256mb memory. 

It's running very well, although a little slow. 

I'm using this box as a headless computer and am connecting via vnc from a windows computer. 

However, when using krfb (remote desktop), the krfb process uses 60-90% of the cpu. This is too high to be useful so i'd like some tips to reduce this. 

So some solutions could be :

1. Trim the eye candy and unnecessary programs from kde. 
2. use a different remote server solution?
3. reduce desktop resolution?

I can't leave kde as I require a kde app, and want to run it from kde. 

So what would you suggest?

(thanks in advance)

G.

---

### Post by Jengu on 2005-11-07
Does krfb have different compression settings? That maybe what's eating the CPU. That sounds strangely high -- remote desktop should be network bound, not CPU bound.

---

### Post by ltmon on 2005-11-07
Have you tried using FreeNX instead (instructions on the ubuntu wiki)?  It is apparently the latest and greatest in remote desktop technology for X at the moment.

L.

---

### Post by grim1234 on 2005-11-07
I haven't tried that, but I'll test it and see if it works. I'm not concerned about the network useage (local lan), but the system is too slow to use at the moment.

Also, which services and software can i get rid of? I'm not using sound so i can remove all sound related services.

---

### Post by grim1234 on 2005-11-07
As for compression, i'm not sure about server side but i'm specifying raw when i connect from vncviewer (windows), which i think is no compression.

---

### Post by grim1234 on 2005-11-07
Seems krfb has a problem with the cpu usage. 

However, i got freenx working and it's amazing! 2-3% cpu max, very very fast and smooth.

most impressive.

link here helped : [https://wiki.ubuntu.com/FreeNX](https://wiki.ubuntu.com/FreeNX)

---

