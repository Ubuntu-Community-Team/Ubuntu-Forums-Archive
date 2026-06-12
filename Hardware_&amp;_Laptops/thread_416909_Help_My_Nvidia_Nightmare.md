---
title: "Help My Nvidia Nightmare"
date: 2007-04-21
forum: Hardware &amp; Laptops
---

### Post by adewale on 2007-04-21
hi someone gave me an nvidia geforce mx 400 ever since i've been battling to get 3d acceleration working i've tried envy and some other drivers from nvidia. They all freeze my pc, even without running any 3d application. My questions are
1) Is it possible to use this card with 3dsupport and if yes is there anyone who has been able to achieve this?
2)In the event of this card not working which card should i buy?
thanks in advance i use edgy

---

### Post by CheeseEatingBulldog on 2007-04-21
That card worked fine for me under edgy with the 8776 nvidia driver from their site. I had beryl/aiglx running fine...until feisty.

---

### Post by adewale on 2007-04-21
thats good to hear i tried the 8762 driver but says something was missing i'll try aagin. apart from that what would i have to download?

---

### Post by CheeseEatingBulldog on 2007-04-21
If you are running Edgy you also need to add "nv" to the /etc/modules file. I downloaded, beryl etc and it worked right for me with AIGLX. 

However since Feisty has come out, there has been a lot of mess with the Nvidia drivers (again), so I don't know what else they changed. (for instance in feisty one has to remove the 'nv' bit from the modules file.

Also it turns out that you must EITHER use the nvidia-glx / linux-restricted-modules-common method OR use the drivers from the nvidia site. I have to admit that I never noticed this, must have been lucky, but under feisty it does clash and won't work.

Just follow the Edgy howto and it should work.

---

### Post by adewale on 2007-04-21
i just installed the nvidia 8776 driver and i think it didn't edit my xorg.conf so i edited it and changed it from nv to nvidia and i got the nvidia logo so i tried glxgears and after sometime it frooze it up what can i do? is there another option apart from this nvidia driver cause they seem to never work for me. Thanks

---

### Post by adewale on 2007-05-20
my nightmare continues. i've tried downloaded everything envy etc disabled my pci share memory  disabled irq allocation to pci it still freezes my pc should i buy a new card or should i try fiesty does it come with nvidia driver pre installed?

---

