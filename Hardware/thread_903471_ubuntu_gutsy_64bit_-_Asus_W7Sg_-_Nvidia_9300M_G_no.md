---
title: "ubuntu gutsy 64bit - Asus W7Sg - Nvidia 9300M G not working"
date: 2008-08-28
forum: Hardware
---

### Post by ebola15 on 2008-08-28
Hi,

I have a new Asus W7SG.

I installed XP and ubuntu gutsy in dual boot.
Ubuntu Gutsy 64 bit works fine but the video card(Nvidia 9300M G).
I try to install the drivers that ubuntu suggest me (restricted dirver) but they dont work (X crash at boot and i find myself in low graphics mode).
I tryed ot install the drivers from nvidia.com 177.67 (64 bit of course).
I followed various guides found online but still no success(X crash at boot and i find myself in low graphics mode).
I tryed to have Xorg.conf modified by nvidia installer but no success
I tryed to modify it myself but nothingagain.
I tryed envy. Nothing again.
Any idea?
In XP to have the video card working one of the Express Root ports must be disabled to resolve an hardware conflict.
In particolar it is PCI bus 0, device 28, function 1 (Intel(R) ICH8 Family PCI Express Root Port 2 - 2841) (here the XP guide [http://forum.notebookreview.com/showthread.php?t=260996](http://forum.notebookreview.com/showthread.php?t=260996)).
Do I have to do something similar in ubuntu too?
Ideas?
](*,)](*,)](*,)](*,)
Thanks

---

### Post by tuxxy on 2008-08-28
Did you try envyng to install them? you may need to downlaod it first from the repos.

---

### Post by mikewhatever on 2008-08-28
It looks like the latest driver available is 173.14.12, but no support for 9xxx series is mentioned. Where did you get 177.67 from?
[http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)

---

