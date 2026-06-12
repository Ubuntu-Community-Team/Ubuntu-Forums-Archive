---
title: "(all) microphones are not being recognized."
date: 2010-05-30
forum: Hardware
---

### Post by kokadu on 2010-05-30
i am using a notebook hp dev5-1110EZ (two years old)...  with ubuntu karmik koala

My sound output is working. (all) my microfones are not working. Actually it seems, that all sound input sources are not recognized (not headset mic, nor inbuilt mic, nor webcam mic). 

in "audio settings" under the tab "input" there is nothing to choose from (all text is in light grey, and no options given to choose from being used as source.even though all 3 mics were connected at some point...)

in alsa mixer: everything is active and turned up. i played around with it for quite a while and with pavumeter (checking if the mic causes any sound vibrations). the strange thing is though, that for the two "input sources" i cannot get a volume level. which then is no wonder that the mics dont work...

referring to the sound trouble shoot manual[: https://help.ubuntu.com/community/SoundTroubleshooting]("https://help.ubuntu.com/community/SoundTroubleshooting"))
-i can play sounds 
-i am in the sound group
-the systems recognized my soundcard 
(STA C92xxSB [HDA ATI SB], Gerät 1: STAC92xx Digital)
-modules and so on were installed.the soundcard is physically installed and recognized by my hardware.    
though it might not completely be supported by alsa, as alsa couldnt give me the correct alsa-driver-type for it.even though it seems like that when you look at the website([http://www.alsa-project.org/main/index.php/Matrix:Vendor-ATI](http://www.alsa-project.org/main/index.php/Matrix:Vendor-ATI)) there should be the apropriate driver. but anyway: sound and built-in cam work ...just the mic not.



I have been cruising the internet for 10 hours now, following all available threads. now there is nothing to find any more, that i have not tried yet ...does somebody have an idea?

thanx& cheers
k

---

### Post by lidex on 2010-05-31
Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
**Please also include the make/model of your PC/Laptop.**
Please post text output using code tags (the # in toolbar)

---

### Post by lidex on 2010-05-31
First, for mic problem, check this.
**Gnome-alsamixer**
Using Alt+F2 run dialog
```
 gnome-alsamixer 
```
**Use 'Edit -> Sound Card Properties' menu to enable elements.**
Soundcard tab to select / adjust levels.
To install:
```
sudo apt-get install gnome-alsamixer
```

Then use pulseaudio volume control (pavucontrol) to select your mic in 'Input Devices' tab.

From alsa documentation:
> Capture Problems
~~~~~~~~~~~~~~~~
The capture problems are often because of missing setups of mixers.
Thus, before submitting a bug report, make sure that you set up the
mixer correctly.  For example, both "Capture Volume" and "Capture
Switch" have to be set properly in addition to the right "Capture
Source" or "Input Source" selection.  Some devices have "Mic Boost"
volume or switch.

When the PCM device is opened via "default" PCM (without pulse-audio
plugin), you'll likely have "Digital Capture Volume" control as well.
This is provided for the extra gain/attenuation of the signal in
software, especially for the inputs without the hardware volume
control such as digital microphones.  Unless really needed, this
should be set to exactly 50%, corresponding to 0dB -- neither extra
gain nor attenuation.  When you use "hw" PCM, i.e., a raw access PCM,
this control will have no influence, though.

---

### Post by kokadu on 2010-06-04
hej lidex!
thank you for answering my post!
this is the output:

output:
```

klabauterin@klabauterin:~$ uname -a
Linux klabauterin 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:05:01 UTC 2009 x86_64 GNU/Linux
klabauterin@klabauterin:~$ aplay -l
**** Liste von PLAYBACK Geräten ****
Karte 0: SB [HDA ATI SB], Gerät 0: STAC92xx Analog [STAC92xx Analog]
  Untergeordnete Geräte: 1/1
  Untergeordnetes Gerät '0: subdevice #0
Karte 0: SB [HDA ATI SB], Gerät 1: STAC92xx Digital [STAC92xx Digital]
  Untergeordnete Geräte: 1/1
  Untergeordnetes Gerät '0: subdevice #0
Karte 1: HDMI [HDA ATI HDMI], Gerät 3: ATI HDMI [ATI HDMI]
  Untergeordnete Geräte: 1/1
  Untergeordnetes Gerät '0: subdevice #0
klabauterin@klabauterin:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.20.
klabauterin@klabauterin:~$ head -n 1 /proc/asound/card*/codec#*
==> /proc/asound/card0/codec#0 <==
Codec: IDT 92HD71B7X

==> /proc/asound/card1/codec#0 <==
Codec: ATI R6xx HDMI


```

the lapttop is a hewlett packard pavilion dv5 (hp dev5-1110EZ)

thank you for looking into it! cheers k

---

### Post by kokadu on 2010-06-04
[B]this is the outcomes of alsamixer and pavucontrol:
[/B]
**alsamixer:**check: everything was enabled (but is showing being disabled on the main alsamixer surface; buttom part.

          

this outcome appeared after in the terminal:
```
     
               klabauterin@klabauterin:~$ gnome-alsamixer 
           
          ** (gnome-alsamixer:3458): WARNING **: gam_toggle_get_state (). No     idea what to do for mixer element "Front Mic Jack Mode"! 
           
          ** (gnome-alsamixer:3458): WARNING **: gam_toggle_get_state (). No     idea what to do for mixer element "Mic Jack Mode"! 
           
          ** (gnome-alsamixer:3458): WARNING **: gam_toggle_get_state (). No     idea what to do for mixer element "IEC958 Playback Source"! 
           
          ** (gnome-alsamixer:3458): WARNING **: gam_toggle_get_state (). No     idea what to do for mixer element "Digital Input Source"! 
           
          ** (gnome-alsamixer:3458): WARNING **: gam_toggle_get_state (). No     idea what to do for mixer element "Digital Input Source"! 
           
          ** (gnome-alsamixer:3458): WARNING **: gam_toggle_get_state (). No     idea what to do for mixer element "Input Source"! 
           
          ** (gnome-alsamixer:3458): WARNING **: gam_toggle_get_state (). No     idea what to do for mixer element "Input Source"!
          
```
          
    
          there are two tabs on the opening surface of alsamixer. the first     tab being: IDT 92HD 71B7x with all the channels. there, the volumes is up on     all of them.
 the second tab ist my soundcard (ATI  R6xx HDMI). there     is no soundlevel to adjust. there is just nothing in it, acutally. (except a little tick can be made at a box with the plain text: IEC958)

          (pls have in mind though, that my sound IS working. but my     microphone not)
          
    
          **pavucontrol:**
          on the tab "input devices": there are no devices to choose     from...!


thank you for looking into it! cheerio k

---

### Post by lidex on 2010-06-04
Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel model=hp-dv5 enable_msi=1 
```
Save. Close. Reboot. Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default.

---

### Post by kokadu on 2010-06-08
Hello!

i did add the line and reboot the system. actually nothing changed though:

in alsamixer:
i do not have any choice for changing the sound card. or in other words f6 does not give options. my one and only "choice" for soundcard is: HDA ATI SB
in capture and in playback levels i cannot change levels, because it doesnt show any "column" on which i could manipulate the volume of the sound for the input sources.

in pavucontrol:
 there is (still) no input device to choose from

do you have any other idea?

thanx a lot for your ideas so far...
cheerio

---

### Post by lidex on 2010-06-08
OK. Right-click the alsa-info script link in my sig and "save as" to your user folder. Then run this command in a terminal:
```
sudo bash utils_alsa-info.sh
```
Enter your user password when prompted. Provide a link for the output or post it here using code tags.

---

### Post by kokadu on 2010-06-10
this is the output

```
bash: utils_alsa-info.sh: No such file or directory
klabauterin@klabauterin:~$ 

```

where should i save the Alsa Info Script.htm from your sig? just within my user "klabauterin"?  ..i did so..
though, the name in the command and the title of the alsa document are different ...

cheers

---

### Post by gradinaruvasile on 2010-06-10
Just a simple question: right-click on the sound icon in the taskbar, select sound preferences, and on one of the tabs (general or something) you have the list of sound cards on your system - you should have the internal one. Under the list is a selector that allows you to select the operation mode of the soundcard - it should be set to stereo duplex or something. Try all the options there - one option (at least) sets the soundcard in "playback only" mode and kills the mic.

---

### Post by lidex on 2010-06-11
> **kokadu said:**
> this is the output

```
bash: utils_alsa-info.sh: No such file or directory
klabauterin@klabauterin:~$ 

```

where should i save the Alsa Info Script.htm from your sig? just within my user "klabauterin"?  ..i did so..
though, the name in the command and the title of the alsa document are different ...

cheers
Looks like you're saving the web page. Right-click on the link and select 'save link as'. Do not left-click and do not change the filename. It should save as 'utils_alsa-info.sh'

---

### Post by kokadu on 2010-06-27
hej thank you  for the suport!!

i just got it to work right now. looking back, it is hard to say what it needed to work out and which of it wasnt needed.

now in the end i have been playing again around endless more combinations with "alsamixer" and the "audio settings" (right click on sound icon in upper right corner).

in audio settings, tab "input":
play around so long with alsamixer. till you have "internal audio stereo" appearing as a choice. (in the beginning i had no choices there at all)
choose microphone 2

tab "hardware":
choose internal audio soundcard
profil:analog stereo duplex (choices for stereo were not working with me)

for some strange reason "pavumeter" still doesnt show any reaction with the microphone...this has been one of my testing tools. 
audio-recorder: mic works in recording.
audiocity: mic doesnt work
skype: mic works.
what i want to say by this: its smart to change your testing tools wether the mic works or not....


in alsamixer:
within the profil "capture": turn down first colunn all the way down. otherwise the other person on skype heard herself double voiced.

cheerio!
k

---

### Post by lidex on 2010-06-27
For mic in Audacity, check this page:
[http://forum.audacityteam.org/viewtopic.php?p=75044#p75044]("http://forum.audacityteam.org/viewtopic.php?p=75044#p75044")

---

