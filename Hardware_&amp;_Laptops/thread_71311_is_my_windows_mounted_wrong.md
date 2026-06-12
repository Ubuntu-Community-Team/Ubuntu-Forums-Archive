---
title: "is my windows mounted wrong?"
date: 2005-10-02
forum: Hardware &amp; Laptops
---

### Post by siku on 2005-10-02
I mounted my windows ntfs partition as per the starters guide:
/dev/hda1       /media/windows  ntfs    nls=utf8,umask=0222 0       0
is what my fstab file reads for the windows partition.
When I try to play songs in the windows partition this is what Rhythmbox tells me:
> ERROR LOADING FILES INTO LIBRARY
This file is not an audio stream:

The file in question is an .mp3 file that I can play in windows?

---

### Post by aysiu on 2005-10-02
Did you reboot after editing your /etc/fstab?

Or you can do this [http://ubuntuguide.org/#remountfstabwithoutreboot](http://ubuntuguide.org/#remountfstabwithoutreboot)

---

### Post by siku on 2005-10-02
yeap,
i did 
umount /dev/hda1
mount /dev/hda1

---

### Post by aysiu on 2005-10-02
[QUOTE=siku]yeap,
i did 
umount /dev/hda1
mount /dev/hda1[/QUOTE] What's this? I meant rebooting the entire computer.

---

### Post by matthew on 2005-10-02
It sounds like your partition is mounted just fine, but that rhythmbox is not recognizing your mp3's as music files. To confirm, go to Places->Computer and look in /media/windows see if the ntfs partitions files are listed. If they are, then the partition is mounted correctly.

My guess is that you need the proper codecs installed to be able to play mp3s in linux. See this page for more info:
[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

---

### Post by codejunkie on 2005-10-03
[QUOTE=siku]yeap,
i did 
umount /dev/hda1
mount /dev/hda1[/QUOTE]
if you can read files from your windows harddrive and there are no warning messages when you boot your computer then your windows partition is mounted correctly. the reason that your not able to play that .mp3 file is ubuntu does not support .mp3's out of the box because of copyright restrictions you have to add playback support you have to follow the guide at [http://ubuntuguide.org/](http://ubuntuguide.org/) to add the extra repositories then open a terminal then copy and paste these codes in there. 
```
sudo apt-get update
```
```
sudo apt-get install gstreamer0.8-plugins totem-xine
```
then 
```
gst-register-0.8
```
let me know if you have any trouble with it and i'll try and help you out.

---

### Post by siku on 2005-10-03
[QUOTE=codejunkie]if you can read files from your windows harddrive and there are no warning messages when you boot your computer then your windows partition is mounted correctly. the reason that your not able to play that .mp3 file is ubuntu does not support .mp3's out of the box because of copyright restrictions you have to add playback support you have to follow the guide at [http://ubuntuguide.org/](http://ubuntuguide.org/) to add the extra repositories then open a terminal then copy and paste these codes in there. 
```
sudo apt-get update
```
```
sudo apt-get install gstreamer0.8-plugins totem-xine
```
then 
```
gst-register-0.8
```
let me know if you have any trouble with it and i'll try and help you out.[/QUOTE]


I think you are probably right, even though I haven't tried what you have said.
This is because I am able to play those songs in xmms.
So I guess it's the rhytmbox thing.
thanks all

---

### Post by siku on 2005-10-03
Thanks that works.
This might be another topic, but I have commented out the backports line
> ## Backports
#deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
#deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted
uncommenting these two lines gave me an error on apt-get update. So I just removed them.
Is it because eI am using breezy and not hoary

---

### Post by matthew on 2005-10-03
[quote=siku]Thanks that works.
This might be another topic, but I have commented out the backports line

uncommenting these two lines gave me an error on apt-get update. So I just removed them.
Is it because eI am using breezy and not hoary[/quote]
There are 2 things happening here.
1. there are no backports for Breezy so these lines aren't needed. What backports are are programs being developed for the latest version of Ubuntu and then set up to be used on the next oldest version. Breezy is still under development so new program versions being used for Breezy are being "backported" for use in Hoary.
2. One of the lines you have above is no longer valid as the backports server has changed...that wouldn't affect you anyway since you are using Breezy. Once the next version begins development watch for info on where/how to enable backports from it to Breezy. For the time being this won't be important for you.

---

