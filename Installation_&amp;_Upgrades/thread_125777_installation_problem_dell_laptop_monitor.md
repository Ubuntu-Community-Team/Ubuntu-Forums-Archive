---
title: "installation problem: dell laptop monitor"
date: 2006-02-04
forum: Installation &amp; Upgrades
---

### Post by joshua neff on 2006-02-04
I've got a Dell Inspiron 1100 that I've had a dual-boot Windows XP/Ubuntu for about 6 months now. I got a free Hoary CD and upgraded to Breezy as soon as it was released. I *love* Ubuntu. My wife and I bought a new desktop for the whole family, and I've decided to reinstall Ubuntu on my laptop as the one and only OS, getting rid of Windows completely.

Since I have the CD of Hoary, I used that, planning on upgrading to Breezy as soon as the installation was complete. The last time I installed, I had no problems. I found the xorg.conf code that fixed the monitor problem on the Web, copied and pasted it, and bingo!, the monitor worked fine. This time, though, it's not going so smoothly, so I thought I'd ask for some help here.

I installed Hoary on the laptop and as expected, the monitor image was too small. Doing a Google search, I found [this website](http://www.geocities.com/randomnumbergenerator2001/), copied the xorg.conf code and pasted it into the file. I've done this twice, and both times when I've rebooted the computer, I get a small, blue screen with a frame of gobbledygook and a text message about not being able to start the X server. And the computer is frozen at that point. The BIOS has been updated to A32, and I haven't had this problem with installing Ubuntu previously. Is the xorg.conf file on that site wrong? Is there a different file somewhere? (I can't remember what site I got the file from last time.) Any help would be greatly appreciated.

---

### Post by lol on 2006-02-05
Sorry I don't really have an answer to your question but:

1 - You should avoid downloading the configuration files of other people. Even if it works for you as well, in my opinion it is much better to try to understand what you need to change in your current file rather than replacing it with a random one...

2 - You should really use the Breezy CD for the installation. There has been improvement in the hardware detection process, and it could be that your monitor will be properly configured during the installation.

It you still have an image smaller than the screen after a clean Breezy install, try posting your xorg.conf file here, and to give more details, like the size of your screen, your resolution, etc...

In the Bios of my Inspiron, there is also an option "LCD Panel Expansion". If I turn this off and try using a smaller resolution than the screen size, I too will have a "small picture". This setting should therefore set to "on". But it is usually simply better to use the resolution of your screen (better image quality).

---

### Post by joshua neff on 2006-02-05
[QUOTE=lol]Sorry I don't really have an answer to your question but:

1 - You should avoid downloading the configuration files of other people. Even if it works for you as well, in my opinion it is much better to try to understand what you need to change in your current file rather than replacing it with a random one...[/quote]

Well, sure. Unfortunately, my Linux knowledge is nowhere near good enough to rewrite my configuration files on my own. I'm learning Linux slowly, but it would take me a long time to get to the point where I could do it on my own, and I'd rather get my laptop installed sooner than later. Since I'd gotten the file off the Web last time, and it worked perfectly, I figured I could do it again.

[QUOTE=lol]2 - You should really use the Breezy CD for the installation. There has been improvement in the hardware detection process, and it could be that your monitor will be properly configured during the installation.[/quote]

Sure, but since I've already got the Hoary installation CD, and since I had little problem getting everything set up last time, I hoped to not have to burn a new CD or wait the 4-6 weeks for a free CD. I don't know why it's such a hassle this time when it was so easy last time. It's the same laptop, the same BIOS, the same release. I just wish I could find the same conf. file.

But, I did download the Breezy iso. Now I'm having a hard time getting my CD-burning software (Sonic DigitalMedia LE v.7) to burn it as anything but an iso--instead of extracting it--which does me no good, obviously. This is more than a little frustrating.

---

### Post by lol on 2006-02-06
I don't know your CD-burning software, but what do you mean by 'extracting files'? If it does it on the CD, then this is what you want. When you read the CD after burning the image, you should actually be able to see all the files, just as if they were 'extracted' from the iso.

---

### Post by joshua neff on 2006-02-06
[QUOTE=lol]I don't know your CD-burning software, but what do you mean by 'extracting files'? If it does it on the CD, then this is what you want. When you read the CD after burning the image, you should actually be able to see all the files, just as if they were 'extracted' from the iso.[/QUOTE]

Sorry, what I meant was when I burned the iso to a CD, it was on the CD just as an iso, not as the actual files needed to install Ubuntu. But I burned a CD at work with Roxio and it worked fine. I'm installing Breezy now.

Which makes this thread in this category obsolete, doesn't it?

---

