---
title: "Can't see top or bottom menu bars"
date: 2009-01-21
forum: Installation &amp; Upgrades
---

### Post by madhatter84gn on 2009-01-21
I just recently upgraded to Jaunty Alpha3 hoping to work on a few things and after the upgrade I can't seem to see either menu bar. I am using ATI HD 3650 and I know I need to enable specific drivers, but I can't manage to see the system menu or the preference menu. 2 questions, is there a way to fire up the menu or settings from the console so I can use proprietary video drivers, or is there another way to get the ATI card working properly? I believe it is the card that is causing the problems because I lost all of the affects and it seems to boot into low graphics mode even after trying the fixX option on the recovery menu.

Thanks in advance.

---

### Post by Axdrenalin on 2009-01-21
I've seen the same thing here. Yesterday, I updated a test box that was running 8.10 (64 bit version) with the "update-manager -d" command, and while everything seemed on the surface to go well, upon reboot there were no bars top or bottom. I was using an NVidia 7300 here and I *did* remove the obsolete files before rebooting.

Since that happened, I downloaded the 9.04 64 bit ISO and did a fresh install using EXT4. When it rebooted the first time after installation, everything was great on the desktop. I downloaded and installed the remaining updates, then rebooted, and once again was missing the top and bottom bars. I just reinstalled 64 bit 8.10 after that happened.

I have another machine here at work I'm testing with, and updated it using the command line update. I did *not* remove the obsolete files, and it came up normally. I'm getting ready to update anything left on it, and will see what it looks like after that reboot.

EDIT: [COLOR="Red"]The 32 bit version I'm running on an older PC at works seems to do just fine. Retrieved all the updates and rebooted, and it came back with both bars intact.[/COLOR]

Does anyone have any idea what is causing the top and bottom bars to go MIA like this yet???

---

### Post by antti64 on 2009-02-05
Hi!

I'm facing same problem. I put Ubuntu 8.10 as a persistent installation to USB-stick. First time everything went fine. After reboot I lost top and bottom menu bars. I can't see any shortcuts, plain wallpaper is shown. 

Where to start digging the problem?

Antti

---

### Post by antti64 on 2009-02-06
Hi!

I managed to return top and bottom panels, but still some problems.

I removed ubuntu-desktop and gnome-session and then reinstalled them.
```

dpkg -r ubuntu-desktop
dpkg -r gnome-session

apt-get install gnome-session
apt-get install ubuntu-desktop
```

Well, top and bottom panels are back, but windowing is not properly working. All application windows are missing top-bar (title) and them
cannot be moved. I have errors relating to metacity in system log. 
I tried to remove and re-install metacity, but not possible....

Antti

---

### Post by antti64 on 2009-02-10
Hi!

I wasn't able to fix this. The problem seemed to be in metacity packet. At least I received crash reports every time when I booted. 

I removed 8.10 completely and re-installed it again. This time I'm using Xorg display drivers. Last time I used nvidia-177 drivers. This time I didn't install them. 

Antti

---

### Post by samwisekoi on 2009-08-17
> **antti64 said:**
> Hi!

I managed to return top and bottom panels, but still some problems.

I removed ubuntu-desktop and gnome-session and then reinstalled them.
```

dpkg -r ubuntu-desktop
dpkg -r gnome-session

apt-get install gnome-session
apt-get install ubuntu-desktop
```Well, top and bottom panels are back, but windowing is not properly working. All application windows are missing top-bar (title) and them
cannot be moved. I have errors relating to metacity in system log. 
I tried to remove and re-install metacity, but not possible....

Antti

This happened to me while/after attempting to purge pulseaudio so I could stick with alsa.  <sigh>

I will now see if the above works for me as well.  (Jaunty amd_64)

 - Sam

---

### Post by samwisekoi on 2009-08-17
> **samwisekoi said:**
> This happened to me while/after attempting to purge pulseaudio so I could stick with alsa.  <sigh>

I will now see if the above works for me as well.  (Jaunty amd_64)

 - Sam

Well, apt-get remove ubuntu-desktop told me it wasn't even there.  I ran the above four commands and all is well again.

<whew>

 - Sam

---

### Post by wacole on 2009-08-20
Just hit this problem on 8.04LTS. Tried the four line fix, but, sadly, it did not work.  Considering [ugh] a reinstall, but was hoping that someone may have hit on an easier fix ... thank you very much for any guidance that is offered.

---

