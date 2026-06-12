---
title: "Acer Aspire One 532h Microphone Not Working"
date: 2010-01-12
forum: Hardware
---

### Post by lagamemnon on 2010-01-12
I just got the sweet new Acer Aspire One 532h with the new Atom N450.

The netbook runs beautifully with Ubuntu 9.10 Karmic, except I can't seem to get the microphone to work.

I ran sudo apt-get install linux-backports-modules-alsa-karmic-generic, after googling that this fixed the problem on some other Acers, but that did not work.

I also tried compiling alsa-driver-1.0.20 according to the instructions here:
[https://help.ubuntu.com/community/AspireOne](https://help.ubuntu.com/community/AspireOne)

Nothing has worked so far, any ideas how I can fix it?

---

### Post by Abdi110 on 2010-01-16
I am thinking of getting this machine as my first netbook. Have you found a solution to your mic problem? Any other problems you've encountered?

Also how's the keyboard?

Thanks!

---

### Post by lagamemnon on 2010-01-16
Everything worked after automatic updates except for the multitouch and internal mic. Hotkeys, wifi, all that stuff worked.

I have found a semi-fix for the mic, it can record some sound, but it's very low quality with a lot of background electronic noise, I followed the guide here:  
[http://ubuntuforums.org/showthread.php?t=1341325](http://ubuntuforums.org/showthread.php?t=1341325)

I haven't found a way to make it work completely yet.

As for the multitouch, I tried following this guide, but still had no luck in making it work:
[https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks#Asus](https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks#Asus) Eee PC 1005HA

The side scroll bar still works.

The computer is pretty great, very thin (.99 inches) and good build quality. 
The keyboard is big enough, but the keys are very flat, so it takes getting used to because you don't feel the edges of the keys so much.

Overall, I like the laptop a lot, but I'm thinking of switching to the Asus 1001P for the same price because I prefer matte screens to glossy, and it has a bit longer battery life and probably better Ubuntu support. Only problem is that it's not out yet.

---

### Post by Mathieup75 on 2010-07-14
Got the microphone working.

In terminal:

[FONT=Courier New]*sudo apt-get install pavucontrol*[/FONT][FONT=Courier New][I]

pavucontrol

[/I][/FONT]
Then:

                                 
[LIST]
[*]Click the "input devices"     tab. Click the lock icon to unlock channels. Set the front right     channel to silence.
[/LIST]

---

### Post by Mathieup75 on 2010-07-14
> **lagamemnon said:**
> 

overall, i like the laptop a lot, but i'm thinking of switching to the asus 1001p for the same price because i prefer matte screens to glossy, and it has a bit longer battery life and probably better ubuntu support. Only problem is that it's not out yet.



That's so funny, I just gave my Asus 1001P to my father inlaw so I can get this Acer.  When comparing the two, the Asus mat screen is not as bright, the keyboard is much louder and the hard drives clicking is also loud.  However, the 1001P battery life is great.

Also, I wrote a thread on getting the multiple devices to work.  It was more of a problem with the Asus than the Acer.


[http://art.ubuntuforums.org/showthread.php?t=1479058](http://art.ubuntuforums.org/showthread.php?t=1479058)

---

### Post by HunterBreedlove on 2010-07-30
Internal mic works; pucks up ALOT of background noise and static.  SKYPE does not recognize the Mic. and the SD card is not recognized for the Acer Aspire One 0532H.  Anyone got this working?

---

### Post by lidex on 2010-07-31
> **HunterBreedlove said:**
> Internal mic works; pucks up ALOT of background noise and static.  SKYPE does not recognize the Mic. and the SD card is not recognized for the Acer Aspire One 0532H.  Anyone got this working?

Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
dpkg -l | grep "alsa"
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
**Please also include the make/model of your PC/Laptop.**
Please post text output using code tags (the # in toolbar)

---

### Post by capemanbob on 2010-08-04
> **Mathieup75 said:**
> Got the microphone working.

In terminal:

[FONT=Courier New]*sudo apt-get install pavucontrol*[/FONT][FONT=Courier New][I]

pavucontrol

[/I][/FONT]
Then:

                                 
[LIST]
[*]Click the "input devices"     tab. Click the lock icon to unlock channels. Set the front right     channel to silence.
[/LIST]

I have an ACER Aspire One AOA 110 ZG5 with UBUNTU 10.04 and this fixed my microphone problem with SKYPE.  Works great now...thanks to Mathieup75.

---

### Post by DedMoroz on 2010-08-27
I too have similar problems. The tip of installing "pavucontrol" did help. Although I think this is more of a temporary fix for now. If you use the new Google Phone link within Gmail, it will reset the pavucontrol settings, so I dont recommend that.

However, all works fine in Skype! Here is the trick. First follow the instructions above with the pavucontrol settings. Then go into Skype. Find the Skype menu and click "options" and then click "sound devices" and uncheck the box marked "allow skype to adjust volume levels". Close and then try a call. Skype works great for me, glad someone came up with a fix for this as I'll be traveling in Europe and this will come in handy so I dont have to use my cellphone roaming, which is expensive!

---

### Post by HunterBreedlove on 2010-09-10
> **lidex said:**
> Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
dpkg -l | grep "alsa"
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
**Please also include the make/model of your PC/Laptop.**
Please post text output using code tags (the # in toolbar)

Acer 0532h netbook - Ubuntu 10.04

uname -a
aplay -l
dpkg -l | grep "alsa"
head -n 1 /proc/asound/card*/codec#* Ran  Results below:

dpkg -l | grep "alsa"
ii  alsa-base                              1.0.22.1+dfsg-0ubuntu3                          ALSA driver configuration files
ii  alsa-utils                             1.0.22-0ubuntu5                                 ALSA utilities
ii  bluez-alsa                             4.60-0ubuntu8                                   Bluetooth audio support
ii  gnome-alsamixer                        0.9.7~cvs.20060916.ds.1-2                       ALSA sound mixer for GNOME
ii  gstreamer0.10-alsa                     0.10.28-1                                       GStreamer plugin for ALSA

---

### Post by MaTiCeK on 2010-12-19
Hi

I have the ao532h and just installed and started using jolicloud, which is based on ubuntu. 

Of course I've ran in the same skype mic problem as others have... The suggested fix is great but only works temporarily, on every reboot I have to change the settings again.

Is there a file I can gedit to make the fix permanent?

Thx for the help.

---

### Post by lidex on 2010-12-20
What about this:
> Then go into Skype. Find the Skype menu and click "options" and then click "sound devices" and uncheck the box marked "allow skype to adjust volume levels".

---

### Post by wijit on 2011-01-20
> **Mathieup75 said:**
> Got the microphone working.

In terminal:

[FONT=Courier New]*sudo apt-get install pavucontrol*[/FONT][FONT=Courier New][I]

pavucontrol

[/I][/FONT]
Then:

                                 
[LIST]
[*]Click the "input devices"     tab. Click the lock icon to unlock channels. Set the front right     channel to silence.
[/LIST]

Thanks mate. I was looking for this for more than 2 years.

---

### Post by lidex on 2011-01-20
> **wijit said:**
> Thanks mate. I was looking for this for more than 2 years.

Whaaat? You, my friend, are as patient as a saint. ;)

---

### Post by thevan on 2011-03-21
Still won't work in Gmail for me. They receive no sound at all. I tried lowering the left channel of the mic to silence as suggested in another thread as well.

---

### Post by lidex on 2011-03-21
> **thevan said:**
> Still won't work in Gmail for me. They receive no sound at all. I tried lowering the left channel of the mic to silence as suggested in another thread as well.

You need to make sure your mic is set up and working correctly first. What happens with 'sound recorder'? Have you tried cheese?

---

### Post by thevan on 2011-03-22
> **lidex said:**
> You need to make sure your mic is set up and working correctly first. What happens with 'sound recorder'? Have you tried cheese?

Have not tried cheese, but sound recorder works fine now (albeit quietly).

---

### Post by hopsephiroth on 2011-04-22
> **Mathieup75 said:**
> Got the microphone working.

In terminal:

[FONT=Courier New]*sudo apt-get install pavucontrol*[/FONT][FONT=Courier New][I]

pavucontrol

[/I][/FONT]
Then:

                                 
[LIST]
[*]Click the "input devices"     tab. Click the lock icon to unlock channels. Set the front right     channel to silence.
[/LIST]

Hey Mathieup75, thanks a lot...:D the mic was the last ting I need to correct work on ubuntu to stay it in!!!!:popcorn::D

---

### Post by Mediosordo on 2011-12-08
> **lidex said:**
> You need to make sure your mic is set up and working correctly first. What happens with 'sound recorder'? Have you tried cheese?


Same problem here with Pavucontrol on an AOne ZG5. Cheese and Sound Recording work ok, but I can't make it work with gmail. 
Any other solution?
Thanks!

---

### Post by ramongm on 2011-12-08
I just resolve the same problem in a Lenovo computer. 
First go to [http://www.alsa-project.org/main/index.php/SoundcardTesting](http://www.alsa-project.org/main/index.php/SoundcardTesting)  to see how to probe your sound card (the % sign is the $ symbol in your  terminal), the capture control in alsamixer must be active and one  channel L or R must be  close to 0 and the other around 75    if still  the microphone does not work, then:
Go to  [http://git.alsa-project.org/?p=alsa-kernel.git;a=blob;f=Documentation/sound/alsa/HD-Audio-Models.txt;hb=HEAD](http://git.alsa-project.org/?p=alsa-kernel.git;a=blob;f=Documentation/sound/alsa/HD-Audio-Models.txt;hb=HEAD)  and find out the model that best match your computer;  open a terminal  and type* sudo gedit /etc/modprobe.d/alsa-base.conf*   , in the file open go to the end and write a new line: options *snd-hda-intel model=asus position_fix*=*1*   substitute "hda-intel" with your sound car identification and "asus"  with the model name of your computer as in the first column at the web  page visited, save the file, reset your computer and it&#347; done.:eek:

---

### Post by lidex on 2011-12-27
> **Mediosordo said:**
> Same problem here with Pavucontrol on an AOne ZG5. Cheese and Sound Recording work ok, but I can't make it work with gmail. 
Any other solution?
Thanks!

And you've installed the google chat plugin?
[http://www.google.com/chat/video](http://www.google.com/chat/video)

---

