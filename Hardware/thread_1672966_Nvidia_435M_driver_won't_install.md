---
title: "Nvidia 435M driver won't install"
date: 2011-01-21
forum: Hardware
---

### Post by Swiftjay on 2011-01-21
I've never had problems on my main computer but installing this graphics card driver seems to be an issue with this laptop.

I just got a Dell XPS 17 and I'm trying to install the graphics card driver.

It's a Nvidia GeForce 435M and I downloaded the .run scrip and went into the terminal and disabled xorg like I would before and installed it but when I went to startx it wouldn't start up it had issues and just refused I had to restore default configurations.

Even trying to install the one that Ubuntu suggested that they made it did the same thing, so right now I'm a bit at a lost.  

Because Ubuntu won't be my main OS to do things it's not a major Issue but with all problems I get slightly peeved that I can't figure out why it doesn't work and I get determined to get it TO work even if it takes a long time...haha.

Has anyone had this problem before and know a work around getting this driver installed?

---

### Post by efflandt on 2011-01-21
There is an x-swat ppa repository that usually has the most recent nvidia drivers for Lucid and Maverick (currently 260.19.29) [http://www.ubuntuupdates.org/ppas/27](http://www.ubuntuupdates.org/ppas/27)

So if you restored your system back to using the nouveau default driver (or Ubuntu nvidia-current), try adding x-swat:

```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
```Then go to System > Administration > Additional Drivers and see if you can "activate" nvidia, then reboot (or if currently using older nvidia-current, remove, activate, and then reboot).

Then check in Synaptic if nvidia-current-modaliases is the then current version or select to update it if not.

---

### Post by cascade9 on 2011-01-22
> **Swiftjay said:**
> I just got a Dell XPS 17 and I'm trying to install the graphics card driver.

It's a Nvidia GeForce 435M and I downloaded the .run scrip and went into the terminal and disabled xorg like I would before and installed it but when I went to startx it wouldn't start up it had issues and just refused I had to restore default configurations.

Even trying to install the one that Ubuntu suggested that they made it did the same thing, so right now I'm a bit at a lost.  

Because Ubuntu won't be my main OS to do things it's not a major Issue but with all problems I get slightly peeved that I can't figure out why it doesn't work and I get determined to get it TO work even if it takes a long time...haha.


XPS17 (new models) have nVidia 'optimus'. nVidia isnt supporting optimus for linux, and if there isnt a BIOS switch to froce the exclusive use of the 435M, installing the nvidia drivers does exactly what happened to you (you lose x totally). 

People are working on optimus drivers for linux, maybe in a year or 3 it will be fixed. Or maybe never.

---

### Post by Swiftjay on 2011-01-22
> **cascade9 said:**
> XPS17 (new models) have nVidia 'optimus'. nVidia isnt supporting optimus for linux, and if there isnt a BIOS switch to froce the exclusive use of the 435M, installing the nvidia drivers does exactly what happened to you (you lose x totally). 

People are working on optimus drivers for linux, maybe in a year or 3 it will be fixed. Or maybe never.



Oh I see, this is a shame, but I guess it's not a major loss, I can still use ubuntu but I just won't be able to do anything major in it but for what I use it for I don't need the graphics card drive installed.  It'll be for working/chatting and windows will be used to do streaming/gaming if I do game.

I do hope maybe some day they will do the driver like you were suggesting that would be great.

Previous person I'll give your thing a try and see what happends who know's maybe that will fix it, i'll post results.

*edit*

No, that didn't fix it still the same situation, oh well I guess I'll have to keep tabs on when this new graphics card is available then.  Thanks everyone closing thread.

---

