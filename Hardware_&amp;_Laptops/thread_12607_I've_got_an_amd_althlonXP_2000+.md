---
title: "I've got an amd althlonXP 2000+"
date: 2005-01-25
forum: Hardware &amp; Laptops
---

### Post by machiner on 2005-01-25
SHould I be running the 686 kernel or the K-7 one?

Right now I'm using the K-7...

---

### Post by Buffalo Soldier on 2005-01-25
k-7

---

### Post by machiner on 2005-01-25
Thanks -- just wanted a second opinion.

---

### Post by philip41 on 2005-01-26
I have an XP2600+, as far as i no i am just running the 386 Kernel, should i be running the K7 also.

If so, do i just run "sudo apt-install linux-k7"

thanks for your help.

---

### Post by rh6866 on 2005-01-26
[QUOTE=philip41]I have an XP2600+, as far as i no i am just running the 386 Kernel, should i be running the K7 also.

If so, do i just run "sudo apt-install linux-k7"

thanks for your help.[/QUOTE]


I suggest you do use the K7 kernel.  I've got an AthlonXP 2400+ and used synaptic  to get the latest kernel for it.  After rebooting and using it without issue for a few days I again used synaptic to remove the old 386 kernel. 

Rick

---

### Post by philip41 on 2005-01-26
[QUOTE=rh6866]I suggest you do use the K7 kernel.  I've got an AthlonXP 2400+ and used synaptic  to get the latest kernel for it.  After rebooting and using it without issue for a few days I again used synaptic to remove the old 386 kernel. 

Rick[/QUOTE]

Good suggestion, what advantages are there to using K7, what have you found.

---

### Post by martyr on 2005-01-26
The only difference is that the k7 kernel has been compiled with AMD K7 CPU optimisation whereas the i386 is a generic compile for the i386 base architecture.

---

### Post by philip41 on 2005-01-26
[QUOTE=martyr]The only difference is that the k7 kernel has been compiled with AMD K7 CPU optimisation whereas the i386 is a generic compile for the i386 base architecture.[/QUOTE]

Thanks guys for the advice.

---

### Post by ubuntu UsER on 2005-01-26
Here [http://www.ubuntuforums.org/showthread.php?t=3713](http://www.ubuntuforums.org/showthread.php?t=3713)
> 9. Installing a CPU specific kernel.
Quote:
1. sudo apt-get install **linux-686 for newer Intel/AthlonXP**
2. sudo apt-get install **linux-k7 for any AMD Processors**
3. sudo apt-get install linux-686-smp for Dual Intel Processors

So? Who has right? ;) I have got AthlonXP 2000+ too, so it is also interesting for me :)

---

### Post by philip41 on 2005-01-26
[QUOTE=ubuntu UsER]Here [http://www.ubuntuforums.org/showthread.php?t=3713](http://www.ubuntuforums.org/showthread.php?t=3713)


So? Who has right? ;) I have got AthlonXP 2000+ too, so it is also interesting for me :)[/QUOTE]

Not sure on that one my self, but i have just changed to the K7, and now Ubuntu Cannot start X.

Looks like i boobed again, says it failed to initialize the Nvidia Kernel Module.

---

### Post by ubuntu UsER on 2005-01-26
[QUOTE=philip41]Not sure on that one my self, but i have just changed to the K7, and now Ubuntu Cannot start X.

Looks like i boobed again, says it failed to initialize the Nvidia Kernel Module.[/QUOTE]

If you didn't delete old kernel, press "esc" during booting and choose your old kernel :)

---

### Post by philip41 on 2005-01-26
[QUOTE=ubuntu UsER]If you didn't delete old kernel, press "esc" during booting and choose your old kernel :)[/QUOTE]

Done that and for some reason it is doing it there aswell.
I have managed to get back into the system by editing "xorg.conf" changing Nvidia to Nv.
But am still at a loss as to what has gone wrong.

On boot up after it fails to start Xserver, i read the log.

Error 1) failed to load module GLcore ( module does not exist)
Error 2) failed to initialize the Nvidia Kernel Module.

Sorry to the first poster for hyjacking the thread.

---

