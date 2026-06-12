---
title: "NVIDIA driver installation problem.."
date: 2017-03-07
forum: Hardware
---

### Post by bchamp on 2017-03-07
I'm using GTX 965m ( ASUS ROG G751 Laptop)
Linux 64 bit

Downloaded this driver.
[http://www.geforce.com/drivers/results/114708](http://www.geforce.com/drivers/results/114708)

After I entered my information.

installed doing
```

sudo apt purge nvidia-*
sudo add-apt-repository ppa:graphics-drivers/ppa
sudo apt update
sudo apt install nvidia-375.
```

After installation I could not get passed sda3_crypt screen, resolution wasn't correct. Definitely not 1920 and couldn't type in my pw as usual. So I booted into recovery..
Changed to Nouveau driver as shown below. I tried all 3 NVIDIA's below, same result as above.
[img]http://i.imgur.com/DSkM37C.png?1[/img]

Seems like Nouveau is the only one working for me...  Not sure why, and would like some insight as to what I may be doing wrong here. Really want nvidia to work...

---

### Post by Bucky Ball on 2017-03-08
Welcome. Not sure why you downloaded any driver. Any reason you thought the NVidia drivers in Additional Drivers prior to this would not work?  

I would remove whatever driver you installed, make sure you have 'Canonical Partners' checked in Software and Updates> Other Software and install 'ubuntu-restricted-extras' (which is in the repositories or you can install via a terminal). Then open a terminal and

```
sudo apt autoremove
sudo apt update
sudo apt full-upgrade
```

(That last command will NOT upgrade your release to a newer one, just the software in your current install to the latest for your release.)

See what's in Additional Drivers now. Is there a 'proprietary, tested' driver there?

---

### Post by Irihapeti on 2017-03-08
*Thread moved to **Hardware**.*

---

### Post by bchamp on 2017-03-08
> **Bucky Ball said:**
> Welcome. Not sure why you downloaded any  driver. Any reason you thought the NVidia drivers in Additional Drivers  prior to this would not work?  

I would remove whatever driver you installed, make sure you have  'Canonical Partners' checked in Software and Updates> Other Software  and install 'ubuntu-restricted-extras' (which is in the repositories or  you can install via a terminal). Then open a terminal and

```
sudo apt autoremove
sudo apt update
sudo apt full-upgrade
```

(That last command will NOT upgrade your release to a newer one, just  the software in your current install to the latest for your release.)

See what's in Additional Drivers now. Is there a 'proprietary, tested' driver there?


No actually, I don't have any idea at all.

Since I didn't mess with the system at all, other than installing several programs I usually use.
Discord, veracrypt, VLC, along with pithos and whatever else. But that was later on and I'm sure has nothing to do with this.

It was the proprietary, tested driver too. 

I also did everything you had said, no proprietary, tested driver. The drivers I had, completely uninstalled. Any other ideas?

I feel like it's the card I have.. considering I see others have a lot of issues too with the same card.

---

### Post by mastablasta on 2017-03-08
does the system also have intel GPU? since it has 4th gen i7 CPU? you didn't post the exact system specifications [SIZE=2][https://ubuntuforums.org/showthread.php?t=1422475](https://ubuntuforums.org/showthread.php?t=1422475)
[/SIZE]
so, you might need this: [SIZE=2][URL="https://wiki.ubuntu.com/Bumblebee"]https://wiki.ubuntu.com/Bumblebee
[/URL]


[/SIZE]

---

### Post by efflandt on 2017-03-08
Did you actually do anything with that .run file your first link pointed to, before adding the ppa and adding nvidia-375? Because if you did run the .run file, that may be conflicting with other drivers and not sure how to uninstall or remove that. 

Try installing it using Additional Drivers now and see if it works. Then go to NVIDIA X-Server Settings and see if you can switch that to Nvidia (might require reboot. Switching Nvidia to Intel just requires logging out of X and back in).

I would not mess with bumblebee. I don't think that has been necessary since 13.10 and it is more complicated to get working with certain games because you need command line parameters. It is also not as fast because it layers Nvidia with Intel for actual display. The newer drivers can separately run Nvidia or Intel and both are faster than using bumblebee (in my experience).

---

### Post by bchamp on 2017-03-08
> **mastablasta said:**
> does the system also have intel GPU? since  it has 4th gen i7 CPU? you didn't post the exact system specifications [SIZE=2][https://ubuntuforums.org/showthread.php?t=1422475](https://ubuntuforums.org/showthread.php?t=1422475)
[/SIZE]
so, you might need this: [SIZE=2][URL="https://wiki.ubuntu.com/Bumblebee"]https://wiki.ubuntu.com/Bumblebee
[/URL]


[/SIZE]

  to update

Tried doing what you mentioned, did not work. Same results as before... 

In fact, I completely reinstalled ubuntu.. I have the proprietary tested driver showing up in addition drivers. Made sure, canonical partners was checked in other software. Applied the driver and rebooted, still nothing. I tried with bumblebee first, same result...

Even tried a different distro(mint), nothing changed here.

> **efflandt said:**
> Did you actually do anything with that .run  file your first link pointed to, before adding the ppa and adding  nvidia-375? Because if you did run the .run file, that may be  conflicting with other drivers and not sure how to uninstall or remove  that. 

Try installing it using Additional Drivers now and see if it works. Then  go to NVIDIA X-Server Settings and see if you can switch that to Nvidia  (might require reboot. Switching Nvidia to Intel just requires logging  out of X and back in).


Oh I have done that. as well.. I'll retry again though, I suppose. Will post results after school.

---

### Post by Bucky Ball on 2017-03-08
> **bchamp said:**
> I tried with bumblebee first, same result...

Perhaps don't try Bumblebee first? That could have made changes you are unaware of and be preventing further progress. Just a stab in the dark ...

---

### Post by bchamp on 2017-03-08
> **Bucky Ball said:**
> Perhaps don't try Bumblebee first? That could have made changes you are unaware of and be preventing further progress. Just a stab in the dark ...

I'm quite annoyed, now.

It didn't work before.. Now nvidia is applied just fine?
I'm pretty sure if I had encrypted the disk as I had done previously, it would not have worked. Since the boot screen looked like it was on a lower res.

But everything else looks normal :)

