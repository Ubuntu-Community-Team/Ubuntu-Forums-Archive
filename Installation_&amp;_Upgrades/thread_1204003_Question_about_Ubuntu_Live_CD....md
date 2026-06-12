---
title: "Question about Ubuntu Live CD..."
date: 2009-07-04
forum: Installation &amp; Upgrades
---

### Post by Aidenstar on 2009-07-04
Is how the Ubunto Live CD runs, any Indication of how Ubunto will run when fully installed?

I'm only asking because I question my computers resources to run ubunto, and the Live CD is kind of running slowly.

Please answer if you have any experience with this...I would greatly appreciate it.

---

### Post by darolu on 2009-07-04
Hey, Ubuntu Live CD (not ubuntO! =p) runs considerably slower than the "real" thing; once Ubuntu is installed it will have all your RAM at its disposal; with the Live CD you are using a good part of it as it actually runs on your RAM (and some temporally space on your HD I believe).

It is normal that your Live CD runs slowly, specially when you run apps for the first time as it has to virtua-install them; if your computer is less than 4 years old the installed version should run nice and smooth; can you tell us your system specs so we can give you a more accurate prediction?

I have a fairly old computer running Ubuntu 9.04, it is a Pentium III @ 650Mhz with 384MB of RAM and a 128 Nvidia video card (FX-5200); and it runs fine, not fast but fine, it is not terribly slow, I can do a lot of stuff with it, including some graphic edition with GIMP, and all "regular" tasks as e-mail, internet, openoffice, etc... but not all of them at the same time of course. If your computer is similar to this one or older, you may want to use Xubuntu instead.

---

### Post by apparle on 2009-07-04
The live CD runs off the RAM i.e. it treats the RAM as local drive.
So the live CD is very slow even on some good computers.
Use the live CD to check if the sound, networks, graphics are working fine.
If you are currently using windows then just try inside windows (WUBI) installation. It doesn't require HDD repartitioning and very easy to remove if you want to. Just start the ubuntu live CD in windows

Or else post your PC configuration and other people guide you

---

### Post by Aidenstar on 2009-07-04
Compaq Presario 5002US 
800 MHz AMD ® Duron &#8482; Processor
200 MHz system bus
40.0 GB 2 UltraDMA Hard Drive
256.0MB Ram
nVIDIA &#8482; TNT2 &#8482; Vanta LT Graphics Card with 8 MB video memory

My computer is also pretty old I think I bought it about 8 years ago. How do you think ubunto would run based on the info I provided you. Thanks for the clarification about the Live CD. How much of an improvement speed wise would I expect with a full installation? Also, wubi is not an option, seeing as though I am still running WinMe. Believe me I would use wubi if I could. Thanks for any help you can give me...

---

### Post by ibutho on 2009-07-04
If Ubuntu is a bit slow on your system, you could try alternatives like Xubuntu which are a bit lighter in terms of resource usage.

---

### Post by Aidenstar on 2009-07-04
Thanks but I don't know exactly how quickly it runs on my system, I haven't yet installed it. I was hoping that someone would be able to tell me whether my system specs were adequate to run ubunto, before installing it. I would prefer to run ubunto rather than xubunto, unless I absolutely have to.

---

### Post by earthpigg on 2009-07-04
the minimum requirement for ubuntu is 256 megs of ram.

the minimum requirement for a *_graphical_* install is 500 megs of ram.

since you have 256 megs, you will probably have to use the alternate install cd:

