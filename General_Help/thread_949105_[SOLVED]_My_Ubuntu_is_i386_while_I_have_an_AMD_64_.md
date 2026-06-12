---
title: "[SOLVED] My Ubuntu is i386 while I have an AMD 64 processor."
date: 2008-10-15
forum: General Help
---

### Post by mroski on 2008-10-15
HI, I have installed Ubuntu 8 Hardy three days ago in my Toshiba A305D laptop (AMD 64) and have now noticed that the installed system architecture is i386.

What problems may be caused by having the wrong architecture?
Sometimes when I turn off I can not turn my laptop on again, it get stucked in the loading bar with the logo of Ubuntu and the black background.
Also I can not install my Atheros AR5007EG with madwifi and I am using ndiswrapper insted, may the amd64 architecture fix this?
Moreover I have problems when watching full screen videos as the screensaver and youtube (enlarged), when I open something in full screen I can not go back, I mean I have to reset because I can not go back to my desktop.

Thanks !

---

### Post by Sam on 2008-10-15
I think you didn't download the right disk. In the [download page](http://www.ubuntu.com/getubuntu/download), be sure to check "64bit AMD and Intel computers".

While you can use a 32 bit system on a 64 bit architecture, you cannot use a 64 bit system on a 32 bit architecture.

---

### Post by drs305 on 2008-10-15
Many users purposely install the 32-bit version on their 64-bit machines. You just didn't do it on purpose!  You won't have any problems and although there have been great gains in the 64-bit world you probably are not giving up a huge amount of performance. There are some issues if you have large amounts of RAM installed.

There are plenty of discussions about 32 vs 64 bit systems, and you can find a lot of them in these forums (there is a dedicated 64-bit forum). If you really want to go 64-bit, there is a new version of ubuntu coming out at the end of the month. I would take the next couple weeks to explore your options.

---

### Post by Sef on 2008-10-15
>  What problems may be caused by having the wrong architecture?

Nothing.  If it had been the wrong architecture then it could not have installed.

---

### Post by sg7791 on 2008-10-15
I have an AMD 64 processor too, and I have tried both 32 and 64-bit Ubuntu. There is no problem using a 32-bit OS on an x64. In fact, I would recommend it. While Ubuntu works great in 64-bit, sometimes performance is app-specific. So running 64-bit software could be buggy as it's still not a COMPLETELY perfected technology.

---

### Post by OutOfReach on 2008-10-15
Nothing bad will happend when you use a 32 bit OS on a 64-bit capable processor.

---

### Post by Yellow Pasque on 2008-10-15
> **sg7791 said:**
> So running 64-bit software could be buggy as it's still not a COMPLETELY perfected technology.

FUD, FUD, FUD. What has not been "perfected" about x86-64 that has been with x86? The only thing I could think of is programmers doing unconventional things with data types because they assume their code shouldn't be portable. 32-bit software may be just as buggy.

> Nothing bad will happen when you use a 32 bit OS on a 64-bit capable processor.
..Except that you'll lose some performance, and that next RAM upgrade may not go so smoothly.

---

### Post by 73ckn797 on 2008-10-15
The only issue for me is I will have to wait for Java to work with what I need. Otherwise I have no problems with it. I run it on another HDD but not for everyday use.

---

### Post by SeanBlader on 2008-10-16
> **Temüjin said:**
> FUD, FUD, FUD. What has not been "perfected" about x86-64 that has been with x86?

Adobe Flash.

---

### Post by Yellow Pasque on 2008-10-16
> **SeanBlader said:**
> Adobe Flash.
LOL, I've seen people running 32-bit complaining about Flash sites, performance, etc.
I've never had any problems with it, and if I did, I could run a 32-bit browser and native Flash on sites that needed it.

Try again.
EDIT: BTW, Flash doesn't show that anything's wrong with x86-64; it just shows how badly Adobe's devs suck, and how little Adobe cares about Linux.

---

### Post by jerome1232 on 2008-10-16
As much as I am into the 64 bit camp there are problems, mostly with closed sourced software (and some open sourced software) that either the company is just not willing to package it for 64bit, or it's actually not possible.

That being said I'm running zsnes on a 64 bit OS, you **cannot** compile this program for 64 bit, luckily 64bit is backwards compatible with 32 bit (I'm using a binary that was compiled on a 32 bit machine).

@Temüjin, Run suns java plugin on a 64 bit machine. :)


edit: You guys know that all modern macs are 64 bit right?

---

### Post by Yellow Pasque on 2008-10-16
> @Temüjin, Run suns java plugin on a 64 bit machine.
No problem. I'll just fire up a 32-bit browser and use that if OpenJDK doesn't work.

"the company is just not willing to package it for 64bit"
Well, actually, Sun claims they're willing, but they've just been extrememly lazy about it.

> you cannot compile (zsnes) for 64 bit
You can compile it on a 64-bit machine with gcc-multilib and use -m32. (And it runs fine on a 64-bit install, so it doesn't support the "install 32-bit on your 64-bit CPU" argument.)

EDIT: Has this been moved to Recurring Discussions yet? :P

---

### Post by jerome1232 on 2008-10-16
> **Temüjin said:**
> EDIT: Has this been moved to Recurring Discussions yet? :P

lol. ^ And not yet surprisingly (must not be getting bumped enough!)

I never got it to work (compiling zsnes as a 32 bit program on the 64 bit machine) Kept tossing up errors, yet compiled just fine on another 32 bit computer. And the 32 bit binary worked great on the 64 bit computer.

Then dfreer made a nice package for 64 bit so I don't have to bother with it anyways (emulators seem to cause the most problems when getting moved to 64-bit that's why I picked that to argue with)

I actually am very surprised at the amount of anti 64 bit though, I run it on every machine that can and have no problems (a little extra setup sometimes)

---

### Post by jespdj on 2008-10-16
> **jerome1232 said:**
> I actually am very surprised at the amount of anti 64 bit though, I run it on every machine that can and have no problems (a little extra setup sometimes)
That's because unfortunately there are a lot of people, who haven't tried 64-bit themselves (or they tried it maybe three years ago), keep on repeating FUD.

They see some thread from someone who is making it unnecessarily hard for himself (by trying to install Flash manually for example) and assume that 64-bit is difficult and doesn't work well.

---

### Post by mroski on 2008-10-16
Hey Folks,

Thanks for the help. While I will mark this topic as [SOLVED] you can still keep on with the discussion.

Thanks !

---

