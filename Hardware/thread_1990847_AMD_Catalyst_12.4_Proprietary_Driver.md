---
title: "AMD Catalyst 12.4 Proprietary Driver"
date: 2012-05-29
forum: Hardware
---

### Post by JoshStrobl on 2012-05-29
Hello everyone, I've been a Linux user since I first switched to Ubuntu on version 8.04 (been distrohopping since, *got comfortable with 12.04 I must say!*) and recently upgraded my laptop. My Toshiba Satellite L305-S5955 from years ago has always ran Ubuntu perfectly (except for a few issues with pulseaudio, but that is besides the point) and uses an integrated Intel graphics card.

I recently upgraded to an HP Pavilion dv6z Quad-Core Edition (my old laptop is at its end-of-life, processor has failed on me). I had it customized to utilized two graphic cards / processors, one that is integrated and one that is dedicated.

I understand there has been some success with Intel/AMD hybrids, however I haven't heard much about AMD/AMD hybrids.

AMD's catalyst 12.4 proprietary driver supposedly has support for hybrid cards, I was wondering if there was anyone with a similar HP model or experience with this sort of thing to let me know if installing Ubuntu at this point (currently running Windows :( ) along with the proprietary drivers (and removing the open source driver) would allow me to utilize both my graphic cards, or if I'd still need to disable one in the BIOS (I'm pretty sure X.Org defaults to the integrated).

1. Integrated - AMD Quad-Core A6-3420M (2.4GHz/1.5GHz)
2. Dedicated - 1GB AMD Radeon HD7690M GDDR5

Do note: I don't care if I need to use Terminal to switch between cards, I'm perfectly comfortable with that.

Thanks ahead of time guys and I apologize also if there are any forum posts buried away on Ubuntu Forums regarding this. Spent plenty of time researching, I assure you.

---

### Post by mastablasta on 2012-05-30
best would be to boot live (maybe with USB & persistance) and try it out yourself.

---

### Post by JoshStrobl on 2012-05-30
Ok, so is there anyone here with any actual help or information regarding using the proprietary drivers and hybrid graphics?

---

### Post by mastablasta on 2012-05-30
have a look here: [http://ubuntuforums.org/showthread.php?t=1942151](http://ubuntuforums.org/showthread.php?t=1942151)
and of course here: [http://ubuntuforums.org/showthread.php?t=1930450](http://ubuntuforums.org/showthread.php?t=1930450)
 
as i mentioned before, best to boot live OS and install the drivers and see if it works.

---

### Post by JoshStrobl on 2012-05-30
> **mastablasta said:**
> have a look here: [http://ubuntuforums.org/showthread.php?t=1942151](http://ubuntuforums.org/showthread.php?t=1942151)
and of course here: [http://ubuntuforums.org/showthread.php?t=1930450](http://ubuntuforums.org/showthread.php?t=1930450)
 
as i mentioned before, best to boot live OS and install the drivers and see if it works.

The first link states you'll need to disable one of the cards in the BIOS, not really what I was asking.

The second link goes to AMD/Intel mix. You read the actual topics right, instead of just doing a quick search?

I'll just go ask on the AMD forums, assuming they have one. Should be able to get a more straightforward answer than "use a LiveCD".

---

### Post by jjiggens on 2012-05-30
Trying the live cd and seeing if it works is actually a good suggestion, not sure why your disregarding that suggestion.  the live cd is always the best way to see if it supports your hardware with out installing. Also, AMD/AMD switching has been done. there are threads and links in this forum that already discuss this.

---

### Post by mastablasta on 2012-05-30
> **JoshStrobl said:**
> The first link states you'll need to disable one of the cards in the BIOS, not really what I was asking.

The second link goes to AMD/Intel mix. You read the actual topics right, instead of just doing a quick search?

I'll just go ask on the AMD forums, assuming they have one. Should be able to get a more straightforward answer than "use a LiveCD".

Using a live cd will also reveal if there is any other issues with dirvers not just AMD card. 

and as mentioend in second link you can have the same combinaiton of CPU and GPU on another laptop and it doesn't mean it will work. which is why you need to try it with live CD. unless someone else had exact same model, type, series whatever that could give you a straight answer you would not know. addiitoanlyl the advice in second link is good for AMD chip as well since it is mainly on how to install drivers directly from AMD.

Putting all that aside AMD drivers are made by AMD. why are you asuming that they would make a driver version for linux (ivnest into it) that works with their competition CPU (Intel) but not with their own CPU?

---