Also.. I'm pretty sure my problem was having intel-microcode enabled.. I HONESTLY did not pay much attention to that at all. I feel like a dumb ass for all this pain for nothing. But I'm learning so forgive me.

Thank you guys anyways

---

### Post by Bucky Ball on 2017-03-09
The Intel-microcode makes no difference. Not a factor in this wouldn't think. Don't feel dumb. We all started somewhere and we've all made plenty of mistakes (that is how we learn :)). You're doing well to this point and hey, you've managed to install the OS, it is up and running fine and you have only one problem, admittedly an annoying one. 

Also, encrypting the disks can create other issues, not related to video, further down the track so I would avoid, as it seems you are, unless you deem it absolutely necessary.

For what it's worth, have you tried booting with the nomodeset option? Boot the machine and choose the kernel you want to boot, but hit 'e' to edit the kernel line. Look for a line that ends in 'quiet splash'. Add a space after the last of that and then 'nomodeset'. Instructions to save that and boot are at the bottom of the screen. Proceed.

Any luck?

---

### Post by bchamp on 2017-03-09
> **Bucky Ball said:**
> The Intel-microcode makes no difference. Not a factor in this wouldn't think. Don't feel dumb. We all started somewhere and we've all made plenty of mistakes (that is how we learn :)). You're doing well to this point and hey, you've managed to install the OS, it is up and running fine and you have only one problem, admittedly an annoying one. 

Also, encrypting the disks can create other issues, not related to video, further down the track so I would avoid, as it seems you are, unless you deem it absolutely necessary.

For what it's worth, have you tried booting with the nomodeset option? Boot the machine and choose the kernel you want to boot, but hit 'e' to edit the kernel line. Look for a line that ends in 'quiet splash'. Add a space after the last of that and then 'nomodeset'. Instructions to save that and boot are at the bottom of the screen. Proceed.

Any luck?

When it was encrypted I could not get type in the pass for it to unlock. Which is really dumb.

The only thing different I did, from the first time I booted ubuntu. Was disable intel-microcode., whilst having nvidia. Nothing else. Well.. at the same time, then I encrypted my disks during my first set of issues. Since I reinstalled without encryption, I'm fine. So it might have been that all along. Slightly annoying to me, but it'll do. Haha. 

Nvidia is installed, and working fine now, thankfully. No issues anymore!  Linux is a little hard to get used to, but I think it's worth it.

---

### Post by Bucky Ball on 2017-03-09
A beautiful thing. Please see Thread Tools at top right to help others by marking the thread as solved. (Or bottom link in my signature for how.)

> **bchamp said:**
> Linux is a little hard to get used to, but I think it's worth it.

Keep an open mind, [don't expect Linux to be a drop in replacement for Windows]("http://linux.oneandoneis2.org/LNW.htm") and enjoy the learning curve. :) Yes, it is worth it. That's what I thought eight (or is that nine?) years ago. Still with *buntu and still loving it. I remember when I first sat down in front of a Windows machine it was more than a little hard. I still sit down at a Mac and it is hard. In six months time you'll be helping us. :)

Good luck and have fun (and consider your mistakes and these minor hurdles and hiccups as 'learning experiences' rather than a negative thing ... but keep good back ups of your personal data! ;)). It gets easier. Once your machine is stable (as it appears to be) you can just get stuck into learning Ubuntu, at least until the middle of the year.

PS: Just a note. LTS releases are released every two years and are supported for five years (Lubuntu and Xubuntu LTS = three years) and everything else is supported for nine months. 14.04 LTS came out in April 2014 (thus the name) and will go EOL April this year. LTS can upgrade via the net to the next LTS, leap frogging the interim releases between them (14.04 LTS > 16.04 LTS). Interim releases (say 14.10 as an example, even though that's EOL) can only upgrade to the next release, i.e. 14.10 > 15.04 > 15.10 > 16.04 LTS > 18.04 LTS. :)

---