### Post by ebola15 on 2008-08-28
Yes i tryed to download the driver manually and then use envy but doesn't work. I downloaded the drivers from here
[http://www.nvidia.it/object/linux_amd64_display_archive_it.html](http://www.nvidia.it/object/linux_amd64_display_archive_it.html)
(italian nvidia website)

---

### Post by mikewhatever on 2008-08-28
I think your card is simply too new for Linux. At least none of the drivers state the support for it.

---

### Post by Onyxblack on 2008-08-28
I had the same problem with my 9800GTX cards yesterday. 

I did figure out how to fix it

this thread should help you - [http://ubuntuforums.org/showthread.php?t=902088](http://ubuntuforums.org/showthread.php?t=902088) 

specifically what i posted last. 

> Ok it seems that my comp doesn't start with the nvidia driver enabled? so far every time ive restarted ive had to run 'sudo nvidia-xconfig' and even then I cant seem to get my resolution 3840x1024... (option isn't avaliable) and cant seem to edit the xorg.config with out having the nvidia driver stoping and me being left having to start all over again...

EDIT: HAH! just got it - but now im afraid to restart... lol

- screen shot for proof!

[http://titansites.com/Screenshot-1.png](http://titansites.com/Screenshot-1.png)

Edit again -

Ok seems i got it starting with the nvidia driver now - needed to

Quote:
sudo nano /etc/default/linux-restricted-modules-common

Edit the DISABLED_MODULES line to make it look like this:-
Code:

DISABLED_MODULES="nv nvidia_new"


only 1 problem left with the display (login screen isn't showing the box's/ - resolution for login screen is only 1 moniter and the username/pass box's are off the screen/ i login blind! lol)- everything else is working like a charm.

---

### Post by ebola15 on 2008-08-28
Thanks Onyxblack I tryed all that already but no solution. When i Startup it says that there was a problem and then it ask me if i want ot start in low graphics mod or chose another driver (vesa).
By the driver supports my card as it says in the  readme.txt of the driver

---

### Post by Onyxblack on 2008-08-28
after installing the nvidia drivers? and starting the x server - does it work?

Try -

(go to comand prompt) 
```
ctrl+alt + f3
```
(stop x server)
```
sudo /etc/init.d/gdm stop
```
(go to driver location)
```
cd <path to driver>
```
(install driver)
```
sudo sh NVIDIA-Linux<whatever>.run
```
(after installing the driver it should bring you back to the comand promp) 
```
sudo /etc/init.d/gdm start
```
(this should bring you back to a WORKING desktop with drivers working, once there do)
```
sudo nano /etc/default/linux-restricted-modules-common
```
(edit the line to make it look like)
```
DISABLED_MODULES="nv nvidia_new" 
```

Restart your comp - should all work after that

---

### Post by Crafty Kisses on 2008-08-28
Post the results of > glxinfo

---

### Post by ebola15 on 2008-08-29
Onyxblack. I did what u suggested (thanks anyway) but no luck alway the same result...low graphic mode.
I also followed everything written on the nvidia website.

the output of glxinfo is

name of display: :0.0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x21 16 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x3a 32 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None

](*,)](*,)

---

### Post by skreo56 on 2008-10-01
Hi ebola15,

I don't know if you finaly sorted out your troubles with the 9300M G, but I'm getting into the same mess with the same computer: an Asus W7Sg.

If you got the solution, please, I'd be glad indeed to hear about it

envyng was pretty useless, and all the drivers I tried on my own just sent me back to the same unsuccessfull result...

Very frustrating...:cry:

---

### Post by ebola15 on 2008-10-02
no no solution. I can tell you that if you install suse at least you can get the resolution up to 1280*768

---

### Post by skreo56 on 2008-10-02
When I upgrated Hardy to Intrepid, I've been able to get the bloody 1280x800, but desperately, I've been thick enough not to save the f... something.so and the xorg.conf both matching!!!

The point is, I tried several things very quickly and when I got the 1280x800, I had no graphical acceleration at all, so I tried some other things, thus overwriting the working xorg.conf a few more times...

That happened last monday and since that time I've just kept trying to remember I way I actually managed to get THE resolution. ( I swear I would not matter today of accelerating anything if only I could step back to 1280x800 :|)

Did you actually hear about people having success under Linux with the 9300M G on an other computers?
That well could be interesting 'cause the computer and the rest of its architecture could eventually be the real matter.

Sincereky I would prefer not! 'ause it would mean a kind of "no way to get the W7SG working properly under Linux"

I still hope that it is only a problem of driver missing at the moment. This would only mean we have to wait 'till we can get it!

But anyway I am gonna try to make the best of it to solve the problem and then, go through further investigations.
I 'll let you know if I ever have something interesting ;)

---

### Post by ebola15 on 2008-10-03
The only thing I know (I have done it) is that under opensuse you get the bloody 1280x800 as soon as you finish the instalation but of course no acceleration. Red Hat gives only command line mode :(

I think I know where the trouble is:

this laptop has been made for Vista.
I have XP on it but to install it you need a trick.
In fact if you try to install the video driver it always says "no graphic card detected for these drivers" to have it working you need to disable a pci port under device manager and thn everythin magically works perfect.
I think in linux is the same way. I opened a thread asking for information on how to diable this f****g PCI port but still no answear
have a look
[http://ubuntuforums.org/showthread.php?t=930859](http://ubuntuforums.org/showthread.php?t=930859)

It will work, there must be a way, there is 1280x800 under suse and it works on XP. Is not driver is the PCI...

Let's go on we will have it working

---

### Post by Jfreu on 2008-10-03
Hi there,
I have exactly the same problem w7sg motherboard with its 9300M G not working
and i have found this : **[http://system76.com/product_info.php?cPath=28&products_id=86](http://system76.com/product_info.php?cPath=28&products_id=86)**

I guess the drivers for the 9300M G and 9300M GS are the same.
So there must be a way to get it working... i'm still looking for a solution.

---

### Post by ebola15 on 2008-10-03
I think that more of driver as i said before is a conflict like the one in XP. at least is the only thing i didn't try since i don't know how to disable that port in ubuntu. I am waiting to see the new ubuntu release with my finger crossed...

---

### Post by skreo56 on 2008-10-21
Sorry Ebola15, I've been off for a few days.

I read the first message you wrote in this topic and I 100% agree with you, as I "dualbooted" the same machine too with XP, and I also experienced the need to disable that blooby PCI ICH8 port to get the VGA card and the webcam be able to work.
Here is a lovely conversation that I had with E.C.E. about all this at it end of August:
[http://forum.notebookreview.com/showthread.php?t=260996](http://forum.notebookreview.com/showthread.php?t=260996)

So I've been thinking the same way and trying to figure out if it was eventualy necessary to disable some pci ports... I didn't explore this way already.

At the moment I'm replacing ubuntu with Mandriva 2008 and adding the nvidia drivers by hand. Tomorrow I'll try Mandriva 2009 (I'm downloading it now...)

As a report of what I did under Ubuntu during the ast two weeks :

1 - "lspci|grep VGA" returns a perfect définition of the card. so it is recognized by the system.

$ lspci|grep VGA
01:00.0 VGA compatible controller: nVidia Corporation 9300M G 042e (rev a1)

2 - compiling the last NVIDIA 177-80 was OK (as with  177-76...) but installing the nvidia.ko felt as usual...
But anyway, with the good kernel-headers, it does compile and let you a /root/NVIDIA-177-80/usr/src/nv/nvidia.ko
I also (desperatly?) tried a manual insmod without anymore luck.

3 - any attempt in loading the nvidia kernel objet (nvidia.ko) either using modproge or insmod, finaly ends in these lines added /var/log/dmesg when you type the command "dmesg|grep NVRM"

Here is what the latter command shows:

NVRM: This PCI I/O region assigned to your NVIDIA device is invalid:
NVRM: BAR1 is 0M @ 0x00000000 (PCI:0001:00.0)
NVRM: The system BIOS may have misconfigured your graphics card.
NVRM: The NVIDIA probe routine failed for 1 device(s)
NVRM: None of the NVIDIA graphics adapters were initialized!


The problem that if really the Bios is the matter then there is not much we can do about it because you probably noticed our Bios is really poor in options.
at least we can update it from 304, 305, 306, 307 when you go to

[http://support.asus.com/download/download.aspx?SLanguage=en-us](http://support.asus.com/download/download.aspx?SLanguage=en-us)


Here I am...

Mandriva 2008 just finished installing. Obiously the 9300M G isn't recognized. As the distribution is older, it is even worth: :)

$ lspci|grep VGA
01:00.0 VGA compatible controller: nVidia Corporation Unknown device 042e (rev a1)

I'll try the script tomorrow and I'll tell you.

then I'll try Mandriva 2009

If it works, there's absolutely no reason indeed that it doesn't work with Ubuntu.

---

### Post by skreo56 on 2008-10-22
Something else that makes me think about Bios and motherboard troubles : 

[http://ubuntuforums.org/showthread.php?t=675203](http://ubuntuforums.org/showthread.php?t=675203)

Milia reports the same problem and the same kernel messages with an other configuration (GeForce 8400M G on an Asus A8sc). Despite his machine is different than ours, finaly, a simple bios update solved everything...

I really have to give a thought to it... all the more considering that two of the bios updates presented in my last post (306 and 307 I guess) have been performed for nvidia matters

Anyway, this morning, I try the nvidia 177-80 on Mandriva 2008.
See you later for comments.

---

### Post by ebola15 on 2008-10-22
Thanks for all this informations.
The only thing I tried is to install the beta of intrepid and both kubuntu and ubuntu get to 1280x800. I am waiting for the final release (only 10 days...) to se if it works. If not I will try the bios update but I am quite worryed about it and i dont want to completely **** my laptop (too much work in it...)

Thanks

---

### Post by skreo56 on 2008-10-22
So do I !!! (and that's probably why I only give a thought to it :mrgreen: :mrgreen: :mrgreen:, at the moment at least, I shall eventualy do that but only as a last resort and if it is prooved indeed that it's THE solution to all our problems)

---

### Post by ebola15 on 2008-10-22
I had a look online and if you use the winflash asus utility it seems a smooth and easy process. I will try end of november after finishing my phd

---

### Post by skreo56 on 2008-10-23
Stop everything ebola15!

I 've got it.

Well, at least I know where is the problem.
If you use more than 2MB of RAM, nvidia driver doesn't load
If it's less or equal 2MB, it works! (I tried it removing my 2MB extension BAR and leaving only 1MB onboard, it worked)

It seems we have 2 solutions : 

BIOS update (if available for the concerned laptop).
Recompiling the kernel after patching it.

A third one well could be praying and expecting debian Leny, ubuntu Intrepid will incorporate these kernel modifications and the very next futur.

I do have to thank Mandriva 2008 for bring me "human readable" NVRM kernel messages that really played the part of clues and hints.


Read all this very carefully and you'll be given all sorts of informations about what you precisely have to do now:

[http://www.nvnews.net/vbulletin/showthread.php?p=1818515#post1818515](http://www.nvnews.net/vbulletin/showthread.php?p=1818515#post1818515)

And also this (even if it's a bit older)

[http://www.nvnews.net/vbulletin/showthread.php?t=96613&page=1](http://www.nvnews.net/vbulletin/showthread.php?t=96613&page=1)

as far as I'm concerned, I'm not gonna wait anymore  and I'll go for it!

will let you know...):P

---

### Post by ebola15 on 2008-10-23
....recompiling the kernel is not really something i am able to do...

assume that i update the bios from XP then I format all my laptop (as i was already planning) removing both win an ubuntu. Then when I reinstall ubuntu is it going to see the card?

There is patch for the bios explicitly for resolving teh fact that XP cannot see the video card....

---

### Post by skreo56 on 2008-10-23
Well concerning the Bios update, even if the update isn't directly concerning Linux, it may have some effects (better than nothing anyway, even if it's at our own risk :mrgreen:).

The thing I'm wondering about is: Are the modifications in 305 and 306 included in 307, or do we have to execute them all, one after the other? (Sort of questions that shows I've never ever done it before...:))

For the kernel, I can afford that and if it shows some good results I can even tell you how to proceed. It's more easy than anyone could think of: nobody ever asked you to be super C coder. You just have to follow a very precise set of ordered actions that well could be refered to as a protocol in fact. The only thing is getting the good kernel source and tools. All the rest is following step after step instructions.

But let's see that latter: I first want to experience the magic side of the bios update.

I'll poste this week-end (saturday or sunday) cause I'll be off tomorrow

---

### Post by skreo56 on 2008-10-24
Little message concerning your post at the top this page.
If you ever try bios update mind winflash and prefere a dos bootable cdrom with aflash. It seems some guys are reporting very bad results using winflash.

---

### Post by skreo56 on 2008-11-01
OK! I have total acceleration now since I recompiled the kernel after changing i386.c file and the nvidia.ko loads perfectly well.

As far as I can see updating the bios wasn't necessary at all

I did it on Fedora 9 x86_64 distrib

The only thing left to solve, is the wifi interface that still doesn't work at the moment.

you can either try to get success using the brand new Intrepid Ibex version online since 3 days or ask me how to proceed. I'm not very familiar with Ubuntu distrib and, thus, I find it easier to proceed with a Fedora or a Mandriva one. Nevertheless If you really want to make it work with Ubuntu, I'll triple boot (just for fun) to show you how to proceed.

---

