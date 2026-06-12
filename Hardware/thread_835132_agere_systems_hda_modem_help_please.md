---
title: "agere systems hda modem help please"
date: 2008-06-20
forum: Hardware
---

### Post by soumen08 on 2008-06-20
hi,
i have a hp6515b laptop which come with an agere systems hda modem. i have read through the net trying to get it to work under linux. scanmodem,winmodem,linmodem and the lot has left me a bit confused and the modem definitely dosent work on my computer under linux. (It works fine under windows where it has a driver). If the community could help me get this modem to work on linux, i'd be thankful since it is the only component of my laptop which dosent work at the moment under linux.
thx,
Soumen

---

### Post by soumen08 on 2008-06-20
well i need to get online with my modem in linux (i hate having to use windows for just the net). please help someone....
thx,
soumen

---

### Post by Odrodzona-Sarmacja on 2008-06-21
Ubuntu doesn't support hda devices any more. It uses sda devices for hda devices now on account of sda drivers being superior to hda drivers and being able to do the job of hda drivers much better. Maybe Ubuntu automatically will recognize it, if you try setting it up as sda device. So I think at least leaving the "how" up to you and others on this forum.

Good luck!

---

### Post by soumen08 on 2008-06-21
hello,
how do we setup a device as an sda device please?
thx,
soumen

---

### Post by Odrodzona-Sarmacja on 2008-06-21
Imho Ubuntu should configure your IDE modem directly as SATA modem, as it does with harddrives. Maybe however a new SATA driver to Linux for your modem is in order...

---

### Post by lswb on 2008-06-21
The HDA in the name of this modem has nothing to do with hard drives or ide/sata, it is just a model number that agere uses. Trying to get it to work by changing disk driver settings will be a waste of time to say the least!

Google for "agere hda modem linux" or similar and you can find some links that will help you. This is a "soft" modem and apparently may require the slmodemd daemon for linux to be able to use it. Here is a thread that may help you get started: 

[http://linmodems.technion.ac.il/archive-seventh/msg00531.html](http://linmodems.technion.ac.il/archive-seventh/msg00531.html)

---

### Post by whizkid515 on 2008-06-21
This should be similar to the Conexant one, which is also an 'HDA' modem. Dell has drivers for these for their Ubuntu laptops, which work on any computer, including mine! The driver is located [here]("http://ftp.us.dell.com/comm/hsfmodem_7.60.00.06oem_i386.deb")

BTW, Is it even possible to connect a modem to IDE or SATA? Even more so in a laptop???

---

### Post by PCA on 2010-02-01
I have a related problem. I also have the agere systems modem on my laptop HP nx7300. The hardware drivers application that came with my Karmic 64bit detects the modem. BUT the problem is that once I install the softmodem sl-modem-daemon, my sound stops working. I have checked the audio settings, nothing was muted, the volume was high enough.... but no sounds.... what to do?:(

---

### Post by scruffyeagle on 2011-08-03
> **whizkid515 said:**
> This should be similar to the Conexant one, which is also an 'HDA' modem. Dell has drivers for these for their Ubuntu laptops, which work on any computer, including mine! The driver is located [here]("http://ftp.us.dell.com/comm/hsfmodem_7.60.00.06oem_i386.deb")

BTW, Is it even possible to connect a modem to IDE or SATA? Even more so in a laptop???

Update as of 08/02/11: I went to the check the page referenced by the link and got 404 error message.

---

