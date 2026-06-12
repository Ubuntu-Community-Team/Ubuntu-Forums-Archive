---
title: "Hello! I am new and of age to speak with on forumz."
date: 2008-09-23
forum: General Help
---

### Post by JoeEnders on 2008-09-23
Hello to all on these forums here. My name is Joe, and I wanted to stop in and greet everyone with a nice hello. I am pleased to announce that after twenty million years of windows, I have finally decided to dive into a linux os. This is because today windows crashed 4 times all causing complete corruption of everything. I lost all my pani poni :(. And all my phat beats. Anyway, I'm happy to say that this Ubuntu is definitely beautiful and fun to use. I feel like a pro with the whole terminal thing. Really my wife is gonna be like "Oh honey your so good with computers, you're such a nerd, come into the bed room darling would you." So thank you creators of this stuff for probably getting me some lovings. As far as I can tell this is stable and what not, I can't really be sure since I've never used this. I've got just about everything working except for my secondary monitor which is my 37 inch samsung tv. And I seem to be unable to listen to sound in Mozilla/ Flash / Imeem / or myspace music (No I don't have a myspace) So if anyone would be so kind to direct me to some help that is in very lamen terms and whatnot, that would be great. Thanks for any help. And I hope I get to know some of the people on here. Teach me the ways.

---

### Post by Idefix82 on 2008-09-23
Welcome on board :)

So can you hear any sound at all? Is this only a problem with Mozilla?

---

### Post by JoeEnders on 2008-09-23
> **Idefix82 said:**
> Welcome on board :)

So can you hear any sound at all? Is this only a problem with Mozilla?

Yes I can hear all sound , Meaning Music, Music Cd's, system sounds. Just not Mozilla and Flash based players. It's depressing. But still. I'm totally pumped about this Os. Really. Thanks for the warm greeting Btw. I give you pop corms :popcorn:

---

### Post by schibros on 2008-09-23
Welcome on board Joe, i think all you have to do is install the firefox plugins for flash, you can navigate to synaptics and search for flash plugins. Synaptics is one of the package managers in ubuntu, and it comes in very handy. A simple search with synaptics will solve your problem.

---

### Post by triphazard on 2008-09-23
It sounds like the classic flash/pulseaudio issue to me...at least I think that's what it was.  Anyway, I had the same problem and I think this thread ([http://ubuntuforums.org/showthread.php?t=807293]("http://ubuntuforums.org/showthread.php?t=807293")) helped me out.  Take a look and see if it'll fix it for you too.

---

### Post by ad_267 on 2008-09-23
How did you install the flash plugin? If you install ubuntu-restricted-extras package and libflashsupport you should have everything you need. Just uninstall the flash plugin and install these and you should be ok.

For the second monitor setup, what video card do you have?

---

### Post by JoeEnders on 2008-09-23
> **schibros said:**
> Welcome on board Joe, i think all you have to do is install the firefox plugins for flash, you can navigate to synaptics and search for flash plugins. Synaptics is one of the package managers in ubuntu, and it comes in very handy. A simple search with synaptics will solve your problem.

Thanks very much for the info. I did exactly what you said, however, it reported an error then closed the app. The error is as follows 

E: Type '“deb' is not known on line 62 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

Any idea on how to correct this. And thank you triphazard for the link to the thread. I hope it helps.

---

### Post by ad_267 on 2008-09-23
Can you post the contents of that file. You can browse to /etc/apt/sources.list with the file browser or in the terminal enter "cat /etc/apt/sources.list"

---

### Post by JoeEnders on 2008-09-23
> **ad_267 said:**
> Can you post the contents of that file. You can browse to /etc/apt/sources.list with the file browser or in the terminal enter "cat /etc/apt/sources.list"

Oh man I hope I did it right. Theres a lot of stuff here. After putting in that command this is what I got. 

#deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release amd64 (20080702.1)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

# Line commented out by installer because it failed to verify:
#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
# Line commented out by installer because it failed to verify:
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
# Line commented out by installer because it failed to verify:
#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
# Line commented out by installer because it failed to verify:
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
# Line commented out by installer because it failed to verify:
#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
# Line commented out by installer because it failed to verify:
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
“deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main”

---

### Post by triphazard on 2008-09-23
yeah, posting the output of cat /etc/apt/sources.list will help identify that problem.

