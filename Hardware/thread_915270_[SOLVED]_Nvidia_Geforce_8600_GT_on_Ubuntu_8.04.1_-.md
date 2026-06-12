---
title: "[SOLVED] Nvidia Geforce 8600 GT on Ubuntu 8.04.1 - black screen on login"
date: 2008-09-09
forum: Hardware
---

### Post by andy80 on 2008-09-09
Hi all

I've installed Ubuntu 8.04.1 on a new PC (intel core 2 duo, 2 Gb ram ecc...) with Asus Nvidia Geforce 8600 GT Silent.

This is the card:

```
andy80@centurion:~$ lspci | grep 8600
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8600 GT (rev a1)
```

I've enabled Nvidia restricted driver and it has been installed. Every time I reboot my PC, instead of GDM login I get a black screen :(

After 4-5 minutes of doing... nothing, the GDM login appears! At this point I'm able to login and Nvidia driver work perfectly! 3D works too, because glxgears runs very very fast!

So... why do I get black screen at the beginning and I'm able to login only after 4-5 minutes? I get no errors in /var/log/Xorg.0.log so I cannot know what is causing this :(

In the attachment you can find my xorg.conf but I don't know if it will be usefull because it doesn't contains anything strange.

Another thing.... I've tried to enable ubuntu-proposed updates, to upgrade kernel and nvidia-glx-new packages, but it doesn't seem to help me anyway :(

How can I fix this problem? Is there anything else I can do to provide you more info to fix this?

Thanks!

---

### Post by in-dust-rial on 2008-09-09
hi,
maybe there are warnings in the xorg.log
?
try to 
```
$dmesg 
```
before while and after login screen, maybe you can see from it where the problem occurs

just guessing
good luck

---

### Post by andy80 on 2008-09-09
I get no errors in dmesg. This is what happens:

1) back screen
2) GDM plays Ubuntu sound (still black screen)
3) 3-4 minutes..... black screen....
4) TADAA! GDM login appears!

:(

I get a similar issue if I do (after I'm logged into Ubuntu and graphic card works): 

1) CTRL+ALT+F1
2) CTRL+ALT+F7.....still black screen!
3) 10-12 seconds......
4) display is ok again!

Any other idea?

p.s: I've tried nvidia beta driver too (177.....)

---

### Post by in-dust-rial on 2008-09-09
did you try this with different kernels?
(still warnings in xorg.log?)

---

