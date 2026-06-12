---
title: "Acer Aspire One - Microphone/Skype"
date: 2009-12-24
forum: Hardware
---

### Post by tconrad on 2009-12-24
For other's, I'm including what worked for me to get the microphone working on the Aspire One (D250).   This is from other info on the web, but putting together in one place.

As reported for the Aspire One, even in Ubuntu 9.10, the microphone did not work right out of the box (everything else did).   This is already reported.

The user needs to get the also 1.0.20 version of the alsa driver (the synaptic manager may already show that you have version 1.0.20).   But it needs compiled with a non-default option.

I followed these specific directions from elsewhere  and it worked nicely (except for a couple missing sudo)


# See this site:  [http://www.linuxquestions.org/questions/linux-laptop-and-netbook-25/mic-issue-with-acer-aspire-one-10-in-ubuntu-unr-729158/](http://www.linuxquestions.org/questions/linux-laptop-and-netbook-25/mic-issue-with-acer-aspire-one-10-in-ubuntu-unr-729158/)

wget [ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.20.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.20.tar.bz2)

tar xjvf alsa-driver-1.0.20.tar.bz2
cd alsa-driver-1.0.20

sudo apt-get install build-essential module-assistant
sudo m-a update
sudo m-a prepare

./configure --with-cards=all
make
sudo make install 

Restart.   Go to System/Preferences/Sound.   Plug in a headset microphone into the front microphone jack (pink one).   Go to Input tab and select "Microphone 2" from the connector.   You should see bars move on the input level (I didn't try the built in mic, but possibly that's Microphone 1".  With that, skype worked perfect.  The video quality was even better than my other PC with external logitech video cam.

I hope this helps folks...

Tim

---

