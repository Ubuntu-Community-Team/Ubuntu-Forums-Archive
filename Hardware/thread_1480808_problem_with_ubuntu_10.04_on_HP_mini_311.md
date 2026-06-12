---
title: "problem with ubuntu 10.04 on HP mini 311"
date: 2010-05-11
forum: Hardware
---

### Post by flashxipho on 2010-05-11
hi,

I recently bought a HP mini 311 netbook. I replaced its harddrive and installed ubuntu 10.04. Since then, I have encountered some very strange problem with its sound and shutdown/reboot.

At times, when I start the computer, it will have no sound, on the GUI the sound is at max, but no sound is available. This sometimes also happen after after upgrades, hibernate, and toggling the wireless radio button.

Strangely, when the sound is out the device will also refuse to be shutdown. If I shutdown the computer using the GUI, it will simply go back to the log in screen without actually shutting down. If I use "sudo shutdown 0", the computer will hang on the loading screen of the shut down process. I had to force the pc to shutdown by holding the power button down.

usually (probably always) after I force a turn-off then start off again. the sound and shutdown become normal. I wonder if anyone have clues regarding to the cause of this problem.

This the info about the computer:

1) installed ubuntu 10.04LTS RC, later upgraded to formal released version. 2) cat /proc/asound/version == "Advanced Linux Sound Architecture Driver Version 1.0.21." however, when doing 'alsaconf' the version displayed is 1.0.23

any help is appreciated. Thanks

---

### Post by Fir3chi3f on 2010-05-12
> **flashxipho said:**
> 
At times, when I start the computer, it will have no sound, on the GUI the sound is at max, but no sound is available. This sometimes also happen after after upgrades, hibernate, and toggling the wireless radio button.

You sneeze and it stops working :lol:

As to why its happening, I don't have a clue and maybe someone else can help with that. 

My only real input is that maybe some of the old config files are still lurking about from the beta. If it isn't too much of a bother you may just try a clean install.

---

### Post by fetuspuppet on 2010-06-30
Without saying to do this, have you tried

apt-get remove --purge [I]package

[/I]I think that removes and purges the config files, however it is pretty dangerous.

---

### Post by Anton32828 on 2010-06-30
I second the suggestion to do a clean re-install of 10.04.
 
I have an HP 110 (not the same as yours, obviously, but still the same manufacturer) that had strange sound problems under 9.04 and 9.10. Those problems went away wth the installation of 10.04.
 
Good luck.

---

### Post by yahmorah25 on 2010-06-30
you probably got a bad copy of ubuntu 10.04

---

### Post by yahmorah25 on 2010-06-30
is it a cd or usb

---

### Post by jeremz on 2010-07-17
I am having exactly the same issues. I have a fresh install from USB. If anyone has any ideas, please share them. thanks

---

### Post by brendan5211 on 2010-09-07
has anyone heard of a solution to these problems? after updating from 9.10 I don't get sound on my internal speakers. headphones plugged in work fine, but other than that I can't make noise with this thing!

---

### Post by chazg33k on 2010-09-10
Howdy.

Your problems with sound coming out of hibernation, general boot issues, and the wifi button not working as it should sounds a lot like a problem with the ACPI handlers.  You're using 10.04LTS on a netbook?  You might have better luck with Ubuntu Netbook Remix.  It'll most likely have better support for the more-often-than-not weird ACPI handlers used by netbooks.  Way back in the day, this was a common problem with installing Linux on almost any laptop.  The kernel mods just weren't well adapted to the funky APM (used before ACPI came about) handles found in laptops at the time.  Dig around a little more, and you're sure to find something.

Sorry I wasn't much help.

---

### Post by wamefefe on 2010-09-13
For those with a problem with internal speakers and mic check out this post

HP G62-222US Sound on headphones only

by DrJohn999

---

### Post by garvinrick4 on 2010-09-13
If all else fails try Ubuntu netbook, you get both gnome and netbook GUI's When you log out you get option of which one you want to use. Little arrow to click on bottom. 10.04 seems fine with recent install. 10.10 netbook is still flaky to say the least. Give 10.04 a try what can you lose and fix one up the other gets the same packages. 
[http://www.ubuntu.com/netbook](http://www.ubuntu.com/netbook)

---

