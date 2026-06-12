---
title: "The Good, the bad and...the frustrating!"
date: 2005-08-11
forum: Hardware &amp; Laptops
---

### Post by ajpr on 2005-08-11
Hi everyone,

I'm new to Ubuntu, and fairly new to Linux.  Not sure where this post should go, as it's a bit of a rant :] Feel free to move it to whereever! (the hardware questions are at the bottom)

OK, well I have used linux a number of times in the past but never went beyond using it, i.e. I never bothered to configure and install the OS more than once and that was a bit of a failure (i installed redhat 8.0 on a laptop), as I could not get all the devices to work properly, the most annoying of which was the sound.  That was 2 years ago and so I decided my main desktop should have Linux so I can learn from it as it might come in useful when applying for jobs within the IT sector (which i am currently doing). 

Anyway, I looked at many distros and ended up choosing Debian due to its package management system.  The debian install worked OK after the second time, first time I didn't realise  that the way to choose "Desktop environment, web server..etc" was by pressing space.  I inadvertently pressed enter when Desktop env was highlighted and of course I ended up with an install about 50mb in size :], no X or anything.  This sent warning bells into my brain, as I spent a good 6 hrs or so trying to install X from the shell, not easy for a sporadic linux user!

So after the 2nd install Debian booted up and I thought, "Yes it's all working"... how wrong could I have been?!!!  Then followed a strange networking problem that only appeared within Debian as my Redhat Laptop worked flawlessly within that area.  Apparently Debian didnt like my router acting as a DNS server, not sure why this is...Had to fix it by making my router send internet DNS servers to the DHCP clients.  This whole thing took a few days of asking people and eventually working it out for myself.

The only other problem I experienced with Debian has been so catastrophic that today I just gave up.  For some reason, Debian did not seem to load my sound card properly and seemed to get confused with my tv card as a sound card.  I tried all sorts of things editing the blacklists within hotplug and discover.conf, but I guess I'm just not that clever.  To get things working I could run alsaconf and then modprobe bttv, but I would have to do this every time I booted the machine.  So I decided to try and watch the boot sequence, but every time the output was too fast to read, so I asked in #debian on freenode.org for some help on getting the boot to log the output.  Some people gave me some advice and I edited the correct files and rebooted.  Unfortunately the reboot did not create any boot log file, and so I went back to irc to ask for some advice and what i might have done wrong.  I guess people lost patience with me even though I was being extremely calm and did no spamming etc, as the person who was helping me ended up calling me a "FUCKING IDIOT".  But I didn't let this get to me, I just waited until he calmed down and spoke to someone else in the channel instead, who told me to read various documents on udev as my dev/console wouldnt load due to a device error.  So i went and tried to read the docs and files on the web about udev, but the words used were just too complicated.  I spent a few hours working out what udev meant and what it actually was supposed to do. So I grasped that, but as I said there were too many words and phrases that I did not understand.  The next problem i had was "how do I link udev to the boot log process?", so I tried to read up and I found out that hotplug "runs" it or something , but I couldnt work out how to troubleshoot my problem using udev.  A few hours of thinking and i realised I wasn't getting anywhere from reading or asking for help in irc.  Then i decided to skip trying to get the boot log to work and just ask for any advice on my sound/tv card problem in irc.  The problem was noone seemed to know and I had been asking for a few days (which was part of the reason for trying to get boot log to work).  Theres plenty of more problems I had with debian, such as the messed up documentation, and conflicting advice from people in #debian.  I think part of the problem might have been that I was told to use alsa sound as originally my sound didn't work due to an on board chip which I ended up disabling anyway.  A lot of docs I read simply weren't relevant to the latest version of Debian , e.g. the whole oss/alsa thing, or weren't relevant to my problem.  

