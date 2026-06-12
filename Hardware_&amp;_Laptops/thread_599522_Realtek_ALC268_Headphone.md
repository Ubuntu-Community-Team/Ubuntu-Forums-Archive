---
title: "Realtek ALC268 Headphone"
date: 2007-11-01
forum: Hardware &amp; Laptops
---

### Post by Scypher on 2007-11-01
I menaged to get the card working and I can change all the volumes of input/headphones/built-in speakers of my laptop the the sound setting (alsamixer) but I have one big problem.

I cant menage to get sound in my headphones when I plug them in, It's like the computer dosent even know they are there...

---

### Post by warbread on 2007-11-07
Bumbxxor.

I have the same problem.  More specifically, when I change system volume, sound reverts back to the speakers but continues to go through the headphones.  I have to unplug then plug the headphones back in at whatever volume level I desire and then not change it unless I'm ready for music to come blaring out of my speakers.  A little embarrassing in the middle of the commons area.  

Ubuntu 7.10 (Real time kernel) recognizes the sound card just fine, and this is a new problem since about a week ago, maybe longer.  I thought it had something to do with me screwing with USB headphones, but now I'm not so sure.

Any ideas, gurus?

:confused:

---

### Post by djcla on 2007-11-07
how are you installing the alsa drivers o are you just using whats came with setup?  I.e. are you using latest revision,?

---

### Post by warbread on 2007-11-07
I can't speak for Scypher, but I installed according to these directions: [http://lddubeau.com/avaktavyam/linux-on-a-compal-ifl90/]("http://lddubeau.com/avaktavyam/linux-on-a-compal-ifl90/").  I installed about a month ago, so I can't imagine that they're too out of date.

---

### Post by djcla on 2007-11-08
what happens on a freash build if you just download the .15 alsa driver /lib / utils direct from there website

extract them somwhere

run a terminal and the following command with ubuntu oin DVD  drive
sudo apt-get install libncurses5-dev build-essential ncurses-dev gettext linux-headers-`uname -r`

then from alsa drivers directory (where you extracted them to)  do 

sudo ./configure
sudo make
sudo make install

Then from Lib directory do the same then from the utils directory etc.


then if you do not edit /etc/modprobe.d/alsa-base and add the options snd-hda-intel model=toshiba line what happens i.e. does the headphone socket work?  then try with the line....

---

### Post by warbread on 2007-11-11
> **djcla said:**
> what happens on a freash build if you just download the .15 alsa driver /lib / utils direct from there website

extract them somwhere

run a terminal and the following command with ubuntu oin DVD  drive
sudo apt-get install libncurses5-dev build-essential ncurses-dev gettext linux-headers-`uname -r`

then from alsa drivers directory (where you extracted them to)  do 

sudo ./configure
sudo make
sudo make install

Then from Lib directory do the same then from the utils directory etc.


then if you do not edit /etc/modprobe.d/alsa-base and add the options snd-hda-intel model=toshiba line what happens i.e. does the headphone socket work?  then try with the line....

I'm not understanding these instructions.  I got the drivers, extracted, compiled and then installed them.  That didn't do any good by itself, but I'm not sure what I'm supposed to be doing in /lib.  

I've had the toshiba line in for as long as I've had this install and it's not working.  Any other thoughts?

---

### Post by warbread on 2007-11-11
By the way, I get this error when I try to test the USB Audio connection in Preferences>Sound:

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open resource for writing.

Does that ring any bells with anyone?

---

### Post by warbread on 2007-12-01
> **warbread said:**
> Bumbxxor.

I have the same problem.  More specifically, when I change system volume, sound reverts back to the speakers but continues to go through the headphones.  I have to unplug then plug the headphones back in at whatever volume level I desire and then not change it unless I'm ready for music to come blaring out of my speakers.  A little embarrassing in the middle of the commons area.  

Ubuntu 7.10 (Real time kernel) recognizes the sound card just fine, and this is a new problem since about a week ago, maybe longer.  I thought it had something to do with me screwing with USB headphones, but now I'm not so sure.

Any ideas, gurus?

:confused:

I've got this figured out.  Looking at a multichannel volume manager, changing the headphone volume doesn't affect the front speakers and changing the PCM volume with the headphones in doesn't reroute the sound from the headphones as it did before.  However, changing the Front channel screws everything up.  So, NP2090 users, make sure you're managing the correct channel.

---

