---
title: "Error on Install"
date: 2009-03-19
forum: Installation &amp; Upgrades
---

### Post by TheSurvivor on 2009-03-19
I downloaded an ISO image of both 8.04, and 8.10 of Ubuntu. I burnt them both to separate disks. My brother took the 8.10 disk and quickly installed it on his laptop. I had used 8.04 recently, and noticed the changes in 8.10 and was excited to get on it as quickly as possible! I installed it, ran it, loved it... Until I got a new video card! I had an old ATI RADEON 9000 Series 64 meg AGP model, and I didn't like it. I went out and bought a nVidia GeForce 5200 FX (512 or 256 meg) PCI model video card. I got it all put together, plugged my computer in, started up, and it failed to boot. My mood now shifted harshly, i placed in the install disk for 8.10. I tried to run a live CD. It got about 10% through loading, and locked up. Same with the install. I disabled GUI and tried it, and just got error after error before locking up once more. I put in Windows XP, and ran that for a while. After having a virus attack, I quickly put 8.04 on my system, but it is not the same at all! I want 8.10 on my computer, but it has to be my video card! It didn't do this until I put it in. Surely, with any hope, I am not the first case of this. Does anyone know what I should do to get 8.10? Any help would be greatly appreciated. Thank you all!

(Computer is a Dell Optiplex GX260 with minor upgrades, including the mentioned graphics card, 640 megabytes of RAM, 40 gig+15 gigabyte Hard drives, DVD/CD-Rom Drive,and an after market fan. Other than that, nothing is changed.)

---

### Post by linux_tech on 2009-03-19
The nvidia 5200 should be compatible, so that should not likely be the issue. But if you are having trouble installing 8,1, then try the alternate cd.

---

### Post by TheSurvivor on 2009-03-19
Well, I tried the alternate CD, and installed it correctly. I followed everything, and then the disk ejected, I removed it, rebooted, and it went through the startup. When it got the "ubuntu" with the orange bar bouncing back and forth, it bounces about 3 times, then begins loading. There are about 20 bars, and it loads 2 and 3/4 bars... And locks up. It gets no-where. The disk has no defects, a fresh burn.

Oh and I just saw this. The number lock is off, but the Caps and Scroll lock lights are blinking simultaneously. It's not rapid-paced, but they are blinking.

Does anyone know what I should do?

EDIT:

At GRUB loading, I pressed ESC and started Ubuntu in recovery Mode. It went through really fast, and I saw it loading things for PCI, and things, but then abruptly, it STOPPED. The last thing I saw was something 
about my AC97 audio.

After the AC97 error, it quickly went to this:
[http://i122.photobucket.com/albums/o280/teddyhorse/image0012.jpg](http://i122.photobucket.com/albums/o280/teddyhorse/image0012.jpg)
After that, the flashing of the keys began. Any help now?

---

### Post by TheSurvivor on 2009-03-19
Just out of theory, seeing how other users were experenceing errors caused by their PCI cards, I took my PCI card out and went with my onboard video. It is only 8 megs. I pressed the power button and crossed my fingers. It got to the point it always locked up at, paused for a moment, and the continued. Now I log into ubuntu, and after the login screen, I get nothing. Along side that, does this mean I'm out a $60-80 graphics card? I know it's not broken, I just used it on windows and Ubuntu 8.04. Can someone please tell me where to go now?

---

### Post by TheSurvivor on 2009-03-20
Well, I fixed my own errors.

For anyone who may get my problem as well:

If you can login and get into a blank screen, restart your computer, and at GRUB, press esc and go to recovery mode. Go for the mode with a root terminal, type these two sentences in:
sudo apt-get remove compiz
sudo apt-get remove compiz-core

Then restart and login like normal.

I for one did this, started up, ran an update, and the reinstalled compiz and now it works fine. I can only wonder if my PCI will work now... I'll edit this to tell if it works or not!

---

### Post by diskord on 2009-06-13
Any luck with this? Did your PCI card start working after you re-installed Compiz?

---

### Post by diskord on 2009-06-13
So I tried this, booted up without the FX5200 plugged in, went in to recovery console and got root prompt. Did the apt-get remove compiz, and neither package was even installed.

Didn't fix my issue at least of kernel panic on boot whenever the FX5200 is plugged in.

This is just ridiculous, I know other people have used the 5200, it has to be something with it in combination of an onboard video card... but what I need to do to fix it is beyond me. Been working on this for over 12 hours, and have made zero progress (or very little).

The one thing I can say is, I believe it is a kernel specific issue, not a distro issue. I tried install Fedora and ran in to the exact same problem, during boot I got a kernel panic and can't go any further.

The really frustrating part, Windows works perfectly... I just don't want to run Windows!

---

