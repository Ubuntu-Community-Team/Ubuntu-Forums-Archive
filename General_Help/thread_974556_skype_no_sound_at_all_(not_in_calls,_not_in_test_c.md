---
title: "skype no sound at all (not in calls, not in test call, no &quot;test sound&quot;)"
date: 2008-11-07
forum: General Help
---

### Post by hachel on 2008-11-07
hi,
i don't get any sound out of skype. I installed it with synaptic and started it. I opened the sound-device-settings, left everything on default and tried the testcall. It quit, saying there is a "problem with audio playback". When I hit "test sound", nothing happens. I changed through every available sound-in, hit apply and tried test-sound again, yet, nothing happens.
I don't know for sure what I should set sound-in to or if I should leave it to default, because in the system sound-preferences, sound playback is on auto detect, and sound works fine here.
Anyway, I have a realtek-onboard-soundcard on my msi-sli-mainboard.
Volume-Control has Device set to "HDA Nvida (Alsa Mixer)" (i have no idea what thats all supposed to mean, it got the hda nivia, a realtek alc883 (OSS Mixer) and two Capure...-devices in there to choose).
Still under volume-control, I have Master and PCM enabled, as those are the only two I need to playback sound (enabled and disabled all the others, like front, line-in etc)
any help?
btw: i googled it, but all the problems and solutions that came up differed to mine, like test calls worked but real calls didn't, or there were actual error-messages etc.

thanks,
hachel

---

### Post by ACMiller on 2008-11-07
Hey, I've had a similar thing with skype (and I also have a realtek onboard soundcard if that means anything). I haven't really looked into why or how, but I know now that I can only use skype without the "problem with audio playback" error like yours if I don't have any other programs open using pulse audio (e.g. music player etc.) - or at least that's what I asssume the problem is due to. I'm sure if I had the time to I could fix this properly, but skype is the only program that is affected by pulse audio's issues for me, so I'm not too concerned.

Anyway, if it helps, great. Otherwise, good luck

---

### Post by Hangwire on 2008-11-07
I had the exact same problem today.

Go to terminal, type:

**sudo killall pulseaudio**

or

**sudo killall -9 pulseaudio**

Restart Skype.

Go to the Sound Settings in Skype and choose Default on everything. Disable the automatic adjustment by Skype. 

Test the Sound, make a test call, everything will work like a charm. (atleast it worked for me!) 

Hope this helps. :)




You should also have alsa. If you have any problems with audio or video players after you kill pulse audio, lurd their options for sound stuff and change from pulseaudio to alsa mixer or anything with alsa.

---

### Post by sirebral on 2008-11-07
Try setting your sound this way:

Sound in: HDA Intel (hw: Intel,0)
Sound Out: Pulse
Ringing: Pulse

This works for me.

I also had to change the Capture volume, Mic Volume, and the Mic Boost in my sound Settings (HDA Intel Alsa Mixer)

---

### Post by hachel on 2008-11-08
hi
i didn't have anything open that would output any audio, so I tried Hangwires solution and it worked.
But this is not permanent, do I have to kill the process evey time I want to use skype?
thanks everyone,
hachel

PS:sirebal, skype doesn't show me any pulse-devices to chose

---

### Post by mac-duff on 2008-11-09
Hi,
I am having the same problem with skype and the kill command helps. So can we not deactivate the hole pulsesound stuff from the booting (dont know how) and is there any advantages of pulseaudio?

Cu

---

### Post by ieBrazil on 2008-11-09
I have this same problem. And I am about to follow the steps folks bring us here.
Just an info: which Skype version is yours?
Check it, please!, on About...

Thank you.



ieBrazil



ps: mine is 2.0.0.72

---

### Post by furiousmanatee on 2008-12-23
same problem here too with skype 2.0.0.72 and 8.04 with nvidia card and restriced drivers. 

kill all pulseaudio seems to have sorted it out - thanks.

would be great to get a permanent fix without having to open the terminal each time, but this works just fine :)

---

### Post by djungelmums on 2008-12-23
Heres a solution for you so you dont have to open terminal and kill pulseaudio everytime you launch skype. This is the method i used:

killall pulseaudio
sudo apt-get remove pulseaudio
sudo apt-get install esound
sudo rm /etc/X11/Xsession.d/70pulseaudio

As you can see this method uninstalls pulseaudio and installs esound instead.

---

### Post by Spartnova on 2009-01-29
Setting sound in and ringing to pulse and sound out to "...hw:..." (the first option after default device for me) fixed my problems.  Everything appears to be working.

I'm running 8.01 x64.

---

### Post by SRG8 on 2009-01-31
So i too have had the skype audio problems except its just on calls/test calls, the sound test works.
iv also tried djungelmums' method and it worked... but then it didnt, it worked for one call. the next time i tried to make a call it was the same old problem again. 
one thing to note the last instruction in that method:

sudo rm /etc/X11/Xsession.d/70pulseaudio

