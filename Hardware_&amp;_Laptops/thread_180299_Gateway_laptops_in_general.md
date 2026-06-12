---
title: "Gateway laptops in general"
date: 2006-05-22
forum: Hardware &amp; Laptops
---

### Post by zapcojake on 2006-05-22
Hello I was curious about peoples expierences with Gateway laptops and Ubuntu in general. Which workout the best? is there any models/options to avoid? are there any that just work out of the box?

---

### Post by cneil on 2006-05-22
I'm using a 7510GX and I've spent a lot of time getting everything working.  I'm a novice Ubuntu user, so I think I'm struggling more than most.  

However, the good thing is that I've been able to get everything working except the wireless card.  There were some quirks.  I had to disable external amplification in the soundcard.  I once accidentally deleted my home directory when trying to make a shard partition (I'm dual booting).  However,  I've been able to use the card reader, configure the sound, and even plug a joystick into the USB port.

The good news is that when I upgraded from 5.10 to dapper the OS began to recognize the wireless card correctly.  I think there should be a way to get it working, but I haven't managed.  There is a hard switch in the wireless card that makes a blue light come on and even when I was able to get a response from -NDISwrapper: hardware present, driver present- the blue light would not come on even if I pushed alt-F2.

I also have one more minor hiccup.  The touchpad works, but I can't disable the tapping so if I hit it I inadvertantly click on things.

So my verdict is to use a new Gateway with plenty of ram, but don't count on the wireless card.

---

### Post by ScrambledDebutante on 2006-05-23
Install seemed to go well on my Gateway M275, but all I get when Ubuntu (Breezy) "boots" is a blank screen.  It's a very nice blank screen, but ultimately...blank.  Any suggestions?  I'd appreciate them.  --SD

---

### Post by cneil on 2006-05-23
Do you even see the ubuntu screen when it starts to run?  
Is it possible to boot into safe mode and get to a simple bash shell?

---

### Post by ScrambledDebutante on 2006-05-23
Nope, just a blank screen.  I saw the Ubuntu screen briefly during the install, but now I see nothing.  I can't imagine how it could make any difference, but this is a dual boot with WinXP (SP2).  I put GRUB in the MBR, so I might be able to boot into safe mode.  I haven't tried, because I wouldn't know what to do if it succeeded.

---

### Post by cneil on 2006-05-24
If you could get a prompt then you know that you have a driver, x-windows, hardware, or configuration file (did I miss anything)  problem.  If you can't even get a prompt, then you know that your entire installation went down the tubes.

Either way, I would just try reinstall my system and pay extra special attention to the prompts.  Try to really know your hardware.  I have instal linux about six or seven times, and in order to get my installation perfect (partitions, drivers, network config) I always have to try more than once.

---

### Post by menkent on 2006-05-30
i've got an old DS450X and the install went pretty smoothly. i haven't figured out how to get the various FN hotkey combos working to control brightness/volume/etc, but it seems to be handling more serious things like the battery and cooling well enough once i turned off some nonsense like the raid controllers that were eating lots of system resources. can't get anything to print to my minolta 1250W, but i can't get that to work with my desktop ubuntu rig either. *shrug*

i guess i'd have less issues than most though since my laptop predates things (like built-in wireless cards) that seem to give people problems.

---

### Post by menkent on 2006-05-30
oh, to address the original question in the thread - it seems like gateway laptops have only limited support in any distro. gateway has really dropped off in general over the last few years, so it might be better to go with a more popular brand/model if you're going to rely on people in the community or forums for help (like most of us beginners end up doing). there are entire wikis out there devoted to linux on thinkpads, but with gateway you'll be more or less on your own.

---

### Post by boyfromthedwarf9 on 2006-06-08
I have the same laptop, this issue is fixed in Dapper, for me at least.  Press FN+F3, to switch between the CRT/LCD Modes.

---

### Post by ramnarayan on 2006-06-13
Just installed Ubuntu Breezy on Gateway MX6121 - seems to work really well except no modem dectected. Can't say anything about the wireless as yet. Sound works, also the scroll part of the touch pad works [unlike in the Windows XP section - ;) ]

