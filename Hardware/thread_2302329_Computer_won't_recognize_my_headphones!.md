---
title: "Computer won't recognize my headphones!"
date: 2015-11-09
forum: Hardware
---

### Post by ryan_2 on 2015-11-09
Hi, so I'm a fairly new linux user, and everything is fine except for the fact that nothing i plug in to my audio jack outputs audio. I've looked online for support but it seems it is always a case by case problem, so i haven't found anything that has worked yet. Would anyone here be able to help me out at all? I'm running on a Eurocom m5 pro laptop with an intel i7-4720HQ processor. 

Any help would be appreciated, I need earphones to work! 

Thanks.

---

### Post by ajgreeny on 2015-11-09
Have you looked in pulseaudio-volume-control?

Headphones and internal speakers in the system are controlled separately from there.

---

### Post by ryan_2 on 2015-11-17
> **ajgreeny said:**
> Have you looked in pulseaudio-volume-control?

Headphones and internal speakers in the system are controlled separately from there.

Where do i find pulseaudio volume control?

---

### Post by ryan_2 on 2015-11-17
So i installed it but my headphones aren't listed anywhere when plugged in. They're not recognized at all.

---

### Post by tgalati4 on 2015-11-18
Try the microphone port.  Sometimes the audio connections are switched internally.

---

### Post by ryan_2 on 2015-11-19
Just tried the mic port, still no luck.

---

### Post by Yellow Pasque on 2015-11-19
```
sudo apt-get install alsa-tools-gui
```
This will give you hdajackretask program, which is a useful GUI to manually specify which jack does what if the driver doesn't autodetect it correctly: [http://voices.canonical.com/david.henningsson/2011/11/29/turn-your-mic-jack-into-a-headphone-jack/](http://voices.canonical.com/david.henningsson/2011/11/29/turn-your-mic-jack-into-a-headphone-jack/)

There is also hdaanalyzer, which includes a jack sense tester: [http://www.alsa-project.org/main/index.php/HDA_Analyzer](http://www.alsa-project.org/main/index.php/HDA_Analyzer)
```
sudo apt-get install python-gtk2 wget
cd ~/; mkdir hda; cd hda
wget -O run.py http://www.alsa-project.org/hda-analyzer.py
sudo python run.py
```
^This will run hdaanalyzer and download some other hda utils. You can close hdaanalyzer and run hda-jack-sense-test.py (The -c and -d options will be different for you depending on what path your sound is in /proc/asound. Try simply omitting them at first.)
```
sudo python hda-jack-sense-test.py -c 1 -d 3   #nothing was plugged into my card
Pin 0x14 (Green Line Out): present = No
Pin 0x15 (Black Line Out): present = No
Pin 0x16 (Orange Line Out): present = No
Pin 0x17 (Grey Line Out): present = No
Pin 0x18 (Pink Mic): present = No
Pin 0x19 (Pink Mic): present = No
Pin 0x1a (Blue Line In): present = No
Pin 0x1b (Green HP Out): present = No

sudo python hda-jack-sense-test.py -c 1 -d 3   #here, I plugged in headphones to Green jack and now it detects its presence
Pin 0x14 (Green Line Out): present = Yes
Pin 0x15 (Black Line Out): present = No
Pin 0x16 (Orange Line Out): present = No
Pin 0x17 (Grey Line Out): present = No
Pin 0x18 (Pink Mic): present = No
Pin 0x19 (Pink Mic): present = No
Pin 0x1a (Blue Line In): present = No
Pin 0x1b (Green HP Out): present = No
```

---

### Post by ryan_2 on 2015-12-01
Hey guys, so I'm still having issues with the audio. It might be important to note that even when hooked up to a TV using HDMI the sound will STILL play out of the built in speakers, and when in pulse audio volume control (or any other audio control program for that matter) nothing shows up other than the default speakers. Any help would be appreciated.

---

### Post by Yellow Pasque on 2015-12-03
Did you try the things in my previous post?

---