### Post by rh6866 on 2005-01-26
[QUOTE=philip41]Good suggestion, what advantages are there to using K7, what have you found.[/QUOTE]

Haven't done any "real" testing to see what the advantages are.  But I can say that everything just seems...  I guess "snappier" would be the only word I can think of right now.  Apps open quicker, I don't get any lag on mouse movement or keyboard entries when typing a document or email like I was noticing when I first installed and was using the default 386 kernel.

---

### Post by philip41 on 2005-01-26
[QUOTE=rh6866]Haven't done any "real" testing to see what the advantages are.  But I can say that everything just seems...  I guess "snappier" would be the only word I can think of right now.  Apps open quicker, I don't get any lag on mouse movement or keyboard entries when typing a document or email like I was noticing when I first installed and was using the default 386 kernel.[/QUOTE]

Hopefully when i get the Nvidia problem sorted i will notice similar differences.

Thanks

---

### Post by philip41 on 2005-01-26
Guys just read another post about using the k7 kernel, i used Synaptic to upgrade, i chose "linux-Image-2.6.10-2-k7".
Should i have used "Linux-restricted-modules-2.6.10-2-k7" instead.

I am back to using 386 at the moment.

---

### Post by machiner on 2005-01-26
I've got the following linux kernel (schtuff) installed:

linux-headers-2.6.8.1-4 (16.10)
linux-headers-2.6.8.1-K7 (16.10)
linux-headers-2.6-K7 (2.6.8.1-14)
linux-image-2.6.8.1-4-K7 (16.10)
linux-image-2.6-K7 (2.6.8.1-14)
linux-image-K7 (2.6.8.1-14)
linux-K7 (2.6.8.1-14)
linux-kernel-headers 2.5.999-test7-bk-16
linux-restricted-modules-2.6.8.1-4-k7
linux-restricted-modules-2.6-k7
linux-restricted-modules-k7
linux-source-2.6.8.1 (16.10)

Seems like a lot doesn't it? I wonder if I can pull some of it out...?

I don't notice any real difference from the 686 kernel, though.

Where did linux-Image-2.6.10-2-k7 come from?

---

### Post by philip41 on 2005-01-26
[QUOTE=machiner]I've got the following linux kernel (schtuff) installed:

linux-headers-2.6.8.1-4 (16.10)
linux-headers-2.6.8.1-K7 (16.10)
linux-headers-2.6-K7 (2.6.8.1-14)
linux-image-2.6.8.1-4-K7 (16.10)
linux-image-2.6-K7 (2.6.8.1-14)
linux-image-K7 (2.6.8.1-14)
linux-K7 (2.6.8.1-14)
linux-kernel-headers 2.5.999-test7-bk-16
linux-restricted-modules-2.6.8.1-4-k7
linux-restricted-modules-2.6-k7
linux-restricted-modules-k7
linux-source-2.6.8.1 (16.10)

Seems like a lot doesn't it? I wonder if I can pull some of it out...?

I don't notice any real difference from the 686 kernel, though.[/quote]

It sure does seem a lot, did you choose to install that lot or did you choose 1 and the rest  get installed with it.

Sorry my Noobness
> 
Where did linux-Image-2.6.10-2-k7 come from?

It was listed in Synaptic. I am running Hoary by the way.

---

### Post by machiner on 2005-01-26
most of 'em were installed as deps.

I need a "real ubuntu guru" to tell me it's cool to remove...X...

I have a sneakin' suspicion that they're necessary though... but I could probably loose the headers.

---

### Post by martyr on 2005-01-26
philip41, simply install "linux-k7" and synaptic will take care of everything else (kernel image, modules etc.). This way, your nvidia module should work too.

---

### Post by philip41 on 2005-01-27
[QUOTE=martyr]philip41, simply install "linux-k7" and synaptic will take care of everything else (kernel image, modules etc.). This way, your nvidia module should work too.[/QUOTE]

Yes finally got to K7.

Thanks to all of you for your Assistance

---

### Post by djsroknrol on 2006-03-31
I've got to add in here that the right kernel jazzed up my 2400+ and it works alot better for me since I dropped the 386 in favor of the K7...

---