But had a bad time with the dual boot - have posted separately for that which is at
[http://ubuntuforums.org/showthread.php?goto=newpost&t=195524](http://ubuntuforums.org/showthread.php?goto=newpost&t=195524)

but in the short while i have been using this Gateway laptop i think Ubuntu willfly on it. 

ram

---

### Post by 56phil on 2006-11-15
I have a gateway laptop.

Model M680 running Edgy (6.10) via upgrade from 6.06.1.

The most serious install problem was with the ATI Radeon X700. X11 would not go past a screen resolution of 1024x768. After Installing the proprietary video driver: 

```

sudo apt-get install xorg-driver-fglrx
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv

```

Adding the desired screen resolutions to the configuration file:

```

gksudo gedit /etc/X11/xorg.conf

```

and finally adding vga=788 to the kernel lines of the boot menu to get the system to shutdown properly:

```

gksudo gedit /boot/grub/menu.lst

```

I got the screen resolution (1680x1050) the system was meant to deliver.

One unresolved that I still have is that the system will not suspend.

Edgy ISO would not finish booting up.

I had to use the safe graphics option to boot from the Dapper (6.06.1). Overall, I'm amazed that so many things went as well as they did. I'm a happy camper.

---

### Post by arjunsharma on 2006-11-17
Well, I have a Gateway 7508GX. I had a hell of a time getting my ATI graphics card on the old Ubuntu (5.10). The wireless was detected but never worked for wireless internet, and I never got sound working. Also, there seemed to be a lack of support/apps for 64-bit processors, and I couldn't get the 32-bit to work without messing up the system time and the music playback (the actual player, since I couldn't hear any sound), both of which would go at double speed.

Anybody care to discuss? Anybody who had any of these problems before and not have them in this current version?

Again thats-
ATI is pain to set up
wireless detected but not useable
NO SOUND (which was actually the biggest reason not to go with Linux, and instead go back to Windows...I need my music and games and sound)
64-bit w/ 32bit Ubuntu causes some things to go at double speed (such as system time and media playback)

Arjun

---

### Post by shmeeter on 2007-04-19
Hey there all.  I am using a 7510gx.  I just recently, like a week ago, installed Dapper LTS amd64.  I fixed the wireless using ndiswrapper fairly easily.  I fixed the touchpad using a guide from ubuntuforums, I believe.  The only thing left is the sound.  I have Java and Flash working.  Follow the post linked from the 64bit sticky.  I have been trying to keep a journal of my progress at [http://www.shmeeter.com/computer/linux/7510gx/index.html](http://www.shmeeter.com/computer/linux/7510gx/index.html), my home page.

Like I say, the only thing I have left is sound.  It works for some stuff, but not others.  Works: Java sound in browser, system sounds.  Not working: Flash sound, games.  Untested: Music, movies.

My totally untested theory is that there is too much crap trying to fight for control of the hardware.  lsmod give me a list like 40 items long!  That's rediculous!  One thing I want to do is recompile the kernel, compiling in the stuff I need, getting rid of the stuff I don't, and not loading the unnecessary modules.

If anybody has any ideas for sound, let us know.

Shmeeter

---

### Post by shmeeter on 2007-04-19
Me again.  Sound kind of works.  I had previously done the whole alsa-oss thing, and got as far as Java and system sounds.  For some reason, the system sounds would sometimes work and sometimes not.  I installed alsamixergui, and disabled external amp, and that helped.  Still not for some stuff, like Flash.  Messed around a little more, and now sound works in the games Armagetron, Gnometris and Planet Penguin Racer.  Works with Java plug-in in Firefox32.  Here are my mixer setting:  Master on, Head(phones?) off, PCM on, Line off, CD off, Mic off, Mic Boost off, Video on, Phone on, IEC958 off, IEC958 Playb(ack?) AC97... on and on, PC speaker on, aux on, capture on, mix on, mix mono on, external amplifier off.

I'm gonna post this somewhere else, too, see if there is more help out there.

Shmeeter

---

### Post by deadspider187 on 2007-04-20
I bought a mx6930 back in November and it works out of the box (a few problems with the sd card reader though).  I highly recommend it. 

Specs:
core 2 duo 1.6 GHz 
1 GB RAM
ipw3945 wireless a/b/g
945 GM graphics
sata hard drive

The video card isn't very good for games, but it will still run beryl and the like.  I picked it up for around $900, but I think it now sells for about $750 at Best Buy.

---

### Post by Afkpuz on 2007-08-17
I'm not sure if they still sell the m680, but I'm dual booting windows and ubuntu 7.04 on mine.  Everything works except the SD card reader and I think that it's possible to make it work, I just need to do some searching.  Oh, the function keys are supported by ubuntu, but some apps (like amarok) don't recognize them.

---

