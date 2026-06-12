---
title: "RAM versus SWAP"
date: 2008-12-24
forum: Installation &amp; Upgrades
---

### Post by aobreyss on 2008-12-24
Bonjour,

I've been trying to find a definite answer to my question, how big should my swap partition be. I have 4GB of RAM on a very fast system. I never user hibernation. I've read about adjusting swapiness, SWAP should be RAM x 1.5 ou x 2 RAM ( which would seem to be overkill), no swap at all. I will mostly run Gnome on an Ubuntu 8.10 installation. Please advise and explain.

Regards, Joyeux Noël

---

### Post by mikewhatever on 2008-12-24
There is no definite answer, like it or not. I'd say you need no swap at all.

---

### Post by oilchangeguy on 2008-12-24
read this:
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

and +1 on your computer needing no swap.

---

### Post by Pumalite on 2008-12-24
Unless is a laptop and you want hibernation. In that case: /swap= 1.4 of your RAM

---

### Post by hyperdude111 on 2008-12-24
You will only NEED swap if you max out your ram. Because you have a large 4GB unless you run a huge number of power apps at once you onl need about 1GB of Ram (just as a precaution).

---

### Post by mikewhatever on 2008-12-24
> **hyperdude111 said:**
> You will only NEED swap if you max out your ram. Because you have a large 4GB unless you run a huge number of power apps at once you onl need about 1GB of Ram (just as a precaution).

Is there a list of power apps? If not, what are they?

---

### Post by Pumalite on 2008-12-24
I'd like to know too...

---

### Post by ibutho on 2008-12-24
Even with a lot of RAM, it wouldn't hurt to have a bit of swap space. You don't necessarily need to have 2x ram because it would be a waste of disk space. 1GB should be more than enough.

---

### Post by zephyrcat on 2008-12-24
I have a Dell XPS M1530 with 4GB of RAM. I just left whatever it came with, so I ended up with 3.4 GB of swap. System Monitor tells me none of that is being used right now, so I would say you are probably OK with none, but it would not hurt to put in a couple of GBs.

---

### Post by mikewhatever on 2008-12-24
Can you also check what amount of RAM is in use. I think the rule of Swap=1.5xRAM applied well in the days when RAM was pricey and most computers only had up to 512 MB.

---

### Post by hyperdude111 on 2008-12-24
Apps like songbird use 100mb+ ram, running ms office 2007 and itunes in wine also use large amounts. 

Virtualbox uses huge amounts as you have to set aside some ram from the host to give to the guest. If the guest is vista you end up losing 512mb of ram.

---

### Post by Pumalite on 2008-12-24
Laptops and hibernation are a different matter. Google it.
[http://www.google.com/search?hl=en&q=ubuntu+ram+and+hibernation+in+laptops&btnG=Google+Search&aq=f&oq=](http://www.google.com/search?hl=en&q=ubuntu+ram+and+hibernation+in+laptops&btnG=Google+Search&aq=f&oq=)

---

### Post by redsoxreed on 2008-12-24
I always make my swap double the size of my RAM if there is less than 2 gigs in the machine.

---

### Post by mikewhatever on 2008-12-24
> **redsoxreed said:**
> I always make my swap double the size of my RAM if there is less than 2 gigs in the machine.

So if there is 1.5 GB of RAM you'll have a 3 GB swap.How much of it do you think gets used?

---

### Post by SuperSonic4 on 2008-12-24
You *really* don't need it. Just make it 512mb to keep the installer happy if necessary. I've been using k3b, k9copy, firefox, kmess, amarok and dolphin at once and not used any swap

---

### Post by upchucky on 2008-12-24
i have 2 gig ram, 1 gig swap, according to my logs nothing has ever been swapped to the swap, however I may not be using any mem hungry apps.

you have 4 gig ram, "tons" unless you are a server. on a stand alone pc with 4 gig you only need 1 gig swap, and im willing to bet it will never get used.

---

### Post by Sef on 2008-12-25
> I think the rule of Swap=1.5xRAM applied well in the days when RAM was pricey and most computers only had up to 512 MB.

That is correct.   Unless you do some extremely graphicly intensive applications (movie ediing, gaming, etc.), 1 gb swap will be more than enough.   If they are extremely graphically intensive, then I would consider 2 gb swap.

---

