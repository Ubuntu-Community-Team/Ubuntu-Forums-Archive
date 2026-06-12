---
title: "iPod Touch says to plug it into to iTunes"
date: 2009-09-10
forum: Hardware
---

### Post by LePow on 2009-09-10
Hi, I just got an iPod Touch and have been trying to turn it on, but whenever I press the home button or the power button, all I can see is an image saying to plug the iPod's USB cable into iTunes. I think they forgot to add a "computer" layer in there, because you can't really plug a device into software, but anyway: where can I install iTunes for Ubuntu? Apple's website doesn't seem to have a link to the Ubuntu version, and I can't see it in the Add/Remove menu.

---

### Post by Sam The Bam 4 on 2009-09-10
> **LePow said:**
> Hi, I just got an iPod Touch and have been trying to turn it on, but whenever I press the home button or the power button, all I can see is an image saying to plug the iPod's USB cable into iTunes. I think they forgot to add a "computer" layer in there, because you can't really plug a device into software, but anyway: how can I install iTunes on Ubuntu? Apple's website doesn't seem to have a link to the Ubuntu version.Hey bud.

Unfortunitly, Apple doesn't make a Ubuntu version of iTunes, it's only for Mac and Windows PC's, but you could possibly try running iTunes(the wndows version) in WINE, thats a program you can get from your Synaptic package manager, and download iTunes and run the .exe file using WINE.

  My sucess with this is rather mute , not a lot works in iTunes, and I dunno if your iPod'll work, worth a try though, or you could just use Rythmbox, or GTKPod that are both compatible with iPod's and will allow you to transfer your music onto it, Not sure about videos though

  There are no doubt other media players/ organisers that allow you to manage you stuff on your iPod,Banshee and Amarok might work too but Apple is in my opinion, very single minded, why they don't make a linux version of iTunes is beyond me, since alot of folk have stuff like iPhones that are very hard to organise without iTunes and since Mac OS-X is UNIX based, as Linux is to a certain degree, they should make a linux version.

  Head to [www.apple.com](www.apple.com), and nag them for one on thier feedback bit of the website, the more linux folk ask, the more likely they'll respond.

Cheers if I was any help to you.
Sam The Bam

---

### Post by estanton on 2009-09-10
Is this your first time running the iPod? I may be incorrect but I believe that it is necessary to let iTunes configure the iPod the first time it boots up.

---

### Post by LePow on 2009-09-10
> **estanton said:**
> Is this your first time running the iPod? I may be incorrect but I believe that it is necessary to let iTunes configure the iPod the first time it boots up.Yes it is, it's just fresh out of the box!
So basically I have to use iTunes but there's no iTunes for Ubuntu? :( Why doesn't Apple make such a version?
I tried installing WINE (funny name by the way) and downloading iTunes 9 for Windows. Then I double-clicked the installer.exe file but the installer crashed. :confused:
WINE did run other Windows programs though! I tried installing Steam and it worked. WINE rocks.

---

### Post by estanton on 2009-09-10
Yeah, if you get iTunes to work within WINE that would be great but personally I'd be a little dubious about whether it would go at all. IMO The quickest option for you would be to simply set up the iPod on a computer running Windows or Mac OSX with iTunes. 
After it's configured you shouldn't have too many problems. However, I have to boot into windows occasionally to use iTunes to wipe and reset my iPod shuffle after rhythmbox manages to scramble it somehow.

---

### Post by Chronon on 2009-09-10
There is some advice here: [https://help.ubuntu.com/community/PortableDevices/iPhone](https://help.ubuntu.com/community/PortableDevices/iPhone)

It looks like you may be able to sync via iTunes running in an XP guest in VirtualBox.

---

### Post by LePow on 2009-09-10
> **estanton said:**
> Yeah, if you get iTunes to work within WINE that would be great but personally I'd be a little dubious about whether it would go at all. IMO The quickest option for you would be to simply set up the iPod on a computer running Windows or Mac OSX with iTunes. 
After it's configured you shouldn't have too many problems. However, I have to boot into windows occasionally to use iTunes to wipe and reset my iPod shuffle after rhythmbox manages to scramble it somehow.I tried it on my brother's computer and it worked fine. I think it's lame for Apple not to provide an Ubuntu version.

Anyway, thanks~

---

### Post by Chronon on 2009-09-10
I just installed iTunes in my guest XP in VirtualBox and it is, in fact syncing music from a shared directory in my Ubuntu home directory as I write this.

One cool feature is that I can drag and drop directories from the shared folder view onto the device without having them added to the iTunes library.

---

