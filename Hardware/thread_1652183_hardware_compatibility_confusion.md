---
title: "hardware compatibility confusion"
date: 2010-12-24
forum: Hardware
---

### Post by HappyLinux on 2010-12-24
ok folks, I'll be getting my new computer soon, but I'm still looking for compatibility on the hardware. so far so good apart from a couple of things. I'll be dual-booting Ubuntu 10.10 64bit with Win7 HP 64bit.

1) the motherboard, which will be Asus P7P55 LX. Apparantly there are 2 problems with Linux and this motherboard. It doesn't matter what distro you use as I've seen reports for half a dozen distro forums on this regard.

The 2 problems with this motherboard, is the onboard sound not working or choppy, but can be sorted with a bit of work, so that's no big deal. The main problem is booting up. For some reason, booting Linux with this board is iffy. There's a 50/50 chance that it will boot straight up into Linux, or produce a blank black screen.

Is there a solution to this?

2) nVidia GeForce GTS450. This is the graphics card coming in the system. I don't really know if this card works or not and with what drivers. I'm finding mixed reports on this matter. One page on this forum says that it works fine [http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1584982]("http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1584982"), others say otherwise.

I wouldn't be using Linux for gaming, that's what Win7 is for, so I'd basically need the card to handle basic graphics, and run my Samsung SyncMaster 943 monitor at 1440x900/60Hz.

Would the 260.19.29 drivers from nVidia or through Ubuntu Synaptics or whatever it's called do the job?

---

### Post by cascade9 on 2010-12-24
Not to sure about problem 1, but problem 2 I actually do. 

The GTS450 now does have offical nVidia drivers out for it, and has since october 13th 2010. Its offically supported by the 260.1912 and higher driver versions. 

Ubuntu 10.10 has version 260.1906 in the repositories, the GTS450 shouldnt run with those drivers. 'Shouldnt' doesnt mean 'wont' though, but that would be a bad idea. (it might be possible to run with nvidia drivers earlier than the 260.1912 release, but thats asking for hardware problems). Going though jockey (System->Administration->Hardware Drivers) should guive you a 'no drivers to install' msg or something like that, I forget the exact message you get.  

All the earlier ubuntu versions have earlier nvidia driver versions. So no current (non-beta anyway) ubuntu release has  drivers of a hgih enough version to support a GTS450 'out of the box'. 

I'm guessing that j0nny in the thread you linked has added some PPA to get more current drivers than the versions in the repo.

---

### Post by HappyLinux on 2010-12-24
Good to know that the card will work with more up to date drivers. I just need to install them. Thing is, I'm no good with command line. Because my last attempt to get use to Linux so many years ago failed due to so much hardware incompatibilities, I just gave up. So I never got to learn how to do much with Linux.

So I'm not sure what "PPA" stands for, or what "sudo apt-get install nvidia-current" means. I'm guessing the part "get install nvidia-current" means get and install the most current nvidia drivers, but I don't know what sudo and apt means.

Guess, when I finally get my system and start trying to use Linux again, I'll have to learn it then.

All that's left is the problem with the motherboard and booting into Linux. Any takers?

---

### Post by cascade9 on 2010-12-25
Oh, dear. Looks like you've got abit of a learnign curve ahead of you... 


To start of with, unlike windows, ubuntu and most other linux distros keep a 'repository' (commonly shortened to 'repo') of installable packages of software. That software can be installed by various methods in ubuntu, like synaptic (package manager GUI), ubuntu software centre (package manager GUI), apt (a command line package manager). 

'sudo' is 'substitute user do'. You can think of it as being like UAC in windows. 

'nvidia-current' is the drivers for the latest nvidia cards (old cards use 173.xx, 96.xx or 71.xx drivers) 

So 'sudo apt-get install nvidia-current' does mean what you guesed it means, 'get the nvidia drivers for current cards and install them, using the apt package manager'  

PPA is 'Personal Package Archive', it allows a 3rd party repo to be used, so that software that has not yet (or will not) appear in the ubuntu repos to be installed with the package manager.

---

### Post by HappyLinux on 2010-12-27
You're right, I do have a lot to learn. I'm no techie when it comes to computing as the most I tend to do is repair, upgrade and maintenance work. Basically, if a component dies, then I replace it installing the drivers with it. Upgrading a graphics card, or cleaning out spyware/viruses and defrag etc.

So I don't really do much techie stuff like command line stuff. Heck, I can't remember how to use DOS/Command Prompt in Windows anymore. So basically, if I can't really get anything working through GUI, then it gets difficult for me, but still, I'm willing to learn the basics in command line again, even in Linux.

---

