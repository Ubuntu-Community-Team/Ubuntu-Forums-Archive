---
title: "Asus 1015PN sound only from headphones, not internal speakers"
date: 2011-05-02
forum: Hardware
---

### Post by telathos on 2011-05-02
I installed a fresh copy of 11.04 i386 on my new Asus Eee 1015PN and the installation went without a hitch, except no sound... I checked to see if the sound was muted or configured to use the HDMI sound. It was unmuted and using the internal stereo speakers... Just for S&Gs I connected a pair of headphones to the headphone jack and to my great surprise... I had sound. 

At this point I'm thinking that the speaker is blown. So I re-install Windows to test with, since it was sound card drivers from Asus. Well I boot-up and have sound flowing beautifully from my speakers. 

Now I'm happy and sad. Happy that the speakers are working, but sad that it has Windows running.

Has anyone ran into an issue like this before??? Thanks

---

### Post by t3dragon on 2011-05-15
I have this exact same problem and cant find an answer anywhere.

---

### Post by Nisitiiapi on 2011-05-18
This just happened to me, too.  It was fine and suddenly, no speaker sound, just headphones.  I've tried different configurations in the sound properties and checked all the volumes in alsamixer, but nothing out of the speakers. Both the intel and nvidia sound cards are found and the intel-hda driver is loaded.  I even tried loading it manually, but no change.  I did just update the BIOS and am wondering if it had something to do with it, though that would be strange.  I may try a boot from liveUSB to see what it does.

EDIT: Reported bug in alsa-base here: [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/784500](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/784500)

There was a similar bug reported under Maverick that noted if you suspend and resume, the sound comes back.  But, I found that just reverses the problem -- sound from speakers, but headphones don't work (sound keeps coming out of speakers).  I tried installing linux-alsa-driver-modules-2.6.38-8-generic, but no help.  Booting from both 11.04 and 10.10 LiveUSBs has the problem.  I was hoping 10.10 didn't have the problem so I could have the option of going back to it.

---

### Post by kakka256 on 2011-05-28
Hi guys,

Any news about this?
I installed 11.04 on my 1015PN yesterday without problems, everything working great, sound through all devices.
Today though i installed vlc, and when playing my first movie i noticed i had no sound via internal speakers.

I'm trying to remember the last thing i did yesterday, something that might have caused this.. I was fiddeling with getting graphic switching (i.e. de/activating ion and 3150) to work, which it was and still is, but i know for sure that i had sound yesterday.  I updated BIOS in default windows install before installing Natty.


EDIT:
Installing the newer alsa drivers, as per the Fixes described here; [https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks#Asus%20Eee%20PC%201015PN](https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks#Asus%20Eee%20PC%201015PN)  fixed my problems.

---

### Post by moresun on 2011-10-24
Hello

I had the same problem
After connecting head phones under windows I got under ubuntu sound only on my head phones and nothing on the speaker.

I went with the solution from [Ubuntu's Hardware Support list]("https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks#Asus_Eee_PC_1015PN")

```
sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
sudo apt-get update
sudo apt-get install linux-alsa-driver-modules-$(uname -r)

alsamixer # to turn up the speaker volume
```


It worked also for my Asus EeePc 1215N with Ubuntu 11.04

Greetings

---

### Post by moresun on 2011-10-27
More details about the new alsa driver can be found on 
[https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules](https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules)

---

