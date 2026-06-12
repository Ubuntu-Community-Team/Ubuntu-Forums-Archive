---
title: "Headphone jack not working"
date: 2006-08-11
forum: Hardware &amp; Laptops
---

### Post by fieldstone on 2006-08-11
I've been having some trouble enabling my headphone output on my new Compaq V3010US laptop. I know the audio chipset is some type of nForce controller, but beyond that I haven't found much about how to fix the problem.

Anyone have any ideas?

---

### Post by drunken-wallaby on 2006-09-17
same here too. I've installed dapper on a hp dv9043ea and got exactly the same problem. When I plug a headphone in, the speakers are not muted. Using alsamixer (as suggested in different topics here) doesn't solve the problem, because I can't set "headphone jack" or something like this.

Anyone?

---

### Post by fieldstone on 2006-09-17
> **drunken-wallaby said:**
> same here too. I've installed dapper on a hp dv9043ea and got exactly the same problem. When I plug a headphone in, the speakers are not muted. Using alsamixer (as suggested in different topics here) doesn't solve the problem, because I can't set "headphone jack" or something like this.

Anyone?

Someone emailed me the solution, which can be found at:

[https://bugtrack.alsa-project.org/alsa-bug/view.php?id=2412](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=2412)


Basically, you have to install ALSA from the source (get the alsa-driver, alsa-libs, and alsa-utils packages, and install them in that order), patch it, and install it. You can find the source at [http://www.alsa-project.org](http://www.alsa-project.org) (right there in the upper right hand corner of the main page).

Before you install alsa-driver, you'll also have to apply the patch from that link to the file hda_generic.c, which is in the alsa-kernel/pci/hda/ directory inside the extracted alsa-drivers directory (wherever you extract it.

After I did this, I had a separate volume control for my headphone jack, and it worked perfectly. (Installing the alsa-oss and alsa-lib-plugins packages from the ALSA site might also help you with the stability of your sound, but it's not strictly necessary and might also break things, depending on your system.)

---

### Post by drunken-wallaby on 2006-09-19
hi fieldstone.

thx for the quick answer. this sounds like quite a bit of work :)

bernhard

---

### Post by drunken-wallaby on 2006-09-21
Just an update. I miserably failed compiling alsa and applying the patch.

Anyway, I decided to upgrade to edgy if the problem persists. At first, I thought that nothing had changed. I manually muted the master and pci and plugged the headphone into the jack and it basically works. That means I do hear sound through the headphone, but **very, very silently**. Basically, you have to have very good ears.

Question: Any suggestions on how to increase the volume? Both master and pcm are at 100% by the way...

---

### Post by fieldstone on 2006-09-21
> **drunken-wallaby said:**
> Just an update. I miserably failed compiling alsa and applying the patch.

Anyway, I decided to upgrade to edgy if the problem persists. At first, I thought that nothing had changed. I manually muted the master and pci and plugged the headphone into the jack and it basically works. That means I do hear sound through the headphone, but **very, very silently**. Basically, you have to have very good ears.

Question: Any suggestions on how to increase the volume? Both master and pcm are at 100% by the way...

Maybe someone else can give you advice on Edgy, but I already tried upgrading to it and found it pretty buggy at this point. Also, the version of ALSA in it is only 1.0.11, which I don't think is even high enough to be able to support the necessary patch.

If you want to try patching and installing ALSA 1.0.12 again, I can try to walk you through it, preferably via some instant messenger service (I use AIM, Yahoo, and Google Talk, so take your pick). Otherwise, I'm out of ideas, though.

---

### Post by drunken-wallaby on 2006-09-22
Hi fieldstone.

Could you please drop me a pm on how I can contact you via msn, icq or (preferably) jabber.

Bernhard

---

