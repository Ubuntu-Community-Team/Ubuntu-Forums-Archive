---
title: "installing driver nvidia 8800 gts 512"
date: 2008-03-09
forum: Hardware &amp; Laptops
---

### Post by Tercesje on 2008-03-09
Hi,

i'm rather a noob concerning Ubuntu (but taking my first steps) and English is not my mothertongue so forgive me if I make some errors while writing :)

I recently bought another graphics card (8800 gts 512Mb), before that one I had an SLI-setup with 2 nvidia 6600gt-cards

after installing ubuntu (I have a dual-boot system with Win Xp) i encountered several problems wich i could resolve eventually but now with my new card i have another...

when i boot into ubuntu, first of all i get a messagebox : "running in low graphics mode etc"

when i try to reconfigure the display settings there, it solves nothing...
so i log in and i have a resultion of 800x600 (i have a widescreen monitor 22" :s )

i cannot seem to change teh resolution nor can i use "restricted drivers" , 
when i want to select restricted drivers i get a message that my system does not require the use of restricted drivers

So i downloaded the drivers for linux from nvidia but when i want to start the setup i get the message that i am running an X-server and i should first exit the x-server before i can continue...

can anybody help me with this one ?

---

### Post by Tercesje on 2008-03-09
i've been looking around in the threads and found some possibilities but for example 

when i put in

sudo nvidia-settings --config enable

i get 

You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.

---

### Post by uberlube on 2008-03-09
How did you install your graphics driver?

---

### Post by Tercesje on 2008-03-09
hmm i couldn't install the driver, i got an error 

" you are running an x-server, you should exit the server...."

i must say

i found someone mentionning "eny"

and envy solved the problem...

so this one is solved for me :)

thx anyway

---

### Post by uberlube on 2008-03-09
I was just about to suggest using envy. k well glad your up and running. :)

---

### Post by Tercesje on 2008-03-10
I did here that envy sometimes causes troubles ???

---

### Post by xjgnsdof on 2008-04-26
I had the same problem, but upgrading (or, in my case, freshly installing) Hardy did away with any need to install drivers or even run Envy.

---

### Post by Tercesje on 2008-04-27
This was parctically a new (fresh install) 

anyway, i did read here and there that it can cause troubles but in my case it solved my problem...

grtz

---

