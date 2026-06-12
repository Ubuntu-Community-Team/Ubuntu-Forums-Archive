---
title: "Afraid to upgrade (installed Automatix about a year ago)"
date: 2008-12-15
forum: Installation &amp; Upgrades
---

### Post by supaneko on 2008-12-15
I am looking to upgrade my 7.10 64-bit PC to the latest version of Ubuntu (8.10?). I have installed Automatix and was thinking of uninstalling it to perform the upgrade. Yes, I know this is considered a "no-no" but as much as I know people hate to hear it, it really is extremely convenient for us 64-bit users.

Every upgrade I have done in the past has resulted in extreme failure. Through one way or another the system is just unusuable and I end up having to do a reformat and complete reinstall. I have been hesitant to do any sort of upgrade simply because I do not want to risk losing my entire system. :o

Are there known issues for other users in my situation? Is there anyone out there who was in the same situation as me and successfully performed an upgrade without ANY issue?

---

### Post by abn91c on 2008-12-15
use synaptic to upgrade, read this about Automatix [http://www.desktoplinux.com/news/NS2442396988.html](http://www.desktoplinux.com/news/NS2442396988.html)

---

### Post by supaneko on 2008-12-20
Does this mean I should attempt the upgrade? As I said before, any time that I did an upgrade (through Synaptic), it resulted in some terrible errors. I had blamed the errors on Automatix thanks to the comments of other users.

WELL... I shall attempt the upgrade tonight. I hope all goes well. :)

Thanks for link, my friend. I will be posting back with, what will hopefully, be a successful and joyous post! :D

---

### Post by taurus on 2008-12-20
Just make sure you comment the repos from Automatix by placing a # in front of those lines in /etc/apt/sources.list before you attend to upgrade your machine.

---

### Post by abn91c on 2008-12-20
go to synaptic or add/remove and remove automatix since is no longer maintained or supported then do the sudo apt-get dist-upgrade

---

### Post by supaneko on 2008-12-20
Alrighty... Well, the upgrade is complete and it was a success! :D

I did not uninstall Automatix prior to the upgrade (I didn't see your reply until just now). And when prompted to remove the "unneeded" packages I said no, which I honestly think is why the upgrade was successful. The packages it listed were primarily addons for my MythTV (XMLtv and various plugins) and a few under-used programs that I forogt I had installed (mgetty, specialty xine codecs, Hydrogen, and a few other audio/video utilities). Why does it seem to pick "randomly" programs? What exactly is it that deems a package as unneeded (I don't see how software I have downloaded and installed, even if used very little, should be removed after an upgrade... 'specially since it is working just fine after the fact).

Once again though, thanks for assistance and "push" for me to upgrade. I have been wanting to do it for quite some time but was quite paranoid about what the end result would be. I am very pleased! :) One thing I am curious is what performance changes have been made, if any. I don't know if it's just a mental thing, power of suggestion-like, or what but I feel as if my system is running much better now. With 4gigs of RAM, an over-clocked dual-core, I thought that I was running at maximum performance. NOW I feel like I am running at maximum performance and can't wait for 8.10! :)

**Thanks again!**

EDIT2: WHOA... I did an upgrade from 7.10 to 8.04. *LOL* Looks like I will get to take advantage of 8.10 a little sooner than I planned. Hehehe...! Sorry, folks?!

---

### Post by supaneko on 2008-12-21
Bahhh... I should have sat at 8.04. :(

After upgrading to 8.10, the computer rebooted and after all of the text part of the OS was loaded and it was ready to startx, everything would stop. There would be no display, on any of my three monitors, and no hard drive movement. Rather odd. I thought that perhaps this was part of the upgrade so I let it sit overnight only to come back and see it was still having an issue. WELL... After replacing my xorg.conf (which, for some reason, had a few extra lines that were causing errors, none of these errors which were being shown on the screen since they were essentially "dead") it was resolved.

I finally boot... AND... NO BLUETOOTH. Now, when all you have for a keyboard and mouse is a Bluetooth set for the two, that is a huge pain the a@(*#$. I am rather disgusted, to say the least, that my Bluetooth is not working. I am even more disgusted to see the extreme number of folks complaining that their Bluetooth is no longer working after the upgrade. What the hell...?! It would have been nice if this was posted on the Ubuntu site, you know, in the "Known Issues" area. I really don't know what to do now. It seems that when I go to pair, it either times out or just gives up because I am constantly given the "Pairing with...mouse...failed!" message. :(

WELL... That wiped away my joy and happiness. I knew that upgrading was a bad idea. For all the wonders and joys that Ubuntu has given me and all the things I find that it is better than Windows, its inability to safely and completely upgrade really makes me question its quality and comparison to Windows. I have never had this issue with any other OS... Just Ubuntu. :(

---

### Post by markbuntu on 2008-12-21
If you had looked in these forums before taking the leap to intrepid you would have seen numerous people reporting problems with bluetooth, sound cards, gpus and a whole bunch of other stuff. 

Ubuntu is not Microsoft, we do not have a $billion to make a new os and test it on every single piece of hardware in existence before it gets released. Reported bugs get fixed as best they can between releases but if no one with some particular hardware tries it out and reports a bug, how can anyone know?

All of the work of reporting and fixing bugs depends on community participation and effort. If you want to avoid problems with your particular hardware in the future join the testing/bug reporting program. Install the alphas and betas of the next release and report any bugs you find at Launchpad.

---

