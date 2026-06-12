---
title: "(Lucid) internal mic not working ALC262"
date: 2010-06-22
forum: Hardware
---

### Post by magic-neophyte on 2010-06-22
On Lucid Lynx 10.04 I got the internal microphone of my VAIO VGN-NS11Z to work on my Intel HDA sound card (lspci says 'rev 03') with

#cat /proc/asound/card0/codec#0 | grep Codec
Codec: Realtek ALC262

Start up a terminal (Applications > Accessories > Terminal) and add the following line to /etc/modprobe.d/alsa-base.conf like so: 

#sudo nano /etc/modprobe.d/alsa-base.conf

Enter your password to proceed. At the end of the file, add the following line:

**options snd-hda-intel model=toshiba-s06**

Note: If you see B's in brackets, leave them out!

Reboot your machine, and the internal microphone should work. If it does not, start up a terminal (Applications > Accessories > Terminal) and start alsamixer (just type alsamixer and press enter). Check whether the Capture settings are correct (press F4 to see Capture settings, use sideways arrows to select a column and up/down arrows to modify the volume accordingly). 

Note: if you activate the Mic setting in the Playback screen (press F3 or F5) then you might get annoying echo/feedback/whistling on your microphone, so leave that set to a low setting (zero works fine).

Cheers,

magic neophyte

---

### Post by magic-neophyte on 2010-06-22
Addendun: Incidentally, the above solution also solved my Skype 2.1 microphone problems, after a few reboots. First try to get Sound Recorder working. Then try to fix Skype.

Important: install Skype from the 'partner' repositories (enable them by removing the # in front of the lines containing the word partner (search with Ctrl-W in nano) in the file /etc/apt/sources.list, then refresh your package cache with 'sudo apt-get install update' and install skype using 'sudo apt-get install skype'). 

Sometimes, you may need to fix Pulse Audio settings, which is the default mixer program for the Xorg window manager in Ubuntu. (In a terminal, do a 'sudo apt-get install paman' and look under Applications > Sound & Video to tweak your pulse audio settings.) Sometimes the terminal-based alsamixer can help to set recording settings to desired levels, where regular volume managers fail.

But more often than not, being unable to use the internal microphone is a sound driver problem. This is solved by looking up your sound card with 'lspci | grep Audio' (in a terminal) and then searching for a fix specific to that sound card.

For the Intel HDA line of cards, look up your card's internal chip, also known as 'codec', as shown in the post above. Then look up the model code you have to add to the end of /etc/modprobe.d/alsa-base.conf in /usr/share/doc/linux-doc/sound/alsa/HD-Audio-Models.txt (install this file by entering 'sudo apt-get install linux-doc' in a terminal. You may need to unzip the file first using gunzip).

---

### Post by Yakir on 2010-08-23
This is my first post here:
Works for me as well: Ubuntu 10.04 (64) on Sony Vaio VGN-SR31M.
Nothing else worked for me (tried various other 'last line' amendments for the same conf file), but this did. 
Thanks a bunch!!! :popcorn:

---

### Post by josel0924 on 2010-09-06
:popcorn: this is great i spent almost half a day trying to fix this...!!! work perfect...!!!):P

---

### Post by edwardblum on 2010-12-24
I can confirm this edit to alsa-base.conf  also work for Samsung R60 Plus in 32 bit Ubuntu 10.10 

Found the model through alsamixer, catting the codec doesn't work for this model of laptop.

---

### Post by roshanmani on 2011-01-14
I have a Sony Vaio VGN-NW23NE running Ubuntu 10.04 and the internal mike was not working.. I finally got it to work by simply editing the /etc/modprobe.d/alsa-base.conf file and adding the line 'options snd-hda-intel model=vaio' (without the quotes) at the end of the file..:popcorn:

---

### Post by roshanmani on 2011-01-16
> **roshanmani said:**
> I have a Sony Vaio VGN-NW23NE running Ubuntu 10.04 and the internal mike was not working.. I finally got it to work by simply editing the /etc/modprobe.d/alsa-base.conf file and adding the line 'options snd-hda-intel model=vaio' (without the quotes) at the end of the file..:popcorn:

Forgot to mention that I also needed to install 'linux-backports-modules-alsa-lucid-generic' and it's supporting package 'linux-backports-modules-alsa-2.6.32-27-generic' using Synaptic Package Manager.

---

### Post by roshanmani on 2011-01-16
.1

---

### Post by roshanmani on 2011-01-16
2

---

### Post by roshanmani on 2011-01-16
3

---

### Post by jaymill on 2011-02-26
Adding Sony Vaio VGN-NS295J to the list of computers that this solves the issue for.

---

