---
title: "BENQ S52 work in breezy need help for sound card"
date: 2005-12-05
forum: Hardware &amp; Laptops
---

### Post by derekyang on 2005-12-05
anybody has the some problem with the sound card in benq S52 ?
i have tried several version of the linux but still can't work.
if any guys is interested in it  , i will show the inf. what you want.
please help. thanks.

---

### Post by invisage01 on 2005-12-21
i just got an S53 V08.. im going to install ubuntu on the weekend when i get some time .. i'll let you know how i go!! :P

---

### Post by JProgrammer on 2006-02-21
I also have a s52 and have had nothing but trouble with it I installed flight 4 yesterday and now have acpi working with a custom dsdt that I debugged as for the audio I still don't have a solution

---

### Post by derekyang on 2006-03-25
Hi , do you have any solution of the sound card now???

---

### Post by JProgrammer on 2006-03-25
Unfortunately I am no closer to a solution to this problem than before it can be tracked in the ALSA [bug report]("https://bugtrack.alsa-project.org/alsa-bug/view.php?id=1134"). I have written a little about it in my [blog]("http://jprogrammer.profusehost.net/2006/03/23/laptop-support-from-where/"). Basically we know it is a CX20551 from Conexant but there is no documentation on this chipset so the that is really what is needed to get it working. So if you are in the US or Canada you could phone them on the contact number but other than that the options are running short.

---

### Post by mips on 2006-03-25
[http://www.linux-quebec.org/wiki/AtelierDuLibre/20060318](http://www.linux-quebec.org/wiki/AtelierDuLibre/20060318)

Try contacting the author of the above page as it 'looks' like he got it working on his Toshiba.

It's in french so you might want to use [http://www.worldlingo.com/en/products_services/worldlingo_translator.html](http://www.worldlingo.com/en/products_services/worldlingo_translator.html)

---

### Post by JProgrammer on 2006-03-26
Not really looking at the trasnlation
>  To try to make function the system its weird "Conexant CX20551-22 stereo Sound Software 16 bits" Looks like no luck there

---

### Post by kesiev on 2006-04-13
Hi guys! I'm trying to get out from this silent laptop... I've tried a bit with different "pci" parameters appended to the kernel (pci=noacpi and pci=routeirq) but with no luck.
Have a look to the referred alsa bugtrack page:

[https://bugtrack.alsa-project.org/alsa-bug/view.php?id=1134](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=1134)

Since some sound is listenable from speakers (a *pop* when changing volume and some 'seaside noise'), should be just a pointing error to the related port/irq?
There is something I can try?

---

### Post by kesiev on 2006-04-15
At the alsa's bugtrack i've posted an alsactl configuration file called "alsasound.conf" that makes some noise from speakers  if loaded. I can helps?

---

### Post by invisage01 on 2006-04-18
I get the same pops and all that.. just can't get any sound! .. im updating to dapper tonight to see how i go with it all.. 

lets hope for the best!

i.

---

### Post by kesiev on 2006-04-19
No luck with dapper... ;)
We are still waiting ALSA support on the bugtrack page...

---

### Post by hyby on 2006-10-29
*BUMP*

I was wondering has anyone got their laptop to work with sound yet? I have a benq s53w-t01 with the same specs as s52. I have tried edgy but i still dont have sound

---

### Post by JProgrammer on 2006-10-29
Have a read of the bug tracking page on alsa. It's still going and going we look like possibly getting a datasheet from a contact within Conexant but we can only hope.

Until then if you really want to use Linux you might consider getting a usb audio device or like me be resigned to the fact you have to use that propitiatory operating system, to get audio.

---

### Post by hyby on 2006-10-30
thanks mate, 

i had a good read of it. It looks as if progress has halted. 
I might consider assisting now since i have handed in my thesis!

---

### Post by hyby on 2006-11-02
i was searching through the fourms and found that this individual had sound on their benq s53w soundcard. the s 53 and s52 series are identicle, other than case colour and cpu and ram speed. Maybe we should chase up or reverse engineer this release. 


[http://www.ubuntuforums.org/showthread.php?t=197508&highlight=benq](http://www.ubuntuforums.org/showthread.php?t=197508&highlight=benq)

---

### Post by rlozano on 2006-11-11
so will this mean that the users of intel8x0 will be mute forever?

---

### Post by hyby on 2007-01-01
Happy New Year....Happy you guys will be. 

Apparently there have been successes in getting sound to function with Benq S52 and S53W in the ALSA bugtrack problem solving arena 
[https://bugtrack.alsa-project.org/alsa-bug/view.php?id=1134#bugnotes](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=1134#bugnotes) 

However,  since i still lack the intelligence of a monkey in linux. I can not get it to work as i do not understand what is happening.

---