Today was the final straw, I managed to get quite far in just 5 days of using it, but I have spent nearly every hour of the day trying to get things simply to work.  I got a lot to work such as: fixed my networking problem, installed nvidia drivers, wine, configured kmail, installed a few programs.  But i am still left with these problems after about 60 hours: messed up sound /tv card system, no printer (the debian docs said something along the lines only very advanced users whould try getting their printers to work...so I didn't try that hard), no webcam.

I know Debian isn't supposed to be easy to use, but I heard good things about it from people so I gave it a go.  Maybe I am an idiot like that guy said to me. I wanted Debian to work so much, and I just couldn't work it out.  

**So today I gave Ubuntu live cd a go, as I heard that that is also good.  I wasn't expecting much, especially as it is based on Debian, yet I was totally surprised that sound was working without me having to mess about with configs and secondly I think it detected my TV card correctly.  Both major plus's, although the webcam thing failed :(**

I also liked the programs that came on the livecd, well chosen and easy to use.  Yet, I'm not sure wether to actually bother with Ubuntu, I looked at the sound setup program (dont know the exact name, in win xp atm, but it was a gui program on one of the menus), and it said it was using oss, which is good but the sndsrc(?) didnt work althought the sndsink did.  not sure what that means tbh!

So what do I do from here, I'm at a bit of a loose end... During my web searching for answers to problems I had, I came across a post from a guy trying to get his tv card working I think.  Linux gurus replied but nothing seemed to help, the guy eventually said something like "I just want it to work, it's as if you need a degree in computer science", to which the Linux gurus responded by insulting him etc.  The guy then said he was going back to windows with all the viruses, trojans, spyware etc, as at least he could use his computer.  I'm in windows atm, I feel kind of the same, I am not that clever (I failed a degree in Computer Science ironically) and so  maybe I shouldn't use an OS that really needs expert knowledge.  I mean, looking through examples in udev and it was all code, I can code a little bit, but I have to know what I'm doing :]  and udev just made no sense to me, nor did half the terminology associated with it.  So what I am asking is:

Should I use Ubuntu?  I tried the livecd, but it's hard to tell wether i will get conflicts with things such as alsa and oss (i have no idea how these work together, but a post on the debian lists suggested giving new users the option to blacklist the one they didnt choose during installation).  I read ... a LOT :] .  I've tried to make sense of it all , and get somewhere... the question I'm asking you all  is:  Is Ubuntu going to "do a Debian" on me?

here's my hardware that might cause problems:
SB16 PCI (i used alsaconf to get this working)
Hauppage WinTV (after running alsaconf i did modprobe bttv)
Philips Toucam (just didnt get anything with this in Debian)
          bootlog.d (i set the entry in this =yes but /dev/console couldn't load due to some device error and udev was beyond me)

p.s. are linux nvidia drivers installed during installation?  or do will I need to edit XFree86config and sh nividia.sh ?  Thanks for the help!!

---

### Post by varunus on 2005-08-11
I can answer your questions, I think.  I'm glad you decided to try Ubuntu; you'll find its a very nice distro.  Just hang with it; it shouldn't explode on you.  One thing you'll need to get used to is the fact that there is no root account; everything is done with "sudo" and by typing *your* password.  sudo keeps track of everything you do as root, so you know exactly what you did if your system breaks.  The community is also extremely friendly; I got through my growing pains in a week, and had all my hardware working.  Just don't be afraid to ask for help; you'll find we're nice. :) And no one here will call you a F***ing idiot.

Sound Blaster 16 - Should be autodetected, as I think it uses the snd-ens1371 driver.  This driver is included with Ubuntu.  You should be ok, though I recommend installing the packages libesd-alsa0 and gstreamer-alsa right after you install, and changing your sound server in System->Preferences->Multimedia System Selector to ALSA.  Everything will just sound better if you do.  (OSS is the older sound system for Linux, ALSA is the newer one.)

Hauppauge WinTV - Almost all of these work.  If you have the "Go" or "Theater" models, you'll need to use the bttv or cx88 drivers; these cards are generally autodetected and the drivers are autoloaded.  You shouldn't need to do anything for them to work.  If you have a PVR150, PVR250, PVR350, or PVR500, you'll need to install the ivtv drivers; unfortunately, you have to compile them from source, but there's a step by step guide on how to do this on Ubuntu in this forum.

Phillips Toucam - Because you also have a PVR card, you may have problems with the card...Here's some more info:
[https://wiki.ubuntu.com//HardwareSupportComponentsMultimediaWebCameras](https://wiki.ubuntu.com//HardwareSupportComponentsMultimediaWebCameras)
I think this is the one 

NVIDIA drivers - Very easy to install.  Follow the instructions here to get the proprietary nvidia drivers that come with Hoary.  You can get them graphically from synaptic!
[http://www.ubuntuguide.org/#installnvidiadriver](http://www.ubuntuguide.org/#installnvidiadriver)
If your card is very new, you'll need to follow the howto on how to get the latest ones from the "Hoary Tips and Tricks" section of the forum.

Good luck!  I think you'll like Ubuntu if you stick with it.

---

### Post by ajpr on 2005-08-11
Thanks for the advice, I appreciate it a lot, and it was quite a fast response!!  Just one more thing, can you give me an example of using this sudo?  I find it easiest to learn by examples :]

---

### Post by varunus on 2005-08-11
Ok, a sudo example:

Ubuntu by default, and Linux in general, only lets each user have access to their home directory.  This is the same thing that MacOS does; the rest of the system is hidden from the user, as programs are not installed by using Installers.  Intead, the program "Synaptic" allos for 16,000 programs to be installed.

The example I will use will be that of desktop themes.  Lets say you have two users on a computer, Jack and Jill.  Jill finds a great theme on the internet, and installs it to her themes folder (/home/jill/.themes).  Lets say that Jack sees Jill using this new theme, and he wants to use it too.  Jill says "hey!  Lets put the theme in the universal themes folder!"  Jack and Jill realize that the universal themes folder is in /usr/share/themes, which neither one of them have access to.

In Debian, the way they would get access to this folder would be to open a terminal and:
```
su
(Type root password)
cp /home/jill/.themes/theme /usr/share/themes/theme
exit
``` 

Ubuntu's way would be for either Jack or Jill to type:
```
sudo cp /home/jill/.themes/theme /usr/share/themes/theme
(Enter the USER password, not the root password)
``` 

Because there is no root account, security is increased.  Hackers don't know the username of the administrator...because there is none?

---

### Post by ajpr on 2005-08-11
That sounds good, thanks again for all the help :]

---

### Post by Ptero-4 on 2005-08-11
[QUOTE=ajpr]Thanks for the advice, I appreciate it a lot, and it was quite a fast response!!  Just one more thing, can you give me an example of using this sudo?  I find it easiest to learn by examples :][/QUOTE]
 sudo is used like this
```
[PirateBook:~] Ptero_4$> sudo lspci
```

---

### Post by Trsnrtr on 2005-08-11
[QUOTE=ajpr]
**So today I gave Ubuntu live cd a go, as I heard that that is also good.  I wasn't expecting much, especially as it is based on Debian, yet I was totally surprised that sound was working without me having to mess about with configs and secondly I think it detected my TV card correctly.  Both major plus's, although the webcam thing failed :(**[/QUOTE]

I gave LINUX a try about 5 years ago on a very limited machine and though I liked it, never stuck with it as I had a pretty good WIN machine at the time also.  Lately, I decided to give LINUX a try again and downloaded numerous live cds and a couple full installs.  I tried several and some worked better than others but I wasn't ready to make the permanent leap yet.  By accident, I ran into a guy at my local computer shop who told me to try Ubunto, so I did.

The first 3-5 days were awful.  I had sound on some apps but not others.  My zip drive wouldn't work, my floppy drive kind of worked, etc., etc. etc. It's been a full week now and through this web site, HOWTOs, the wiki site and others, I've managed to get everything going except my scanner which currently doesn't have any avaiable drivers.  No big deal.  

I guess my point is, the info is here if you dig deep enough.  Half the stuff that I've got running was through commands that I gleaned from this website and I don't have a clue what I'm doing.  Regardless, I've got all of my sound now, can play movie DVDs, wav files, read my camera media, write cds and ISOs, print flawlessly and on and on.  I'm pretty happy.   I'll start tackling Windows games pretty soon and I have no doubt that I'll get them running sooner or later.

This is my first post here and I want to thank everyone for the help that they provided to me through this site without even knowing it.  And to the new user, hang in there and keep at it!

-Denny

---

### Post by Gezzer on 2005-08-12
[QUOTE=Trsnrtr]I gave LINUX a try about 5 years ago on a very limited machine and though I liked it, never stuck with it as I had a pretty good WIN machine at the time also.  Lately, I decided to give LINUX a try again and downloaded numerous live cds and a couple full installs.  I tried several and some worked better than others but I wasn't ready to make the permanent leap yet.  By accident, I ran into a guy at my local computer shop who told me to try Ubunto, so I did.

The first 3-5 days were awful.  I had sound on some apps but not others.  My zip drive wouldn't work, my floppy drive kind of worked, etc., etc. etc. It's been a full week now and through this web site, HOWTOs, the wiki site and others, I've managed to get everything going except my scanner which currently doesn't have any avaiable drivers.  No big deal.  

I guess my point is, the info is here if you dig deep enough.  Half the stuff that I've got running was through commands that I gleaned from this website and I don't have a clue what I'm doing.  Regardless, I've got all of my sound now, can play movie DVDs, wav files, read my camera media, write cds and ISOs, print flawlessly and on and on.  I'm pretty happy.   I'll start tackling Windows games pretty soon and I have no doubt that I'll get them running sooner or later.

This is my first post here and I want to thank everyone for the help that they provided to me through this site without even knowing it.  And to the new user, hang in there and keep at it!

-Denny[/QUOTE]


you and anybody else are more then welcome
glad to hear that u read the info on this site
its a gold mine if u r prepared to do a bit of digging ...

---

