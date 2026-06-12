---
title: "acer aspire 5315 with ubuntu"
date: 2008-02-23
forum: Hardware &amp; Laptops
---

### Post by dragons on 2008-02-23
i have a acer aspire 5315, and have just installed ubuntu 7.10 on it (it had vista basic on it before, and constantly stayed bogged down). now my sound will not work, and my modem. however i think the modem is because i can't obtain a dns number from people pc, and i can live without it being online for i have 3 other computers which sad to say can connect to the internet via windows xp. if i can get the sound to work it would be awesome! any ideas? these are the specs for it:
acer aspire 5315
intel celeron processor 540
1.86 ghz, 533 mhz fsb, 1mb l2 cache
up to 252mb mobile intel graphic media accelerator x3100
1gb ddr2 ram
160gb hardrive
dvd/cd-rw combo
802.11b/g wlan
in the book it says: audio intel high definition audio support.

like i said i can live with it if it has the sound.  ubuntu runs awesome on it! and of course i would like to get the vista install completely off of the hardrive, however as anyone knows they made vista almost impossible to get rid of once it is installed on a hardrive, it won't even let you go back to other versions of windows.  any help in getting my sound working would be greatly appreciated.  thanks, and have a great day.:)

---

### Post by Yellow Pasque on 2008-02-23
```
sudo gedit /etc/modprobe.d/alsa-base
```
Add/change this line:
```
options snd-hda-intel model=acer 
```

You may also need to upgrade to ALSA 1.0.16. Here are some scripts that make it easy.
[http://ubuntuforums.org/showpost.php?p=4298894&postcount=24](http://ubuntuforums.org/showpost.php?p=4298894&postcount=24)

---

### Post by dragons on 2008-02-24
okay let's start at the beginning. i left something out that i didn't think of. think of me as a preschooler when it comes to ubuntu, or maybe worse.  i know pretty much nothing about it. i did download the 2 files suggested (on one of my windows machines since ubuntu won't let me connect the laptop), and have put them on my desktop on my laptop via a thumbdrive. so i physically have the alsa_1.sh , and the alsa_2.sh on the laptop desktop, however you lost me from there. and i have no idea where to put codes, or how, or what i am to do with these 2 files? you are talking to someone who has done windows, but would love to make the switch to a linux based system.  and there is so much i love about ubuntu!!!!!! other than the hardware issues. so please try to understand it will take me more directions to understand. you say to download the 2 files, and get them on the desktop: i have that, but after that i am lost.  and then you had:
Code:
sudo gedit /etc/modprobe.d/alsa-base
then:
Add/change this line:
Code:
options snd-hda-intel model=acer
i just don't get what to do with any of it.  any help would be appreciated.  thank you. sorry i am so lost.

---

### Post by Yellow Pasque on 2008-02-24
No problem. I'll go as slow/detailed as you need me to.

Click on the Applications menu, select "Accessories" and then "Terminal"
Copy and paste these commands:
```
cd ~/Desktop
sudo chmod 777 alsa_1.sh
sudo chmod 777 alsa_2.sh
sudo gedit /etc/modprobe.d/alsa-base
```
The last command should bring up a text editor (like Notepad) with the alsa-base file. If there is already an options line in the file, add "snd-hda-intel model=acer" (no quotes) to it. If not, make your own 'options' line at the end of the file and add "snd-hda-intel model=acer" (no quotes) to it. Now save the file and exit. This should bring you back to the Terminal. Now copy/paste this command:
```
sudo sh ./alsa_1.sh
```
This will run the first script which will ask you to reboot when it's finished. Do so.
After you've restarted and logged back in, click on the Applications menu, select "Accessories" and then "Terminal"
Copy and paste these commands:
```
cd ~/Desktop
sudo sh ./alsa_2.sh
```

Your sound should work now...
You may need to go back into the terminal (Applications -> Accessories -> Terminal) and enter:
```
alsamixer
```
Make sure all the channels are unmuted.
Also go to the System menu, select Preferences, and then Sound. Make sure ALSA is being used for all of the options there.

---

### Post by dragons on 2008-02-24
i have done all of thee above, and here is what i have: when i push the sound + or - it pops up on the screen, and lets me go up, or down as it should. also the one in the tool bar pops up, and works as it is suppose to. and in the sound preferences everything is set to alsa, and nothing is muted on any of them.  however the sound still does not work. any ideas?  i know when the vista was on it the sound worked fine.  so there has to be something i am missing.  any help would be greatly appreciated. and thanks for your previous help thus far temujin.

---

### Post by talib on 2008-04-07
thanx for the guide,
i had the same problem, but not anymore its the easy way to install sound in aspire 5315


have a nice time

:guitar::popcorn::KS:KS:KS:KS

---

