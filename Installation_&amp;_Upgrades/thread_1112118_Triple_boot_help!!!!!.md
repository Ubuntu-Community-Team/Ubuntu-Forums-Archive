---
title: "Triple boot help!!!!!"
date: 2009-03-31
forum: Installation &amp; Upgrades
---

### Post by Gordowmay on 2009-03-31
OK, I'm going to say it I'm a newbie! There that's off my chest.
I'm new to Ubunto and I really don't know scripting and I would like to learn. I need to setup a system that has a triple boot. windows 2000 server, XP pro, and Ubunto 7.1. I would like Ubunto to be the bootloader. Is there a simple way of doing it? Also witch is a better bootloader and easist to work with GRUB or LILO? These are the quetions that I have and I would be very happy if I could get this triple boot to work!

---

### Post by coffeecat on 2009-03-31
> **Gordowmay said:**
> Is there a simple way of doing it?

Yes. Install Ubuntu last! :)

If you make two primary partitions (boot flags set) for your two Windows versions and install them and then Install Ubuntu, the Ubuntu installer will pick up the presence of the two Windows OSs and set up grub with a menu automatically.

Grub is the bootloader that Ubuntu uses by default. I don't know whether it's better than Lilo (depends what you're used to I suspect) but it's the one to go for if only because it is the Ubuntu default.

Before you install post details of the hard-drive(s) you intend to use, how big, how big the Windows partitions are going to be, and someone will post advice on how to get Linux partitions on there as well.

**Edit:** I've just noticed that you refer to Ubuntu 7.10. This is an old version - if support hasn't ceased already it soon will. Go to [the Ubuntu download site](http://www.ubuntu.com/getubuntu/download) and get yourself either 8.04 or 8.10.

---

### Post by dandnsmith on 2009-03-31
I agree with installing Ubuntu last

> **coffeecat said:**
> 
If you make two primary partitions (boot flags set) for your two Windows versions and install them
I think it better to make only one 'active', in order to not get BIOS complaints on booting, and also not to get a problem with Windows.

Install Win2000 before XP.

---

### Post by coffeecat on 2009-03-31
> **dandnsmith said:**
> I think it better to make only one 'active'

I was under the, perhaps mistaken, impression that Windows itself needed the boot flag set in order to be able to boot up. But I bow to superior knowledge here; I don't have the experience of a dual-boot of two version of Windows. Neither am I likely to. I only keep Windows going for two reasons:

1. To keep myself acqainted with the interface for when I help friends.

2. To remind myself why I switched to Linux. :wink:

---

### Post by uidb4056 on 2009-03-31
> **coffeecat said:**
> I was under the, perhaps mistaken, impression that Windows itself needed the boot flag set in order to be able to boot up. But I bow to superior knowledge here; I don't have the experience of a dual-boot of two version of Windows. Neither am I likely to. I only keep Windows going for two reasons:

1. To keep myself acqainted with the interface for when I help friends.

2. To remind myself why I switched to Linux. :wink:

If you don't need to run windows using the real hardware (playing, etc) you can install virtualbox in ubuntu and you can create on it virtual machines for windows or other linux distros. The main advantage is that you don't need to reboot to run these virtual machines, you can have them on a window in ubunto and switch back and forth as you need.

I would recomend to install the verision from sun ( [http://virtualbox.org/wiki/Downloads](http://virtualbox.org/wiki/Downloads)  ) becose the version on repositories doesn't give support for USB.

---

### Post by Gordowmay on 2009-04-01
Thank you all for the help! I'll have to give the advise you all gave me a try. My main concern was what order to install the other OS's. Thank you for clearing that up! The size of the hard drive I'm using is a 500 Gig drive. I was thinking of making the partions at least 150 Gigs each. Again thank you all for the help!:p

---

### Post by dandnsmith on 2009-04-03
> I was under the, perhaps mistaken, impression that Windows itself needed the boot flag set in order to be able to boot up

Yes, Windows needs it, but when you do the second Windows install, the booting is all done via the first, so only one is marked - unless you've gone to the trouble of making the first one hidden before doing the second install (which can give you other problems).

---

### Post by meierfra. on 2009-04-03
```
Yes, Windows needs it,
```
Not quite right.  If you boot Windows via the Grub menu,  Windows does not need  a boot flag.  Indeed, if Grub is your main boot loader,  boot flags play no role whatsoever  (except that some bios refuse to boot  hard drives without an active primary partition)

---

