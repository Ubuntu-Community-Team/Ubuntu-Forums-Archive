---
title: "Display crash after update- need help troubleshooting."
date: 2008-12-16
forum: Hardware
---

### Post by johnlugh on 2008-12-16
Hi, after installing some updates last night and rebooting, my display keeps messing up. I have Ubuntu Intrepid on a Dell XPSM1330 (nvidia graphics). I noticed that some of these were to do with X11...

Most of the time, I can't see my BIOS load screen and only get an empty dark-blue screen. Sometimes I get a black screen which slowly fills up to be striped.

And sometimes (but rarely) my BIOS does load up but it crashes. On these occasions I went into recovery mode and tried the fix XServer option- which allows me to boot into ubuntu normally, but after a short while blue and black stripes crash everything.

From what I can see, the automatic fix option resets my xorg.conf file- so there could be some incompatibility with my customised file from before the update. But even after the 'fix', it still doesn't work right? 

Btw, when I do manage to choose to boot normally, after a certain point the text goes all skewed and the characters become 'strange' :P (I haven't got splash boot). 

Help would be really appreciated, I'm finding it hard to troubleshoot when I can't get access to my files easily and I'm no expert.

---

### Post by zedx555 on 2008-12-16
You can't see your BIOS screen might mean something has gone wrong with your hardware. By what I know, your OS should not edit your BIOS. Perhaps something might have gone wrong with your GPU or CPU. You might want to check their temps if you can. I remember such things were happening when I tried to overclock my computer once.

---

### Post by johnlugh on 2008-12-16
I'm not sure if you misunderstood me. I don't see the BIOS loading screen most of the time, but I'm pretty sure it's loading. Think it's all an issue with the display settings, but I can't figure out what.

Is there a way of accessing my files/terminal without the display working?

---

### Post by CoolHand on 2008-12-16
I can't add hard facts to your post but the latest updates have broken my desktop as well and it seems X related.  I thing the libx11 updates are broken.  Just my opinion but I doubt we are the only ones with issues.

PS...try hitting ctrl-alt and one of the F# keys like F2.  It should give you a terminal.

---

### Post by johnlugh on 2008-12-16
Ok, I can't seem to see anything on the screen now other than a blank screen which fills up with stripes.

I can't see the bios loading, grub options or anything but it sounds to me like ubuntu is loading properly. 

When should I be trying to bring up a terminal with ctrl+alt+f? So far it hasn't done anything and because I can't see anything typing random things is probably not a good idea. 

Is this a hardware problem? Seems too coincidental with the update timing, but for some reason the display is getting worse (now I don't see anything other than stripes...) Anyone else experiencing similar symptoms?

---

### Post by CoolHand on 2008-12-16
It sounds like X isn't even starting for you thus you can't switch to a term.  You can try to crash X with ctrl-alt-backspace.  Asside from that if you have your install CD drop that in.  You can boot with that and then mount the real drive and edit files that way.  I would turn off X all together.  Reboot and in the terminal do what I did...downgrade X to the previous version.  I did that this way:

On my good box I ran to find out the version numbers:
dpkg -l | grep libx11
Version was 2:1.1.5-2ubuntu1

On broken box I ran:
sudo apt-get install libx11-6=2:1.1.5-2ubuntu1
sudo apt-get install libx11-data=2:1.1.5-2ubuntu1
sudo apt-get install libx11-xcb1=2:1.1.5-2ubuntu1

If that doesn't work you may be back to the drawing board.

---

### Post by johnlugh on 2008-12-16
I'm afraid I still can't get anything up and running. All I see is the same stripey pattern on the screen- it's so annoying. 

The live disc was loading but the screen stayed the same...unless I've somehow messed the screen up I'm clueless as to how to continue trying to solve this. 

I've only caught a flicker of the BIOS load screen, but this has only happened once and there were still stripes running down the screen. 

Could an update have done this much damage? I would think that at least the boot screen would be displayed but it's not looking good atm.

Any ideas would be brilliant.

---

### Post by johnlugh on 2008-12-16
hmm.. for some reason everything started working? :P

i managed to get into a terminal and checked my libx11 but it was the same as your working one. did a filecheck and then everything booted normally.. very strange. 

only problem is now my suspend is broken- i get a blank screen but I think that's more easily fixable and is a known issue with this laptop. 

thanks for the help, fingers crossed I won't need any more.

---

### Post by johnlugh on 2008-12-16
I'm afraid the problem still persists. After a while the screen becomes kinda tinged with blue for some reason and then hangs. 

I could provide some info about my xorg.conf files before the update and my current one if necessary. Currently I can't even view them unfortunately. I think that after trying the recovery fix, the current one is very basic- under display there isn't anything specific about nvidia or drivers like my old one. Would this be the problem? Unfortunately, I can't access these files atm.

Any help would be awesome as it's really worrying me as I need to use this laptop for work.

---

