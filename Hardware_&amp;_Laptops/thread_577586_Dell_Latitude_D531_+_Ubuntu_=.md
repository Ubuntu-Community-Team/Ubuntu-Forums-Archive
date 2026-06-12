---
title: "Dell Latitude D531 + Ubuntu = ???"
date: 2007-10-16
forum: Hardware &amp; Laptops
---

### Post by shayke on 2007-10-16
Hi
I want to buy this laptop because it has exactly what I want and need, but I read in some places that it has many problems with Ubuntu installation, and especially with the ATI Radeon X1270 graphic card.
Now, I can't and I won't to leave Ubuntu for any laptop, so I would be glad to know if this laptop has full Ubuntu support before buying it, and if there is special pages on that model and Ubuntu? 
Is Gutsy going to have full support for this laptop? I will appreciate very much any information you can give me :)

---

### Post by shayke on 2007-10-25
Hi
I still would be glad to know if any of you have some experience with Ubuntu installed on d531, especially  after Gutsy is out there for about a week :)
Thanks!

---

### Post by hotani on 2007-10-29
Don't even try it. Find another laptop. The live CD will NOT BOOT. You could probably get gutsy installed with the alternate CD, but then you will be plagued with wireless driver, display and sound issues.

My old D600 works great however. Your best bet is to go online to dell's site and order one of their laptops with ubuntu pre-installed. Then you'll know for certain everything works.

---

### Post by filcap on 2007-11-04
Hi!
I'm currently running Ubuntu 7.10 on a Dell Latitude D531.
I didn't meet any problem in booting with the live cd.
However I'm experiencing problems with the sound card: actually I currently have no sound. This is a regression in comparison with the previous version (7.04), since the sound worked like a charm with Feisty. I have been trying for a week to fix this problem (recompile alsa, modify alsa-base,...) but no chance...
Moreover I had to use ndiswrapper in order to get the wireless card working.
   Bye!

---

### Post by konungursvia on 2007-11-05
There is a simple solution, to install one backport package for sound. I did it yesterday. I'll find the package and let you know again here.

---

### Post by konungursvia on 2007-11-05
Try installing this and then reboot:

sudo apt-get install linux-backports-modules-generic

---

### Post by konungursvia on 2007-11-05
Sorry for the multiple posts. I installed that backport, and fixed sound, but as for graphics, saw there was no compositing. Installed a glx package and now have emerald and compiz compositing. But I keep losing the mount on my external usb ntfs hard drives, after about 5 to 10 minutes of operation. Any ideas?

---

### Post by konungursvia on 2007-11-05
> **hotani said:**
> Don't even try it. Find another laptop. The live CD will NOT BOOT. You could probably get gutsy installed with the alternate CD, but then you will be plagued with wireless driver, display and sound issues.

My old D600 works great however. Your best bet is to go online to dell's site and order one of their laptops with ubuntu pre-installed. Then you'll know for certain everything works.

This post, if once true, is now dated. I bought a D531 over the web from Delll with xp and assumed I could easily install gutsy. I did, and virtually everything is working fine. Given that whenever I have installed debian, dapper, feisty and gutsy on laptops, I've had some tweaking to do, this one is has been the EASIEST. I had to download a backported alsa package (3 min) to get sound going, and had to download a similar glx package (8 min) to get compositing and compiz working nicely. Now, I'm just doing minor tweaks and fixes. 

The issue that persists, a minor one, is that volume seems to increase slowly as time goes on. I'm looking into that one. So far, I'm loving this new machine, both in linux and xp (which I use for Adobe Acrobat Professional, WordPerfect, World of Warcraft, Photoshop).

---

### Post by cos4 on 2007-11-19
I've also got that volume problem. Has anyone found a solution to that?

Another thing that strikes me is connected with alsa. When I have a look(sys config manager KDE) at the modules which are started I find the info that alsa-utils is not running. When I click on start the popup windows states that it is started but the menu entry is still on "not started". 
Is alsa used? If yes why aren't the alsa-utils started or put differently can anyone explain this weird behaviour or experience the same? Just to have that clear - the sound is working.

