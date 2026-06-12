---
title: "Dell Studio 15 No Sound"
date: 2008-09-25
forum: General Help
---

### Post by Blarion on 2008-09-25
I just installed Ubuntu onto my new Dell laptop, and I can't get any sound. Please help.

---

### Post by marioquark on 2008-10-10
i changed every output module in system - preferences - audio
to ALSA. it works (i hear low volume sounds...).
my headphones don't work. i'm finding a solution...

i wolud use pulseaudio engine, i'll try.
note that i'm using Intrepid Beta.

---

### Post by jmaygarden on 2008-10-18
I have the same problem. The volume is way too low on my Studio 15.

---

### Post by netpro25 on 2008-11-12
Use this script to update to xx.18a stable. This fixes the low volume issue on the Dell Studio Laptop. 

[http://ubuntuforums.org/showthread.php?t=962695](http://ubuntuforums.org/showthread.php?t=962695)

**Note:** Seems to be a bug with the headphone jack that was introduced in xx.18 that will be fixed in the .19 release. So keep the above page for reference to download an update script when xx.19 is released.

**For the Impatient (Like Me):**
If you can't wait for xx.19 then you can download an "ALSA fresh [Driver] snapshot" from the alsa site: [http://www.alsa-project.org/snapshot/](http://www.alsa-project.org/snapshot/), following the instructions in the INSTALL file (./configure, make, sudo make install, sudo ./snddevices, sudo alsa-utils, reboot) to compile from source. The latest version resolves all the headphone related issues, both jacks work properly and the sound is muted for speakers when headphones are plugged in.


Thanks,
Marcel

---

### Post by pspotts on 2008-12-30
Thanks for this. Got a new Studio 15 for Christmas and the sound problems were vexing...all better now!  ;-)

Pete

---

### Post by Mac Jingles on 2009-02-28
I have same issue, with same Dell Studio 15. Will try the script...

---

### Post by Benempire on 2009-03-07
Hello everyone,

I don't know if it was mentioned here before, but i'll give it a quick shot:

You can try to install OSS instead of alsa.

Go to:
[http://www.opensound.com/download.cgi](http://www.opensound.com/download.cgi)

Download the debian package (e.g. to your Desktop)
Install the package:
- go to download folder (cd /home/YOURNAME/Desktop/)
- sudo dpkg -i oss-linux-4.1-1051_i386.deb
Restart your system

Worked well on my Studio 15. Haven't checked mic though.

Good luck & good night,
Ben

PS: "sudo apt-get install oss-linux" might work aswell.
PS2: I tried the script. Didn't work on my machine.

---

### Post by WarWizard89 on 2009-07-04
After a clean install of Jaunty on a new Studio 15 I had a problem of having no sound at all.

I had to add the line "options snd-hda-intel model=dell-m6" to the file /etc/modprobe.d/alsa-base and it seems to work perfectly fine now.

I found instructions here. [https://help.ubuntu.com/community/HdaIntelSoundHowto]("https://help.ubuntu.com/community/HdaIntelSoundHowto")

The model you need to type in for your soundcard could be different from mine, but that page tells you how to find out the correct model if that one doesn't work.

Hope this is helpful for someone.

---

### Post by rapsodia on 2009-10-31
> **WarWizard89 said:**
> After a clean install of Jaunty on a new Studio 15 I had a problem of having no sound at all.

I had to add the line "options snd-hda-intel model=dell-m6" to the file /etc/modprobe.d/alsa-base and it seems to work perfectly fine now.

I found instructions here. [https://help.ubuntu.com/community/HdaIntelSoundHowto]("https://help.ubuntu.com/community/HdaIntelSoundHowto")

The model you need to type in for your soundcard could be different from mine, but that page tells you how to find out the correct model if that one doesn't work.

Hope this is helpful for someone.



Thank you for the info it worked great btw this is on my new dell studio 15 i7core 720  with soundcard High Definition Audio 2.2 

cat /proc/asound/card0/codec#* | grep Codec
this line gives me:

Codec: IDT 92HD73C1X5


hopefully this will help other people.

---

