---
title: "Feisty (7.04) Upgrade nvidia Sound Problem (snd-hda-intel) ASUS A8M Laptop"
date: 2007-04-20
forum: Hardware &amp; Laptops
---

### Post by Slade Winstone on 2007-04-20
Hi,

Upgraded my ASUS A8M Laptop to Feisty (7.04) and my sound stopped working.  ](*,)

nForce Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2) = snd-hda-intel.

The following fixes the sound problem:

I added the following to the end of '/etc/modprobe.d/alsa-base' and restarted my computer:

Code:

# Added according to tips from launchpad.net.
options snd-hda-intel model=3stack

Thanks to the posts in the Feisty development threads.  ):P 

Slade.

---

### Post by shironeko on 2007-04-22
Does this work for every other sound card?

---

### Post by Slade Winstone on 2007-04-22
From the posts it seemed to be working for snd-hda-intel, but can only vouch for mine :)

Good-luck.

---

### Post by shironeko on 2007-04-22
could you please tell where you did get this from?
Maybe I can find a solution for my soundcard too.

---

### Post by the lush on 2007-04-24
This sounds like it may fix my problem, just one question, how do I add that line to the file?

---

### Post by arrizaba on 2007-04-24
> **the lush said:**
> This sounds like it may fix my problem, just one question, how do I add that line to the file?

Try any editor, for instance:

sudo nano /etc/modprobe.d/alsa-base
sudo gedit /etc/modprobe.d/alsa-base

or, my favorite ;),

sudo vim /etc/modprobe.d/alsa-base

---

### Post by swayze on 2007-04-24
wow. thank you dude! 

I have an asus a8m as well, just by chance came upon your solution, youre a life saver.

---

### Post by the lush on 2007-04-25
OK, I tried this last night on an Asus A8JS and it worked perfectly. Thanks so much.

I now only need to sort out my screen resolution so that it is correct when the system boots and I will have a perfect system. Oh, and need to figure out Bluetooth, but that is a very minor concern. I even have Word and Excel running perfectly in Crossover Office!

---

### Post by Slade Winstone on 2007-04-29
To those having problems with Asus A8 model laptops, I have collected a number of fixes for my Asus A8M laptop on the A8M wiki page.  I currently have everything working on my A8M for Edgy and Feisty

[https://wiki.ubuntu.com/LaptopTestingTeam/AsusA8M](https://wiki.ubuntu.com/LaptopTestingTeam/AsusA8M)

Check it out and feel free to ask questions.

:popcorn: 

Slade.

---

### Post by sickrandir on 2007-05-04
I have an asus a8jc and it has almost the same hardware. Unfortunately this fix does not seem to work for me. I have a clean installation of feisty. If I boot with the live cd of dapper or edgy the audio just works! Help me please or I will have to downgrade to edgy...

---

### Post by chewjoel on 2007-05-17
It doesn't work on my Asus M2400N.
Please somebody have any solution for my soundcard problem with Feisty?

---

### Post by hmjgriffon on 2007-05-22
> **Slade Winstone said:**
> Hi,

Upgraded my ASUS A8M Laptop to Feisty (7.04) and my sound stopped working.  ](*,)

nForce Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2) = snd-hda-intel.

The following fixes the sound problem:

I added the following to the end of '/etc/modprobe.d/alsa-base' and restarted my computer:

Code:

# Added according to tips from launchpad.net.
options snd-hda-intel model=3stack

Thanks to the posts in the Feisty development threads.  ):P 

Slade.

sure that gives you sound but if you actually turn it up, it sounds like crap, not worth it. Also when you plug in the headphones the speakers keep playing, worthless. I hope ALSA or whoever fixes this soon because it looks like about a bazillion people are having the same problems. I understand its all free and you can't really complain, but it still sucks.

---

### Post by wireless on 2007-05-23
Hey all
Im not sure about other laptops but under thinkpad x60 switching the modem on under bios fixed the sound issue.
take a look :
> [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/109428](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/109428)
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/109428/comments/14](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/109428/comments/14)

---

### Post by afilonov on 2007-05-25
This link helped me with System76 (which is Asus...)
[https://bugs.launchpad.net/ubuntu/+bug/105582](https://bugs.launchpad.net/ubuntu/+bug/105582)

---

