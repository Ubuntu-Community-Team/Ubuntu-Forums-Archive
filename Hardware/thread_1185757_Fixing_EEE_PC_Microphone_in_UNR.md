---
title: "Fixing EEE PC Microphone in UNR"
date: 2009-06-12
forum: Hardware
---

### Post by Orbital_sFear on 2009-06-12
I like to use skype but found that it wouldn't work with the default installation of UNR on my EEE 1000 HE.

Here is what I did to fix it.
1. Open a terminal
2. cd /etc/rc2.d
3. sudo mv S50pulseaudio s50pulseaudio
4. reboot

My Mic now works using the HDA Intel (Alsa mixer).  I haven't found any side issues that this has caused but I haven't done much testing either.

I do with ubuntu.

---

### Post by chadk5utc on 2009-06-13
Hows your wireless work?
Have you noticed any speed issues?up/down



Chad




Asus 1000HE 32GB SSD 2GB RAM Eeebuntu 2.0 Plus Extras 100% Working

---

### Post by Orbital_sFear on 2009-06-13
wireless seems fine but I'd like to keep this thread talking about the mic.  Going on a wireless tangent wont help newbie's with mics that don't work

---

### Post by Orbital_sFear on 2009-06-13
Configuring Skype:

After turning off pulse audio skype still didn't work out of the box.  Here is what I did to fix it.

1. Open skype
2. Click Main Menu -> Options (Ctrl + O)
3. Click Sound Devices
4. Set all 3 options to HDA Intel (hw:Intel,0)
5. Click through the tests on there and things should be configured and working correctly

---

### Post by babooka on 2009-11-12
Doesn't seem to help on the fresh install of 9.10, 1005ha.

---

### Post by deanrd on 2009-11-27
Same thing for me - no mic still after above changes.  1005ha Asus
Works in XP so I know the mic is good, just not UNR.

Dean

---

### Post by babooka on 2009-11-30
Solved by installing karmic backports

---

### Post by completeidiot on 2009-12-29
I am also having the microphone problem in UNR Karmic Koala on my 1005ha. Most of the threads I am reading get off topic and onto wifi tangents so I'm still not clear on the real solution. Everyone seems to suggest installing backports. Which ones? In package manager there seems to be quite a few and I am hoping not to cause any additional problems, so far this is the only problem I have had.

---

### Post by completeidiot on 2009-12-29
also want mic to work in skype. but it doesn't even work in the sound recorder so far.
Thanks

---

### Post by babooka on 2009-12-29
> **completeidiot said:**
> I am also having the microphone problem in UNR Karmic Koala on my 1005ha. Most of the threads I am reading get off topic and onto wifi tangents so I'm still not clear on the real solution. Everyone seems to suggest installing backports. Which ones? In package manager there seems to be quite a few and I am hoping not to cause any additional problems, so far this is the only problem I have had.


That's what I've got:

root@weepc:~# dpkg --get-selections | grep backports
linux-backports-modules-alsa-2.6.31-16-generic	install
linux-backports-modules-alsa-karmic-generic	install

---

### Post by completeidiot on 2009-12-29
and that's how to fix it in terminal?

---

### Post by babooka on 2009-12-30
Oh.

Edit /etc/apt/sources.list.d/backports.list and add the following text




```
deb http://archive.ubuntu.com/ubuntu karmic-backports main universe multiverse restricted 
```



$ sudo gedit /etc/apt/sources.list.d/backports.list

update the apt db:
$ sudo apt-get update


install backports
$ linux-backports-modules-alsa-karmic-generic


Reboot

---

### Post by completeidiot on 2009-12-30
I did the installations mentioned in post #10 and that allowed me to record sound, but it's still not working in skype. It's showing pulseaudio as my input device. From what I have read cancelling pulse audio will cause all sorts of other problems. I would like to avoid that.
Also, you lost me in post 12

---

### Post by completeidiot on 2009-12-30
Problem solved
After doing the installations mentioned in post 10 and rebooting. All I had to do was go back to volume controls once again and increase microphone volume.....again

---

### Post by amillionsheep on 2010-01-11
I have an Acer AspireONE and am having the same issues. The internal Microphone works with the sound recorder but not with Skype. The only option I have in skype for sound input is 'PulseAudio Server'.

I did the steps above in Terminal and got the following:

> joshua@joshua-laptop:~$ sudo gedit /etc/apt/sources.list.d/backports.list
joshua@joshua-laptop:~$ sudo apt-get update
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Translation-en_US
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-backports Release.gpg [189B] 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-backports/main Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic Release.gpg                  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Translation-en_US       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Translation-en_US 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Translation-en_US   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Translation-en_US 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates Release.gpg          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-backports/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-backports/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-backports/restricted Translation-en_US
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-backports Release [37.1kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic Release                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates Release                                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Packages                                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Packages                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Sources                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Sources                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Packages                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Sources                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Packages        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Packages  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Sources         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Sources   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Packages    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Sources      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Packages   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Sources    
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-backports/main Packages [65.2kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Sources
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-backports/universe Packages [11.3kB]
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-backports/multiverse Packages [14B]
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-backports/restricted Packages [14B]
Fetched 114kB in 2s (47.5kB/s)
Reading package lists... Done
joshua@joshua-laptop:~$ linux-backports-modules-alsa-karmic-generic
linux-backports-modules-alsa-karmic-generic: command not found
Forgive my extreme nubness. :/

---

### Post by amillionsheep on 2010-01-11
I did the following and it looks as though it installed the packages.

sudo apt-get install linux-backports-modules-alsa-karmic-generic

I rebooted and still, internal microphone does not work with skype.

---

### Post by THEHiTechRedneck on 2010-01-12
I have UNR installed on an Acer Aspire One AOD250.

Being a complete Linux noob I Googled the Skype/mic issue and found the pulseaudio removal fix.  

sudo apt-get remove pulseaudio

Then rebooted.

The mic now works with Skype. However, the Sound Recorder is another issue. When selected I now get an error message that reads "Your audio capture settings are invalid. Please correct them with the Sound Preferences under the System-Preferences menu".  

When I then go to the Preferences panel and select "Sound" I got a new error message reading: "Waiting for sound system to respond." It never responds.

So far this seems to be the only pulseaudio removal issue I've come across but it doesn't mean there won't be more in the near future. However, since I use Skype daily and I've never yet used the sound recorder, maybe it's a decent trade-off?

Also, when I check the packages in the Package Manager, UNR is no longer showing as installed. Does this mean that removing pulseaudio somehow removes UNR? My desktop is functioning normally, as are all the other apps I use regularly (OO, .pdf viewer, etc.). It concerns me as I'm wondering if this changes how the update manager views the system.

It really would be nice if someone could post up a fool-proof solution to this annoying little mic issue. Otherwise UNR is awesome.

---

