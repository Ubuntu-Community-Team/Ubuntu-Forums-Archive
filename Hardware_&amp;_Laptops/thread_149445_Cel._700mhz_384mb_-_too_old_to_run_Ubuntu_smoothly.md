---
title: "Cel. 700mhz 384mb - too old to run Ubuntu smoothly?"
date: 2006-03-23
forum: Hardware &amp; Laptops
---

### Post by niigatapeter on 2006-03-23
I’ve been trying to find a suitable installation for my old 700mhz Cel. 384mb Toshiba laptop computer for almost a year now, and I’ve tried a few different linux flavors, mostly the ones related to Ubuntu (Kubuntu and Xubuntu). The results were always the same: the desktop interfaces being a bit slow, and always problems with displaying video. 

Recently I came up with the theory that it might be the acceleration function of my graphics card that doesn’t work properly with the normal “linux drivers”. My computer of Japanese brand, was probably only released here in Japan, so the model number V2/470CRC might be Greek to most people. However, I know that it’s equipped with a graphics card Trident CyberBlade XP.

The card seems to be correctly recognized by the linux system&#12289;but graphics are, without doubt, slow in Gnome, KDE as well as in X (!). I use my computer manly for web browsing, and watching movies. Realplayer clips, and mplayer with w32codecs clips are too jerky to be watchable (both the video and the sound is jerky). DivX movies are also jerky but not as bad as the Real and Mplayer clips. I should also mention that I’ve tried to change the settings in the realplayer software to make it run more smoothly, but alas no effect.

So...  Has anybody made any experiences with the CyberBlade XP chipset?   Or is it possibly the case that my computer is too low-end to run a modern linux system on it?

cheers

---

### Post by xXx 0wn3d xXx on 2006-03-23
I have used it with 499 mhz processor + 128 of ram and it ran fairly well.

---

### Post by stuporglue on 2006-03-23
700 Mhz is plenty for a good Linux system. It might be a little slow for Gnome or KDE, but probably no more slow than Windows. 

You might need to do a little bit of tweaking to get video acceleration enabled, but a quick look on Google seems to indicate it's possible. 

If you're worried about the speed of the system, check out Xubuntu. [https://wiki.ubuntu.com/Xubuntu](https://wiki.ubuntu.com/Xubuntu)

The Xubuntu in Dapper is VERY very nice. Dapper is the developers version, but if you're going to use Xubuntu, I'd recomend going with that.  The Breezy version is pretty good too though.

---

### Post by jml on 2006-03-24
I agree that both KDE and Gnome are very high overhead environments.  If you can't get better performance by tweeking your video settings, you might want to try a window manager that requires less resources to run.  Several light weight window managers that I like are IceWM, Window Maker and Fluxbox.

If all else fails, you might want to try a lighter weight Linux distribution like Damn Small Linux.  It includes most major categories of applications, test editor, word processor, spreadsheat, web browser, e-mail client, etc.  All in a distribution that is about 50-60meg in size.  Its a live CD with an install option so you can download it and try it on your laptop befor you install it.

Joe

---

### Post by az on 2006-03-24
I'm sitting next to a box with a trident cyberblade onboard chip (8 megs of shared memory!) and an amd-k6II 533 MHz processor!

There is no hardware acceleration in linux (and barely in windows) for those chips.  That should not affect the desktop, since the regular desktop is not accelerated.  

Depending on the quality of the video, you may need a faster processor or better disk i/o to get better performance.  You only really need hardware acceleration for some gl-screensavers and games.

---

### Post by aragorn2909 on 2006-03-24
I'll just confirm what Azz has said.  I've got an old toshiba laptop with this graphic card, and Ubuntu runs just fine on it.

---

### Post by djheadley on 2006-03-24
I'm running a triple boot (Windows, Ubuntu, Kubuntu) on a Celeron-433, 256MB Ram with 8 MB shared for video and I think Ubuntu runs just fine.  The video chipset is SiS and I didn't install the drivers (I did but it broke things so I did a re-install).

DJ

---

### Post by outrage on 2006-03-24
Just to confirm what others have said, I'm currently typing this from my Ubuntu laptop...a Compaq Armada 1750 (366mhz, 192mb ram, 4mb ati video).  Gnome can be a bit slow at times, but if you tweak it right, 700mhz will fly.

---

### Post by niigatapeter on 2006-03-24
Thanks everybody for your help!    I have a more precise question to those of you with 700mhz celeron, or less:    is Realplayer jerky on your computers?  Xubuntu is installed on my system right now (so tweaking Gnome is not an option here), and real is still jerky.

---

### Post by djheadley on 2006-03-24
I don't use RealPlayer because I only have dial-up, but when I play DVDs they are kind of jerky.  I assume that I need more memory but this mobo won't go much higher in that department.

---

### Post by niigatapeter on 2006-03-25
[QUOTE=azz]There is no hardware acceleration in linux (and barely in windows) for those chips.  That should not affect the desktop, since the regular desktop is not accelerated.  

Depending on the quality of the video, you may need a faster processor or better disk i/o to get better performance.  You only really need hardware acceleration for some gl-screensavers and games.[/QUOTE]

Thanks for your help, but you're wrong about the hardware acceleration. If you still have Windows installed on your computer, try to switch off hardware acceleration in the Media Player, and play a videofile.   You will find that the acceleration is absolutely essential for playing videofiles on old computers such as ours. 

All the videos that I'm trying to play in Xubuntu are playable in Windows XP, so the computer resources should not be the problem, I'd say. There must be a way to enable acceleration in linux :neutral:

---

### Post by arathorn2nd on 2006-03-25
I'm currently using Dapper flight5 in a Duron 750Mhz/256Mb in a crappy motherboard for browsing, email, writting reports and even file-serving my music and video collection for my laptop. No problems at all, just a few seconds to load each application.

I must say it runs faster than Windows, but of course, there are some stuff out of this computers reach, like playing DVDs without hardware acceleration. But afterall, Windows couldn't do it as well.

---

### Post by stuporglue on 2006-03-25
[QUOTE=niigatapeter]All the videos that I'm trying to play in Xubuntu are playable in Windows XP, so the computer resources should not be the problem, I'd say. There must be a way to enable acceleration in linux :neutral:[/QUOTE]

Not necicairily. Acceleration depends on the drivers, and since Windows and Linux don't use the same drivers.  In many cases the Windows drivers support things Linux doesn't, or supports the same features better. Occasionally the Linux driver might support something Windows doesn't.

---

### Post by LateNighter on 2006-03-26
Just an Idea, But it just might work.

 You said your Laptop was Made in Japan for Japan if my memory serves.

 With all the many Langs that Ubuntu is made in.

 If there is one in Japanese Try it, It's my thought there maybe something in an English Version that it can't quite Understand....

 But then again I know English and theres alot I don't understand....\\:D/

---

