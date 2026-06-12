---
title: "No sound Compaq Presario CQ62"
date: 2010-10-01
forum: Hardware
---

### Post by Tystick86 on 2010-10-01
I have a dual boot with a Compaq Presario. I have sound from my lap top speakers and head phone jack in windows but only in my head phone jack in Ubuntu. I will be happy to give my output of any consul commands but I am a novice Linux user and have no idea which ones you need.

Thank you to all that help.

---

### Post by mrhhug on 2010-10-01
hmmm  try entering this into terminal ```
alsamixer
``` see if anything is muted especially master

---

### Post by Tystick86 on 2010-10-01
No master is maxed as well as PCM.

Card: HDA ATI SB
Chip: Realtek ID 270

---

### Post by mrhhug on 2010-10-01
have you tried ```
gnome-volume-control
```

dude something is muted somewhere... not sure where but tats how it seems to me

---

### Post by Tystick86 on 2010-10-01
Gnome-volume-control looks good no mutes.

I was thinking it was a driver issue or a Kernal setting because if I plug headphones in it plays and I am not sure but I think a software mute wouldn't do that.

---

### Post by mrhhug on 2010-10-01
under gnome-volume-control check all the tabs:
under hardware make sure you sound card is configured to make noise;
under output make sure that your internal sound card is selected and the proper connector is selected;
under applications check to see if anything is muted there

---

### Post by Tystick86 on 2010-10-01
Thank you for your help all of those things are good though. Under Hardware the card is set up for input and output. Under input and output the internal card is set and when I have an application running that uses sound it shows up is not muted and will produce audio through the head phone jack just not the on bored laptop speakers.

---

### Post by Tystick86 on 2010-10-01
So there have been some developments. I booted into windows then later today booted back into Ubuntu. I have no idea what changed but the sound works now :)

---

### Post by Tystick86 on 2010-10-01
Alright so here is how this is going:

If I am in windows and reboot to windows
I get sound

If I am in windows and reboot to Linux
I get sound

If I am in Linux and reboot to Windows
I get sound

If I am in Linux and reboot to Linux
There is no sound

Any Ideas as to why this happens
Please and thank you

System:
Compaq Presario CQ62
Windows 7 ultimate
Ubuntu 10.4
If you need more info just ask

---

### Post by cbarnardo on 2010-10-23
I have the same problem. If I boot into Windows and then back into Lucid the sound from the builtin speakers works. If I boot straight into Lucid the sound does not work. The sound from the headphone jack always works. There is something muting or disabling the builtin speakers. I have no idea what it could be. Any ideas?

---

### Post by cbarnardo on 2010-10-23
This fixes it [https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules](https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules)

---

### Post by Tystick86 on 2010-10-27
So I recently updated to 10.10 and every thing works now. I did not get a chance to try the fix in the post right above this one I haven't seen the thread in a while. If some one tried that fix please post if it worked in case some one is reading later and wants to stay at 10.4. Thank you for the help. Hope you all have a fantastic Halloween...Peace.

---

### Post by M@x on 2010-11-03
The fix of cbarnardo works! I have a Compaq Presario CQ56 with a dual boot of Windows7 and Ubuntu 10.04. If your speakers are not working but the headphones are, just do the following:

sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
sudo apt-get update
sudo apt-get install linux-alsa-driver-modules-$(uname -r)

restart and it's done! 8)

Thanks a lot cbarnardo!

Cheers :D

---

### Post by CiscoPixie on 2010-12-12
Hi,

I did this: applications->accessories->terminal
then type:  sudo apt-get install linux-backports-modules-alsa-lucid-generic

Make sure backports are enabled in the update manager settings :)

---

### Post by montoyamanuel18 on 2011-03-24
> **M@x said:**
> The fix of cbarnardo works! I have a Compaq Presario CQ56 with a dual boot of Windows7 and Ubuntu 10.04. If your speakers are not working but the headphones are, just do the following:

sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
sudo apt-get update
sudo apt-get install linux-alsa-driver-modules-$(uname -r)

restart and it's done! 8)

Thanks a lot cbarnardo!

Cheers :D 

Hello, I'm new to Ubuntu.. It keeps asking for a password when I do this. and when I try to type anything it won't let me... any suggestions?

---

### Post by Tystick86 on 2011-03-24
There are some comands that can really mess your system up so in linux we log in with a user with lower permissions. This user can gain higher permissions by using the comand sudo. When you start a command with sudo it will ask for a password but for security reasons wont show anything as you type it. Simply enter your user password that you made when installed the system.

By the way welcome to linux. There is a bit of a learning curv but its worth it.

---

### Post by hershey680 on 2011-04-16
Sorry for bringing an old post of of the grave, but was there ever a fix for that?

---

### Post by mrhhug on 2011-04-16
hershey680, 

     you live on cocoa ave? mmm smells soooo good there - at least since ive been there 2 years ago. 


    by the lack of new requests, im guessing that the fix posted by cbarnardo. worked for most. what specific issues are you having?

---

