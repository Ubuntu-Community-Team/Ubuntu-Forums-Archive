---
title: "ASUS F8SG using Ubuntu"
date: 2008-10-01
forum: Hardware
---

### Post by Ng Oon-Ee on 2008-10-01
Just bought one of these, have it running fully on Ubuntu. 32-bit Hardy (I really should try 64-bit one day, but no guts currently, this is a workhorse machine here).

I couldn't really find much help about this model through mr Google, so I thought I'd just post about my main problem, getting the nVidia 9300M to work.

Basically, I had to remove all traces of the Hardy restricted hardware drivers through synaptic (search nvidia and remove all), and then use EnvyNG to install the latest drivers (auto-detect doesn't work with EnvyNG, you have to manually install). I think its the 173.14.12 driver currently.

Anyway, if anyone has issues with the ASUS F8SG, feel free to ask here. I know I would have appreciated someone having previously posted this up =). I presume all ASUS F8 series notebooks would be similar as well, except for the graphics card.

P.S - the only feature not working on this model is the fingerprint reader (or at least, that I couldn't get to work, didn't really try very hard to be fair, its just a waste of space IMHO).

---

### Post by simplesnake on 2008-11-21
Have you had the chance to try a live 64 bit Ubuntu or any other 64 bit distro?

---

### Post by Ng Oon-Ee on 2008-11-21
Ah, you have this laptop as well?

I'm running 64-bit Intrepid currently, no big problems, what I had was easily addressed through this forum. I'd be willing to share the specific steps I took to get this guy up and running, if anyone is interested.

---

### Post by simplesnake on 2008-11-24
I was actually considering buying either the N80Vn-X1 or the F8Sp-X1. Both have similar architecture so I figured if a F8 series could run 64 bit the others could too. I am interested in the "steps" you had to take however.

---

### Post by Ng Oon-Ee on 2008-11-24
Okay, for a bit more background, then, I do some amateur recordings and editing so I'm using Ubuntu Studio, 64 bit. Which is just 64 bit Ubuntu with some other programs, an RT kernel (which doesn't work for 8.10, but nevermind), JACK, and nice themes. Basically meaning, no big difference :).

Anyway, here's my personal notes on what I would have to do to get my system back to this state. Some of this stuff is personal to me and not necessary for everyone. This isn't specifically for 64-bit, however, there are specific 64-bit things somewhere here.

```
Re-modify /etc/fstab
Also, install samba and smbfs from the repositories for windows networking
```
This is done because I have a dual-boot setup. Basically I modify fstab so that I can mount my shared data drive in a particular location, with full permissions, and samba/smbfs allow me to connect to shared drives in my office.

