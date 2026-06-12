---
title: "Please help a newbie out! (9.04 install problems)"
date: 2009-10-24
forum: Installation &amp; Upgrades
---

### Post by Bad Wolf on 2009-10-24
Hi everyone! So I've decided to try linux. And nothing seems to work. My setup - a 6 or 7 year old HP desktop with XP pro SP2, 512 ram and an 80 gig hard drive (about 30 gig free). I downloaded ubuntu 9.04, burned a cd, tried re-booting and it freezes. First asks me for language preference, then goes to the screen with options to "install/try without installing/check disk/whatever", no matter which one I choose it goes to the next screen where it says "ubuntu" and the thin progress bar under it gets to about one-fifth and freezes there. I waited for a good 30 mins - nothing. Every time it does the same thing. So I tried going the roundabout way and downloaded Wubi, which in turn downloaded 9.04 all over again, then did whatever its supposed to do. I re-booted and my pc gave me an option to choose which OS i want to use. I tried Ubuntu, and it went right back to the same screen with a freezing progress bar. Sorry if I'm not making sense, im really frustrated. Please shed some light on this mess! Thanks in advance

---

### Post by oboedad55 on 2009-10-24
What kind of video card do you have? You might want to try 9.10. It's a RC but it's working well for a lot of people.

---

### Post by motsteve on 2009-10-24
That definitely sounds like it is failing something in the hardware test.  Is XP Pro still working?  You also have to read all the screen messages very carefully until you get used to using the OS.  You might also consider trying Mint because it is basically Ubuntu.  My luck with Karmic Koala (9.10) has been a disaster time and again.  Please don't give up.  You won't be sorry you switched to Ubuntu.

---

### Post by Bucky Ball on 2009-10-24
Try 8.04 LTS Alternate CD. If that doesn't work perhaps Xubuntu Alternate CD.

---

### Post by motsteve on 2009-10-24
I just thought of something else.  Try downloading and burning PMagic.  When you boot it you'll be running Linux and using the common drivers.  Also, this disk is crammed pack full of various utilities including test utilities.  You may want to test out your hard drive for health and also your ram.  There's no telling what is marginal.

---

### Post by Donnie Love on 2009-10-24
I'm having the same problem. According to the installation instructions at:
 
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
 
"4. Select **Install Ubuntu** and press **Enter**. The Welcome window appears. "
 
But the Welcome window never appears. I get the progress bar as described by Bad Wolf and then nothing. I would try 9.10, but there's no documentation on it and as I know nothing about installing operating systems, I need detailed instructions.

---

### Post by Bad Wolf on 2009-10-24
Thank you for all your replies, looks like Donnie Love and I are experiencing the exact same thing. My video card is built into the motherboard. XP works fine, except lately it's been getting slower and slower at everything it does. As in, I click the start button, go get a cup of coffee, come back, thats when the start menu appears. Yeah, that slow. So I cleaned the registry, defragged both partitions of my HD, wiped out all the usual temp stuff - still slow. That's when I started considering linux.
Problem is, I can not afford to lose some of the data on the hard drive, specifically a couple of music production pieces of software that would cost me around $800 to replace, plus some other stuff... So,
I'm thinking, I should just stop terrorizing the poor computer, go and get a new hard drive for a clean Ubuntu install (to hell with dual boot), and turn my old hd into an external one. At least this way my old drive will get some rest from years of abuse.
In the meantime I'm going to try Pmagic. Thanks again!

---

### Post by Donnie Love on 2009-10-24
I got 9.10 to install, or it seemed to install OK, but when I rebooted this prompt came up:
 
[EMAIL="user@Ritard:~$"]user@Ritard:~$[/EMAIL]
 
(Ritard is the name of the computer.) I've been trying different commands like "start" "go" "boot" "load" "win" "open, you *******", but I don't know what the proper response is. What do I do next...???

---

### Post by Bucky Ball on 2009-10-24
```
startx
```

---

### Post by Donnie Love on 2009-10-25
startx command not found

---

### Post by motsteve on 2009-10-25
Do a "sudo startx".  Right now you are in user mode.  If it goes out and tries to start and then comes back with an xserver error or such, then your xorg.conf file is screwed up.  This happens a lot when installing and is a whole new problem.

---

### Post by Donnie Love on 2009-10-25
I tried "startx", it told me to type some gibberish to install something-or-other, then the prompt again. I typed "startx" again and it went black and the monitor powered off.

---

### Post by motsteve on 2009-10-25
I just checked and found out that startx is in /usr/bin, so if the command still doesn't work do:

lsb_release -a

This will give you distro info.  If that doesn't work do: uname -a and publish the results.

---

### Post by motsteve on 2009-10-25
Write down as much as you can about the error message and send that up.

---

### Post by Donnie Love on 2009-10-25
"lsb_release -a" gave me:
 
No LSB modules are available.
Distributor ID: Ubuntu
Description: Ubuntu 9.10
Release: 9.10
Codename: karmic
 
"uname -a" gave me:
 
Linux ubuntu 2.6.31-14-generic-pae #48-Ubunutu SMP Fri Oct 16 15:22:42 UTC 2009 i686 GNU/Linux

---

### Post by motsteve on 2009-10-25
You are trying to install Karmic (Ubuntu 9.10), just so as to get all this straight, right?  If the gobbledly gook you got when you entered startx involves xserver, then you have the same problem as I have trying to update my 9.04 to 9.10, but I'm running a 64bit version of both.  If this is your case, then I'm totally unqualified to help as it has kicked my butt for several days now.  I just went back to 9.04 and will wait until the 64 bit version of Karmic gets straightened out.

---

