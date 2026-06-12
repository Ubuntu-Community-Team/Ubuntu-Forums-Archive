---
title: "Nvidia 96.xx driver fails in Ubuntu 10.10"
date: 2010-10-15
forum: Hardware
---

### Post by macstevejb on 2010-10-15
It's just a shame that there wasn't any forewarning before upgrading to Ubuntu 10.10 that Xorg 1.9 is not compatible with the nvidia v96.xx legacy driver and therefore broke my upgrade requiring me to revert to Ubuntu 10.04.

There must be so many people using older hardware with this driver for whom Meerkat will not currently work.

I sure hope that a new nvidia legacy driver is available soon.

regards

---

### Post by mikewhatever on 2010-10-15
The bug is indeed unfortunate, but, there was a forewarning.
[https://wiki.ubuntu.com/MaverickMeerkat/ReleaseNotes#Graphics%20and%20Display](https://wiki.ubuntu.com/MaverickMeerkat/ReleaseNotes#Graphics%20and%20Display)
> The new Xorg 1.9 available in Maverick is not compatible with nVidia based chipsets that use the (nvidia-96) and (nvidia-173) drivers. (626974) 
Too bad people never read release notes.

---

### Post by macstevejb on 2010-10-15
Ah ok...duly noted, too late for me..my fault!

Even so, I do think it's pretty bad when Ubuntu extols the virtues of being eminently suitable for older hardware and yet this problem recurs almost at every upgrade or when a new version of Xorg becomes available.

I do appreciate that this is beyond Ubuntu's control and is really down to Nvidia themselves. I have the feeling that sooner or later, they are going to withdraw driver support for these old legacy cards.

Just hope it's not quite yet.

Does anybody know if an upgraded Nvidia v96.xx driver is going to be available anytime soon?

regards

---

### Post by trasgo777 on 2010-10-15
Same problem here.

 Question, my xubuntu 10.10 load to the xfce loging screen and after login, it comes back to the login screem ¿¿¿????

---

### Post by spodesabode on 2010-11-02
Hi Guys,

Just thought I'd chime in on this thread, in case anyone is Googling this topic.

I've got an Nvidia Geforce Ti4600 (4 series) which doesn't get picked up in the restricted drivers. I manually installed nvidia-96 to no avail. 

And of course, this led me here after a bit of hunting, suggesting that X.org 1.9 is the issue (well, nvidia is the issue) and that it looks like we might not see a patch in the near future.

---

### Post by spearson2010 on 2010-11-03
It would appear that a new 96.xx driver was added yesterday.

[ftp://download.nvidia.com/XFree86/Linux-x86/]("ftp://download.nvidia.com/XFree86/Linux-x86/")

Anyone have any luck with it yet?

---

### Post by fluxlizard on 2010-11-04
Stupid thing broke mine too.

So which driver is it and can we expect the restricted drivers app to soon detect our cards and install the appropriate driver?

---

### Post by cascade9 on 2010-11-04
> **spodesabode said:**
> Hi Guys,

Just thought I'd chime in on this thread, in case anyone is Googling this topic.

I've got an Nvidia Geforce Ti4600 (4 series) which doesn't get picked up in the restricted drivers. I manually installed nvidia-96 to no avail. 

And of course, this led me here after a bit of hunting, suggesting that X.org 1.9 is the issue (well, nvidia is the issue) and that it looks like we might not see a patch in the near future.

spodesabode? Same as the website? I remember reading 'jam jar watercooling' years ago. ;)

---

### Post by macstevejb on 2010-11-10
ok it has now been packaged and available in this ppa:

[https://launchpad.net/~dajhorn/+archive/nvidia-96/](https://launchpad.net/~dajhorn/+archive/nvidia-96/)

works great on my old box!
:)

---

### Post by MonsterTrimble on 2010-11-17
I'll second that - added the PPA to my Lucid laptop, upgraded the driver then ran dist-upgrade. Flawless.

---

