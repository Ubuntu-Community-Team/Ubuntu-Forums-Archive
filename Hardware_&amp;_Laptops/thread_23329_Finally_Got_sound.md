---
title: "Finally Got sound"
date: 2005-04-01
forum: Hardware &amp; Laptops
---

### Post by lanji on 2005-04-01
after 2 week of trying and searching finally got my Sblive 24bit sound card to work 
with help from this post [http://www.ubuntuforums.org/showthread.php?t=21211](http://www.ubuntuforums.org/showthread.php?t=21211)


 cd /usr/src
sudo wget [ftp://ftp.alsa-project.org/pub/driv...r-1.0.9rc2.tar.bz2](ftp://ftp.alsa-project.org/pub/driv...r-1.0.9rc2.tar.bz2)
tar xvjf alsa-driver-1.0.9rc2.tar.bz2
cd alsa-driver-1.0.9ec2
sudo ./configure --with-cards=ca0106 --with-sequencer=yes;make;make instal

after then type
sudo nano /etc/modules
add in

snd-pcm-oss
snd-emu10k1
snd-mixer-oss
then hit Ctrl O to save the setting
Then reboot your pc you should have sound. You might have to run alsamixer after 

but there is a problem is that the sound is so chopy and slow, it  delay so much when i play MP3 sound from hard drive.

is there any solution to fix that problem?

---