### Post by Donnie Love on 2009-10-25
No, there was nothing about "xserver" in it. It said something like type sudo [something] to install xinlin (or something). Nothing more than that. I did what it said and the message doesn't come up anymore.

---

### Post by motsteve on 2009-10-25
I reread the thread and I am puzzled why 9.04 gave you a problem and this Karmic install got as far as it did.  You're probably tired of installing and burning and I don't blame you, but this is an endeavour worth every bit of patience.  Did PMagic help at all in any of its utilities? For that matter, did it boot?  I sense a hard drive problem here.  They get temperamental before they go, just like people. :)

---

### Post by Donnie Love on 2009-10-25
I haven't tried the PMagic. I'll see what it does. I am trying to patient; I have no other choice. I must get this computer working or I'm out of business.

---

### Post by Donnie Love on 2009-10-25
OK, here's where I'm at:
 
The suggestion was made on another forum (I've been on several over the past few days) to try "safe graphics mode" on the 9.04 CD. That seems to have worked. If I have any more problems (as I'm sure I will) I'll be back. Thanks everybody for your patience and advice! :P

---

### Post by motsteve on 2009-10-25
Please do come back and I hope you enjoy Ubuntu as much as I do.

Steve

---

### Post by Bad Wolf on 2009-10-25
Hi again, I'm back with updates. Here's whats going on: I got a new hard drive, which works fine. Tried each of the three 9.04 cds i burned, one 9.10 cd and even one openSUSE 11.1 cd. Still nothing. Still the same hang-up right after the "welcome/choose your language" screens. I even found a different cd-drive and hooked it up - same story. So....

If I still have any wits left about me, then the most logical explanation seems to be that every cd I've burned so far is somehow screwed up. Could it be the case? And if so, could there be a problem with my burner? It burns program ISOs just fine and i have no problems installing those. So is it the download? Bad locations? Uhhhhhhhhhh....:confused:

P.S. Re-downloaded and burned another openSUSE 11.1. Tried every cd in safe mode, oem install, regular mode - all to no avail. WHAT GIVES????

---

### Post by Bucky Ball on 2009-10-25
Does it boot from CDs apart from the Ubuntu ones you've burnt? Have you another bootable CD you can try. That would narrow what the problem might be.

---

### Post by ndefontenay on 2009-10-25
Hi.

it's a bit outside of the topic at hand but I couldn't help to notice that you have a very expensive piece of software install on a very old computer showing signs of fatigue.

You should address the issue very seriously because even with just windows, the day will come when it's going to fail you. You'll have to find a way to re-install it on another hardware at one point.

Other than the software, you should backup your production on an external hard drive in different places. (another computer +  external hard drive).

You are currently trying to install ubuntu. This is an excellent piece of computer technology but it can't help the hardware part. 

Before you keep trying installing it, I strongly suggest you backup anything valuable to you.

---

### Post by hogu on 2009-10-25
if its mission critical that you not loose the data on the drive, you really should back it up somewhere before you mess around with the partitions.

ubuntu is pretty good, but nothing is perfect`

---

### Post by motsteve on 2009-10-26
I thought everything was fine, yesterday.  Oh well!  Bucky Ball's suggestion is good.  Check if it reads your Windows installer disk or anything that you knew used to work with the CD drive.  Also, if you burned the PMagic CD, it has to load a linux system on before it even cranks up, so try that if your known good CD works okay.

---

### Post by Bad Wolf on 2009-10-26
Hello yet again. First of all, everyone, thanks a bunch for all the help and suggestions. And yes, at this point I am officially giving up on trying to revive this old piece of junk. Time to let go. Not that I'm that sentimental, just broke:). Once I get an extra couple hundred together, I'll get a new(er?) computer and go from there. Regardless of how decent my new hardware is going to be, I'm still very interested in all things Linux, so I'd like to stick around on this forum. Thanks again!

---

### Post by Bucky Ball on 2009-10-27
Stick around by all means! I think the L in Linux stand for Learning, not sure about the other letters!

As you are a bit broke, you are probably going to accumulate bits as you get the money. You could start with a hard drive and give that a shot in the old machine. Then again, a new motherboard will be begging for SATA and the old motherboard probably won't accommodate.

Also, if you are putting a machine together and want to stick with all things Linux, you might want to check [_My HOWTO _]("http://ubuntuforums.org/showthread.php?t=1179877")link. All components used (except the printer but that takes 10 minutes to setup) will work out of the box. It might give you some ideas for your build if nothing else.

Good luck with it and please mark the thread as 'solved'. :)

---

### Post by motsteve on 2009-10-27
Don't quit now.  At least let us know if your CD drive is reading.  I easily put Ubuntu on my neighbor's Dell Optiplex 1 which is 11 years old and it plays nicely.  Talk about broke, she's on Social Security only.  Bucky Ball is right about the learning and I think that Linux is fun as well as keeping your brain from turning to mush using Windoz. :)

---

### Post by Bad Wolf on 2009-10-27
Re: Bucky Ball and Motsteve,

CD drive is reading ok, CD-burner burns fine as well. And I even bought a new(ish) hard drive which is also fine and wiped clean. At some point I even tried a different cd drive - same results. A few other attempts convinced me that something is wrong with the motherboard. Considering my entire system consists of only a couple of parts - power supply (ok), hard drive (have a newer one), ram (checks out fine), optical drives (uh, not too sure how much longer they have to live, could use new ones) and a motherboard, I seem to have 3 options. 1- get a barebone system for about $200, 2- a new pc (saw some decent ones at local retailers for $300ish with some nice options including win7 home premium) or 3- craigslist (some very usable stuff for under $150). Last one seems like the way to go for now.

---