this promptyl returned this in terminal:

rm: cannot remove `/etc/X11/Xsession.d/70pulseaudio': No such file or directory

I'm not sure whether this mattered or not or if this is why it only worked for one call.

---

### Post by cornelis spronk on 2009-02-02
I have looked through a multitude of threads and websites without solving my Skype problem for Intrepid 8.10.  When I do the test call, I can hear the Skype voice, but Skype does not hear my voice and return it to me.  I have played around with all the buttons, and adjusted all the volume controls without success.

Otherwise I am very happy with this distribution.  Where can I get some help?

---

### Post by any.linux12 on 2009-02-02
Mine is not intel, it's an amd but try it like this couse I had the same  problem and solved it with this

---

### Post by agkrish on 2009-05-10
> **SRG8 said:**
> So i too have had the skype audio problems except its just on calls/test calls, the sound test works.
iv also tried djungelmums' method and it worked... but then it didnt, it worked for one call. the next time i tried to make a call it was the same old problem again. 
one thing to note the last instruction in that method:

sudo rm /etc/X11/Xsession.d/70pulseaudio

this promptyl returned this in terminal:

rm: cannot remove `/etc/X11/Xsession.d/70pulseaudio': No such file or directory

I'm not sure whether this mattered or not or if this is why it only worked for one call.

am getting exactly the same message - no such file or directory. Skype test call works only upto the playback and NOT the audio capture.

HP Pavilion dv5-1050ee
AMD Turion X2 Ultra 64 
ATI Radeon
Ubuntu 8.1 (32-bit) co-existing with Vista (32-bit)

---

### Post by chosenbeans on 2009-05-12
The way I deal with this is close everything that could possibly be using the sound device. Rhythmbox, Firefox, Xmms, VLC..EVERYTHING. Then I go to skype and in the sound options I choose my mic(which is my webcam,usually at the bottom of the drop down menu) for sound in. For sound out I choose the first selection available under default. I choose the same thing for ringing. When I do a test call all is fine. The only thing that bugs me (in all linux distros) is that once skype is using the sound device it completely HOGS it. This means anything else that uses sound like VLC or Firefox will not play. 

I have been looking for a way to solve this. My guess is install something like e-sound or configure pulse to do it. I have not tried it yet. I need to try it soon though otherwise windows will be used more often. Oh god!

---

### Post by bhishan on 2009-05-15
> **djungelmums said:**
> Heres a solution for you so you dont have to open terminal and kill pulseaudio everytime you launch skype. This is the method i used:

killall pulseaudio
sudo apt-get remove pulseaudio
sudo apt-get install esound
sudo rm /etc/X11/Xsession.d/70pulseaudio

As you can see this method uninstalls pulseaudio and installs esound instead.

thanks, worked perfectly for me

---

### Post by bcmiller on 2009-08-30
> **bhishan said:**
> thanks, worked perfectly for me

This worked for me as well. Thanks a lot.

---

### Post by depaulmatthew on 2009-11-17
> **bcmiller said:**
> This worked for me as well. Thanks a lot.
worked for me as well.. thanks a ton :)

---

### Post by aryangor on 2009-12-22
> **djungelmums said:**
> Heres a solution for you so you dont have to open terminal and kill pulseaudio everytime you launch skype. This is the method i used:

killall pulseaudio
sudo apt-get remove pulseaudio
sudo apt-get install esound
sudo rm /etc/X11/Xsession.d/70pulseaudio

As you can see this method uninstalls pulseaudio and installs esound instead.

worked for me as well, thanks a lot!! :KS

---

### Post by Koffeehaus on 2011-02-22
> **Hangwire said:**
> I had the exact same problem today.

Go to terminal, type:

**sudo killall pulseaudio**

or

**sudo killall -9 pulseaudio**


Finally I know what's the problem!! Thanks

---

### Post by Koffeehaus on 2011-02-24
Also try muting left channel in Input Devices using PulseAudio Volume Control (not installed by default). This also did the trick for me.


As to no test sound - System > Preferences > Sound > Sound Effects. Unmute and scroll up Alert Volume

---

### Post by Scot_Bernard on 2011-02-26
> **Koffeehaus said:**
> Also try muting left channel in Input Devices using PulseAudio Volume Control (not installed by default). This also did the trick for me.


As to no test sound - System > Preferences > Sound > Sound Effects. Unmute and scroll up Alert Volume
Yes, unmute alert volume solved the sound out problem, for sound in justa adjusting the input device, all of this in the pulse preferences.

I'm using ubuntu 10.04 and Skype 2.1.0.81

---

### Post by Comrade7 on 2011-02-26
Hey there.
I had the same issue yesterday, did the killall deal and all that jazz,
ended up finding out about a thingy called "aslamixer" you put into terminal.  worked sortof like a master volume control on a windows machine.
heres the screencap.
hope it helps someone with something :D

---