### Post by in-dust-rial on 2008-09-09
[http://www.nvnews.net/vbulletin/showthread.php?t=73994]("http://www.nvnews.net/vbulletin/showthread.php?t=73994")

[http://ubuntuforums.org/archive/index.php/t-247653.html]("http://ubuntuforums.org/archive/index.php/t-247653.html"):guitar:

---

### Post by andy80 on 2008-09-10
It looks like I've fixed the problem!
I've added this line to my **xorg.conf**

```
Option "DPMS" "true"
```

into the **Monitor** section.

I've tested it only with 2 or 3 reboot and I've not the problem anymore. I also tried to switch to text console (CTRL+ALT+F1) and switch back to graphic mode and it works without any problem!

I hope to have fixed it!

Thanks to all :)

---

### Post by andy80 on 2008-09-11
It's not fixed at all :(
Still that problem and it doesn't happen always!!! Damn it!

I've tried to use another Asus Geforce 8600, nothing to do... still the same problem. I'm currently using an Asus Geforce 8800 GS, and I still have the same problem :(

Any idea?

---

### Post by Casper Hansen on 2008-09-11
Sounds odd. Have the exact same graphics card. I used EnvyNG to install the nVidia driver. Maybe that would help? What kernel are you using?

---

### Post by Bright010957 on 2008-09-11
Was it a new installation of your Ubuntu 8.04 version?
I have a Asus 8600 GT Silent too and I upgraded from 7.10 to 8.04 and I had so serieus problems with my grafics. But after a fresh installation of Ubuntu 8.04 is was alright.

---

### Post by andy80 on 2008-09-11
> **Casper Hansen said:**
> Sounds odd. Have the exact same graphics card. I used EnvyNG to install the nVidia driver. Maybe that would help? What kernel are you using?

Now I've tried to upgrade to Intrepid Ibex 8.10, but still no success :(
I was using 2.6.24 I think.. latest available with 8.04 Ubuntu.

And I've tried all kind of drivers... both from nvidia-glx-new and Nvidia.com website (173... and 177...).

I'll try to do a fresh install of 8.10, then I'll try again 8.04 if no success.

p.s: the card has only a DVI out, and I'm using the adapter shipped with the card, with a Samsung Syncmaster 710v. Could this be a problem?

---

### Post by andy80 on 2008-09-11
> **Bright010957 said:**
> Was it a new installation of your Ubuntu 8.04 version?
I have a Asus 8600 GT Silent too and I upgraded from 7.10 to 8.04 and I had so serieus problems with my grafics. But after a fresh installation of Ubuntu 8.04 is was alright.

Yes, it was a fresh installation.

---

### Post by andy80 on 2008-09-11
Another note: I can reproduce this problem everytime! I just need to do this (for example):

- CTRL + ALT + F1, so a switch to a text console
- CTRL + ALT + F7, so I come back to graphic mode and....... et voila'!

at this point (when the resolution should come back to 1280x1024), I get the black screen :(

Then I wait 3-4 minutes and the screen is no more black.

How can I investigate better this problem? I can send you all the logs you want.. just ask :)

---

### Post by andy80 on 2008-09-13
It was a problem (a strange one!) of my LCD monitor! I'm now using another LCD monitor from a friend of mine and it works perfectly! I've never had that problem anymore since I'm using this one.

---

### Post by vishal_karira on 2008-09-13
> **andy80 said:**
> Hi all

I've installed Ubuntu 8.04.1 on a new PC (intel core 2 duo, 2 Gb ram ecc...) with Asus Nvidia Geforce 8600 GT Silent.

This is the card:

```
andy80@centurion:~$ lspci | grep 8600
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8600 GT (rev a1)
```

I've enabled Nvidia restricted driver and it has been installed. Every time I reboot my PC, instead of GDM login I get a black screen :(

After 4-5 minutes of doing... nothing, the GDM login appears! At this point I'm able to login and Nvidia driver work perfectly! 3D works too, because glxgears runs very very fast!

So... why do I get black screen at the beginning and I'm able to login only after 4-5 minutes? I get no errors in /var/log/Xorg.0.log so I cannot know what is causing this :(

In the attachment you can find my xorg.conf but I don't know if it will be usefull because it doesn't contains anything strange.

Another thing.... I've tried to enable ubuntu-proposed updates, to upgrade kernel and nvidia-glx-new packages, but it doesn't seem to help me anyway :(

How can I fix this problem? Is there anything else I can do to provide you more info to fix this?

Thanks!

i have also got the same problem but my log in screen is not coming even after ten minutes
i havealso tried to install nvidia graphics driver in my compaq cq50-106au
the screen comes to a hault after going two to three grey level colour changes 
and at last haults at a screen with strips of various colours
how could i recover from this problem
or how could i get back to the originala system
or how could i repair it back ot normal

---

### Post by in-dust-rial on 2008-09-13
you still may search for xorg.conf monitor settings on the web for your production line.

and still i am missing this two times requested xorg logs WARNINGS
and i am sure, that the warings will be like, cant apply modes, tryin back to whatever ...

still good luck
(if its truly the monitor, give it back if you can =)

&hf

---

### Post by andy80 on 2008-09-13
> **in-dust-rial said:**
> you still may search for xorg.conf monitor settings on the web for your production line.

and still i am missing this two times requested xorg logs WARNINGS
and i am sure, that the warings will be like, cant apply modes, tryin back to whatever ...

still good luck
(if its truly the monitor, give it back if you can =)

&hf

the monitor is not new :(
I bought it 2-3 years ago I think.... I'll buy a new Asus LCD 22'', 16:9 :)

---

