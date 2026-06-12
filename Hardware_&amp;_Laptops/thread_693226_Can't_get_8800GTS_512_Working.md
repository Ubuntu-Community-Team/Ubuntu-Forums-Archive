---
title: "Can't get 8800GTS 512 Working"
date: 2008-02-10
forum: Hardware &amp; Laptops
---

### Post by Wesgoood on 2008-02-10
Hi, a little new to Ubuntu and Linux for that matter. I know there is a lot of these threads. I've followed a lot of instructions but could never get 169.09 installed correctly. 

Now when I log in to ubuntu...I get 3 split grainy screens...this is the second time this has happened from a second fresh installation and it's getting rather annoying. I would just like some help on this because, I really would like to use Ubuntu bu jeez..its just been very very frustrating as of now.

My Specs are.

Q6600
8800GTS 512
780i
4gb ddr2

---

### Post by pondochris on 2008-02-10
I have the same card and I got it working by using envy. I tried the .deb to no avail so I googled envy, installed it and it found the drivers and installed flawlessly.  After about a week I found the fan terribly loud (it was stuck at 100%). I installed nvclock from source and that fixed it.  With nvclock you can overclock and adjust the fan easily.  I hope this helps.

---

### Post by Wesgoood on 2008-02-10
Yep that seemed to do the trick, just now my sound isnt working for some reason. I am getting the following error when going to volume control, "No volume control GStreamer plugins and/or devices found". Which is strange since well, it worked before.

---

### Post by pondochris on 2008-02-11
Hmm I can't quite remember the command but I think it might be alsaconfig. You may need to uninstall then reinstall your audio drivers through synaptic. First though, did you restart your pc? Just after I installed the nvidia drivers, I had issues with sound and couldn't get the correct resolution. After reboot all was well.

If you still can't get it let me know and I'll be home by then and will be able to take a look through my notes...that's one thing I have learned is to take good notes every time I overcome an obstacle in linux.

---

### Post by Wesgoood on 2008-02-11
Yeh I rebooted my PC, thats when I think it started. Also yeh max res i can get is about 1024x768, when I should be able to get 1440x900. Sound is really the main thing I need though.

---

### Post by pondochris on 2008-02-11
ahh looking through my notes, what I ended up having to do is download the current source code for alsa and compile it.I got it here :[http://www.icewalkers.com/Linux/Software/56600/ALSA-driver.html](http://www.icewalkers.com/Linux/Software/56600/ALSA-driver.html) .

also for the screen resolution run this command to reconfiigure your xserver to better take advantage of the nvidia driver by running this.  

> sudo dpkg-reconfigure -phigh xserver-xorg

this should get ya back to 100%

---

### Post by swazidoughman on 2008-02-11
the G92 512MB version of the GTS is only officially supported by 169.25  & up

thats too bad though :[  you are totally missing out on some
tux racer at 2560x1600 :guitar:

---

### Post by pondochris on 2008-02-12
> **swazidoughman said:**
> the G92 512MB version of the GTS is only officially supported by 169.25  & up

thats too bad though :[  you are totally missing out on some
tux racer at 2560x1600 :guitar:

all of the 8800 cards are on the g92 core dude.

did ya get it working wesgood?

---

### Post by fogcat on 2008-02-12
Just a silly thought:  after starting up w/the new card...is your monitor correctly identified?:confused:

I have had a similar problem even with an older G6200 (same problem) but fixed it w/a properly identified monitor...

Just a thought.

Dan Mac

---

### Post by patrickfromspain on 2008-02-12
> **pondochris said:**
> all of the 8800 cards are on the g92 core dude.

did ya get it working wesgood?
I'm afraid that's not true... older 8800 were based on the G80

---

### Post by pondochris on 2008-02-12
> **patrickfromspain said:**
> I'm afraid that's not true... older 8800 were based on the G80

I guess ya got me there.  Shame on me for not taking a quick peek first! Whoopsie!

---

### Post by mohbana on 2008-02-16
has anyone managed to get the restricted drivers manager to detect the 8800 gts without having to install anything (envy or the official nvidia drivers.  Currently i am getting the "your hardware does not need any restricted drivers"!

thanks

---

### Post by Wesgoood on 2008-02-21
Sorry for not responding in forever on this subject but yes, all of the instructions did work. I'm rockin out with my res at max and sound workin. Thank you much for the help. 

Be nice if we could get this temporarily stickied. ...although this is the first thread that pops up on google when you type "Install 8800GTS drivers for 7.04".

---