[http://www.ubuntu.com/getubuntu/downloadmirrors#alternate](http://www.ubuntu.com/getubuntu/downloadmirrors#alternate)

(only the alternate install is text-based, once you install you will have a graphical user interface)

if you find ubuntu with the gnome desktop (default) to slow, you can try installing xubuntu-desktop - not quite as intuitive to use, but snappier.

---

### Post by Aidenstar on 2009-07-04
Thanks but I tried running the graphic install from the Live CD, and everything seemed to work alright, although very slowly. I think I should be able to install that way.

---

### Post by darolu on 2009-07-04
> **Aidenstar said:**
> Compaq Presario 5002US 
800 MHz AMD ® Duron ™ Processor
200 MHz system bus
40.0 GB 2 UltraDMA Hard Drive
256.0MB Ram
nVIDIA ™ TNT2 ™ Vanta LT Graphics Card with 8 MB video memory

My computer is also pretty old I think I bought it about 8 years ago. How do you think ubunto would run based on the info I provided you. Thanks for the clarification about the Live CD. How much of an improvement speed wise would I expect with a full installation? Also, wubi is not an option, seeing as though I am still running WinMe. Believe me I would use wubi if I could. Thanks for any help you can give me...

You will be running it fine, won't be fast but won't be THAT slow either, just be careful not to run many applications at the same time, don't open very large images, etc... you'll have to be careful with your memory usage; you won't suffer much either though, I think you'll be able to run music, messenger and browser just fine (no heavy websites though).

You can run the graphical install, I've done it with 256MB but it will be slow and there are small chances some packages fail to install but it will install, don't run the LiveCD and install from there, jump directly to the install option; although I would strongly recommend using the Alternate CD, has the same options but doesn't look pretty, is all old-school blue screens with grey and red, but you shouldn't have problems, is very intuitive; if you have questions you can always ask here or read the documentation.

I also recommend a fairly large SWAP space, I would recommend 1GB of SWAP, 2GB would be better, more than 2GB would be a waste.

Xubuntu would run very nice on your system, if you have the opportunity download the LiveCD and try it, the major difference is it uses XFCE instead of GNOME, but it manages packages just the same and you can use the same applications; XFCE is pretty cool, I like it a lot, and it does save a lot of system resources compared to GNOME and even more compared to KDE (Kubuntu), so you probably would like to try it.

---

### Post by Aidenstar on 2009-07-05
Wow...thanks that was very specific. Sorry but I'm not exactly sure what you mean by SWAP space. Once Ubuntu is installed isn't it relatively easy to switch over to xubuntu? I think I read something about that.

---

### Post by SunnyRabbiera on 2009-07-05
> **Aidenstar said:**
> Is how the Ubunto Live CD runs, any Indication of how Ubunto will run when fully installed?

I'm only asking because I question my computers resources to run ubunto, and the Live CD is kind of running slowly.

Please answer if you have any experience with this...I would greatly appreciate it.

Well a live CD does give a good example of how Ubuntu can run on your system, and if it can run on your system.
But yes a Live CD can be quite slow, depending on your hardware of course.
But once Ubuntu is intalled it will run like magic.

---

### Post by Mark Phelps on 2009-07-05
Unless I misread your specs, you have an 800MHz CPU and a system memory of 256MB -- which is the bare minimum to run Ubuntu.  While experience varies by every user and machine, I tried Ubuntu on a laptop with just those specs -- and it ran so slowly as to be all but useless.  I replaced it with Xubuntu, and that ran faster, I think primarily due to the reduced graphics and CPU resource demands due to NOT running Gnome or KDE.

With your minimal machine, if you insist on an Ubuntu version, I would recommend installing Xubuntu right off, not installing Ubuntu and then switching desktops.

Also, you should check out distrowatch.com for other "minimal" Linux distros.

---

### Post by earthpigg on 2009-07-05
> **Aidenstar said:**
> Wow...thanks that was very specific. Sorry but I'm not exactly sure what you mean by SWAP space. Once Ubuntu is installed isn't it relatively easy to switch over to xubuntu? I think I read something about that.

swap space is a chunk of your hard drive ('partition') that you dedicate to being... well, i guess 'backup RAM' is one way to think about it. when you run out of ram (likely, with only 256 mb) it starts using the swap partition as ram - it will be slower, of course, since ram is faster than your hard drive - but its certainly better than having your computer simply lock up.

to install xubuntu, enter this in a terminal:

```
sudo apt-get install xubuntu-desktop
```

then log off, and select 'xubuntu' in the login screen in the 'options' menu under 'select session'. when you login, you will be using xubuntu.

if you decide you prefer xubuntu and want do free up hard drive space, you can uninstall gnome with:

```
sudo apt-get remove ubuntu-desktop
```

---

### Post by Aidenstar on 2009-07-05
Thanks I'll keep that in mind. I'll look in to xubunto.

---

### Post by Aidenstar on 2009-07-05
> **earthpigg said:**
> swap space is a chunk of your hard drive ('partition') that you dedicate to being... well, i guess 'backup RAM' is one way to think about it. when you run out of ram (likely, with only 256 mb) it starts using the swap partition as ram - it will be slower, of course, since ram is faster than your hard drive - but its certainly better than having your computer simply lock up.

to install xubuntu, enter this in a terminal:

```
sudo apt-get install xubuntu-desktop
```

then log off, and select 'xubuntu' in the login screen in the 'options' menu under 'select session'. when you login, you will be using xubuntu.

if you decide you prefer xubuntu and want do free up hard drive space, you can uninstall gnome with:

```
sudo apt-get remove ubuntu-desktop
```



Thanks that is very helpful, upon installation how do you set aside swap space on your partition. Sorry as you can probably tell I am a novice. If that's all you have to do I think I am going to install ubuntu and if it runs to slowly I will switch it to xubuntu.Thanks that clarified a lot.

---

### Post by Aidenstar on 2009-07-06
> **darolu said:**
> You will be running it fine, won't be fast but won't be THAT slow either, just be careful not to run many applications at the same time, don't open very large images, etc... you'll have to be careful with your memory usage; you won't suffer much either though, I think you'll be able to run music, messenger and browser just fine (no heavy websites though).

Thanks you were absolutely right, I fully installed Ubuntu last night. It runs farely well. Not fast but not slow. Its as fast as I need it to be. I really like it so far, hopefully I don't have any major problems with it . I can't wait to start tinkering with it..

---

### Post by XProflmfao on 2009-07-06
> **Aidenstar said:**
> Is how the Ubunto Live CD runs, any Indication of how Ubunto will run when fully installed?

I'm only asking because I question my computers resources to run ubunto, and the Live CD is kind of running slowly.

Please answer if you have any experience with this...I would greatly appreciate it.
Yeah, like everyone says here, the CD runs considerably slower than the actual thing when you download it since you're running the entire OS from just that CD, which probably has a slower reading rate than your hard drive. Once you download Ubuntu, it's WAY faster than using a CD. I wouldn't be using the CD to actually use your computer everyday if I were you.... Also, remember to dual-boot first or make a copy of all your files that you'll want before downloading, or you'll end up like me, accidentally deleting my files when I downloaded Ubuntu.

---