```
Setup Nautilus bookmarks

Install EnvyNG-core (GTK was deprecated somehow)
Run in terminal, select 177. driver.
Restart needed at this point.
```
The bookmarks are for my own navigation to certain key directories (I don't use the home folder much, use my shared drive for everything). I use EnvyNG to install the proprietary nvidia drivers.

```
Install compizconfig-settings-manager, emerald, fusion-icon
Add trunk PPA for Avant
deb http://ppa.launchpad.net/awn-testing/ubuntu intrepid main
deb-src http://ppa.launchpad.net/awn-testing/ubuntu intrepid main
Install all contents

Install pidgin, pidgin-guifications, thunderbird, add the multi-platform lightning add-on

Install sun-java6-bin and sun-java6-fonts for Java, flashplugin-nonfree for Flash
```
Some software I use. I prefer the trunk repo for Avant because they have nicer and more up-to-date applets. I use Pidgin, Thunderbird, and Firefox both in Windows and Linux, with shared profiles on my shared drive (lightning is platform specific but can be shared as well, I followed a guide on how to do that. Its in their wiki). The java I've installed is for Eclipse IDE (my programming environment) and Matlab, SOME java webpages don't work, but not a biggie for me. Iced Java works, in this case, but its slower for actually running apps. You can have both installed and can select specifics for each app, I believe. Flash is for flash, of course.

```
Install developmental Wine using
wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -
sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/intrepid.list -O /etc/apt/sources.list.d/winehq.list
Or refer to http://www.winehq.org/site/download-deb
Also alsa-oss from repositories. This is 64-bit, so you need to download the 32-bit alsa-oss from packages.ubuntu.com, extract the /lib files to /usr/lib32
```
This is the most 64-bit specific part. I use the latest Wine just to report bugs (haven't found any yet) with the programs I use (mainly games, and esword). Alsa-oss is the best way to get sound through pulseaudio from Wine, but 64-bit doesn't play nice with 32-bit wine, so I install the 32-bit Alsa-oss. Wine doesn't come in 64-bit, but can be installed anyway. Lots of dependencies though.

```
Install Unison 2.27.57 from the repositories
```
I use this program for backup and synchronization. Very recommended. Multi-platform as well.

```
Setup Vista fonts using vista-fonts-installer.sh and setup proper smoothing using the appropriate .fonts.conf (or copy .fonts.conf and symlink to existing .fonts folder)

Add medibuntu repository using
sudo wget http://www.medibuntu.org/sources.list.d/intrepid.list -O /etc/apt/sources.list.d/medibuntu.list
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

Install build-essential, googleearth-*.*, skype, msttcorefonts, firestarter, gparted, grsync, cheese, rar, p7zip-full, w64codecs, gstreamer0.10-plugins-ugly, gstreamer0.10-plugins-bad, amarok, libxine1-allplugins, totem-xine, gnome-do
```
These are proprietary stuff I add. Vista fonts I got from a guide in these forums, makes Openoffice more compatible. I use google earth extensively, and the rest are programs (and codecs/audio) that I use often.

```
Edit xorg.conf adding SHMConfig option for touchpad and multi-display settings. Also add the following two lines to /etc/udev/rules.d/10-local.rules for mouse plugin/out to turn off/on the touchpad.
ACTION=="add", SUBSYSTEM=="input", ID_CLASS="mouse", RUN+="/usr/bin/synclient TouchpadOff=1"
ACTION=="remove", SUBSYSTEM=="input", ID_CLASS="mouse", RUN+="/usr/bin/synclient TouchpadOff=0"
```
Basically allows my touchpad to be turned off. If you're interested in this I can post up my xorg.conf.

```
Follow the guide to compile FFmpeg from source. Follow the steps in the "Modified..." file.

Install openoffice.org, openclipart-openoffice.org, gnumeric

Follow the guide under "Multiple Sound Solution" for running jack with Pulseaudio. Add the following lines to /etc/security/limits.conf
@audio          -       rtprio          99
@audio	-	nice	-10
@audio	-	memlock	452192
Add your user to the audio and pulse-rt groups

Setup readahead for shorter login time.
```
Some other stuff. I use ffmpeg for video/audio conversion often, and need an un-stripped version, hence the need to compile from source. There is a guide in these forums for setting up Jack and Pulseaudio properly, which I use since I do audio recording. Readahead is something I just found, cuts almost half a mintue off my login time.



Now that I've looked back through that, nothing much different with 64-bit setup, really. Issues with Wine (only 32-bit) and Firefox plugins (flash and java) are really the only things I've come across, both easily solvable.

---

### Post by simplesnake on 2008-12-05
Thanks for all of that, I am please to say my new ASUS F8VA-B1 is running Ubuntu 8.10 64 bit. 

For those having a white screen issue with a fresh install, try installing 8.04 64 bit first, next install ati-graphics drivers, then do a distro upgrade. 

Sound still needs some tweaking though, in /etc/modprobe.d/alsa-base you'll need to add the line options snd-hda-intel model=m51va and reboot.

My only issue left is the under powered wireless card, the AzureWave AR5B91. The card was recognized under 8.10 but I have to sit right next to my wireless router to get anything over 60% signal strength. Thoughts from anyone?

---

### Post by Ng Oon-Ee on 2008-12-05
> **simplesnake said:**
> Thanks for all of that, I am please to say my new ASUS F8VA-B1 is running Ubuntu 8.10 64 bit. 

For those having a white screen issue with a fresh install, try installing 8.04 64 bit first, next install ati-graphics drivers, then do a distro upgrade. 

Sound still needs some tweaking though, in /etc/modprobe.d/alsa-base you'll need to add the line options snd-hda-intel model=m51va and reboot.

My only issue left is the under powered wireless card, the AzureWave AR5B91. The card was recognized under 8.10 but I have to sit right next to my wireless router to get anything over 60% signal strength. Thoughts from anyone?

Ah, maybe you could detail what was the problem with sound that was solved by that step. Wouldn't want any1 to just apply it to generically solve any sound problem, after all (in my experience its mainly problems with Pulse/Flash/proprietary codecs rather than sound drivers, except in some cases like yours).

As for the wireless card, I have had no problems with mine so far, its an Intel wireless though. Would suggest posting a new thread to ask that, as I doubt many read this particular thread who know how to diagnose it.

---

### Post by simplesnake on 2008-12-08
I do tend to get ahead of myself from time to time. The alsa based sound did not work at all. Adding this option comes from searching other sources, I don't take credit for it.

---

