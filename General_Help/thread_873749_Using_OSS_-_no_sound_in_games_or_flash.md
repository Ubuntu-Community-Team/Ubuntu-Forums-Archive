---
title: "Using OSS - no sound in games or flash"
date: 2008-07-29
forum: General Help
---

### Post by Steve Roderick on 2008-07-29
Hello, I'm fairly new to Linux/Ubuntu. I have a Soundblaster x-fi ExtremeGamer card. I followed the instructions here: [http://ubuntuforums.org/showpost.php?p=4874981&postcount=2](http://ubuntuforums.org/showpost.php?p=4874981&postcount=2), to get sound enabled through OSS instead of Alsa. It worked for desktop sounds and music but I'm still getting no sound in games or flash.

I also have an onboard soundcard but I don't know how to setup up linux to use it (as a last resort in case I can't get my soundblaster x-fi to work).

Can somebody please help? Thanks.

---

### Post by cronholio on 2008-07-29
So you didn't have any sound from Flash or games using ALSA, or why did you choose to use OSS?

---

### Post by Steve Roderick on 2008-07-29
Apparently Alsa doesn't yet support x-fi cards. So I followed some tutorials to install OSS instead because it has support for these cards.

It worked for regular desktop sounds, music and movies, but I can't get the sound to work in games (ie: scummvm, zsnes) or Flash. ???

---

### Post by cronholio on 2008-07-29
This may help: [http://joey.ubuntu-rocks.org/blog/2007/11/18/sound-with-oss-pa-flash/]("http://joey.ubuntu-rocks.org/blog/2007/11/18/sound-with-oss-pa-flash/").

---

### Post by Steve Roderick on 2008-07-29
Thanks for your help, but the problem still persists. I installed libflashsupport (OSS version) but I still can't get any sound from flash or games.

---

### Post by papsynot on 2008-07-29
I think you should install libsdl1.2debian-oss package for sound in games. Flash needs libflashsupport which should be provided by installing flashplugin-nonfree-extrasound.

---

### Post by AhmedSoliman on 2008-07-31
I have the same problem exactly! please suggest a solution...

---

### Post by Shakaboom on 2008-08-27
I too have x-fi and am forced to use OSS. I got the flash sound working after uninstalling flashplugin non-free from the repository and installing flash 9 from the tarball from adobe. 

It still gave very bad performance on full screen though, so i decided to try flash 10 beta. It made all flash play at fast-forward speed, including chipmunk sound. So i removed libflashplayer.so from ~./mozilla and reinstalled flash 9.

After this, there was no sound at all anymore, ive tried to uninstall as clean as i could and reinstall over and over again, but still no sound anymore! Please help!

---

### Post by Yellow Pasque on 2008-08-27
1. Some users are getting confused with the libflashsupport package available in the Ubuntu repo. That version is for ALSA+PulseAudio and you should remove it (with Synaptic GUI or apt-get remove)
2. Save this: [http://ubuntuforums.org/attachment.php?attachmentid=69426&stc=1&d=1219884013](http://ubuntuforums.org/attachment.php?attachmentid=69426&stc=1&d=1219884013) to your Desktop
3. Run these commands
```
cd ~/Desktop
gunzip libflashsupport.so.gz
sudo mv libflashsupport.so /usr/lib
sudo ln -s /usr/lib/libflashsupport.so /usr/lib/firefox/plugins
sudo ln -s /usr/lib/libflashsupport.so /usr/lib/mozilla/plugins
sudo ln -s /usr/lib/libflashsupport.so /usr/lib/firefox-addons/plugins
```
If you're running 64-bit :
```
sudo cp /usr/lib/libflashsupport.so /usr/lib32/
```
7. If you're still having issues, see this: [http://ubuntuforums.org/showpost.php?p=5374886&postcount=273](http://ubuntuforums.org/showpost.php?p=5374886&postcount=273)

For zsnes, make sure your zsnes launcher uses "zsnes -ad oss" for the best performance or do as a previous poster suggested and get the SDL-OSS library package

---

### Post by TinkerJ on 2008-08-31
This works! This is the solution!

Just excited to finally get sound back in flash after switching to OSS4.
Just wish I could get the volume keys working...

---

### Post by Yellow Pasque on 2008-08-31
TinkerJ, your volume keys should work if you have the patched libgstoss.so
Are you running x86 or amd64 Ubuntu?

There was a note at the end of the OSS4 guide about this. I re-did the guide in Ubuntu Documentaion format to make things easier to find.
[https://help.ubuntu.com/community/OpenSound#The%20GNOME%20Mixer/Volume%20Control](https://help.ubuntu.com/community/OpenSound#The%20GNOME%20Mixer/Volume%20Control)

---

### Post by thomosnr on 2008-10-12
Great....it worked perfectly!

---

### Post by David Brant on 2009-05-08
This worked for me too. :)

[http://ubuntuforums.org/showthread.php?t=1145116](http://ubuntuforums.org/showthread.php?t=1145116)

I'm still not sure what it is i'm running with (OSS or ALSA) because i have to set everything to OSS in sysyem/preference/sounds to satisfy desktop sounds, music and flash even though i can run with the ALSA or OSS mixer. I selected ALSA, only because it has more options.

---

### Post by datacrusher on 2009-08-18
well, i followed the steps and now i got sound on youtube, but only using opera browser. on firefox the video is chunky, with no sound. 

how do i use the same plugin of opera to firefox? im using firefox 3.0.12

---

### Post by lestatius on 2009-10-12
I just installed ubuntu 64 bit and I got the normal sound to work, but I haven't been able to get the flash sound to work, after having followed this guide. Am I missing something?

---

### Post by mrwoc on 2010-06-03
> **Temüjin said:**
> 1. Some users are getting confused with the libflashsupport package available in the Ubuntu repo. That version is for ALSA+PulseAudio and you should remove it (with Synaptic GUI or apt-get remove)
2. Save this: [http://ubuntuforums.org/attachment.php?attachmentid=69426&stc=1&d=1219884013](http://ubuntuforums.org/attachment.php?attachmentid=69426&stc=1&d=1219884013) to your Desktop
3. Run these commands
```
cd ~/Desktop
gunzip libflashsupport.so.gz
sudo mv libflashsupport.so /usr/lib
sudo ln -s /usr/lib/libflashsupport.so /usr/lib/firefox/plugins
sudo ln -s /usr/lib/libflashsupport.so /usr/lib/mozilla/plugins
sudo ln -s /usr/lib/libflashsupport.so /usr/lib/firefox-addons/plugins
```
If you're running 64-bit :
```
sudo cp /usr/lib/libflashsupport.so /usr/lib32/
```
7. If you're still having issues, see this: [http://ubuntuforums.org/showpost.php?p=5374886&postcount=273](http://ubuntuforums.org/showpost.php?p=5374886&postcount=273)

For zsnes, make sure your zsnes launcher uses "zsnes -ad oss" for the best performance or do as a previous poster suggested and get the SDL-OSS library package

Thank you so much, this worked perfectly, i spent ages trying to get flash to work, and you solved my problem :)

---

### Post by OmegaPhil on 2010-07-16
Thanks Temüjin, this makes flash in Opera usable for me (was contemplating gnash in Firefox with some hacks for Youtube).

---

### Post by Totoyo on 2010-12-11
Thank you so much~~ Temüjin
It works for me`~~ ^^

---

