---
title: "Unable to install graphic driver"
date: 2012-03-29
forum: Hardware
---

### Post by xbobby_bobx on 2012-03-29
Hey guys I'm having a problem with my ATI graphic card.. I have an ATI Radeon x1200 on Ubuntu 11.10 with the latest updates.. The problem is when I used the default driver I faced a massive lag and I couldn't work out anything to make it better and the text was very scrambled so I can't read all the text. The graphic card is not supported anymore by AMD/ATI and the latest driver was for 9.04

I saw a post that said I can install the old driver on the new one using compatibility mode.. I tried it and it installed but the problem is when I reboot and go to Jokey to activate it, it gives me an error in the log says "could not rebound fglrx" can somebody help me to find the proper driver for it?

---

### Post by Yellow Pasque on 2012-03-29
The "proper" driver was already installed to begin with. Trying to install fglrx/Catalyst is the wrong approach.

---

### Post by xbobby_bobx on 2012-03-29
True.. But it's so laggy.. I mean come on on Windows it work just fine, but on Ubuntu it'f painfully slow, and I need Ubuntu for my school work. :/

---

### Post by Yellow Pasque on 2012-03-29
You can try latest drivers with: [https://launchpad.net/~xorg-edgers/+archive/ppa?field.series_filter=oneiric](https://launchpad.net/~xorg-edgers/+archive/ppa?field.series_filter=oneiric)

---

### Post by xbobby_bobx on 2012-03-29
I think I installed them before, actually they were the previous drivers which gave me scetchy texts and laggy menus. But let me try to update the ppa.

---

### Post by xbobby_bobx on 2012-03-29
Nope.. No luck, the resolution is fixed and the effects are working but it's so laggy and scrambled text came back.

---

### Post by mastablasta on 2012-03-30
perhaps you should report a bug.
 
also turn of the special effects see if that helps.
those X1** ones have really poor support in Linux.

---

### Post by xbobby_bobx on 2012-03-30
I am gonna report it, and the effects worked fine on the 10.10 and 11.04, it's not the graphic card it's the drivers that are supported, they are getting worse and worse. I don't blame Canonical though, they don't have time to build drivers for old graphic cards.

---

### Post by Yellow Pasque on 2012-03-30
Have you tried running without KMS? (boot with nomodeset or radeon.modeset=0 )

---

### Post by xbobby_bobx on 2012-03-30
Good idea.. How to do that?

---

### Post by pqwoerituytrueiwoq on 2012-03-30
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)
have you tried like that ?
it worked on my a6-3500 on 11.10 (still has some flickering and window manager reloads but there is no tearing)
just note you are downloading 12.3 that guide uses 12.2 so update the commands for the difference in the file name

---

### Post by xbobby_bobx on 2012-03-30
I believe I can do that.. But I believe I installed these from Synaptic, is it the fglrx optimized package? Because if so, it doesn't work at all, and when I click on the AMD center it fails to run.. I can gice it a shot pqwoerituytrueiwoq.

---

### Post by pqwoerituytrueiwoq on 2012-03-30
since it does some compiling you would think it would be optimized
that was the 1st time i ever had a guide that compiled something actually work for me
it was at least worth a try

---

### Post by xbobby_bobx on 2012-03-30
Aye.. I'm working on it right now, I will let you know in a bit.

---

### Post by xbobby_bobx on 2012-03-30
Negative.. I installed everything according to the instructions, but when I tried to run the AMD centre it failed to start, and the fglrxinfo give me a Badrequest message, which means the driver is not exactly installed and Jokey showing nothing. Any other ideas?

---

### Post by Yellow Pasque on 2012-03-30
> **xbobby_bobx said:**
> Good idea.. How to do that?
First, purge fglrx because it's not going to work no matter how (many times) you install it. Make sure it's all removed: [https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:__Need_to_fully_remove_-fglrx_and_reinstall_-ati_from_scratch](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:__Need_to_fully_remove_-fglrx_and_reinstall_-ati_from_scratch)
Also make sure /etc/X11/xorg.conf is deleted or moved.

Then, edit /etc/default/grub and add radeon.modeset=0 to this line so it looks like:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash radeon.modeset=0"
```

---

### Post by Wootyeah on 2012-04-09
Can anyone say if this has worked?  I am stuck in a similar situation, just trying to get some decent 3D to work for this laptop, open-source or not.

---

### Post by xbobby_bobx on 2012-04-09
I was working on it for a while and nope it doesn't work.. I installed KDE it kinda runs smoother.

---