as for pulseaudio, it might be worth setting your audio preferences to use ALSA instead of pulse in Preferences > Sound (I think...am using Windows at work atm) to stop it happening again.

---

### Post by JoeEnders on 2008-09-23
> **triphazard said:**
> yeah, posting the output of cat /etc/apt/sources.list will help identify that problem.

as for pulseaudio, it might be worth setting your audio preferences to use ALSA instead of pulse in Preferences > Sound (I think...am using Windows at work atm) to stop it happening again.

Yes, the link to the thread helped. I don't however have ALSA selected or pulseaudio. I have my on board sound selected. I also have a PCI card, but I almost had brain bleed trying to figure out how to get it to work. Thanks again though. Enjoy your day at work.

---

### Post by kokkus on 2008-09-23
Hi and welcome to Ubuntu.

OK here are som tips for you before you start use things.

1. You have to enable your graphic driver
System > administrator > Hardware drivers

2. Install the ubuntu-restricted-extras from terminal
sudo apt-get install ubuntu-restricted-extras

3. Recover your lost MP3s and stuff from your formated windows
Go to synatic package manager and search for testdisk. Install it and go to terminal root terminal and type photorec.

And have fun with Ubuntu.
Good luck:)

---

### Post by JoeEnders on 2008-09-23
> **kokkus said:**
> Hi and welcome to Ubuntu.

OK here are som tips for you before you start use things.

1. You have to enable your graphic driver
System > administrator > Hardware drivers

[B]2. Install the ubuntu-restricted-extras from terminal
sudo apt-get install ubuntu-restricted-extras[/B]

[B]3. Recover your lost MP3s and stuff from your formated windows
Go to synatic package manager and search for testdisk. Install it and go to terminal root terminal and type photorec.[/B]

And have fun with Ubuntu.
Good luck:)

Thanks for the tips, once again however, after entering **apt-get install ubuntu-restricted-extras**, I get an error saying:

E: Type '“deb' is not known on line 62 in source list /etc/apt/sources.list
E: The list of sources could not be read.

 As for recovering music, Like I said my computer crashed 4 times or whatever, so all that music is gone. There is a fresh install of Tiny Xp by ExpErience on the HDD, but I haven't set it up yet. Been having to much fun with this Ubuntu.

---

### Post by ad_267 on 2008-09-23
That very last line shouldn't be in the file. It looks like you installed automatix or something and it's messed up your sources.list file.
```
“deb http://www.getautomatix.com/apt edgy main”
```

Press Alt+F2 and run "gksu gedit /etc/apt/sources.list" and then delete that very bottom line and save the file. Then if you run "sudo apt-get update" or click on reload in Synaptic you should be able to install the packages.

---

### Post by JoeEnders on 2008-09-23
> **ad_267 said:**
> That very last line shouldn't be in the file. It looks like you installed automatix or something and it's messed up your sources.list file.
```
“deb http://www.getautomatix.com/apt edgy main”
```

Press Alt+F2 and run "gksu gedit /etc/apt/sources.list" and then delete that very bottom line and save the file. Then if you run "sudo apt-get update" or click on reload in Synaptic you should be able to install the packages.

That fixed it instantly. Thank you very much. That was a great help. Any suggestions on what I should grab from this beast program?

Also, to all who gave me all this help, since Im a newb, I present you with metals, and pop corms. :guitar::popcorn:

---

### Post by ad_267 on 2008-09-24
Well from synaptic it's a good idea to install ubuntu-restricted-extras and libflashsupport. There's heaps of applications available, you can also look in Applications - Add/Remove and see what takes your fancy.

---

### Post by ad_267 on 2008-09-24
Hi you can post questions here rather than sending pm's, most people enable the automatic subscription option for a thread so see when it's updated.

I have a 19 inch and 15 inch dual monitor setup with an nVidia 6600gt so the process should be the same.

First make sure the nvidia drivers are enabled. Go to System - Administration - Hardware Drivers and make sure the nvidia drivers are enabled and in use. Tick the option to use them and restart your computer if they're not already.

Then press Alt-F2 and run "gksu nvidia-settins". If nvidia-settings isn't already installed you can install it from Synaptic. Then enable your second monitor with TwinView and set your resolution and make sure you tick "save to X configuration file".

---

