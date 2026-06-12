---
title: "hda intel does not work after instalation"
date: 2007-06-11
forum: Hardware &amp; Laptops
---

### Post by kamwla on 2007-06-11
after successful installation of hda intel alsa drivers there is no sound 
when i try to open system>preferences>sound I get his message 
'
'The application "gnome-sound-properties" attempted to change an aspect of your configuration that your system administrator or operating system vendor does not allow you to change. Some of the settings you have selected may not take effect, or may not be restored next time you use the application.''

when i go to details i get 

Can't overwrite existing read-only value: Can't overwrite existing read-only value: Value for `/system/gstreamer/0.10/default/audiosink' set in a read-only source at the front of your configuration path
Any ideas how to deal with it :-(

---

### Post by kamwla on 2007-06-11
after successful installation of hda intel alsa drivers there is no sound
when i try to open system>preferences>sound I get his message
'
'The application "gnome-sound-properties" attempted to change an aspect of your configuration that your system administrator or operating system vendor does not allow you to change. Some of the settings you have selected may not take effect, or may not be restored next time you use the application.''

when i go to details i get

Can't overwrite existing read-only value: Can't overwrite existing read-only value: Value for `/system/gstreamer/0.10/default/audiosink' set in a read-only source at the front of your configuration path
Any ideas how to deal with it

---

### Post by froebi on 2007-06-11
Hi,

what type of sound card do you have? Do you have on-board sound? What chip set?

I had problems with the hda-intel driver as well. The driver knows different models. And it makes a big difference which model you choose. Of course the model depends on your card. I had to build and install the alsa-stuff. See this howto for instructions: [HdaIntelSoundHowto]("https://help.ubuntu.com/community/HdaIntelSoundHowto").

btw. I have on-board sound. My chip set is realtek alc660. I use model 3stack-660.

cheers,
  Christian

---

### Post by kamwla on 2007-06-11
I use Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller on Toshiba P100-188 i have installed alsa drivers before. therefore I doubt weather the problem is in drivers. It seems like the installation did not update audiosink as it is set as read only. I have tried everything without any result :-(

---

### Post by froebi on 2007-06-12
Hmm, sorry, I don't have any experience with this card.

Did you try every model possible for the hda-intel driver?

Did you scan dmesg output for error messages while loading the hda-intel module?

Otherwise I'm out of ideas.

Christian

---

