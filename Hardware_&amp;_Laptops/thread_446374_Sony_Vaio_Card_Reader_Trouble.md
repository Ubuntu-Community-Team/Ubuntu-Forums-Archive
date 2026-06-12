---
title: "Sony Vaio Card Reader Trouble"
date: 2007-05-16
forum: Hardware &amp; Laptops
---

### Post by RelativelyQuantum on 2007-05-16
Hi all.

I run Feisty on a Sony Vaio VGN-TX750P. On the end facing me as I type is a built Memory Stick and SD card reader, respectively, neither of which I can get working. The light near the readers flashes when I insert a card, however, nothing appears on my desktop. If anyone can give me some advice I would greatly appreciate it.

---

### Post by omorphos on 2007-06-07
im having the same problem, if anyone knows how to fix it please let me know.  i assume i need to find a driver for it..?i have Vaio vgn-TX770P

---

### Post by heldmar on 2007-06-10
I have the same problem and reading many forums, it seems theres no answer to this problem yet, so we Vaio user will have to wait to use our Memory Stick drives with Ubuntu :(

---

### Post by robbster on 2007-06-11
Same problem here. I'd suggest, everyone of us will write an eMail to Sony and ask them to publish the specifications of the card readers. Maybe they will pay more attention to linux users so that somebody can program a driver for that hardware.

---

### Post by nithrandil on 2007-06-16
Vaio A130B, same issue.. please sony!!!:(

---

### Post by Depressed Man on 2007-06-16
I don't have the exact same problem, but I figure it may be worth noting and it may be helpful to someone (I'll go scrounge up my model name tomorrow). But my Sony VAIO card reader actually works (as far as I know). If I plug anything into it, Ubuntu detects it and pops it up. I can navigate the directories though I can't actually see any images (it's a 2 GB SD card that I take pictures on using a Canon A620). 

Just wondering, does everyone's card reader appear on the right side and did their laptops come with some device that goes into that card reader port to let them fit other types of cards in there?

---

### Post by IntuitiveNipple on 2007-06-18
If the built-in card-slot is connected to a Texas Instruments 5-in-1 Flash card chip-set the kernel modules to support MemoryStick or xD cards on the TI chip-set are [in the early stages](http://openfacts.berlios.de/index-en.phtml?title=TI_FlashMedia_xx12/xx21_driver) and not available unless you build them yourself.

---

### Post by Brian_X7 on 2007-06-21
I've gotten this to work on newer versions of the kernel (2.21rc5 and newer).  Google around, especially in the Gentoo forums on the tifm drivers.

---

### Post by Speedy Badger on 2007-06-23
In fact it's very easy to get the SD card working. You just have to add "tifm_sd" line to your /etc/modules file and reboot. SD cards will be recognized and mounted. (Thanks to Lauri Taimila website [http://www.taimila.com/vaio.php](http://www.taimila.com/vaio.php))
As for the Memory stick reader, it seems nothing can be done for the moment...

---

### Post by dseybert on 2007-09-08
> **Speedy Badger said:**
> As for the Memory stick reader, it seems nothing can be done for the moment...

Anyone find a fix for this yet?

---

### Post by Depressed Man on 2007-10-25
Dunno about memory sticks and SD cards..but for my VAIO FE series (texas instruments 5 in one card reader) both the memory sticks and SD card usually worked with Feisty (haven't tested in Gutsy) yet.

Well with my 2GB SD card it detects and says photos are on there, it just can't find them after I click the import button.

---

### Post by dgray_from_dc on 2008-02-25
Same problem here.  I've got an (older) PCG-R505JL with a memory stick slot that just blinks when media are inserted.  I don't think that Linux is even aware of the slot!

It wasn't until Gutsy that the Slim dock with the CD/DVD combo could be detected and I could even perform a full install.  After that, Gutsy has worked better then XP ever could (except talking to my PSP memory sticks).

---

