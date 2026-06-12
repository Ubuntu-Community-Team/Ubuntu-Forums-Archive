---
title: "intel hd graphics driver not detected and switched by a incompatible another"
date: 2019-07-06
forum: Hardware
---

### Post by muhammedabdeelrachid2005 on 2019-07-06
So, hello everybody i'm new to this community :)
I have joined because of my Intel HD Graphics problem. so in ANY Linux distribution or ANY Ubuntu flavor hardware acceleration is broken...:( so i thought to my self its the driver i have checked the driver updater and nothing... and then after googling and find there is a command i can put to the terminal and its "lspci" seeing that in the following picture that it recognized my VGA as a processor made sense : [ATTACH=CONFIG]283571[/ATTACH]
and its not the same in my windows, to clear stuff out i have tried in my Sister's PC which had Intel HD Graphics 4000 ( which the VRAM is less then mine ) and it got the right drivers :/.
another note that other drivers are mixed too with The same {Intel Atom Z}.
 My question is : Is there a solution? and if there is id like to hear it :)

My regards,
Rachid

---

### Post by CatKiller on 2019-07-06
They aren't mixed up; it's your processor that's providing the graphics.

You aren't lacking hardware acceleration; that gpu is just terrible.

---

### Post by muhammedabdeelrachid2005 on 2019-07-07
why just doesnt it use the gpu?i don't want to make my processor do all the things... any way to manual or automatically do that?

---

### Post by CatKiller on 2019-07-07
It is using the GPU. The GPU is part of the processor. It's called integrated graphics. That particular one just isn't very good, since it's a particularly cheap, particularly low-power, particularly old one.

---

### Post by MartyBuntu on 2019-07-07
Do you have a separate graphics card in that machine?

It's a pretty weak processor...don't expect any solution from drivers to be "magic".

---