Edit:The volume problem seems to be connected to the volume regulation(maybe also to the key binding of the laptop). I do not always experience this problem, mostly though in connection with using the key bindings(at least it seems as if thats the problem right now).

---

### Post by larseko on 2007-12-10
I recently bought one of these for the school I work for. Things came up not great, but OK at first. Ubuntu asked if it should install nonfree drivers for the graphics card and the wireless (I think, at least it was Broadcom), but there are some problems:

- no sound, as stated. Could not find the backport mentioned, but haven't been looking much yet.
- the console is garbled, I can log in (I think), but mostly no proper charset present
- when doing the first big update, it stopped during the configuring of cups. I had to restart it, and now the gnome session for the admin account won't load. When logging in the arrow on the background just stays put.
- again, a bit hard to troubleshoot when the console doesn't work ;)

I thought I'd kind of log this in this post for the D531. If anyone has suggestions, I'm grateful. I will also post my finds here, though.

---

### Post by tinman6700 on 2007-12-10
I am having a similar problem starting gnome on a latitude c600 with an ati rage mobility video card. The driver that loads automatically won't let me go past 800x600, and when I change drivers gnome wont run. Does anyone know how to fix this, or even get back to the original settings

---

### Post by larseko on 2008-01-03
So I've got several PCs up and running with 7.10, and thought I was ready for final deployment. I had sound, wireless etc. working. Or so I thought, until I tried wireless from a bit of a distance (a couple of rooms away from a perfectly working, non-cheap, 3com router). Wireless is extremely unstable, and I can't get it to connect at all if it's not less than about 15m from the router. Where there were no problems whatsoever with the old D505PCs  with Ubuntu 6.06, I cannot connect at all with these computers (there are 8 of them). The one of the PCs which has XP installed, shows none of these symptoms, so I am guessing this is driver related.

Has anyone experienced a similar problem running Ubuntu 7.10 with a Broadcom 4311? I'd appreciate any input, as this is a major show stopper for me.

---

### Post by larseko on 2008-01-04
Actually, when installing ndiswrapper and friends according to the broadcom no-fluff guide here, the network works much better. It still shows weak signal strength, yeah, even weaker than before, but it just isn't a problem anymore. The network also seems stable.

Just do a search for "broadcom no-fluff", and you will get the guide I'm talking about. Choose option 2b.

---

### Post by Worp8d on 2008-03-05
I have the same version of Ubuntu, 7.10, and the same Broadcom chipset.  I followed the no-fluff guide but option 2b didn't work for me.  I did it all again with option 2a and now I have the same situation, somewhat weak signal strength but it seems to work.

On a different note, I have installed linux-backports-modules-generic but sound still does not work.  Does anyone have any other ideas?

---

### Post by segalerez on 2008-03-24
> **cos4 said:**
> I've also got that volume problem. Has anyone found a solution to that?
So do I...

---

### Post by ds3 on 2008-03-28
With regards to the volume, try updating ALSA to 1.0.16 instead of using the backport.
Instructions on how to do this are at:
[http://www.linlap.com/wiki/Configuring+the+audio+and+updating+ALSA+for+Ubuntu+7.10](http://www.linlap.com/wiki/Configuring+the+audio+and+updating+ALSA+for+Ubuntu+7.10)
The only thing I did before starting the procedure listed there was to stop the current ALSA version using: 
sudo /etc/init.d/alsa-utils stop
I haven't noticed the volume problem, but then I've only had the machine a few days and haven't tested it extensively.

---

### Post by hotani on 2008-04-02
Good News Everyone!

I just popped an 8.04 Beta Live CD into a D531 and it booted like a champ. I played a couple of vid and sound files from the examples folder and there is sound!

Here's a breakdown of functionality (keep in mind this is pre-updates. According to update manager there are about 350 to install):
**Video**: works, but no 3D - for that you would still need to use the fglrx driver
**Wireless**: Unfortunately wireless does not seem to be working. I'm not seeing any of my local networks
**Suspend**: Works!

EDIT:
- Wireless works after enabling b43-fwcutter and bcm43xx-fwcutter, then rebooting. The proprietary driver config app is broken, otherwise that would be the place to enable this. 
- Desktop effects work after enabling the fglrx driver

So that is it. Hardy is the version for this laptop!

---

