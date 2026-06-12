---
title: "Lenovo ideapad b560g"
date: 2010-11-06
forum: Hardware
---

### Post by pek007 on 2010-11-06
hi,

i bought this computer. it had installed windows 7 and since i am fan of ubuntu, i installed ubuntu. and there problems begin...

1. the touchpad didnt worked at all. if i pluged in mouse it was ok. after 2 days of looking for solution i found this thread: [http://ubuntuforums.org/showpost.php?p=8816327&postcount=6](http://ubuntuforums.org/showpost.php?p=8816327&postcount=6) and everything started to working almoust. side scroll dont work for up and also the multi touch dont work... but i can live with that part...

2. problem is graphic card... it have gma hd in procesor (i3) and second one is nvidia 310m. when i put on drivers everything goes black after booting grub... so the search for solution began... i turned around a lot of threads... and i try out few different thing... but non of them worked :( so, now i am asking if someone have the toturial or anything how to fix this drivers? it looks like no matter what i try, still dont work as it should :(

thanks for your help 
ziga

---

### Post by P4man on 2010-11-06
"optimus" (the combined intel IGP and nvidia card) isnt properly supported on linux. You have to set one or the other in the bios and if you select the nvidia card in the bios, you can active the nvidia drivers. To save battery life, you may want to use the intel IGP instead (at the expense of 3D/gaming performance, but you may not need that under ubuntu anyway)

---

### Post by pek007 on 2010-11-07
yes, i was also thinking about that... than i saw igp and i didnt know what is that... if this is gma... 
after all, i just reinstalled ubuntu and just didnt turned on drivers of nvidia... everything works nice... so i will leave without drivers... i will use them only in windows :S

btw, if you have any idea how to fix touchpad? that it will work as it should? maybe multitouch and scroling?

thank you for your help and explanation,
ziga

---

### Post by P4man on 2010-11-07
IGP= integrated graphics processor. ITs what is in your chipset (or CPU nowadays) and usually by intel. Low power and low performance. Discrete graphics is a seperate, higher performance graphics chip, like one by nVidia.

As for the touchpad.. not sure. You could try installing 'pointing devices' in software center if its a synaptic touchpad.

---

### Post by pek007 on 2010-11-07
how can i know if is synaptic touchpad?

thx

---

### Post by P4man on 2010-11-07
Just install the app. If your touchpad isnt supported  by it, it wont have a lot of options.

---

### Post by pek007 on 2010-11-08
ok, thank you, i will try.

i just whant you to ask, i looked into bios, and have only 2 potions. to set igd or optimus. but there is no nvidia that i can set in bios?

thank you

---

### Post by P4man on 2010-11-08
I suspect setting it to optimus will enable the nvidia gpu and let you install the nvidia drivers and run the discrete nvidia gpu (on windows this setting would dynamically switch between igp and nvidia depending if you run a 3d app; on linux I suspect it will always be using the nvidia gpu).

If you dont have a pressing need for 3d performance, id leave it on IGP. Saves a lot of battery and intel IGPs tend to work fairly well with linux, they are plenty fast enough for compiz and the like, and rather good at videoplayback. Just not exactly great for gaming.

---

### Post by pek007 on 2010-11-08
well, no problems... in linux i dont play games... 
i tryed to have on optimus and installed nvidia drivers, and after only had black screen. so, i just leave optimus and dont touch nvidia drivers :) and i hope everything works as it should...

---

### Post by P4man on 2010-11-08
my sig would likely have contained a solution for the black screen, but if you dont intend to game, you are better off using the intel IGP.

---

### Post by gradinaruvasile on 2010-11-08
Currently Optimus (the integrated-add-on card switcheroo) is NOT supported on Linux by nvidia.
Certain laptops have an explicit option of using the nvidia card, those work with the nvidia driver. But the ones that dont, are not supported and you can only  use the integrated intel card.

[http://www.nvnews.net/vbulletin/showthread.php?t=144750&page=6](http://www.nvnews.net/vbulletin/showthread.php?t=144750&page=6)

---

### Post by pek007 on 2010-11-08
ok, thank you for your help... i think i am happy now... just installing last time ubuntu on my machine now... hope it will work everything at least 2 years :D

thx and bye

---

