---
title: "Raid setup"
date: 2010-01-03
forum: Hardware
---

### Post by Rexhunt on 2010-01-03
Hi at home I have a number of computers set up in a network and one of them I am attempting to organise as a server for everyting that may ever need serving. Among the things that I want to serve is files particularly storage for my music that is accessable by windows, linux, and mac os 9.
 
The computer is currently a PIII @550mhz and a bit more than 300 mb of sd ram. It is running as a headless machine ubuntu 8.04 and is accesable over the network. Unfortunantly  there is no internet connection in the room with the computer in it there is an internet connection on a windows vista desktop which I can use periodically.
 
It has 2 isa slots and I have in one of my drawers 3 isa cards with parrelel ports serial ports etc. each of them also has ide.
 
Now my question is would it be worth setiing up a software raid array through all of this without bying any extra software however I am happy to download software.
 
Thanks in advance.

---

### Post by IcarusR on 2010-01-03
ISA is very old standard, now obselete. Not many mobo have ISA slots. 
My guess is that it would not be quick at writing to the raid. If I remember correctly ISA is only 16bit where as PCI is 32bit.

Only one way to find out though, give it a try.

---

### Post by Rexhunt on 2010-01-03
So does Ubuntu 8.04 hav the nnessacery softwarre orr wwould I have to download some?

---

### Post by IcarusR on 2010-01-03
I believe dmraid is the software you want. I'm not sure if it will have been installed by default on you 8.04 box. If not it may be on the origional CD.
Later kernels than the one on 8.04 have much better support for raid built in. 
Might be worth considering installing later version of ubuntu.

Strongly recomend you do some reading up on the subject as there are a lot of decisions to be considered. Software raid or fakeraid. raid 0, 1, 5, etc.

My server has a 3ware pci card which does hardware raid, onboard cpu & ram.
There is still a lot of debate as to which is the best. Most go for hardware. Downside is cost of card £200 +++ for a good card.

You will need to use samba to share the files with other OS boxes. Strongly suggest you download latest version.

---

### Post by Rexhunt on 2010-01-03
Would a newer version run on the machine at a reasonable pace?
 
Also can I download samba and such from a windows machine and then copy it onto the server?

---

### Post by Rexhunt on 2010-01-03
It will have to be software raid due to cost restraints. Do you know any reading material suiable for free on the internet?

---

